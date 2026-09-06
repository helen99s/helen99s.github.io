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

  <p class="role-line">
    <i class="fas fa-user-graduate" aria-hidden="true"></i>
    副教授 · 硕士生导师
  </p>

  <div class="profile-meta">

    <span>
      <i class="fas fa-university" aria-hidden="true"></i>
      国防科技大学系统工程学院
    </span>

    <span>
      <i class="fas fa-envelope" aria-hidden="true"></i>
      <a href="mailto:liujiyuan13@nudt.edu.cn">
        liujiyuan13@nudt.edu.cn
      </a>
    </span>

  </div>

  <div class="profile-links">

    <a href="https://scholar.google.com/citations?user=frKTkdoAAAAJ"
       target="_blank">
      <i class="fas fa-graduation-cap" aria-hidden="true"></i>
      Google Scholar
    </a>

    <a href="https://github.com/liujiyuan13"
       target="_blank">
      <i class="fab fa-github" aria-hidden="true"></i>
      GitHub
    </a>

    <a href="https://liujiyuan13.github.io/"
       target="_blank">
      <i class="fas fa-globe" aria-hidden="true"></i>
      English Homepage
    </a>

  </div>

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
.lang-en {
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
  display: inline-block;
  width: auto;
  margin-right: 0.7rem;
  vertical-align: -0.04em;
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
  grid-template-columns: repeat(3, minmax(0, 285px));
  gap: 12px;
  justify-content: start;
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
  width: 100%;
  height: 180px;
  object-fit: contain;
  object-position: center;
  box-sizing: border-box;
  padding: 6px;
  background: #fff;
  border-bottom: 1px solid #e4eaf2;
}

.work-body {
  display: flex;
  flex: 1;
  flex-direction: column;
  padding: 10px 12px 12px;
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


@media (max-width: 1100px) {
  .works-grid {
    grid-template-columns: repeat(2, minmax(0, 285px));
  }
}

@media (max-width: 700px) {
  .works-grid {
    grid-template-columns: 1fr;
  }

  .work-card img {
    height: 180px;
  }
}

.section-lead {
  color: #59636f;
  line-height: 1.75;
  margin: 0.2rem 0 1rem;
}

.research-grid {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 14px;
  margin: 1rem 0 1.6rem;
}

.research-card {
  position: relative;
  border: 1px solid #d8e1ed;
  border-radius: 10px;
  padding: 18px 18px 16px;
  background: #fff;
}

.research-index {
  color: #365f91;
  font-size: 0.82rem;
  font-weight: 800;
  letter-spacing: 0.08em;
  margin-bottom: 10px;
}

.research-card h3 {
  color: #2f3945;
  font-size: 1.05rem;
  margin: 0 0 10px;
}

.research-card p {
  color: #58616c;
  font-size: 0.92rem;
  line-height: 1.7;
  margin: 0;
}

.research-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 6px;
  margin-top: 14px;
}

.research-tags span {
  background: #f3f6fa;
  border: 1px solid #dde5ef;
  border-radius: 999px;
  color: #365f91;
  font-size: 0.72rem;
  padding: 4px 8px;
}

@media (max-width: 900px) {
  .research-grid {
    grid-template-columns: 1fr;
  }
}

.experience-timeline {
  position: relative;
  margin: 1rem 0 1.7rem;
  padding-left: 22px;
}

.experience-timeline::before {
  content: "";
  position: absolute;
  left: 5px;
  top: 8px;
  bottom: 8px;
  width: 2px;
  background: #dbe3ed;
}

.experience-item {
  position: relative;
  display: grid;
  grid-template-columns: 135px 1fr;
  gap: 18px;
  padding: 0 0 22px 14px;
}

.experience-item::before {
  content: "";
  position: absolute;
  left: -21px;
  top: 7px;
  width: 10px;
  height: 10px;
  border: 3px solid #365f91;
  border-radius: 50%;
  background: #fff;
}

.experience-date {
  color: #365f91;
  font-weight: 700;
  font-size: 0.86rem;
  padding-top: 2px;
}

.experience-content h3 {
  font-size: 1rem;
  margin: 0 0 4px;
}

.experience-content p {
  color: #4e5965;
  margin: 0 0 3px;
}

.experience-content span {
  color: #7a8490;
  font-size: 0.84rem;
}

