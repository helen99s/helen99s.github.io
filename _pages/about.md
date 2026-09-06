---
permalink: /
title: ""
excerpt: ""
author_profile: true
redirect_from:
  - /about/
  - /about.html
---

{% if site.google_scholar_stats_use_cdn %}
{% assign gsDataBaseUrl = "https://cdn.jsdelivr.net/gh/" | append: site.repository | append: "@" %}
{% else %}
{% assign gsDataBaseUrl = "https://raw.githubusercontent.com/" | append: site.repository | append: "/" %}
{% endif %}
{% assign url = gsDataBaseUrl | append: "google-scholar-stats/gs_data_shieldsio.json" %}

<span class='anchor' id='about-me'></span>

# Jiyuan Liu (刘吉元)

<div class="profile-lead">
  <p class="role-line lang-en">
    <i class="fas fa-user-graduate" aria-hidden="true"></i>
    Associate Professor
  </p>

  <p class="role-line cn lang-zh">
    <i class="fas fa-user-graduate" aria-hidden="true"></i>
    副教授
  </p>

  <div class="profile-meta">
    <span class="lang-en">
      <i class="fas fa-university" aria-hidden="true"></i>
      College of Systems Engineering, National University of Defense Technology
    </span>

    <span class="lang-zh">
      <i class="fas fa-university" aria-hidden="true"></i>
      国防科技大学系统工程学院
    </span>
  </div>

  <div class="profile-links">
    <a href="https://liujiyuan13.github.io/" target="_blank">
      <i class="fas fa-globe" aria-hidden="true"></i>
      English Homepage
    </a>
  </div>
</div>

<div class="language-toggle" role="group" aria-label="Language selector">
  <button type="button" data-lang-switch="zh">中文</button>
  <button type="button" data-lang-switch="en">English</button>
</div>

<nav class="quick-nav" aria-label="Quick links">
  <a href="#about"><i class="fas fa-id-card" aria-hidden="true"></i><span class="lang-en">About</span><span class="lang-zh">个人简介</span></a>
  <a href="#openings"><i class="fas fa-user-plus" aria-hidden="true"></i><span class="lang-en">Openings</span><span class="lang-zh">招生</span></a>
  <a href="#research"><i class="fas fa-microscope" aria-hidden="true"></i><span class="lang-en">Research</span><span class="lang-zh">研究方向</span></a>
  <a href="#works"><i class="fas fa-layer-group" aria-hidden="true"></i><span class="lang-en">Works</span><span class="lang-zh">代表成果</span></a>
  <a href="#projects"><i class="fas fa-tasks" aria-hidden="true"></i><span class="lang-en">Projects</span><span class="lang-zh">科研项目</span></a>
  <a href="#news"><i class="far fa-calendar-alt" aria-hidden="true"></i><span class="lang-en">News</span><span class="lang-zh">最新动态</span></a>
  <a href="#publications"><i class="fas fa-book-open" aria-hidden="true"></i><span class="lang-en">Publications</span><span class="lang-zh">代表论文</span></a>
  <a href="#service"><i class="fas fa-hands-helping" aria-hidden="true"></i><span class="lang-en">Service</span><span class="lang-zh">学术服务</span></a>
</nav>

