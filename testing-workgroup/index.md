---
layout: page
title: 测试工作组
---

测试工作组是一个帮助指导 Swift 代码测试体验、库和工具的团队。

测试工作组将：

* 管理 [Swift Testing](https://github.com/swiftlang/swift-testing) 和
  [Corelibs XCTest](https://github.com/swiftlang/swift-corelibs-xctest) 项目，
  并对它们的功能提案进行审查。
* 识别能够满足 Swift 社区测试需求的改进。
* 追求 Swift Testing [愿景文档](https://github.com/swiftlang/swift-evolution/blob/main/visions/swift-testing.md)中概述的长期功能方向。
* 促进测试功能和库在相关工具中的集成。
* 向其他工作组、指导小组和核心团队传达 Swift 社区未满足的测试需求。

当前测试工作组由以下人员组成：

{% assign people = site.data['testing-workgroup'].members | sort: "name" %}
<ul>
{% for person in people %}
<li>{{ person.name }}
{%- if person.affiliation -%}
, {{ person.affiliation }}
{% endif %}
{% if person.handle %}
(<a href="https://forums.swift.org/new-message?username={{person.handle}}">@{{person.handle}}</a>)
{% endif %}
</li>
{% endfor %}
</ul>

## 章程

测试工作组的最终目标是增强 Swift 中编写和运行测试的体验和实用性，以提高整个生态系统的软件质量。为实现这一目标，工作组开发了像 Swift Testing 这样的库，实现了社区所需的核心功能；它与常用工具、IDE 和 CI 系统的维护者协调，以集成它们并推广测试工作流程；必要时，它还会与其他 Swift 社区团体合作，在其领域内追求与测试相关的改进。与其他团体经常合作的领域包括：

* [swift-package-manager](https://github.com/swiftlang/swift-package-manager) 的 `swift test` 子命令；
* [vscode-swift](https://github.com/swiftlang/vscode-swift) 插件中的测试子系统；以及
* [sourcekit-lsp](https://github.com/swiftlang/sourcekit-lsp) 中的静态测试发现逻辑。

工作组的一个核心功能是对 Swift Testing 项目的功能和 API 提案进行社区审查。它对该项目的治理由其配套的[愿景文档](https://github.com/swiftlang/swift-evolution/blob/main/visions/swift-testing.md)指导。工作组还寻找机会深化测试库与工具和 IDE 的集成，支持额外的测试风格（如性能或 UI），或解决影响测试工作流程的问题。工作组成员定期评估 Swift 生态系统中的新兴趋势，并讨论测试如何更好地支持这些趋势。

## 成员资格

测试工作组的成员资格基于贡献，并预计会随时间演变。添加新成员和移除不活跃成员需要现有成员投票并达成一致同意。成员总数限制在十人以内，以保持团队规模足够小以保持效率。

核心团队选择工作组的一名成员担任主席。主席对工作组没有特殊权限，但他们负责确保其顺利运作，包括：

* 组织和领导定期会议，
* 确保工作组与社区有效沟通，以及
* 在必要时协调工作组代表与其他 Swift 工作组或团队之间的会议。

如果您想加入工作组，请在论坛上向 [@testing-workgroup](https://forums.swift.org/new-message?groupname=testing-workgroup) 发送消息，您将被邀请参加下一次可用的小组会议进行讨论。有关如何贡献和向小组展示您的兴趣的示例，请参见[社区参与](#community-participation)。

工作组成员将尽可能通过共识独立做出决定，并在就重要决定达成共识遇到特殊挑战时向核心团队提出议题。

## 会议

测试工作组每两周在太平洋时间周一下午 1:00（美国太平洋时间）举行会议。会议在[偶数周](http://www.whatweekisit.org/)举行，除非提前另行通知。

许多工作组会议旨在进行开放讨论，任何 Swift 社区成员都可以通过提前向 [@testing-workgroup](https://forums.swift.org/new-message?groupname=testing-workgroup) 发送消息请求邀请来参加。一些会议保留给小组成员进行私下讨论，例如对正在审查的提案做出决定。

## 沟通

测试工作组在论坛的 [swift-testing](https://forums.swift.org/c/development/swift-testing/103) 类别中与更广泛的 Swift 社区进行沟通。也可以通过向 [@testing-workgroup](https://forums.swift.org/new-message?groupname=testing-workgroup) 发送消息私下联系工作组。

如果工作组在定期会议期间做出任何重要决定，成员将在一周内在论坛上发布相关信息。每个提案审查的结果将由其审查管理员在专门用于该提案的单独主题中宣布。

## 社区参与

欢迎所有人帮助改进 Swift 的测试体验并参与测试工作组的倡议。以下是一些可以考虑的参与方式：

* 在 Swift 论坛上讨论想法。您可以在 [swift-testing](https://forums.swift.org/c/development/swift-testing/103) 类别中创建新主题，或在任何主题中添加 `testing` 标签。
* 在测试工作组管理的项目中（如 [swift-testing](https://github.com/swiftlang/swift-testing)）开启 GitHub issues 来跟踪增强或报告错误。
* 为 [swift-testing](https://github.com/swiftlang/swift-testing) 贡献错误修复或增强功能。（参见 [CONTRIBUTING](https://github.com/swiftlang/swift-testing/blob/main/CONTRIBUTING.md)。）
* 扩展 [swift-testing](https://github.com/swiftlang/swift-testing) 以支持其他平台。（参见 [Porting](https://github.com/swiftlang/swift-testing/blob/main/Documentation/Porting.md)。）
* 开发新的自动化测试工具或改进现有工具。
* 通过在论坛上向 [@testing-workgroup](https://forums.swift.org/new-message?groupname=testing-workgroup) 发送消息，直接向测试工作组成员提供反馈。工作组主席将未解决的问题和主题带到工作组，在定期会议期间进行讨论。工作组决定对这些问题的行动。
* 参加测试工作组的定期视频会议。向 [@testing-workgroup](https://forums.swift.org/new-message?groupname=testing-workgroup) 发送消息请求访问权限，因为会议必须保持相对较少的参与者数量。