@media (max-width: 700px) {
  .experience-item {
    grid-template-columns: 1fr;
    gap: 4px;
  }
}

.info-grid {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 14px;
  margin: 1rem 0 1.7rem;
}

.info-card {
  border: 1px solid #d8e1ed;
  border-radius: 10px;
  padding: 18px;
  background: #fff;
}

.info-icon {
  color: #365f91;
  font-size: 1.15rem;
  margin-bottom: 10px;
}

.info-card h3 {
  font-size: 1rem;
  margin: 0 0 10px;
}

.info-card p {
  color: #59636f;
  font-size: 0.88rem;
  line-height: 1.6;
  margin: 0 0 6px;
}

@media (max-width: 900px) {
  .info-grid {
    grid-template-columns: 1fr;
  }
}

.info-grid {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 14px;
  margin: 1rem 0 1.7rem;
}

.info-card {
  border: 1px solid #d8e1ed;
  border-radius: 10px;
  padding: 18px;
  background: #fff;
}

.info-icon {
  color: #365f91;
  font-size: 1.15rem;
  margin-bottom: 10px;
}

.info-card h3 {
  font-size: 1rem;
  margin: 0 0 10px;
}

.info-card p {
  color: #59636f;
  font-size: 0.88rem;
  line-height: 1.6;
  margin: 0 0 6px;
}

@media (max-width: 900px) {
  .info-grid {
    grid-template-columns: 1fr;
  }
}

.service-grid {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 14px;
  margin: 1rem 0 1.7rem;
}

.service-card {
  border-top: 3px solid #365f91;
  background: #f8fafc;
  padding: 18px;
}

.service-card > i {
  color: #365f91;
  font-size: 1.1rem;
  margin-bottom: 10px;
}

.service-card h3 {
  font-size: 1rem;
  margin: 0 0 8px;
}

.service-card p {
  color: #59636f;
  font-size: 0.88rem;
  line-height: 1.65;
  margin: 0;
}

@media (max-width: 900px) {
  .service-grid {
    grid-template-columns: 1fr;
  }
}

.recruit-grid {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 14px;
  margin: 1rem 0 1.7rem;
}

.recruit-card {
  border: 1px solid #d8e1ed;
  border-radius: 10px;
  background: #fff;
  padding: 18px;
}

.recruit-icon {
  color: #365f91;
  font-size: 1.15rem;
  margin-bottom: 10px;
}

.recruit-card h3 {
  color: #303b47;
  font-size: 1rem;
  margin: 0 0 10px;
}

.recruit-card p {
  color: #59636f;
  font-size: 0.88rem;
  line-height: 1.7;
  margin: 0 0 8px;
}

.recruit-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 7px;
  margin: 0 0 12px;
}

.recruit-tags span {
  background: #f3f6fa;
  border: 1px solid #dde5ef;
  border-radius: 999px;
  color: #365f91;
  font-size: 0.76rem;
  padding: 5px 9px;
}

.recruit-note {
  color: #818a95 !important;
  font-size: 0.8rem !important;
}

.recruit-email a {
  color: #365f91;
  font-weight: 600;
}

@media (max-width: 900px) {
  .recruit-grid {
    grid-template-columns: 1fr;
  }
}

</style>

-----

<span class='anchor' id='about'></span>

# <i class="fas fa-id-card section-icon" aria-hidden="true"></i><span class="lang-en">About</span><span class="lang-zh">个人简介</span>

<p>
刘吉元，<a href="https://www.nudt.edu.cn/yssz/xtgcxy/index.htm" target="_blank" rel="noopener noreferrer">国防科技大学系统工程学院</a>副教授、硕士生导师，主要从事多视图学习理论、算法及其应用研究，重点关注多视图聚类、联邦多视图学习、多核学习以及复杂场景下的表示与信息融合。
</p>

<p>
2022年获国防科技大学博士学位，本科就读于钱学森创新拓展班。2016至2017年获国家留学基金委（CSC）资助，赴加拿大 Simon Fraser University
<a href="https://www.cs.sfu.ca/~jcliu/" target="_blank" rel="noopener noreferrer">Jiangchuan Liu 教授</a>团队访问交流；
自2019年起接受
<a href="https://xinwangliu.github.io/" target="_blank" rel="noopener noreferrer">刘新旺教授</a>、
杨岳湘教授及
<a href="https://ml.cs.uni-kl.de/people/marius-kloft.php" target="_blank" rel="noopener noreferrer">Marius Kloft 教授</a>
等联合指导。
</p>