<script>
(function () {
  var params = new URLSearchParams(window.location.search);
  var initialLang = params.get("lang") === "en" ? "en" : "zh";
  var root = document.documentElement;
  var mainNavLabels = {
    "#about-me": { zh: "首页", en: "Home" },
    "#openings": { zh: "招生", en: "Openings" },
    "#research": { zh: "研究方向", en: "Research" },
    "#works": { zh: "代表成果", en: "Works" },
    "#publications": { zh: "代表论文", en: "Publications" },
    "#service": { zh: "学术服务", en: "Service" },
    "/files/CV_Yunkang_CAO.pdf": { zh: "简历", en: "CV" }
  };

  function getMainNavLabels(link) {
    var href = link.getAttribute("href");
    if (mainNavLabels[href]) {
      return mainNavLabels[href];
    }

    try {
      var url = new URL(href, window.location.href);
      if (url.pathname === "/files/CV_Yunkang_CAO.pdf") {
        return mainNavLabels["/files/CV_Yunkang_CAO.pdf"];
      }
      if (url.origin === window.location.origin && url.hash && (url.pathname === "/" || url.pathname === window.location.pathname)) {
        return mainNavLabels[url.hash];
      }
    } catch (error) {
      return null;
    }

    return null;
  }

  function updateMainNav(lang) {
    document.querySelectorAll(".masthead a[href], .greedy-nav a[href]").forEach(function (link) {
      var labels = getMainNavLabels(link);
      if (labels) {
        link.textContent = labels[lang];
      }
    });
  }

  function setLanguage(lang, updateUrl) {
    var nextLang = lang === "en" ? "en" : "zh";
    root.setAttribute("data-lang", nextLang);
    root.setAttribute("lang", nextLang === "en" ? "en" : "zh-CN");
    updateMainNav(nextLang);

    document.querySelectorAll("[data-lang-switch]").forEach(function (button) {
      var isActive = button.getAttribute("data-lang-switch") === nextLang;
      button.classList.toggle("is-active", isActive);
      button.setAttribute("aria-pressed", isActive ? "true" : "false");
    });

    if (updateUrl && window.history && window.history.replaceState) {
      var url = new URL(window.location.href);
      if (nextLang === "en") {
        url.searchParams.set("lang", "en");
      } else {
        url.searchParams.delete("lang");
      }
      window.history.replaceState({}, "", url.pathname + url.search + url.hash);
    }
  }

  root.setAttribute("data-lang", initialLang);
  root.setAttribute("lang", initialLang === "en" ? "en" : "zh-CN");

  document.addEventListener("DOMContentLoaded", function () {
    setLanguage(initialLang, false);
    document.querySelectorAll("[data-lang-switch]").forEach(function (button) {
      button.addEventListener("click", function () {
        setLanguage(button.getAttribute("data-lang-switch"), true);
      });
    });

    document.querySelectorAll(".masthead a[href^='#'], .quick-nav a[href^='#']").forEach(function (link) {
      link.addEventListener("click", function (event) {
        var hash = link.getAttribute("href");
        var target = hash ? document.querySelector(hash) : null;
        if (!target) {
          return;
        }

        event.preventDefault();
        target.scrollIntoView({ block: "start" });
        if (window.history && window.history.replaceState) {
          window.history.replaceState({}, "", window.location.pathname + window.location.search + hash);
        } else {
          window.location.hash = hash;
        }
      });
    });
  });
})();
</script>

<style>
html:not([data-lang="en"]) .lang-en {
  display: none !important;
}

html[data-lang="en"] .lang-zh {
  display: none !important;
}

.profile-lead {
  border-left: 4px solid #365f91;
  margin: 0.8rem 0 1rem;
  padding: 0.1rem 0 0.1rem 1rem;
}

.role-line {
  font-weight: 700;
  margin: 0 0 0.3rem;
}

.role-line i,
.profile-meta i,
.profile-links i,
.quick-nav i,
.section-icon {
  color: #365f91;
  margin-right: 0.35rem;
}

.role-line.cn {
  color: #38485c;
}

.profile-meta {
  display: grid;
  gap: 0.25rem;
  margin: 0.75rem 0;
}

.profile-meta span {
  align-items: baseline;
  display: flex;
  line-height: 1.55;
}

.profile-meta i {
  flex: 0 0 1.15rem;
  text-align: center;
}

.profile-links,
.quick-nav {
  display: flex;
  flex-wrap: wrap;
  gap: 0.45rem;
}

.language-toggle {
  display: flex;
  gap: 0.35rem;
  justify-content: flex-end;
  margin: 0.85rem 0 0.7rem;
}

.language-toggle button {
  background: #fff;
  border: 1px solid #d8e1ed;
  border-radius: 999px;
  color: #365f91;
  cursor: pointer;
  font-size: 0.86rem;
  font-weight: 700;
  line-height: 1;
  padding: 0.42rem 0.75rem;
}

.language-toggle button.is-active {
  background: #365f91;
  border-color: #365f91;
  color: #fff;
}

.profile-links a,
.quick-nav a {
  align-items: center;
  border: 1px solid #d8e1ed;
  border-radius: 6px;
  display: inline-flex;
  line-height: 1.2;
  padding: 0.36rem 0.55rem;
  text-decoration: none;
}

.profile-links a:hover,
.quick-nav a:hover {
  background: #f4f7fb;
}

.section-icon {
  display: inline-block;
  width: 1.2rem;
}

