---
redirect_from: "server/guides/packaging"
layout: page
title: 将应用程序打包以供部署
---

一旦应用程序为生产环境构建完成，它仍然需要打包才能部署到服务器上。有几种策略可以用于打包 Swift 应用程序以进行部署。

## Docker

如今，使用容器技术（如 [Docker](https://www.docker.com)）打包应用程序是最流行的方法之一。

使用 Docker 的工具，我们可以将应用程序构建并打包为 Docker 镜像，将其发布到 Docker 仓库，然后直接在服务器上或支持 Docker 部署的平台（如 [Kubernetes](https://kubernetes.io)）上启动它。包括 AWS、GCP、Azure、IBM 在内的许多公共云提供商都鼓励这种部署方式。

下面是一个在 CentOS 上构建和打包应用程序的 `Dockerfile` 示例：


```Dockerfile
#------- build -------
FROM swift:centos8 as builder

# 设置工作区
RUN mkdir /workspace
WORKDIR /workspace

# 将源代码复制到 docker 镜像
COPY . /workspace

RUN swift build -c release --static-swift-stdlib

#------- package -------
FROM centos
# 复制可执行文件
COPY --from=builder /workspace/.build/release/<executable-name> /

# 设置入口点（应用程序名称）
CMD ["<executable-name>"]
```

要使用 `Dockerfile` 从应用程序的源位置创建本地 Docker 镜像，请使用 `docker build` 命令，例如：

```bash
$ docker build . -t <my-app>:<my-app-version>
```

要测试本地镜像，请使用 `docker run` 命令，例如：

```bash
$ docker run <my-app>:<my-app-version>
```

最后，使用 `docker push` 命令将应用程序的 Docker 镜像发布到您选择的 Docker 仓库，例如：

```bash
$ docker tag <my-app>:<my-app-version> <docker-hub-user>/<my-app>:<my-app-version>
$ docker push <docker-hub-user>/<my-app>:<my-app-version>
```

此时，应用程序的 Docker 镜像已准备好部署到运行 docker 的服务器主机，或支持 Docker 部署的平台。

有关 Docker 的更多完整信息，请参阅 [Docker 的文档](https://docs.docker.com/engine/reference/commandline/)。


### Distroless

[Distroless](https://github.com/GoogleContainerTools/distroless) 是 Google 的一个项目，旨在创建仅包含应用程序及其运行时依赖项的最小镜像。它们不包含包管理器、shell 或任何其他您期望在标准 Linux 发行版中找到的程序。

由于 distroless 支持 Docker 并基于 Debian，在其上打包 Swift 应用程序与上述 Docker 过程非常相似。下面是一个在 distroless 的 C++ 基础镜像上构建和打包应用程序的 `Dockerfile` 示例：

```Dockerfile
#------- build -------
# 使用 Ubuntu Bionic 构建，因为它与 Debian 运行时兼容
FROM swift:bionic as builder

# 设置工作区
RUN mkdir /workspace
WORKDIR /workspace

# 将源代码复制到 docker 镜像
COPY . /workspace

RUN swift build -c release --static-swift-stdlib

#------- package -------
# 在 distroless C++ 上运行，因为它包含
# Swift 程序需要的所有(*)运行时依赖项
FROM gcr.io/distroless/cc-debian10
# 复制可执行文件
COPY --from=builder /workspace/.build/release/<executable-name> /

# 设置入口点（应用程序名称）
CMD ["<executable-name>"]
```

注意，上述使用 `gcr.io/distroless/cc-debian10` 作为运行时镜像，这对于不使用 `FoundationNetworking` 或 `FoundationXML` 的 Swift 程序应该有效。为了提供更完整的支持，我们（社区）可以向 distroless 提交 PR，引入一个包含 `libcurl` 和 `libxml` 的 Swift 基础镜像，分别用于 `FoundationNetworking` 和 `FoundationXML`。


## Archive (Tarball, ZIP file, etc.)

由于在 Mac 或 Windows 上不（尚未）支持交叉编译 Swift 到 Linux，我们需要使用虚拟化技术（如 Docker）来编译我们目标运行在 Linux 上的应用程序。

这并不意味着我们必须将应用程序也打包为 Docker 镜像才能部署。虽然使用 Docker 镜像进行部署方便且流行，但应用程序也可以使用简单且轻量的归档格式（如 tarball 或 ZIP 文件）打包，然后上传到服务器，在服务器上解压并运行。

以下是使用 Docker 和 `tar` 构建和打包应用程序以在 Ubuntu 服务器上部署的示例：

首先，从应用程序的源位置使用 `docker run` 命令构建它：

```bash
$ docker run --rm \
  -v "$PWD:/workspace" \
  -w /workspace \
  swift:bionic \
  /bin/bash -cl "swift build -c release --static-swift-stdlib"
```

注意，我们正在绑定挂载源目录，以便构建将构建工件写入本地驱动器，我们稍后将从中打包它们。

接下来，我们可以创建一个包含应用程序可执行文件的暂存区：


```bash
$ docker run --rm \
  -v "$PWD:/workspace" \
  -w /workspace \
  swift:bionic  \
  /bin/bash -cl ' \
     rm -rf .build/install && mkdir -p .build/install && \
     cp -P .build/release/<executable-name> .build/install/'
```

注意，此命令可以与上面的构建命令结合使用——我们将它们分开以使示例更具可读性。

最后，从暂存目录创建一个 tarball：

```bash
$ tar cvzf <my-app>-<my-app-version>.tar.gz -C .build/install .
```

我们可以通过将 tarball 解压到目录并在 Docker 运行时容器中运行应用程序来测试 tarball 的完整性：

```bash
$ cd <extracted directory>
$ docker run -v "$PWD:/app" -w /app bionic ./<executable-name>
```

可以使用 `scp` 等工具将应用程序的 tarball 部署到目标服务器，或者在更复杂的设置中使用配置管理系统（如 `chef`、`puppet`、`ansible` 等）。


## 源分发

Another distribution technique popular with dynamic languages like Ruby or Javascript is distributing the source to the server, then compiling it on the server itself.

To build Swift applications directly on the server, the server must have the correct Swift toolchain installed. [Swift.org](/download/#linux) publishes toolchains for a variety of Linux distributions, make sure to use the one matching your server Linux version and desired Swift version.

The main advantage of this approach is that it is easy. Additional advantage is the server has the full toolchain (e.g. debugger) that can help troubleshoot issues "live" on the server.

The main disadvantage of this approach that the server has the full toolchain (e.g. compiler) which means a sophisticated attacker can potentially find ways to execute code. They can also potentially gain access to the source code which might be sensitive. If the application code needs to be cloned from a private or protected repository, the server needs access to credentials which adds additional attack surface area.

In most cases, source distribution is not advised due to these security concerns.

另一种在动态语言（如 Ruby 或 Javascript）中流行的分发技术是将源代码分发到服务器，然后在服务器上编译。

要直接在服务器上构建 Swift 应用程序，服务器必须安装正确的 Swift 工具链。[Swift.org](https://www.swift.org/download/#linux) 发布了适用于各种 Linux 发行版的工具链，请确保使用与您的服务器 Linux 版本和所需 Swift 版本匹配的工具链。

这种方法的主要优点是简单。额外的优点是服务器具有完整的工具链（例如调试器），可以帮助在服务器上“实时”排除问题。

这种方法的主要缺点是服务器具有完整的工具链（例如编译器），这意味着复杂的攻击者可能会找到执行代码的方法。他们还可能获得对源代码的访问权限，这可能是敏感的。如果应用程序代码需要从私有或受保护的存储库中克隆，服务器需要访问凭据，这增加了额外的攻击面。

在大多数情况下，由于这些安全问题，不建议使用源代码分发。

## 静态链接和 Curl/XML

**注意：** 如果您使用 `-static-stdlib` 编译并使用 Curl 与 FoundationNetworking 或 XML 与 FoundationXML，您必须在目标系统上安装 libcurl 和/或 libxml2 才能使其工作。