<p>
围绕上述方向形成了系列研究成果，相关工作发表于 TPAMI、NeurIPS、ICML、CVPR、ICCV、ACM MM 等重要国际期刊与会议。代表性研究涵盖
<a href="#works">联邦多视图聚类、对比多视图核学习、大规模多视图聚类及不完整多视图深度聚类</a>
等方向。
</p>

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

<p class="lang-en">
For more updates, please visit the <a href="https://liujiyuan13.github.io/" target="_blank">English Homepage</a>.
</p>



-----

<span class='anchor' id='experience'></span>

# <i class="fas fa-briefcase section-icon" aria-hidden="true"></i>教育与工作经历

<div class="experience-timeline">

  <div class="experience-item">
    <div class="experience-date">2025 — 至今</div>
    <div class="experience-content">
      <h3>副教授</h3>
      <p>国防科技大学 · 系统工程学院</p>
    </div>
  </div>

  <div class="experience-item">
    <div class="experience-date">2022 — 2025</div>
    <div class="experience-content">
      <h3>讲师</h3>
      <p>国防科技大学 · 系统工程学院</p>
    </div>
  </div>

  <div class="experience-item">
    <div class="experience-date">2017 — 2022</div>
    <div class="experience-content">
      <h3>硕博研究生</h3>
      <p>国防科技大学 · 计算机学院</p>
      <span>2022年获博士学位</span>
    </div>
  </div>

  <div class="experience-item">
    <div class="experience-date">2016 — 2017</div>
    <div class="experience-content">
      <h3>访问学生</h3>
      <p>Simon Fraser University · Canada</p>
      <span>Jiangchuan Liu 教授团队，国家留学基金委（CSC）资助</span>
    </div>
  </div>

  <div class="experience-item">
    <div class="experience-date">2013 — 2017</div>
    <div class="experience-content">
      <h3>本科 · 钱学森创新拓展班</h3>
      <p>国防科技大学</p>
    </div>
  </div>

</div>

-----


<span class='anchor' id='openings'></span>

# <i class="fas fa-user-plus section-icon" aria-hidden="true"></i>招生与培养

<div class="opening-highlight">
  <i class="fas fa-bullhorn" aria-hidden="true"></i>
  欢迎对多视图学习、机器学习及相关研究方向感兴趣的同学联系交流。
  具体招生名额及要求以学校当年招生政策和导师安排为准。
</div>

<div class="recruit-grid">

  <div class="recruit-card">
    <div class="recruit-icon">
      <i class="fas fa-compass"></i>
    </div>

    <h3>主要招生方向</h3>

    <div class="recruit-tags">
      <span>多视图学习</span>
      <span>联邦多视图学习</span>
      <span>多视图聚类</span>
      <span>表示学习</span>
      <span>智能信息融合</span>
    </div>

    <p class="recruit-note">
      具体研究内容可参见下方“研究方向”模块。
    </p>
  </div>


  <div class="recruit-card">
    <div class="recruit-icon">
      <i class="fas fa-graduation-cap"></i>
    </div>

    <h3>招生信息</h3>

    <p>
      面向计算机、人工智能、自动化及相关专业背景的学生开展科研与研究生培养。
    </p>

    <p>
      具体招生类型、名额及申请要求以后续招生通知和导师安排为准。
    </p>
  </div>


  <div class="recruit-card">
    <div class="recruit-icon">
      <i class="fas fa-envelope"></i>
    </div>

    <h3>申请与联系</h3>

    <p>
      有意申请或参与科研的同学，可邮件联系并附个人简历、成绩单及简要研究兴趣介绍。
    </p>

    <p class="recruit-note">
      邮件主题建议注明：姓名 · 学校 · 专业 · 申请类型
    </p>
  </div>

</div>


-----

<span class='anchor' id='research'></span>

# <i class="fas fa-microscope section-icon" aria-hidden="true"></i>研究方向

<p class="section-lead">
主要围绕多源异构数据的表示、融合与学习开展研究，重点关注多视图学习理论与算法，以及面向复杂现实场景的高效、可靠机器学习方法。
</p>