.opening-highlight {
  background: #fff7f5;
  border: 1px solid #efcbc4;
  border-left: 4px solid #b02418;
  border-radius: 8px;
  color: #8f1d14;
  font-weight: 700;
  margin: 0.8rem 0 1rem;
  padding: 0.72rem 0.9rem;
}

.opening-highlight p {
  margin: 0 0 0.35rem;
}

.opening-highlight p:last-child {
  margin-bottom: 0;
}

.opening-highlight i,
.news-icon,
.work-kicker i {
  color: #365f91;
  margin-right: 0.35rem;
}

.news-archive {
  border-top: 1px solid #d8e1ed;
  margin-top: 0.75rem;
  padding-top: 0.55rem;
}

.news-archive summary {
  color: #365f91;
  cursor: pointer;
  font-weight: 700;
}

.news-archive[open] summary {
  margin-bottom: 0.5rem;
}

.news-archive-list ul {
  margin-top: 0;
}

.opening-highlight i {
  color: #b02418;
}

.metrics-grid {
  display: grid;
  gap: 0.7rem;
  grid-template-columns: repeat(auto-fit, minmax(135px, 1fr));
  margin: 1rem 0;
}

.metric-item {
  border: 1px solid #d8e1ed;
  border-radius: 8px;
  padding: 0.65rem 0.75rem;
}

.metric-item i {
  color: #365f91;
  margin-right: 0.35rem;
}

.metric-item strong {
  color: #22364f;
  display: inline-block;
  font-size: 1.18rem;
  margin-right: 0.2rem;
}

.metric-item span {
  color: #526171;
  display: block;
  font-size: 0.86rem;
  margin-top: 0.15rem;
}

.works-grid {
  display: grid;
  gap: 14px;
  grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
  margin: 1rem 0 1.6rem;
}

.work-card {
  background: #fff;
  border: 1px solid #d9e1ec;
  border-radius: 8px;
  display: flex;
  flex-direction: column;
  overflow: hidden;
}

.work-card img {
  background: #f7f9fc;
  border-bottom: 1px solid #e4eaf2;
  height: 210px;
  object-fit: contain;
  width: 100%;
}

.work-body {
  display: flex;
  flex: 1;
  flex-direction: column;
  padding: 12px 14px 14px;
}

.work-kicker {
  color: #365f91;
  font-size: 0.82rem;
  font-weight: 700;
  margin: 0 0 6px;
}

.work-body h3 {
  font-size: 1.05rem;
  margin: 0 0 8px;
}

.work-body p {
  line-height: 1.55;
  margin: 0 0 8px;
}

.work-links {
  font-weight: 700;
  margin-top: auto;
}

@media (max-width: 560px) {
  .work-card img {
    height: 180px;
  }
}
</style>

-----

<span class='anchor' id='about'></span>

# <i class="fas fa-id-card section-icon" aria-hidden="true"></i><span class="lang-en">About</span><span class="lang-zh">个人简介</span>

刘吉元，国防科技大学系统工程学院副教授，主要从事多视图学习理论、算法及其应用研究。入选中国指挥与控制学会青年人才托举工程、湖南省“芙蓉计划”青年人才和国防科技大学高层次创新人才。荣获2025年CCF科技成果一等奖、全军优秀博士学位论文奖和CCF信息系统专委会优秀博士学位论文奖，并入选全球前2%顶尖科学家榜单。
{: .lang-zh}

近年来围绕多视图学习、联邦学习、聚类与表示学习等方向开展研究，相关成果发表于 TPAMI、NeurIPS、ICML、CVPR、ICCV、AAAI、ACM MM 等国际期刊和会议。已发表40余篇CCF A类和中科院一区学术论文，其中包括3篇TPAMI长文，2篇论文进入ESI 1%高被引论文列表，学术引用2000余次，授权国家发明专利10余项。
{: .lang-zh}

主持或承担国家自然科学基金、教育部、军委科技委等科研项目，并担任CCF理论计算机科学专委执行委员、CAAI信息融合专委委员、CAAI粒计算与知识发现专委委员，以及多个国际期刊和会议的领域主席、高级程序委员、程序委员和审稿人。
{: .lang-zh}

