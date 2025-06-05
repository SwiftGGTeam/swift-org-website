---
layout: new-layouts/base
title: 使用案例
---

<section id="cloud-services-case-hero" class="section">
    <div class="hero-content">
        <h1>使用 Swift 构建云服务</h1>
        <p>副标题文本</p>
        <ul>
            {% for box in site.data.new-data.use-case.hero-boxes %}
                <li>
                    <span class="title">{{ box.title }}</span>
                    <span class="text">{{ box.text }}</span>
                </li>
            {% endfor %}
        </ul>
        <a href="/" data-text="开始使用">开始使用</a>
        <div class="swoop swoop-1"></div>
        <div class="swoop swoop-2"></div>
    </div>
</section>

{% assign frameworks_packages = site.data.new-data.get-started.frameworks-packages %}

<div id="frameworks-packages" class="section">
    <div class="content">
        <img class="section-icon" src="{{ frameworks_packages.image }}" alt="{{ frameworks_packages.image_alt }}" />
        <h2>{{ frameworks_packages.title }}</h2>
        <ul class="featured">
            {% for package in frameworks_packages.featured %}
                <li>
                    <img src="{{ package.logo }}" alt="{{ package.logo_alt }}" />
                    <div>
                        <span class="name">{{ package.name }}</span>
                        <span class="text">{{ package.text }}</span>
                        <a href="{{ package.link }}">{{ package.link_text }}</a>
                    </div>
                </li>
            {% endfor %}
        </ul>
        <ul class="others">
            {% for package in frameworks_packages.others %}
                <li>
                    <div>
                        <span class="name">{{ package.name }}</span>
                        <span class="text">{{ package.text }}</span>
                        <a href="{{ package.link }}">{{ package.link_text }}</a>
                    </div>
                </li>
            {% endfor %}
        </ul>
        <a href="{{ frameworks_packages.link }}">{{ frameworks_packages.link_text }}</a>
    </div>
</div>