<div class="research-grid">

  <div class="research-card">
    <div class="research-index">01</div>
    <h3>多视图学习与聚类</h3>
    <p>
      围绕多源异构数据中不同视图之间的一致性与互补性，研究多视图表示学习、聚类、多核学习与信息融合方法，探索更加完整、可靠的潜在结构。
    </p>
    <div class="research-tags">
      <span>Multi-view Clustering</span>
      <span>Representation Learning</span>
      <span>Multiple Kernel Learning</span>
    </div>
  </div>

  <div class="research-card">
    <div class="research-index">02</div>
    <h3>联邦多视图学习</h3>
    <p>
      面向数据分散、隐私保护和跨客户端协同场景，研究联邦环境下的多视图表示与聚类方法，重点关注异构数据协同、通信效率与模型泛化。
    </p>
    <div class="research-tags">
      <span>Federated Learning</span>
      <span>Privacy</span>
      <span>Distributed Learning</span>
    </div>
  </div>

  <div class="research-card">
    <div class="research-index">03</div>
    <h3>复杂场景多视图学习</h3>
    <p>
      面向真实应用中的缺失视图、大规模数据、动态数据和噪声干扰等问题，研究鲁棒、高效和可扩展的多视图学习方法。
    </p>
    <div class="research-tags">
      <span>Incomplete Views</span>
      <span>Large-scale Learning</span>
      <span>Robust Learning</span>
    </div>
  </div>

</div>

-----

-----

<span class='anchor' id='works'></span>

# <i class="fas fa-layer-group section-icon" aria-hidden="true"></i><span class="lang-en">Representative Works</span><span class="lang-zh">代表性成果</span>

<p class="lang-zh">
围绕多视图学习、多核学习、联邦协同、大规模数据和不完整数据等问题，形成了一系列具有代表性的研究成果。以下工作均为以第一作者身份完成的代表性论文。
</p>

<p class="lang-en">
Selected first-author works on multi-view learning, multiple kernel learning, federated learning, large-scale clustering, and incomplete multi-view learning.
</p>


<div class="works-grid">


<!-- ===================================================== -->
<!-- 1. Communication-Efficient Federated Multi-view Clustering -->
<!-- ===================================================== -->

<div class="work-card">

  <img
    src="/images/works/federated-mvc.jpg"
    alt="Communication-Efficient Federated Multi-view Clustering">

  <div class="work-body">

    <p class="work-kicker">
      <i class="fas fa-network-wired" aria-hidden="true"></i>
      TPAMI 2025
    </p>

    <h3>
      Communication-Efficient Federated Multi-view Clustering
    </h3>

    <p class="lang-zh">
      面向数据分散与隐私受限场景，研究通信高效的联邦多视图聚类方法，实现跨客户端多视图信息的有效协同建模。
    </p>

    <p class="lang-en">
      Communication-efficient federated multi-view clustering for distributed and privacy-preserving scenarios.
    </p>

    <p class="work-links">
      <a href="https://liujiyuan13.github.io/pdfs/CeFMC_early_access.pdf"
     target="_blank" rel="noopener noreferrer">Paper</a>
      ·
      <a href="https://github.com/liujiyuan13/CeFMC-code_release"
     target="_blank" rel="noopener noreferrer">Code</a>
    </p>

  </div>

</div>



<!-- ===================================================== -->
<!-- 2. Contrastive Multi-view Kernel Learning -->
<!-- ===================================================== -->

<div class="work-card">

  <img
    src="/images/works/cmkl.jpg"
    alt="Contrastive Multi-view Kernel Learning">

  <div class="work-body">

    <p class="work-kicker">
      <i class="fas fa-project-diagram" aria-hidden="true"></i>
      TPAMI 2023
    </p>

    <h3>
      Contrastive Multi-view Kernel Learning
    </h3>

    <p class="lang-zh">
      将对比学习思想引入多视图核学习，通过不同视图及核表示之间的结构关系建模，提升多源数据的表示与聚类能力。
    </p>

    <p class="lang-en">
      Contrastive learning for effective multi-view kernel representations and clustering.
    </p>

    <p class="work-links">
      <a href="https://liujiyuan13.github.io/pdfs/Contrastive_Multi-view_Kernel_Learning.pdf"
     target="_blank" rel="noopener noreferrer">Paper</a>
      ·
      <a href="https://github.com/liujiyuan13/CMK-code_release"
     target="_blank" rel="noopener noreferrer">Code</a>
    </p>

  </div>