<div class="metrics-grid">

  <div class="metric-item">
    <i class="fas fa-file-alt" aria-hidden="true"></i>
    <strong>40+</strong>
    <span class="lang-zh">CCF A类 / 中科院一区论文</span>
    <span class="lang-en">High-quality Publications</span>
  </div>

  <div class="metric-item">
    <i class="fas fa-book" aria-hidden="true"></i>
    <strong>3</strong>
    <span class="lang-zh">TPAMI 长文</span>
    <span class="lang-en">TPAMI Papers</span>
  </div>

  <div class="metric-item">
    <i class="fas fa-quote-right" aria-hidden="true"></i>
    <strong>2000+</strong>
    <span class="lang-zh">学术引用</span>
    <span class="lang-en">Citations</span>
  </div>

  <div class="metric-item">
    <i class="fas fa-lightbulb" aria-hidden="true"></i>
    <strong>10+</strong>
    <span class="lang-zh">授权发明专利</span>
    <span class="lang-en">Granted Patents</span>
  </div>

</div>

-----

<span class='anchor' id='news'></span>

# <i class="far fa-calendar-alt section-icon" aria-hidden="true"></i><span class="lang-en">News</span><span class="lang-zh">最新动态</span>

- <i class="far fa-calendar-alt news-icon" aria-hidden="true"></i><span class="lang-zh">**2026.07**：3 篇论文被 **ACM Multimedia 2026（CCF A）**录用，研究涉及联邦多视图聚类、主锚图学习和不完整多视图聚类。</span><span class="lang-en">**2026.07**: Three papers were accepted by **ACM Multimedia 2026 (CCF A)**.</span>

- <i class="far fa-calendar-alt news-icon" aria-hidden="true"></i><span class="lang-zh">**2026.05**：1 篇论文被 **ICML 2026（CCF A）**录用，研究面向多视图聚类中的层次化锚图学习。</span><span class="lang-en">**2026.05**: One paper was accepted by **ICML 2026 (CCF A)**.</span>

- <i class="far fa-calendar-alt news-icon" aria-hidden="true"></i><span class="lang-zh">**2026.02**：1 篇论文被 **CVPR 2026（CCF A）**录用，研究面向基于张量化锚点引导的大规模多视图子空间聚类。</span><span class="lang-en">**2026.02**: One paper was accepted by **CVPR 2026 (CCF A)**.</span>

- <i class="far fa-calendar-alt news-icon" aria-hidden="true"></i><span class="lang-zh">**2026.02**：受邀担任 **ACM Multimedia 2026 Area Chair（领域主席）**。</span><span class="lang-en">**2026.02**: Invited to serve as an **Area Chair of ACM Multimedia 2026**.</span>

- <i class="far fa-calendar-alt news-icon" aria-hidden="true"></i><span class="lang-zh">**2026.01**：1 篇论文被 **Neural Networks** 录用。</span><span class="lang-en">**2026.01**: One paper was accepted by **Neural Networks**.</span>

- <i class="far fa-calendar-alt news-icon" aria-hidden="true"></i><span class="lang-zh">**2025**：荣获 **CCF 科技成果一等奖**。</span><span class="lang-en">**2025**: Received the **CCF Science and Technology Achievement First Prize**.</span>

<p class="lang-zh">
更多最新成果请访问 <a href="https://liujiyuan13.github.io/" target="_blank">英文个人主页</a>。
</p>

<p class="lang-en">
For more updates, please visit the <a href="https://liujiyuan13.github.io/" target="_blank">English Homepage</a>.
</p>



-----

<span class='anchor' id='experience'></span>

# <i class="fas fa-briefcase section-icon" aria-hidden="true"></i><span class="lang-en">Experience</span><span class="lang-zh">教育与工作经历</span>

<div class="lang-zh">

- **2025 - 至今**　国防科技大学系统工程学院，**副教授**

- **2022 - 2025**　国防科技大学系统工程学院，**讲师**

- **2017 - 2022**　国防科技大学计算机学院，**硕博研究生**  
  2022年获博士学位。

- **2016 - 2017**　加拿大西蒙菲莎大学（Simon Fraser University），**访问学生**  
  在 Jiangchuan Liu 教授团队开展交流学习，获国家留学基金委（CSC）资助。

- **2013 - 2017**　国防科技大学，**钱学森创新拓展班，本科**

</div>

<div class="lang-en">

- **2025 - Present** — Associate Professor, College of Systems Engineering, National University of Defense Technology

- **2022 - 2025** — Lecturer, College of Systems Engineering, National University of Defense Technology

- **2017 - 2022** — M.Sc.-Ph.D. Student, College of Computer Science, National University of Defense Technology

- **2016 - 2017** — Visiting Student, Simon Fraser University, Canada

