---
layout: new-layouts/install-linux-version
title: 安装 Swift
---

{% include /new-includes/assigns/linux-platform-builds.html
    platform="ubi 9"
    aarch64="true"
    branch_dir="development"
    development="main"
    docker_tag="nightly-rhel-ubi9"
    development_builds=site.data.builds.development.ubi9
    aarch64_development_builds=site.data.builds.development.ubi9-aarch64
    development_2="release/6.2"
    docker_tag_2="nightly-6.2-rhel-ubi9"
    development_builds_2=site.data.builds.swift-6_2-branch.ubi9
    aarch64_development_builds_2=site.data.builds.swift-6_2-branch.ubi9-aarch64
    branch_dir_2="swift-6.2-branch"
%}

{% include /new-includes/components/linux-releases.html
  docker_tag=docker_tag
  development_builds=development_builds
  development_builds_2=development_builds_2
  platform=platform
  development=development
  development_2=development_2
  platform_name_url=platform_name_url
  branch_dir=branch_dir
  branch_dir_2=branch_dir_2
%}