</div>



<!-- ===================================================== -->
<!-- 3. Large-scale Multi-view Tensor Clustering -->
<!-- ===================================================== -->

<div class="work-card">

  <img
    src="/images/works/large-scale-mvc.jpg"
    alt="Large-scale Multi-view Tensor Clustering with Implicit Linear Kernels">

  <div class="work-body">

    <p class="work-kicker">
      <i class="fas fa-database" aria-hidden="true"></i>
      CVPR 2025
    </p>

    <h3>
      Large-scale Multi-view Tensor Clustering with Implicit Linear Kernels
    </h3>

    <p class="lang-zh">
      面向大规模多视图数据，研究基于隐式线性核与张量建模的高效聚类方法，提升多视图学习在大规模场景下的计算效率与可扩展性。
    </p>

    <p class="lang-en">
      Scalable tensor-based multi-view clustering with implicit linear kernels for large-scale data.
    </p>

    <p class="work-links">
      <a href="https://openaccess.thecvf.com/content/CVPR2025/papers/Liu_Large-scale_Multi-view_Tensor_Clustering_with_Implicit_Linear_Kernels_CVPR_2025_paper.pdf"
     target="_blank" rel="noopener noreferrer">Paper</a>
      ·
      <a href="https://github.com/liujiyuan13/LMTC-code_release"
     target="_blank" rel="noopener noreferrer">Code</a>
    </p>

  </div>

</div>



<!-- ===================================================== -->
<!-- 4. Incomplete Multi-view Deep Clustering -->
<!-- ===================================================== -->

<div class="work-card">

  <img
    src="/images/works/incomplete-mvc.jpg"
    alt="Incomplete Multi-view Deep Clustering with Data Imputation and Alignment">

  <div class="work-body">

    <p class="work-kicker">
      <i class="fas fa-puzzle-piece" aria-hidden="true"></i>
      NeurIPS 2025
    </p>

    <h3>
      Incomplete Multi-view Deep Clustering with Data Imputation and Alignment
    </h3>

    <p class="lang-zh">
      面向现实数据中的视图缺失问题，将数据补全与跨视图表示对齐相结合，实现更加鲁棒的不完整多视图深度聚类。
    </p>

    <p class="lang-en">
      Deep clustering for incomplete multi-view data through joint data imputation and representation alignment.
    </p>

    <p class="work-links">
      <a href="https://proceedings.neurips.cc/paper_files/paper/2025/file/8092824cd98b783ccba168446141d822-Paper-Conference.pdf"
     target="_blank" rel="noopener noreferrer">Paper</a>
      ·
      <a href="https://github.com/liujiyuan13/IMDC-DIA-code_release"
     target="_blank" rel="noopener noreferrer">Code</a>
    </p>

  </div>

</div>



<!-- ===================================================== -->
<!-- 5. One-pass Multi-view Clustering -->
<!-- ===================================================== -->

<div class="work-card">

  <img
    src="/images/works/one-pass-mvc.jpg"
    alt="One-pass Multi-view Clustering for Large-scale Data">

  <div class="work-body">

    <p class="work-kicker">
      <i class="fas fa-bolt" aria-hidden="true"></i>
      ICCV 2021
    </p>

    <h3>
      One-pass Multi-view Clustering for Large-scale Data
    </h3>

    <p class="lang-zh">
      面向大规模多视图数据的计算与存储压力，研究单遍式多视图聚类方法，在降低数据访问与计算开销的同时保持有效的聚类性能。
    </p>

    <p class="lang-en">
      One-pass multi-view clustering for efficient learning from large-scale multi-view data.
    </p>

    <p class="work-links">
      <a href="https://liujiyuan13.github.io/pdfs/One-pass_Multi-view_Clustering_for_Large-scale_Data.pdf"
     target="_blank" rel="noopener noreferrer">Paper</a>
      ·
      <a href="https://github.com/liujiyuan13/OPMC-code_release"
     target="_blank" rel="noopener noreferrer">Code</a>
    </p>

  </div>

</div>



<!-- ===================================================== -->
<!-- 6. Optimal Neighborhood Multiple Kernel Clustering -->
<!-- ===================================================== -->