- **2013 - 2017** — Undergraduate Student, Qian Xuesen Class, National University of Defense Technology

</div>

-----


<span class='anchor' id='openings'></span>

# <i class="fas fa-user-plus section-icon" aria-hidden="true"></i><span class="lang-en">Openings</span><span class="lang-zh">招生与培养</span>

<div class="opening-highlight">
<p class="lang-zh">
<i class="fas fa-bullhorn" aria-hidden="true"></i>
欢迎对多视图学习、机器学习及相关研究方向感兴趣的同学联系交流。具体招生名额及要求以学校当年招生政策和导师安排为准。
</p>

<p class="lang-en">
<i class="fas fa-bullhorn" aria-hidden="true"></i>
Prospective students interested in multi-view learning, machine learning, and related topics are welcome to get in touch. Please refer to the English homepage for additional information.
</p>
</div>

### <span class="lang-zh">研究方向</span><span class="lang-en">Research Topics</span>

<div class="lang-zh">

- **多视图学习与聚类**：多源异构数据中的一致性、互补性建模与聚类分析。
- **联邦多视图学习**：面向隐私保护和分布式场景的多视图协同学习。
- **复杂场景多视图学习**：面向缺失视图、大规模数据、动态数据等现实问题的鲁棒学习方法。
- **表示学习与智能信息融合**：研究面向复杂数据的表示、融合与学习方法。

</div>

<div class="lang-en">

- Multi-view learning and clustering
- Federated multi-view learning
- Multi-view learning under complex scenarios
- Representation learning and intelligent information fusion

</div>

### <span class="lang-zh">我们期待这样的你</span><span class="lang-en">What We Value</span>

<div class="lang-zh">

- 对机器学习、人工智能及相关研究问题具有浓厚兴趣；
- 具有较好的数学基础和逻辑分析能力；
- 具有一定的 Python / matlab 等编程基础；
- 具有较强的自主学习能力、责任心和科研热情；
- 不要求已有相关论文成果，更看重学习能力、研究兴趣和持续投入。

</div>

<div class="lang-en">

- Strong interest in machine learning and artificial intelligence;
- Solid mathematical and analytical foundations;
- Basic programming skills in Python / PyTorch;
- Self-motivation, responsibility, and enthusiasm for research.

</div>

### <span class="lang-zh">联系我们</span><span class="lang-en">Contact</span>

<div class="lang-zh">

有意申请或参与科研的同学，可将**个人简历、成绩单及简要研究兴趣介绍**发送至老师邮箱。

> 邮箱：**[这里后续填写老师邮箱]**

邮件主题建议注明：**姓名 + 学校 + 专业 + 申请类型**。

</div>

<div class="lang-en">

