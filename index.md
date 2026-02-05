---
layout: new-layouts/base
title: Swift 编程语言
atom: true
---

<div class="animation-container">
    <canvas id="purple-swoop" width="1248" height="1116"></canvas>
    <canvas id="white-swoop-1" width="1248" height="1116"></canvas>
    <canvas id="orange-swoop-top" width="1248" height="1116"></canvas>
    <canvas id="orange-swoop-bottom" width="1248" height="1116"></canvas>
    <canvas id="white-swoop-2" width="1248" height="1116"></canvas>
    <canvas id="bird" width="1248" height="1116"></canvas>
</div>
<section id="what-is-swift" class="section">
    <div class="hero-content">
        <h1>Swift 是一款强大的跨平台通用编程语言。<br /> 新手易学，专家称心。</h1>
        <div class="sub-text"><h2>快速、现代、安全，写起代码乐无边。</h2></div>
        <a href="/install/" data-text="安装">安装</a>
        <p>适用于 Linux、macOS 和 Windows 的工具</p>
        <h2>使用 Swift 创造</h2>
    </div>
    <nav aria-label="Get started with Swift">
        <ul class="primary-links">
            {% for item in site.data.new-data.landing.get-started-primary %}
            <li>
                <a href="{{ item.link }}" data-text="{{ item.data-text }}">
                    <i class="{{ item.icon }}"></i>
                    <div>
                        <h3 class="title">{{ item.title }}</h3>
                        <p class="subtitle">{{ item.subtitle }}</p>
                    </div>
                </a>
            </li>
            {% endfor %}
        </ul>
        <ul class="secondary-links">
            {% for item in site.data.new-data.landing.get-started-secondary %}
            <li>
                <a href="{{ item.link }}" data-text="{{ item.data-text }}">
                    <h4 class="title">{{ item.title }}</h4>
                </a>
            </li>
            {% endfor %}
        </ul>
    </nav>
    <div class="swoop swoop-0 swoop-anim"></div>
</section>
{% assign pillar1_callouts = site.data.new-data.landing.callouts | slice: 0, 3 %}
{% assign pillar2_callouts = site.data.new-data.landing.callouts | slice: 3, 2 %}
{% assign pillar3_callouts = site.data.new-data.landing.callouts | slice: 5, 1 %}

<section id="pillar-1" class="section pillar">
    <div class="pillar-wrapper content-wrapper">
        <p class="pillar-intro">
            Swift 是唯一一种可以从嵌入式设备和内核扩展到应用程序和云基础设施的语言。它简单、富有表现力，具有令人难以置信的性能和安全性。并且它与 C 和 C++ 具有无与伦比的互操作性。
        </p>
        <br />
        <p class="pillar-intro">
            正是易用性、速度、安全性以及 Swift 的所有优势的结合，使其如此独特。
        </p>
    </div>
    {% for callout in pillar1_callouts %}
{% include new-includes/components/callout.html
    title=callout.title
    subtitle=callout.subtitle
    text=callout.text
    code=callout.code
    index=forloop.index
%}
    {% endfor %}

    <div class="swoop swoop-1 swoop-anim"></div>

</section>

<section id="pillar-2" class="section pillar">
    {% for callout in pillar2_callouts %}
{% include new-includes/components/callout.html
    title=callout.title
    subtitle=callout.subtitle
    text=callout.text
    code=callout.code
    index=forloop.index
%}
    {% endfor %}
    <div class="swoop swoop-2 swoop-anim"></div>
</section>

<section id="pillar-3" class="section pillar">
    {% for callout in pillar3_callouts %}
{% include new-includes/components/callout.html
    title=callout.title
    subtitle=callout.subtitle
    text=callout.text
    code=callout.code
    index=forloop.index
    links=callout.links
%}
    {% endfor %}
</section>
