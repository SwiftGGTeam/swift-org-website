---
layout: page
title: 社区概览
---

Swift.org 社区的唯一目标是打造世界上最好的通用编程语言。我们将以开放的方式共同开发这门语言，欢迎任何想要参与的人做出贡献。这份指南文档描述了 Swift 社区的组织方式，以便我们能够共同努力为 Swift 添加令人惊叹的新功能，并让更多平台的开发者都能使用它。

## 交流方式

Swift 语言是开放开发的，所有关于语言或社区流程的技术或管理话题都应该在 Swift 公共论坛上讨论。我们鼓励公开对话，Swift 语言的活跃开发者应该关注相关的论坛类别。

* 论坛类别目录和邮件说明在[论坛部分](#forums)。
* 所有 Swift 项目的源代码都可以在 GitHub 上找到：[github.com/apple][github]。
* Swift 语言的问题跟踪系统维护在：[github.com/swiftlang/swift/issues][bugtracker]。

项目空间内的所有交流都应遵守 Swift 项目的[行为准则](/code-of-conduct)。

## 社区结构

要推动 Swift 编程语言的发展，使其具有连贯、清晰的演进方向，需要强有力的领导。领导层来自社区，并与更广泛的贡献者和用户群体密切合作。社区内的角色包括：

* __[项目负责人](#project-lead)__ 从社区中任命技术领导者。Apple Inc. 是项目负责人，通过其代表与社区互动。
* __[核心团队](#core-team)__ 是负责 Swift 项目战略方向和监督的小型团队。
* __[代码所有者](/contributing/#code-owners)__ 是负责 Swift 代码库特定领域的个人。
* __[提交者](/contributing/#commit-access)__ 是拥有 Swift 代码库提交权限的任何人。
* __[成员](/contributing/#member)__ 是 GitHub 上 swiftlang 组织的任何成员。
* __[贡献者](/contributing/#contributor)__ 是通过编写代码、在论坛上回答问题、报告或分类问题、参与 Swift 演进过程或其他方式为 Swift 做出贡献的任何人。
* __指导小组__
   * __[生态系统](/ecosystem-steering-group)__ 是一个专注于 Swift 包和工具方向的小型专家团队。
   * __[语言](#language-steering-group)__ 是一个推动 Swift 语言朝着连贯方向前进的小型专家团队。
   * __[平台](/platform-steering-group)__ 是一个使 Swift 语言及其工具能够在新环境中使用的小型专家团队。
* __工作组__
   * __[C++ 互操作性](/cxx-interop-workgroup)__ 是一个致力于添加 Swift 和 C++ 之间双向互操作支持的团队。
   * __[贡献者体验](/contributor-experience-workgroup)__ 是一个支持 Swift 项目贡献者的团队，包括在 Swift 论坛上的贡献。
   * __[文档](/documentation-workgroup)__ 是一个帮助指导 Swift 文档体验的团队。
   * __[服务器端 Swift](/sswg)__ 是一个推广使用 Swift 开发和部署服务器应用程序的团队。
   * __[测试](/testing-workgroup)__ 是一个帮助指导 Swift 代码测试体验、库和工具的团队。
   * __[网站](/website-workgroup/)__ 是一个帮助指导 Swift.org 网站演进的团队。

最重要的是，每个使用 Swift 的人都是我们扩展社区中宝贵的成员。

#### 项目负责人

[通过论坛联系](https://forums.swift.org/new-message?username=tkremenek)

Apple Inc. 是项目负责人，并作为项目的仲裁者。项目负责人任命来自全球 Swift 贡献者社区的领导担任领导角色。社区领导者和代码贡献者共同努力不断改进 Swift，这门语言将通过所有参与者的良好工作而不断进步。

[Ted Kremenek](mailto:kremenek@apple.com) 是 Apple 指定的代表，作为项目负责人的代言人。

#### 核心团队

[通过论坛联系](https://forums.swift.org/new-message?groupname=core-team)

核心团队为 Swift 社区的各种工作组和计划提供凝聚力，提供支持和战略协调。项目负责人任命核心团队成员，以带来经验、专业知识和领导力的组合，使团队能够共同作为 Swift 项目及其社区的有效管理者。核心团队成员预计会随时间变化。

当前核心团队成员：

{% assign people = site.data.core_team | sort: "name" %}
{% for person in people %}* {{ person.name }}
{% endfor %}

我们感谢以下荣誉核心团队成员的服务：

{% assign people = site.data.core_team_emeriti | sort: "name" %}
{% for person in people %}* {{ person.name }}
{% endfor %}

#### 语言指导小组

[通过论坛联系](https://forums.swift.org/new-message?groupname=language-workgroup)

语言指导小组由 Swift 项目负责人和核心团队确定的专家组成，他们具有平衡的视角和专业知识，能够审慎地审查、指导和战略性地协调语言变更。语言指导小组审查并帮助迭代来自社区的[语言演进提案](/contributing/#evolution-process)，作为这些提案的批准者。工作组成员帮助推动 Swift 语言朝着连贯的方向发展，以创建最好的通用编程语言。语言指导小组的成员预计会随时间变化。

当前语言指导小组成员：

{% assign people = site.data.language_wg | sort: "name" %}
{% for person in people %}* {{ person.name }}
{% endfor %}

{% include_relative _forums.md %}


[homepage]: ./index.html "Swift.org home page"
[community]: ./community.html  "Swift.org community overview"
[contributing_code]: /contributing/#contributing-code  "Contributing Code"
[test_guide]: ./test_guide.html "Detailed guide to writing good Swift tests"
[blog]: ./blog_home.html  "Swift.org engineering blog"
[faq]: ./faq.html  "The FAQ for all things Swift.org"
[downloads]: ./downloads.html  "Download recent builds of Swift tools"
[forums]:  ./forums.html
[contributors]: ./CONTRIBUTORS.txt "View all Swift project authors"
[owners]: ./CODE_OWNERS.txt "View all Swift project code owners"
[license]: ./LICENSE.txt "View the Swift license"


[email-conduct]: mailto:conduct@swift.org  "Send email to the code of conduct working group"
[email-owners]: mailto:code-owners@forums.swift.org  "Send email to the code owners"
[email-users]: mailto:swift-users@swift.org  "Email other users of Swift"
[email-devs]: mailto:swift-dev@swift.org  "Email the developer discussion list"
[email-lead]: mailto:project-lead@swift.org "The leaders at Apple responsible for Swift.org"

[github]: https://github.com/apple  "Apple's home page on GitHub"
[repo]: git+ssh://github.com/apple "Link to the repo hosted on GitHub"
[bugtracker]:  http://github.com/swiftlang/swift/issues

[swift-apple]: https://developer.apple.com/swift  "Apple developer home page for Swift"