For detailed application information, please visit the [English Homepage](https://liujiyuan13.github.io/).

</div>

-----

<span class='anchor' id='research'></span>

# <i class="fas fa-microscope section-icon" aria-hidden="true"></i><span class="lang-en">Research</span><span class="lang-zh">研究方向</span>

<div class="lang-zh">

刘吉元老师主要围绕**多源异构数据的表示、融合与学习**开展研究，重点关注多视图学习理论与算法，以及面向复杂现实场景的高效、可靠机器学习方法。

### 01 多视图学习与聚类

围绕多源异构数据中不同视图之间的**一致性与互补性**，研究多视图表示学习、聚类、多核学习与信息融合方法，探索如何从多源数据中学习更加完整、可靠的潜在结构。

### 02 联邦多视图学习

面向数据分散、隐私保护和跨客户端协同场景，研究**联邦环境下的多视图表示与聚类方法**，重点关注异构数据协同、通信效率、隐私保护及模型泛化等问题。

### 03 复杂场景下的多视图学习

面向真实应用中的**缺失视图、大规模数据、动态数据及噪声干扰**等问题，研究鲁棒、高效和可扩展的多视图学习方法，提升模型在复杂开放环境下的适应能力。

</div>

<div class="lang-en">

Research focuses on multi-view learning and machine learning for heterogeneous multi-source data, with particular interests in representation learning, clustering, federated learning, and learning under complex real-world scenarios.

### 01 Multi-view Learning and Clustering

Learning consistent and complementary representations from heterogeneous multi-view data, with interests in multi-view clustering, representation learning, multiple kernel learning, and information fusion.

### 02 Federated Multi-view Learning

Developing collaborative multi-view learning methods under distributed and privacy-preserving settings, with emphasis on data heterogeneity, communication efficiency, privacy, and generalization.

### 03 Multi-view Learning in Complex Scenarios

Developing robust and scalable multi-view learning methods for incomplete views, large-scale data, dynamic environments, and noisy observations.

</div>

-----

<span class='anchor' id='works'></span>

# <i class="fas fa-layer-group section-icon" aria-hidden="true"></i><span class="lang-en">Representative Works</span><span class="lang-zh">代表性成果</span>

<p class="lang-zh">
围绕多视图学习中的一致性与互补性建模、联邦协同、大规模学习和不完整数据等问题，形成了一系列代表性研究成果。
</p>

<p class="lang-en">
Selected representative works on multi-view learning, federated learning, large-scale clustering, and incomplete multi-view learning.
</p>

<div class="works-grid">

<!-- 1. Federated MVC -->
<div class="work-card">
  <img src="/images/works/federated-mvc.jpg" alt="Federated Multi-view Clustering">
  <div class="work-body">
    <p class="work-kicker">
      <i class="fas fa-network-wired"></i> TPAMI 2025
    </p>

    <h3>Communication-Efficient Federated Multi-view Clustering</h3>

    <p class="lang-zh">
      面向数据分散与隐私受限场景，研究通信高效的联邦多视图聚类方法，实现跨客户端多视图信息的协同建模。
    </p>

    <p class="lang-en">
      Communication-efficient federated multi-view clustering for distributed and privacy-preserving scenarios.
    </p>

    <p class="work-links">
      <a href="#">Paper</a> ·
      <a href="#">Code</a>
    </p>
  </div>
</div>


<!-- 2. Contrastive Multi-view Kernel Learning -->
<div class="work-card">
  <img src="/images/works/cmkl.png" alt="Contrastive Multi-view Kernel Learning">
  <div class="work-body">
    <p class="work-kicker">
      <i class="fas fa-project-diagram"></i> TPAMI 2023
    </p>

    <h3>Contrastive Multi-view Kernel Learning</h3>

    <p class="lang-zh">
      将对比学习思想引入多视图核学习，通过不同视图及核表示之间的结构关系提升多源数据的聚类表示能力。
    </p>

    <p class="lang-en">
      Contrastive learning for multi-view kernel representations and clustering.
    </p>

    <p class="work-links">
      <a href="#">Paper</a> ·
      <a href="#">Code</a>
    </p>
  </div>
</div>


<!-- 3. Consistency and Large-scale MKC -->
<div class="work-card">
  <img src="/images/works/consistency-mkc.png" alt="Consistency and Large-scale Multiple Kernel Clustering">
  <div class="work-body">
    <p class="work-kicker">
      <i class="fas fa-layer-group"></i> TPAMI 2024
    </p>

    <h3>On the Consistency and Large-Scale Extension of Multiple Kernel Clustering</h3>

    <p class="lang-zh">
      从一致性角度研究多核聚类机制，并进一步面向大规模数据扩展高效多核聚类方法。
    </p>

    <p class="lang-en">
      Consistency analysis and scalable extension of multiple kernel clustering.
    </p>

    <p class="work-links">
      <a href="#">Paper</a> ·
      <a href="#">Code</a>
    </p>
  </div>
</div>


<!-- 4. Large-scale MVC -->
<div class="work-card">
  <img src="/images/works/large-scale-mvc.png" alt="Large-scale Multi-view Tensor Clustering">
  <div class="work-body">
    <p class="work-kicker">
      <i class="fas fa-database"></i> CVPR 2025
    </p>

    <h3>Large-scale Multi-view Tensor Clustering with Implicit Linear Kernels</h3>

    <p class="lang-zh">
      面向大规模多视图数据，研究基于隐式线性核与张量建模的高效聚类方法，提升多视图学习的可扩展性。
    </p>

    <p class="lang-en">
      Scalable tensor-based multi-view clustering with implicit linear kernels.
    </p>

    <p class="work-links">
      <a href="#">Paper</a> ·
      <a href="#">Code</a>
    </p>
  </div>
</div>


<!-- 5. Incomplete MVC -->
<div class="work-card">
  <img src="/images/works/incomplete-mvc.png" alt="Incomplete Multi-view Deep Clustering">
  <div class="work-body">
    <p class="work-kicker">
      <i class="fas fa-puzzle-piece"></i> NeurIPS 2025
    </p>

    <h3>Incomplete Multi-view Deep Clustering with Data Imputation and Alignment</h3>

    <p class="lang-zh">
      面向现实数据中的视图缺失问题，将数据补全与跨视图表示对齐相结合，实现更加鲁棒的不完整多视图深度聚类。
    </p>

    <p class="lang-en">
      Deep clustering for incomplete multi-view data through joint imputation and alignment.
    </p>

    <p class="work-links">
      <a href="#">Paper</a> ·
      <a href="#">Code</a>
    </p>
  </div>
</div>


<!-- 6. One-pass MVC -->
<div class="work-card">
  <img src="/images/works/one-pass-mvc.png" alt="One-pass Multi-view Clustering">
  <div class="work-body">
    <p class="work-kicker">
      <i class="fas fa-bolt"></i> ICCV 2021
    </p>

    <h3>One-pass Multi-view Clustering for Large-scale Data</h3>

    <p class="lang-zh">
      面向大规模多视图数据的计算与存储压力，研究单遍式多视图聚类方法，提高大规模场景下的学习效率。
    </p>

    <p class="lang-en">
      One-pass multi-view clustering for efficient learning from large-scale data.
    </p>

    <p class="work-links">
      <a href="#">Paper</a> ·
      <a href="#">Code</a>
    </p>
  </div>
</div>

</div>

-----

<span class='anchor' id='projects'></span>

# <i class="fas fa-tasks section-icon" aria-hidden="true"></i><span class="lang-en">Projects & Honors</span><span class="lang-zh">科研项目与荣誉</span>

### <span class="lang-zh">人才计划</span><span class="lang-en">Talent Programs</span>

<div class="lang-zh">

- 入选**中国指挥与控制学会青年人才托举工程**
- 入选**湖南省“芙蓉计划”青年人才**
- 入选**国防科技大学高层次创新人才**

</div>

<div class="lang-en">

- Young Talent Support Program, Chinese Institute of Command and Control
- Hunan Province Furong Young Talent Program
- High-level Innovative Talent Program, National University of Defense Technology

</div>

### <span class="lang-zh">代表性荣誉</span><span class="lang-en">Selected Honors</span>

<div class="lang-zh">

- **2025年 CCF 科技成果一等奖**
- **全军优秀博士学位论文奖**
- **CCF 信息系统专委会优秀博士学位论文奖**
- 入选**全球前2%顶尖科学家榜单**

</div>

<div class="lang-en">

- CCF Science and Technology Achievement First Prize, 2025
- Outstanding Doctoral Dissertation Award of the PLA
- CCF Information Systems Technical Committee Outstanding Doctoral Dissertation Award
- Listed among the world's top 2% scientists

</div>

### <span class="lang-zh">科研项目</span><span class="lang-en">Research Projects</span>

<div class="lang-zh">

主持或承担**国家自然科学基金、教育部、军委科技委等科研项目5项**，围绕多视图学习理论、算法及相关应用开展研究。

</div>

<div class="lang-en">

Principal investigator or key participant in research projects funded by the National Natural Science Foundation of China, the Ministry of Education, and related national defense research programs.

</div>

-----

<span class='anchor' id='publications'></span>

# <i class="fas fa-book-open section-icon" aria-hidden="true"></i><span class="lang-en">Representative Publications</span><span class="lang-zh">代表性论文</span>

<p class="lang-zh">
近年来围绕多视图学习、联邦学习、多核学习以及复杂场景下的表示与聚类等方向开展研究。以下列出部分代表性论文，完整论文列表请访问
<a href="https://liujiyuan13.github.io/" target="_blank">English Homepage</a>。
</p>

<p class="lang-en">
Selected publications on multi-view learning, federated learning, multiple kernel learning, and clustering. For the complete publication list, please visit the
<a href="https://liujiyuan13.github.io/" target="_blank">English Homepage</a>.
</p>

<ol>

<li>
<strong>Hierarchical Anchor Graph Learning for Multi-View Clustering</strong><br>
International Conference on Machine Learning (<strong>ICML</strong>), 2026, CCF A.
</li>

<li>
<strong>Scalable Multi-View Subspace Clustering with Tensorized Anchor Guidance</strong><br>
IEEE/CVF Conference on Computer Vision and Pattern Recognition (<strong>CVPR</strong>), 2026, CCF A.
</li>

<li>
<strong>Communication-Efficient Federated Multi-view Clustering</strong><br>
IEEE Transactions on Pattern Analysis and Machine Intelligence (<strong>TPAMI</strong>), 2025, CCF A.
</li>

<li>
<strong>Incomplete Multi-view Deep Clustering with Data Imputation and Alignment</strong><br>
Conference on Neural Information Processing Systems (<strong>NeurIPS</strong>), 2025, CCF A.
</li>

<li>
<strong>Large-scale Multi-view Tensor Clustering with Implicit Linear Kernels</strong><br>
IEEE/CVF Conference on Computer Vision and Pattern Recognition (<strong>CVPR</strong>), 2025, CCF A.
</li>

<li>
<strong>Intra-view and Inter-view Correlation Guided Multi-view Novel Class Discovery</strong><br>
IEEE/CVF International Conference on Computer Vision (<strong>ICCV</strong>), 2025, CCF A.
</li>

<li>
<strong>On the Consistency and Large-Scale Extension of Multiple Kernel Clustering</strong><br>
IEEE Transactions on Pattern Analysis and Machine Intelligence (<strong>TPAMI</strong>), 2024, CCF A.
</li>

<li>
<strong>Decouple then Classify: A Dynamic Multi-view Labeling Strategy with Shared and Specific Information</strong><br>
International Conference on Machine Learning (<strong>ICML</strong>), 2024, CCF A.
</li>

<li>
<strong>Contrastive Multi-view Kernel Learning</strong><br>
IEEE Transactions on Pattern Analysis and Machine Intelligence (<strong>TPAMI</strong>), 2023, CCF A.
</li>

<li>
<strong>Stability and Generalization of Kernel Clustering: From Single Kernel to Multiple Kernel</strong><br>
Conference on Neural Information Processing Systems (<strong>NeurIPS</strong>), 2022, CCF A.
</li>

<li>
<strong>One-pass Multi-view Clustering for Large-scale Data</strong><br>
IEEE/CVF International Conference on Computer Vision (<strong>ICCV</strong>), 2021, CCF A.
</li>

<li>
<strong>Optimal Neighborhood Multiple Kernel Clustering with Adaptive Local Kernels</strong><br>
IEEE Transactions on Knowledge and Data Engineering (<strong>TKDE</strong>), 2020, CCF A, ESI 1% Highly Cited Paper.
</li>

</ol>

<p class="lang-zh">
更多论文及最新成果请参见
<a href="https://liujiyuan13.github.io/" target="_blank">英文个人主页</a>。
</p>

<p class="lang-en">
More publications are available on the
<a href="https://liujiyuan13.github.io/" target="_blank">English Homepage</a>.
</p>

-----


<span class='anchor' id='service'></span>

# <i class="fas fa-hands-helping section-icon" aria-hidden="true"></i><span class="lang-en">Academic Service</span><span class="lang-zh">学术服务</span>

<div class="lang-zh">

- **学术组织任职**：CCF理论计算机科学专委会执行委员、CAAI粒计算与知识发现专委会委员、CAAI信息融合相关专委会委员。

- **期刊审稿**：长期担任 IEEE TPAMI、IEEE TKDE、IEEE TIP、IEEE TNNLS、IEEE TCSVT、Information Fusion、Frontiers of Computer Science 等国际期刊审稿人。

- **会议服务**：担任 NeurIPS、ICML、ICLR、CVPR、ICCV、ACM Multimedia、WWW、AAAI、IJCAI 等国际会议领域主席、高级程序委员、程序委员或审稿人。

</div>

<div class="lang-en">

- Executive Committee Member of the CCF Technical Committee on Theoretical Computer Science, and committee member of relevant CAAI technical committees.

- Reviewer for IEEE TPAMI, IEEE TKDE, IEEE TIP, IEEE TNNLS, IEEE TCSVT, Information Fusion, Frontiers of Computer Science, and other journals.

- Area Chair / Senior Program Committee / Program Committee Member / Reviewer for NeurIPS, ICML, ICLR, CVPR, ICCV, ACM Multimedia, WWW, AAAI, IJCAI, and other major conferences.

</div>

-----

<script type='text/javascript' id='clustrmaps' src='//cdn.clustrmaps.com/map_v2.js?cl=ffffff&w=300&t=tt&d=QltdrDBXR7cYztdXsLCBfSeruYl8EMVZ7i3zpSoGzP4&co=2d78ad&cmo=3acc3a&cmn=ff5353&ct=ffffff'></script>
