---
redirect_from:
  - '/download/'
layout: new-layouts/install
title: 安装 Swift - Windows
---

{% assign windows_dev_builds = site.data.builds.development.windows10 | sort: 'date' | reverse %}
{% assign windows_arm64_dev_builds = site.data.builds.development.windows10-arm64 | sort: 'date' | reverse %}
{% assign windows10_6_1_builds = site.data.builds.swift-6_1-branch.windows10 | sort: 'date' | reverse %}
{% assign windows10_arm64_6_1_builds = site.data.builds.swift-6_1-branch.windows10-arm64 | sort: 'date' | reverse %}
{% assign tag = site.data.builds.swift_releases.last.tag %}
{% assign platform = site.data.builds.swift_releases.last.platforms | where: 'name', 'Windows 10' | first %}

<div class="content">
  <div class="release-box section">
    <div class="content">
      {% include new-includes/components/code-box.html content = site.data.new-data.install.windows.releases.latest-release.winget %}
    </div>
  </div>
  <h2>其他安装选项</h2>
  <div class="releases-grid">
    <div class="release-box section">
      <div class="content">
        <div class="code-box content-wrapper">
          <h2>手动安装</h2>
          <p class="body-copy">
            下载 Swift 安装程序 (.exe)
          </p>
          <div class="link-wrapper">
            {% for arch in platform.archs %}
              <div class="link-single">
                <a href="https://download.swift.org/{{ tag | downcase }}/windows10{% if arch != "x86_64" %}-{{ arch }}{% endif %}/{{ tag }}/{{ tag }}-windows10{% if arch != "x86_64" %}-{{ arch }}{% endif %}.exe" class="body-copy">下载 ({{ arch }})</a>
              </div>
            {% endfor %}
            <div class="link-single">
              <a href="/install/windows/manual" class="body-copy">安装说明</a>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="release-box section">
      <div class="content">
        <div class="code-box content-wrapper">
          <h2>容器</h2>
          <p class="body-copy">
            官方容器镜像可用于在各种发行版上编译和运行 Swift。
          </p>
          <div class="link-wrapper">
            <div class="link-single">
              <a href="https://hub.docker.com/_/swift" class="body-copy">{{ site.data.builds.swift_releases.last.name }}-windowsservercore-ltsc2022</a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
  <h2>历史版本</h2>
  <div>
    <p class="content-copy">可以使用手动安装程序安装 Windows 上的 Swift 历史版本，<a href="/install/windows/archived">详细说明请点击这里</a>。</p>
  </div>
  <div class="release-box section">
    <div class="content">
        <details class="download" style="margin-bottom: 0;">
        <summary>历史版本</summary>
        {% include install/_older-releases.md platform="Windows 10" %}
        </details>
    </div>
  </div>
  <h2>开发快照</h2>
  <div>
    <p class="content-copy">Swift 快照是从分支自动创建的预构建二进制文件。这些快照不是官方发布版本。它们已经通过了自动化单元测试，但尚未经过官方发布所需的完整测试。</p>
  </div>
  <div>
    <p class="content-copy">
      <a class="content-link" href="/install/windows/manual/">安装说明</a>
    </p>
  </div>
  <div class="releases-grid">
    <div class="release-box section">
      <div class="content">
        <div class="code-box content-wrapper">
          <h2>main</h2>
          <p class="body-copy">
            <small>{{ windows_dev_builds.first.date | date: '%B %-d, %Y' }}</small><br />
            安装包 (.exe)
          </p>
          <div class="link-wrapper">
            <div class="link-single">
              <a href="https://download.swift.org/development/windows10/{{ windows_dev_builds.first.dir }}/{{ windows_dev_builds.first.download }}" class="body-copy">下载 (x86_64)</a>
            </div>
            <div class="link-single">
              <a href="https://download.swift.org/development/windows10-arm64/{{ windows_arm64_dev_builds.first.dir }}/{{ windows_arm64_dev_builds.first.download }}" class="body-copy">下载 (arm64)</a>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="release-box section">
      <div class="content">
        <div class="code-box content-wrapper">
          <h2>release/6.1</h2>
          <p class="body-copy">
            <small>{{ windows10_6_1_builds.first.date | date: '%B %-d, %Y' }}</small><br />
            安装包 (.exe)
          </p>
          <div class="link-wrapper">
            <div class="link-single">
              <a href="https://download.swift.org/swift-6.1-branch/windows10/{{ windows10_6_1_builds.first.dir }}/{{ windows10_6_1_builds.first.download }}" class="body-copy">下载 (x86_64)</a>
            </div>
            <div class="link-single">
              <a href="https://download.swift.org/swift-6.1-branch/windows10-arm64/{{ windows10_arm64_6_1_builds.first.dir }}/{{ windows10_arm64_6_1_builds.first.download }}" class="body-copy">下载 (arm64)</a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
  <div class="release-box section">
    <div class="content">
        <details class="download">
        <summary>历史快照 (main)</summary>
        {% include install/_older_snapshots.md builds=windows_dev_builds name="windows" platform_dir="windows10" branch_dir="development" %}
        </details>
    </div>
  </div>
  <div class="release-box section">
    <div class="content">
        <details class="download">
        <summary>历史快照 (release/6.1)</summary>
        {% include install/_older_snapshots.md builds=windows10_6_1_builds name="windows" platform_dir="windows10" branch_dir="swift-6.1-branch" %}
        </details>
    </div>
  </div>
</div>
