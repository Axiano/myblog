---
title: Cards 魔改
date: 2021-03-02
published: true
license: true
slug: cards
tags: [hexo,cards]
cate: 笔记
cover_image: "./images/cards.png"
canonical_url: false
description: "一个hexo简约的主题"
---

:::note 前言
虚拟机的简绍这里就不多说了，因为没有时间去查资料，所以下面我会直接开始教程。
你按照我的教程很简单，有什么问题可以直接群里问我。
:::
 <h2 id="头部图标替换"><a href="#头部图标替换" class="headerlink" title="头部图标替换"></a>头部图标替换</h2><h3 id="替换准备"><a href="#替换准备" class="headerlink" title="替换准备"></a>替换准备</h3><p>进入<strong>Iconfont</strong>网站的图标下载到本地</p>
<h3 id="引入CSS"><a href="#引入CSS" class="headerlink" title="引入CSS"></a>引入CSS</h3><p>先把刚才下载的文件解压出来，然后放到这个目录下</p>
<figure class="highlight plain"><table><tr><td class="code"><pre><span class="line">cards\source\css\style\</span><br></pre></td></tr></table></figure>
<p>打开<strong>main.styl</strong>这个文件在上面的目录中<br>引入<strong>CSS</strong> 文件</p>
<figure class="highlight plain"><table><tr><td class="code"><pre><span class="line">@import &#39;font&#x2F;iconfont.css&#39;;</span><br></pre></td></tr></table></figure>
<p><strong><u>提示：这里的font是刚才自己的解压出来得文件夹</u></strong></p>
<h3 id="打开header文件"><a href="#打开header文件" class="headerlink" title="打开header文件"></a>打开header文件</h3><p>找到下面的目录</p>
<figure class="highlight plain"><table><tr><td class="code"><pre><span class="line">\cards\layout\_partial\source</span><br></pre></td></tr></table></figure>
<p>找到这段代码并且注释掉</p>
<figure class="highlight plain"><table><tr><td class="code"><pre><span class="line">&lt;% theme.navbar.menu.forEach((item) &#x3D;&gt; &#123; %&gt;</span><br><span class="line">      &lt;a href&#x3D;&quot;&lt;%&#x3D; url_for(item.url) %&gt;&quot; class&#x3D;&quot;navbar-menu button&quot;&gt;&lt;%&#x3D; item.name %&gt;&lt;&#x2F;a&gt;</span><br><span class="line">       &lt;% &#125;); %&gt;</span><br></pre></td></tr></table></figure>
<p>添加自己的图标</p>
<figure class="highlight plain"><table><tr><td class="code"><pre><span class="line">&lt;a href&#x3D;&quot;&#x2F;&quot; class&#x3D;&quot;iconfont icon-shouye&quot;&gt;&lt;&#x2F;a&gt;</span><br><span class="line">&lt;a href&#x3D;&quot;&#x2F;archives&quot; class&#x3D;&quot;iconfont icon-guidang&quot;&gt;&lt;&#x2F;a&gt;</span><br><span class="line">&lt;a href&#x3D;&quot;&#x2F;about&quot; class&#x3D;&quot;iconfont icon-wode&quot;&gt;&lt;&#x2F;a&gt;  </span><br><span class="line">&lt;a href&#x3D;&quot;&#x2F;artitalk&quot; class&#x3D;&quot;iconfont icon-feichuan2&quot;&gt;&lt;&#x2F;a&gt;</span><br></pre></td></tr></table></figure>

<h3 id="修改heaer的CSS"><a href="#修改heaer的CSS" class="headerlink" title="修改heaer的CSS"></a>修改heaer的CSS</h3><p>找到下面目录中的<strong>header.styl</strong></p>
<figure class="highlight plain"><table><tr><td class="code"><pre><span class="line">cards\source\css\style\_functions</span><br></pre></td></tr></table></figure>
<p>找的下面的代码</p>
<figure class="highlight plain"><table><tr><td class="code"><pre><span class="line">.header__right</span><br></pre></td></tr></table></figure>
<p>然后在下面添加</p>
<figure class="highlight plain"><table><tr><td class="code"><pre><span class="line">.icon-shouye</span><br><span class="line">.icon-guidang</span><br><span class="line">.icon-wode</span><br><span class="line">.icon-feichuan2</span><br><span class="line">    text-decoration none</span><br><span class="line">    font-size 22px</span><br><span class="line">    padding 16px 10px 16px 10px</span><br><span class="line">    border-radius 5px</span><br><span class="line"></span><br></pre></td></tr></table></figure>

<h2 id="首页卡片弧度自定义"><a href="#首页卡片弧度自定义" class="headerlink" title="首页卡片弧度自定义"></a>首页卡片弧度自定义</h2><h3 id="配置文件设置"><a href="#配置文件设置" class="headerlink" title="配置文件设置"></a>配置文件设置</h3><p>主题的配置文件可以直接开启卡片圆角</p>
<figure class="highlight plain"><table><tr><td class="code"><pre><span class="line"># 弧度设置</span><br><span class="line">radius: </span><br><span class="line">  main_radius: 5px</span><br></pre></td></tr></table></figure>
<p>但是如果添加头图，这个连头图左右下角，也会添加圆角<br>个人感觉不好看</p>
<h3 id="自定义弧度"><a href="#自定义弧度" class="headerlink" title="自定义弧度"></a>自定义弧度</h3><p>找到下面的目录</p>
<figure class="highlight plain"><table><tr><td class="code"><pre><span class="line">cards\source\css\style\_pages</span><br></pre></td></tr></table></figure>
<p>打开<strong>post.styl</strong>这个文件<br>找到下面这段代码</p>
<figure class="highlight plain"><table><tr><td class="code"><pre><span class="line">.post-entry__header</span><br><span class="line">.post__header</span><br><span class="line">    margin calc(var(--space) * -1) !important</span><br><span class="line">    margin-bottom calc(var(--space) &#x2F; 2) !important</span><br><span class="line">    overflow hidden</span><br><span class="line">    border-radius $radius_main</span><br></pre></td></tr></table></figure>
<p>把<strong>border-radius $radius_main</strong>注释掉添加下面的代码</p>
<figure class="highlight plain"><table><tr><td class="code"><pre><span class="line">border-top-left-radius:2em;</span><br><span class="line">border-top-right-radius:2em;</span><br></pre></td></tr></table></figure>
    </div>