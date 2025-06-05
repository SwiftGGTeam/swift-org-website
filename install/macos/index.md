---
redirect_from:
  - '/download/'
layout: new-layouts/install
title: 安装 Swift - macOS
---

{% assign xcode_dev_builds = site.data.builds.development.xcode | sort: 'date' | reverse %}
{% assign xcode_6_2_builds = site.data.builds.swift-6_2-branch.xcode | sort: 'date' | reverse %}

<div class="content">
  <div class="release-box section">
    <div class="content">
      {% include new-includes/components/code-box.html with-tabs = true content = site.data.new-data.install.macos.releases.latest-release.swiftly%}
    </div>
  </div>
  <div class="release-box section">
    <div class="content">
      {% include new-includes/components/code-box.html content = site.data.new-data.install.macos.releases.latest-release.xcode%}
    </div>
  </div>
  <div class="releases-grid">
    <div class="release-box section">
      <div class="content">
        <div class="code-box content-wrapper">
          <h2>包安装程序</h2>
          <p class="body-copy">
            Swiftly 自动化的工具链包安装程序 (.pkg) 可作为独立下载使用。
          </p>
          <div class="link-wrapper">
            <a href="https://download.swift.org/{{ site.data.builds.swift_releases.last.tag | downcase }}/xcode/{{ site.data.builds.swift_releases.last.tag }}/{{ site.data.builds.swift_releases.last.tag }}-osx.pkg" class="body-copy">下载工具链</a>
          </div>
          <div class="link-single">
            <a href="/install/macos/package_installer" class="body-copy">安装说明</a>
          </div>
        </div>
      </div>
    </div>
    <div class="release-box section">
      <div class="content">
        {% include new-includes/components/static-linux-sdk.html %}
      </div>
    </div>
  </div>
  <div class="release-box section">
    <div class="content">
        <details class="download" style="margin-bottom: 0;">
        <summary>历史版本</summary>
        {% include_relative _older-releases.md %}
        </details>
    </div>
  </div>
  <h2>开发快照</h2>
  <div>
    <p class="content-copy">Swift 快照是从分支自动创建的预构建二进制文件。这些快照不是官方发布版本。它们已经通过了自动化单元测试，但尚未经过官方发布版本所需的完整测试。</p>
    <p class="content-copy">安装开发快照最简单的方法是使用 Swiftly 工具。在<a href="/install/macos/swiftly">说明页面</a>上了解更多信息。</p>
  </div>
  <h3>工具链</h3>
  <div>
    <p class="content-copy">
      <a class="content-link" href="/install/macos/package_installer">安装说明</a>
    </p>
  </div>
  <div class="releases-grid">
    <div class="release-box section">
      <div class="content">
        <div class="code-box content-wrapper">
          <h2>main</h2>
          <p class="body-copy">
            <small>{{ xcode_dev_builds.first.date | date: '%B %-d, %Y' }}</small><br />
            工具链包安装程序 (.pkg)
          </p>
          <div class="link-wrapper">
            <a href="https://download.swift.org/development/xcode/{{ xcode_dev_builds.first.dir }}/{{ xcode_dev_builds.first.debug_info }}" class="body-copy">调试符号</a>
          </div>
          <div class="link-wrapper">
            <a href="https://download.swift.org/development/xcode/{{ xcode_dev_builds.first.dir }}/{{ xcode_dev_builds.first.download }}" class="body-copy">下载工具链</a>
          </div>
        </div>
      </div>
    </div>
    <div class="release-box section">
      <div class="content">
        <div class="code-box content-wrapper">
          <h2>release/6.2</h2>
          <p class="body-copy">
            <small>{{ xcode_6_2_builds.first.date | date: '%B %-d, %Y' }}</small><br />
            工具链包安装程序 (.pkg)
          </p>
          <div class="link-wrapper">
            <a href="https://download.swift.org/swift-6.2-branch/xcode/{{ xcode_6_2_builds.first.dir }}/{{ xcode_6_2_builds.first.debug_info }}" class="body-copy">调试符号</a>
          </div>
          <div class="link-wrapper">
            <a href="https://download.swift.org/swift-6.2-branch/xcode/{{ xcode_6_2_builds.first.dir }}/{{ xcode_6_2_builds.first.download }}" class="body-copy">下载工具链</a>
          </div>
        </div>
      </div>
    </div>
  </div>
  <div class="release-box section">
    <div class="content">
        <details class="download" style="margin-bottom: 0;">
        <summary>历史快照 (main)</summary>
        {% include_relative _older-development-snapshots.md %}
        </details>
    </div>
  </div>
  <div class="release-box section">
    <div class="content">
        <details class="download" style="margin-bottom: 0;">
        <summary>历史快照 (release/6.2)</summary>
        {% include_relative _older-6_2-snapshots.md %}
        </details>
    </div>
  </div>
  <h3>静态 Linux SDK</h3>
  <div>
    <p class="content-copy">
      <a class="content-link" href="/documentation/articles/static-linux-getting-started.html">安装说明</a>
    </p>
  </div>
  {% include new-includes/components/static-linux-sdk-dev.html %}
</div>