<div class="work-card">

  <img
    src="/images/works/onmkc.jpg"
    alt="Optimal Neighborhood Multiple Kernel Clustering with Adaptive Local Kernels">

  <div class="work-body">

    <p class="work-kicker">
      <i class="fas fa-project-diagram" aria-hidden="true"></i>
      TKDE 2020 · ESI Highly Cited
    </p>

    <h3>
      Optimal Neighborhood Multiple Kernel Clustering with Adaptive Local Kernels
    </h3>

    <p class="lang-zh">
      面向多核聚类中的局部结构建模问题，通过自适应局部核学习刻画样本邻域关系，提升多核聚类的表示能力与聚类性能。该工作入选 ESI 高被引论文。
    </p>

    <p class="lang-en">
      Adaptive local kernel learning for effective neighborhood modeling in multiple kernel clustering. This work was selected as an ESI Highly Cited Paper.
    </p>

    <p class="work-links">
      <a href="https://liujiyuan13.github.io/pdfs/Optimal_Neighborhood_Multiple_Kernel_Clustering_with_Adaptive_Local_Kernels.pdf"
     target="_blank" rel="noopener noreferrer">Paper</a>
      ·
      <a href="https://github.com/liujiyuan13/ON-ALK_release_code"
     target="_blank" rel="noopener noreferrer">Code</a>
    </p>

  </div>

</div>


</div>

-----

-----

<span class='anchor' id='projects'></span>

# <i class="fas fa-tasks section-icon" aria-hidden="true"></i>科研项目与荣誉

<div class="info-grid">

  <div class="info-card">
    <div class="info-icon">
      <i class="fas fa-user-tie"></i>
    </div>
    <h3>人才计划</h3>
    <p>中国指挥与控制学会青年人才托举工程</p>
    <p>湖南省“芙蓉计划”青年人才</p>
    <p>国防科技大学高层次创新人才</p>
  </div>

  <div class="info-card">
    <div class="info-icon">
      <i class="fas fa-award"></i>
    </div>
    <h3>代表性荣誉</h3>
    <p>2025年 CCF 科技成果一等奖</p>
    <p>全军优秀博士学位论文奖</p>
    <p>CCF 信息系统专委会优秀博士学位论文奖</p>
    <p>全球前2%顶尖科学家榜单</p>
  </div>

  <div class="info-card">
    <div class="info-icon">
      <i class="fas fa-flask"></i>
    </div>
    <h3>科研项目</h3>
    <p>
      主持或承担国家自然科学基金、教育部、军委科技委等科研项目5项。
    </p>
    <p>
      聚焦多视图学习理论、算法及相关应用研究。
    </p>
  </div>

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


<p class="lang-en">
More publications are available on the
<a href="https://liujiyuan13.github.io/" target="_blank">English Homepage</a>.
</p>

-----


<span class='anchor' id='service'></span>

# <i class="fas fa-hands-helping section-icon" aria-hidden="true"></i>学术服务

<div class="service-grid">

  <div class="service-card">
    <i class="fas fa-users"></i>
    <h3>学术组织</h3>
    <p>
      CCF理论计算机科学专委会执行委员、CAAI粒计算与知识发现专委会委员、CAAI信息融合相关专委会委员。
    </p>
  </div>

  <div class="service-card">
    <i class="fas fa-book-open"></i>
    <h3>期刊服务</h3>
    <p>
      IEEE TPAMI、TKDE、TIP、TNNLS、TCSVT、Information Fusion、Frontiers of Computer Science 等期刊审稿人。
    </p>
  </div>

  <div class="service-card">
    <i class="fas fa-globe"></i>
    <h3>会议服务</h3>
    <p>
      NeurIPS、ICML、ICLR、CVPR、ICCV、ACM MM、WWW、AAAI、IJCAI 等会议领域主席、高级程序委员、程序委员或审稿人。
    </p>
  </div>

</div>

-----

<script type='text/javascript' id='clustrmaps' src='//cdn.clustrmaps.com/map_v2.js?cl=ffffff&w=300&t=tt&d=QltdrDBXR7cYztdXsLCBfSeruYl8EMVZ7i3zpSoGzP4&co=2d78ad&cmo=3acc3a&cmn=ff5353&ct=ffffff'></script>
