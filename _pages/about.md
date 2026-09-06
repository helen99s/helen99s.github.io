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

- <i class="far fa-calendar-alt news-icon" aria-hidden="true"></i><span class="lang-en">*2026.08*: Our paper [*"Irregularity-Aware 3D Anomaly Detection for Product Quality Control"*](https://ieeexplore.ieee.org/document/11670526/) has been accepted by **IEEE Transactions on Automation Science and Engineering (TASE)**.</span><span class="lang-zh">*2026.08*: 论文 [*"Irregularity-Aware 3D Anomaly Detection for Product Quality Control"*](https://ieeexplore.ieee.org/document/11670526/) 获 IEEE Transactions on Automation Science and Engineering（TASE）录用。</span>
- <i class="far fa-calendar-alt news-icon" aria-hidden="true"></i><span class="lang-en">*2026.07*: Our paper *"Towards Active Real-to-Twin Inspection: A New Paradigm for Zero-Shot Anomaly Detection"* was selected as a Best Student Paper Finalist at **IEEE CYBER 2026**.</span><span class="lang-zh">*2026.07*: 论文 *"Towards Active Real-to-Twin Inspection: A New Paradigm for Zero-Shot Anomaly Detection"* 入选 IEEE CYBER 2026 Best Student Paper Finalist。</span>
- <i class="far fa-calendar-alt news-icon" aria-hidden="true"></i><span class="lang-en">*2026.07*: Congratulations to Wenzhuo Sun. His project, *"Zero-shot Industrial Anomaly Detection Based on Active Embodied Vision and a Digital Twin,"* which I supervise, has been approved as a key-support project under the National Undergraduate Innovation Training Program.</span><span class="lang-zh">*2026.07*: 恭喜孙文卓！其负责并由本人指导的项目《基于主动具身视觉与数字孪生的零样本工业异常检测关键技术研究》获批为国家级大学生创新训练计划重点支持领域项目。</span>
- <i class="far fa-calendar-alt news-icon" aria-hidden="true"></i><span class="lang-en">*2026.06*: I was elected Deputy Director of the Department of Robotics Engineering, School of Artificial Intelligence and Robotics, Hunan University.</span><span class="lang-zh">*2026.06*: 当选湖南大学人工智能与机器人学院机器人工程系副主任。</span>
- <i class="far fa-calendar-alt news-icon" aria-hidden="true"></i><span class="lang-en">*2026.05*: Congratulations to Yuhuan Du. His first-author paper, *"OmniPose-AD: Canonical Normal Rendering for Unaligned 3D Anomaly Detection,"* received the Best Student Paper Award at ICAIS & ISAS 2026. I am the corresponding author.</span><span class="lang-zh">*2026.05*: 恭喜杜禹寰！其以第一作者完成的论文《OmniPose-AD: Canonical Normal Rendering for Unaligned 3D Anomaly Detection》获 ICAIS & ISAS 2026 Best Student Paper Award，本人担任通讯作者。</span>
- <i class="far fa-calendar-alt news-icon" aria-hidden="true"></i><span class="lang-en">*2026.05*: Our paper *"Cross-source Medical Anomaly Detection via Prompt-guided Diffusion Representations"* has been accepted by **Pattern Recognition**.</span><span class="lang-zh">*2026.05*: 论文 *"Cross-source Medical Anomaly Detection via Prompt-guided Diffusion Representations"* 获 Pattern Recognition 录用。</span>

<details class="news-archive">
<summary><span class="lang-en">View earlier news</span><span class="lang-zh">查看往期动态</span></summary>
<div class="news-archive-list" markdown="1">

- <i class="far fa-calendar-alt news-icon" aria-hidden="true"></i><span class="lang-en">*2026.04*: The *Pattern Recognition* Special Issue on *Foundation Models for Anomaly Detection, Reasoning, and Recovery* officially closed for submissions, receiving more than 230 manuscripts.</span><span class="lang-zh">*2026.04*: Pattern Recognition 特刊 *"Foundation Models for Anomaly Detection, Reasoning, and Recovery"* 正式截稿，累计收到 230 余篇稿件。</span>
- <i class="far fa-calendar-alt news-icon" aria-hidden="true"></i><span class="lang-en">*2026.03*: Our paper *"Visual Anomaly Detection under Complex View-Illumination Interplay: A Large-Scale Benchmark"* has been accepted by **Pattern Recognition**.</span><span class="lang-zh">*2026.03*: 论文 *"Visual Anomaly Detection under Complex View-Illumination Interplay: A Large-Scale Benchmark"* 获 Pattern Recognition 录用。</span>
- <i class="far fa-calendar-alt news-icon" aria-hidden="true"></i><span class="lang-en">*2026.01*: Our survey paper *"A Comprehensive Survey for Real-World Industrial Defect Detection"* has been accepted by **Journal of Manufacturing Systems (JMS)**.</span><span class="lang-zh">*2026.01*: 综述论文 *"A Comprehensive Survey for Real-World Industrial Defect Detection"* 获 Journal of Manufacturing Systems 录用。</span>
- <i class="far fa-calendar-alt news-icon" aria-hidden="true"></i><span class="lang-en">*2025.12*: Our paper on [Zero-shot 3D Anomaly Detection](https://arxiv.org/pdf/2409.13162) has been accepted by **IEEE TSMC**.</span><span class="lang-zh">*2025.12*: 零样本 3D 异常检测论文获 IEEE TSMC 录用。</span>
- <i class="far fa-calendar-alt news-icon" aria-hidden="true"></i><span class="lang-en">*2025.11*: Three papers on high-resolution point cloud anomaly detection, zero-shot anomaly generation, and foundation models for anomaly detection have been accepted by **AAAI 2026**, including two oral presentations.</span><span class="lang-zh">*2025.11*: 课题组 3 篇论文获 AAAI 2026 录用，分别围绕高分辨率点云异常检测、零样本异常生成和异常检测基础模型展开，其中 2 篇入选 Oral。</span>
- <i class="far fa-calendar-alt news-icon" aria-hidden="true"></i><span class="lang-en">*2025.09*: I serve as the Executive Guest Editor for the *Pattern Recognition* Special Issue on *Foundation Models for Anomaly Detection, Reasoning, and Recovery*.</span><span class="lang-zh">*2025.09*: 担任 Pattern Recognition 特刊 *"Foundation Models for Anomaly Detection, Reasoning, and Recovery"* 执行客座编辑。</span>
- <i class="far fa-calendar-alt news-icon" aria-hidden="true"></i><span class="lang-en">*2025.05*: Congratulations to Xiaohao Xu. The paper *"Customizing Visual-Language Foundation Models for Multi-Modal Anomaly Detection and Reasoning,"* co-first-authored by Xiaohao Xu and me, received the Best Student Paper Award at **IEEE CSCWD 2025**.</span><span class="lang-zh">*2025.05*: 恭喜徐晓豪！论文《Customizing Visual-Language Foundation Models for Multi-Modal Anomaly Detection and Reasoning》获 IEEE CSCWD 2025 Best Student Paper Award，我与徐晓豪为共同第一作者。</span>
- <i class="far fa-calendar-alt news-icon" aria-hidden="true"></i><span class="lang-en">*2025.04*: We organized the CVPR 2025 pre-conference "Industrial Vision" special session, attracting more than 5,000 online viewers.</span><span class="lang-zh">*2025.04*: 组织 CVPR 2025 预会议“工业视觉”专场，线上观看人数超过 5000。</span>
- <i class="far fa-calendar-alt news-icon" aria-hidden="true"></i><span class="lang-en">*2025.03*: Two papers on unified anomaly detection and unseen anomaly generation have been accepted by **CVPR 2025**.</span><span class="lang-zh">*2025.03*: 统一异常检测与未见异常生成方向的 2 篇论文获 CVPR 2025 录用。</span>

</div>
</details>


-----

<span class='anchor' id='experience'></span>

# <i class="fas fa-graduation-cap section-icon" aria-hidden="true"></i><span class="lang-en">Education and Experience</span><span class="lang-zh">学习与工作经历</span>

<ul>
  <li><span class="lang-en"><strong>2025.05 - Present</strong>, Assistant Professor / Associate Research Fellow, School of Artificial Intelligence and Robotics, Hunan University.</span><span class="lang-zh"><strong>2025.05 至今</strong>，湖南大学，人工智能与机器人学院，助理教授 / 副研究员。</span></li>
  <li><span class="lang-en"><strong>2020.09 - 2025.06</strong>, Ph.D. in Mechanical Engineering, Huazhong University of Science and Technology. Advisor: <a href="https://scholar.google.com.hk/citations?user=FuSHsx4AAAAJ&hl=en&oi=sra">Prof. Weiming Shen</a>.</span><span class="lang-zh"><strong>2020.09 - 2025.06</strong>，华中科技大学，机械工程，博士，导师：沈卫明教授。</span></li>
  <li><span class="lang-en"><strong>2023.10 - 2024.10</strong>, Visiting Ph.D. Researcher, Politecnico di Milano. Host: <a href="https://boracchi.faculty.polimi.it/">Prof. Giacomo Boracchi</a>.</span><span class="lang-zh"><strong>2023.10 - 2024.10</strong>，米兰理工大学，计算机科学，访问博士生，合作导师：Giacomo Boracchi。</span></li>
  <li><span class="lang-en"><strong>2016.09 - 2020.06</strong>, B.E. in Mechanical Design, Manufacturing and Automation, Huazhong University of Science and Technology.</span><span class="lang-zh"><strong>2016.09 - 2020.06</strong>，华中科技大学，机械设计制造及其自动化，学士。</span></li>
</ul>

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
Selected works on multi-view learning, federated learning, large-scale clustering, and incomplete multi-view learning.
</p>

<div class="works-grid">

  <div class="work-card">
    <img src="/images/work_fmvc.png" alt="Federated Multi-view Clustering">
    <div class="work-body">
      <p class="work-kicker">
        <i class="fas fa-network-wired"></i>
        TPAMI 2025
      </p>
      <h3>Communication-Efficient Federated Multi-view Clustering</h3>
      <p class="lang-zh">
        面向数据分散与隐私受限场景，研究通信高效的联邦多视图聚类方法，实现跨客户端多视图信息的协同建模。
      </p>
      <p class="lang-en">
        Communication-efficient federated multi-view clustering under distributed and privacy-preserving settings.
      </p>
      <p class="work-links">
        <a href="#">Paper</a>
        ·
        <a href="#">Code</a>
      </p>
    </div>
  </div>


  <div class="work-card">
    <img src="/images/work_cmkl.png" alt="Contrastive Multi-view Kernel Learning">
    <div class="work-body">
      <p class="work-kicker">
        <i class="fas fa-project-diagram"></i>
        TPAMI 2023
      </p>
      <h3>Contrastive Multi-view Kernel Learning</h3>
      <p class="lang-zh">
        将对比学习思想引入多视图核学习，通过不同视图与核表示之间的结构关系提升多源数据的聚类表示能力。
      </p>
      <p class="lang-en">
        Contrastive learning for multi-view kernel representations and clustering.
      </p>
      <p class="work-links">
        <a href="#">Paper</a>
        ·
        <a href="#">Code</a>
      </p>
    </div>
  </div>


  <div class="work-card">
    <img src="/images/work_lmvc.png" alt="Large-scale Multi-view Tensor Clustering">
    <div class="work-body">
      <p class="work-kicker">
        <i class="fas fa-database"></i>
        CVPR 2025
      </p>
      <h3>Large-scale Multi-view Tensor Clustering with Implicit Linear Kernels</h3>
      <p class="lang-zh">
        面向大规模多视图数据，研究基于隐式线性核和张量建模的高效聚类方法，提升多视图学习在大规模场景下的可扩展性。
      </p>
      <p class="lang-en">
        Scalable tensor-based multi-view clustering with implicit linear kernels.
      </p>
      <p class="work-links">
        <a href="#">Paper</a>
        ·
        <a href="#">Code</a>
      </p>
    </div>
  </div>


  <div class="work-card">
    <img src="/images/work_imvc.png" alt="Incomplete Multi-view Deep Clustering">
    <div class="work-body">
      <p class="work-kicker">
        <i class="fas fa-puzzle-piece"></i>
        NeurIPS 2025
      </p>
      <h3>Incomplete Multi-view Deep Clustering with Data Imputation and Alignment</h3>
      <p class="lang-zh">
        面向现实数据中的视图缺失问题，将数据补全与跨视图表示对齐结合，实现更加鲁棒的不完整多视图深度聚类。
      </p>
      <p class="lang-en">
        Deep clustering for incomplete multi-view data through joint imputation and alignment.
      </p>
      <p class="work-links">
        <a href="#">Paper</a>
        ·
        <a href="#">Code</a>
      </p>
    </div>
  </div>

</div>

-----
-----

<span class='anchor' id='projects'></span>

# <i class="fas fa-tasks section-icon" aria-hidden="true"></i><span class="lang-en">Selected Research Projects</span><span class="lang-zh">部分科研项目</span>

<ol>
  <li><span class="lang-en">National Natural Science Foundation of China, Major Program Topic, <strong>Cross-species Multi-sensory and Multi-granularity Bionic Perception</strong>, 62595801, 2026/01 - 2030/12, ongoing, participant.</span><span class="lang-zh">国家自然科学基金委员会重大项目课题，<strong>跨物种多感官多粒度仿生感知</strong>，62595801，2026/01 - 2030/12，在研，参与。</span></li>
  <li><span class="lang-en">Yuelushan Laboratory Seed Industry Special Project, <strong>Key Technologies and Applications for Crop Holographic Phenotype Acquisition and Analysis</strong>, YLS-20026-ZY01003, 2026/03 - 2028/03, ongoing, sub-project leader.</span><span class="lang-zh">岳麓山实验室种业专项，“人工智能+生物育种”技术攻关项目，<strong>作物全息表型采集与解析关键技术及应用</strong>，YLS-20026-ZY01003，2026/03 - 2028/03，在研，子课题负责人。</span></li>
  <li><span class="lang-en">Fuyao University of Science and Technology, School of Intelligent Manufacturing and Future Technology Open Fund, <strong>Semi-supervised Industrial Image Anomaly Detection via Defect Generation</strong>, FIMFYUST-2025B05, 2025/07 - 2027/07, ongoing, principal investigator.</span><span class="lang-zh">福耀科技大学智造与未来技术学院开放基金，<strong>基于缺陷生成的半监督工业图像异常检测算法研究</strong>，FIMFYUST-2025B05，2025/07 - 2027/07，在研，主持。</span></li>
  <li><span class="lang-en">Zhejiang University Hangzhou International Innovation Center entrusted project, <strong>AI Defect Sample Generation Algorithm Development</strong>, 2026/01 - 2026/12, ongoing, principal investigator.</span><span class="lang-zh">浙江大学杭州国际科创中心委托项目，<strong>AI 缺陷样本生成算法开发</strong>，2026/01 - 2026/12，在研，主持。</span></li>
  <li><span class="lang-en">Fundamental Research Funds for the Central Universities, <strong>Foundation-model-driven Anomaly Detection, Reasoning, and Recovery</strong>, 2025/10 - 2030/10, ongoing, principal investigator.</span><span class="lang-zh">中央高校基本科研基金项目，<strong>基于基础模型驱动的异常检测、推理与修复技术研究</strong>，2025/10 - 2030/10，在研，主持。</span></li>
</ol>

-----

<span class='anchor' id='teaching'></span>

# <i class="fas fa-chalkboard-teacher section-icon" aria-hidden="true"></i><span class="lang-en">Teaching</span><span class="lang-zh">开设课程</span>

## <i class="fas fa-user-graduate section-icon" aria-hidden="true"></i><span class="lang-en">Undergraduate Courses</span><span class="lang-zh">本科生课程</span>

- <span class="lang-en">Mathematical Foundations of Artificial Intelligence, 32 hours</span><span class="lang-zh">人工智能中的数学基础，32 学时</span>
- <span class="lang-en">Circuit Experiments, 32 hours</span><span class="lang-zh">电路实验，32 学时</span>
- <span class="lang-en">Electronic Technology Practice II, 32 hours</span><span class="lang-zh">电子技术实践 II，32 学时</span>

## <i class="fas fa-graduation-cap section-icon" aria-hidden="true"></i><span class="lang-en">Graduate Courses</span><span class="lang-zh">研究生课程</span>

- <span class="lang-en">Philosophy and Ethics in Artificial Intelligence, 32 hours</span><span class="lang-zh">人工智能中的哲学与伦理，32 学时</span>
- <span class="lang-en">Robotics for the Future, 32 hours</span><span class="lang-zh">面向未来的机器人，32 学时</span>

-----

<span class='anchor' id='publications'></span>

# <i class="fas fa-book-open section-icon" aria-hidden="true"></i><span class="lang-en">Representative Publications</span><span class="lang-zh">代表性论文</span>

Note: \* indicates equal contribution. † indicates corresponding author.
{: .lang-en}

说明：\* 表示共同第一作者，† 表示通讯作者。完整列表请见 [Google Scholar](https://scholar.google.com/citations?hl=zh-CN&user=aLJ8_G4AAAAJ&view_op=list_works&sortby=pubdate).
{: .lang-zh}

[![Citations](https://img.shields.io/badge/Citations-2300%2B-007ec6?logo=google-scholar&logoColor=white)](https://scholar.google.com/citations?hl=zh-CN&user=aLJ8_G4AAAAJ)
[![H-index](https://img.shields.io/badge/H--index-21-2563eb?logo=google-scholar&logoColor=white)](https://scholar.google.com/citations?hl=zh-CN&user=aLJ8_G4AAAAJ)
[![GitHub](https://img.shields.io/badge/GitHub-caoyunkang-181717?logo=github&logoColor=white)](https://github.com/caoyunkang)

## <i class="fas fa-magic section-icon" aria-hidden="true"></i><span class="lang-en">Anomaly Generation</span><span class="lang-zh">异常生成</span>

<ol>
  <li>Sun H, Cao Y（曹云康）, Dong H, et al. Unseen Visual Anomaly Generation. <i>IEEE/CVF Conference on Computer Vision and Pattern Recognition</i>, 2025. doi:10.1109/CVPR52734.2025.02375. CCF-A.</li>
  <li>Jiang Y, Luo W, Zhang H, Shen W, Cao Y†（曹云康）. Anomagic: Crossmodal Prompt-driven Zero-shot Anomaly Generation. <i>AAAI Conference on Artificial Intelligence</i>, 2026. doi:10.48550/arXiv.2511.10020. CCF-A.</li>
  <li>Cheng Y, Cao Y（曹云康）, Wang D, et al. Boosting global-local feature matching via anomaly synthesis for multi-class point cloud anomaly detection. <i>IEEE Transactions on Automation Science and Engineering</i>, 22: 12560-12571, 2025. doi:10.1109/TASE.2025.3544462. 中科院二区.</li>
  <li>Cao Y（曹云康）, Yao H, Cai Y, Zhang Y, Chen H, Zhang H, Shen W. Cross-source medical anomaly detection via prompt-guided diffusion representations. <i>Pattern Recognition</i>, 2026, 180(Part A): 113985. doi:10.1016/j.patcog.2026.113985.</li>
</ol>

## <i class="fas fa-search section-icon" aria-hidden="true"></i><span class="lang-en">Anomaly Detection</span><span class="lang-zh">异常检测</span>

<ol>
  <li>Cheng Y, Cao Y（曹云康）, Yao H, Luo W, Zhang J, Shen W. <a href="https://ieeexplore.ieee.org/document/11670526/">Irregularity-Aware 3D Anomaly Detection for Product Quality Control</a>. <i>IEEE Transactions on Automation Science and Engineering</i>, 2026. doi:10.1109/TASE.2026.3728551. 中科院二区.</li>
  <li>Cao Y（曹云康）, Zhang J, Frittoli L, et al. AdaCLIP: Adapting CLIP with Hybrid Learnable Prompts for Zero-Shot Anomaly Detection. <i>European Conference on Computer Vision</i>, 2025. doi:10.1007/978-3-031-72761-0_4. CCF-B.</li>
  <li>Luo W*, Cao Y*（曹云康）, Yao H, et al. Exploring Intrinsic Normal Prototypes within a Single Image for Universal Anomaly Detection. <i>IEEE/CVF Conference on Computer Vision and Pattern Recognition</i>, 2025. doi:10.1109/CVPR52734.2025.00932. CCF-A.</li>
  <li>Cao Y（曹云康）, Xu X, Cheng Y, et al. Personalizing Vision-Language Models with Hybrid Prompts for Zero-Shot Anomaly Detection. <i>IEEE Transactions on Cybernetics</i>, 55(4): 1917-1929, 2025. 中科院一区.</li>
  <li>Cao Y（曹云康）, Xu X, Liu Z, et al. Collaborative discrepancy optimization for reliable image anomaly localization. <i>IEEE Transactions on Industrial Informatics</i>, 19(11): 10674-10683, 2023. 中科院一区.</li>
  <li>Cao Y（曹云康）, Yao H, Luo W, et al. VarAD: Lightweight High-Resolution Image Anomaly Detection via Visual Autoregressive Modeling. <i>IEEE Transactions on Industrial Informatics</i>, 21(4): 3246-3255, 2025. 中科院一区，高被引论文.</li>
  <li>Cao Y（曹云康）, Xu X, Shen W. Complementary pseudo multimodal feature for point cloud anomaly detection. <i>Pattern Recognition</i>, 156: 110761, 2024. doi:10.1016/j.patcog.2024.110761. 中科院一区.</li>
  <li>Cheng Y*, Cao Y*（曹云康）, Xie G, et al. Towards zero-shot point cloud anomaly detection: A multi-view projection framework. <i>IEEE Transactions on Systems, Man, and Cybernetics: Systems</i>, 53(3): 1747-1760, 2026. doi:10.1109/TSMC.2025.3648581. 中科院一区.</li>
  <li>Cao Y（曹云康）, Cheng Y, Zhang Y, et al. Visual anomaly detection under complex view-illumination interplay: A large-scale benchmark. <i>Pattern Recognition</i>, 2026.</li>
</ol>

## <i class="fas fa-brain section-icon" aria-hidden="true"></i><span class="lang-en">Anomaly Understanding</span><span class="lang-zh">异常理解</span>

<ol>
  <li>Li Y, Cao Y（曹云康）, Liu C, et al. IAD-R1: Reinforcing Consistent Reasoning in Industrial Anomaly Detection. <i>AAAI Conference on Artificial Intelligence</i>, 2026. doi:10.48550/arXiv.2508.09178. CCF-A, Oral.</li>
  <li>Xu X, Cao Y（曹云康）, Zhang H, Sang N, Huang X. Customizing Visual-Language Foundation Models for Multi-Modal Anomaly Detection and Reasoning. <i>International Conference on Computer Supported Cooperative Work in Design</i>, 2025. CCF-C, Best Student Paper Award.</li>
  <li>Zhang Y, Cao Y（曹云康）, Xu X, et al. LogiCode: An LLM-Driven Framework for Logical Anomaly Detection. <i>IEEE Transactions on Automation Science and Engineering</i>, 22: 7712-7723, 2025. 中科院二区.</li>
  <li>Cai W, Huang W, Cao Y（曹云康）, et al. Towards VLM-based Hybrid Explainable Prompt Enhancement for Zero-Shot Industrial Anomaly Detection. <i>International Joint Conference on Artificial Intelligence</i>, 2025. CCF-A.</li>
</ol>

## <i class="fas fa-robot section-icon" aria-hidden="true"></i><span class="lang-en">Embodied Perception</span><span class="lang-zh">具身感知</span>

<ol>
  <li>Liu J*, Cao Y*（曹云康）, Chen Y*, Li C, Du Y, Zhang H. Towards Active Real-to-Twin Inspection: A New Paradigm for Zero-Shot Anomaly Detection. <i>The 16th IEEE International Conference on CYBER Technology in Automation, Control, and Intelligent Systems</i>, 2026. arXiv:2605.25407. Best Student Paper Finalist.</li>
  <li>Du Y, Zhang H, Cheng Y, Huang C, Cao Y†（曹云康）. OmniPose-AD: Canonical Normal Rendering for Unaligned 3D Anomaly Detection. <i>2026 Joint International Conference on Automation-Intelligence-Safety and International Symposium on Autonomous Systems</i>, 2026: 1-6. doi:10.1109/ICAISISAS68969.2026.11567774. Best Student Paper.</li>
  <li>Cheng Y, Sun Y, Zhang H, Shen W, Cao Y†（曹云康）. Towards high-resolution 3D anomaly detection: A scalable dataset and real-time framework for subtle industrial defects. <i>AAAI Conference on Artificial Intelligence</i>, 2026. doi:10.48550/arXiv.2507.07435. CCF-A, Oral.</li>
  <li>Zhang H, Liu H, Biekezati B, Cao Y（曹云康）, et al. FPF: A Focused Perception Framework for Small Defect Identification in Complex Power Scenarios. <i>IEEE Transactions on Industrial Informatics</i>, doi:10.1109/TII.2025.3649024, 2026. 中科院一区.</li>
</ol>

-----

<span class='anchor' id='patents'></span>

# <i class="fas fa-certificate section-icon" aria-hidden="true"></i><span class="lang-en">Selected Authorized Patents</span><span class="lang-zh">代表性授权专利</span>

<ol>
  <li>张辉，杜瑞，别克扎提·巴合提，陈厚权，邱宇，张恺宁，曹云康，王耀南. 一种基于霍奇分解与多模态融合的部件分割方法及系统：中国，ZL202511195689.2，2025年10月31日，授权。</li>
  <li>张辉，唐友源，杜瑞，别克扎提·巴合提，陈厚权，张恺宁，曹云康，邱宇，王耀南. 一种基于结构感知框架的架空电力线覆冰厚度检测方法和系统：中国，ZL202511195907.2，2025年10月31日，授权。</li>
  <li>沈卫明，程育奇，曹云康，张以恒，孙依晗，谭宇翔，张雨昕. 一种复杂零件缺陷数据标注方法、缺陷检测方法及多视角多光照数据采集装置：中国，ZL202510060769.0，2025年12月2日，授权。</li>
  <li>沈卫明，程育奇，曹云康. 一种考虑原型分数校正的点云异常检测方法及设备：中国，ZL202510040267.1，2026年2月17日，授权。</li>
  <li>沈卫明，程育奇，曹云康. 一种点云数据局部异常生成方法及系统：中国，ZL202410633098.8，2025年2月11日，授权。</li>
  <li>沈卫明，程育奇，曹云康. 一种考虑多层级特征的多类别点云异常检测方法及系统：中国，ZL202410622146.3，2025年2月11日，授权。</li>
  <li>沈卫明，程育奇，曹云康. 一种考虑提示学习的零样本点云异常检测方法及系统：中国，ZL202410359413.2，2024年11月5日，授权。</li>
  <li>沈卫明，姜雨欣，曹云康. 基于原型学习引导的判别分割网络的小样本缺陷检测方法：中国，ZL202311254405.3，2025年11月4日，授权。</li>
  <li>沈卫明，刘照阁，徐晓豪，曹云康. 基于像素单点及多元配对的无监督异常检测方法：中国，ZL202310570510.1，2026年1月6日，授权。</li>
  <li>沈卫明，姜雨欣，曹云康. 一种工业缺陷检测方法及系统：中国，ZL202310570502.7，2025年11月21日，授权。</li>
</ol>

-----

<span class='anchor' id='awards'></span>

# <i class="fas fa-award section-icon" aria-hidden="true"></i><span class="lang-en">Awards</span><span class="lang-zh">科研获奖经历</span>

<ol>
  <li><span class="lang-en">Key Technologies and Applications of Multimodal Perception and Collaborative Optimization for Collaborative Intelligent Manufacturing, China Association of Inventions Invention Entrepreneurship Award, Project Award Second Prize, 3rd ranked, Dec. 2025.</span><span class="lang-zh">面向协同智能制造的多模态感知与协同优化关键技术及应用，中国发明协会发明创业奖项目奖二等奖，排名第三，2025年12月。</span></li>
  <li><span class="lang-en">Key Technologies and Applications of Multimodal Perception and Collaborative Optimization for Collaborative Intelligent Manufacturing, Gold Award of the 29th National Invention Exhibition, 3rd ranked, Oct. 2025.</span><span class="lang-zh">面向协同智能制造的多模态感知与协同优化关键技术及应用，第二十九届全国发明展览会金奖，排名第三，2025年10月。</span></li>
  <li><span class="lang-en">Yunkang Cao, Xiaohao Xu, Chen Sun, Yuqi Cheng, Liang Gao, Weiming Shen. Runner-up, CVPR Visual Anomaly and Novelty Detection Challenge, Jun. 2023.</span><span class="lang-zh">Yunkang Cao, Xiaohao Xu, Chen Sun, Yuqi Cheng, Liang Gao, Weiming Shen. CVPR Visual Anomaly and Novelty Detection Challenge，全球亚军，2023年6月。</span></li>
  <li><span class="lang-en">Xiaohao Xu, Yunkang Cao, Huaxin Zhang, Nong Sang, Xiaonan Huang. Best Student Paper Award, IEEE Computer Supported Cooperative Work in Design, May 2025.</span><span class="lang-zh">Xiaohao Xu, Yunkang Cao, Huaxin Zhang, Nong Sang, Xiaonan Huang. IEEE Computer Supported Cooperative Work in Design，Best Student Paper Award，2025年5月。</span></li>
  <li><span class="lang-en">Yuhuan Du et al. <i>OmniPose-AD: Canonical Normal Rendering for Unaligned 3D Anomaly Detection</i>, Best Student Paper Award, ICAIS & ISAS, 2026. Yuhuan Du is the student first author; Yunkang Cao is the corresponding author.</span><span class="lang-zh">杜禹寰等，<i>OmniPose-AD: Canonical Normal Rendering for Unaligned 3D Anomaly Detection</i>，ICAIS & ISAS 2026 Best Student Paper Award。杜禹寰为学生第一作者，曹云康为通讯作者。</span></li>
  <li><span class="lang-en">Yunkang Cao, National Scholarship for Ph.D. Students, Nov. 2024.</span><span class="lang-zh">曹云康，博士研究生国家奖学金，2024年11月。</span></li>
</ol>

-----

<span class='anchor' id='service'></span>

# <i class="fas fa-hands-helping section-icon" aria-hidden="true"></i><span class="lang-en">Academic Service</span><span class="lang-zh">学术服务</span>

## <i class="fas fa-edit section-icon" aria-hidden="true"></i><span class="lang-en">Editorial and Reviewing Service</span><span class="lang-zh">编委与审稿服务</span>

- <span class="lang-en">Editorial Board Member, *Pattern Recognition*.</span><span class="lang-zh">*Pattern Recognition* 编委。</span>
- <span class="lang-en">Lead organizer of the Special Issue on "Foundation Models for Anomaly Detection, Reasoning, and Recovery."</span><span class="lang-zh">牵头组织“面向缺陷检测、推理与修复的基础模型”专题特刊。</span>
- <span class="lang-en">Special Session Chair, IEEE CSCWD 2025.</span><span class="lang-zh">IEEE CSCWD 2025 专题主席。</span>
- <span class="lang-en">Reviewer for TPAMI, IJCV, CVPR, ICCV, NeurIPS, AAAI, IJCAI, *Pattern Recognition*, IEEE TCYB, IEEE TII, and other journals and conferences.</span><span class="lang-zh">担任 TPAMI、IJCV、CVPR、ICCV、NeurIPS、AAAI、IJCAI、Pattern Recognition、IEEE TCYB、IEEE TII 等期刊与会议审稿人。</span>

## <i class="fas fa-users section-icon" aria-hidden="true"></i><span class="lang-en">Workshop and Forum Organization</span><span class="lang-zh">研讨会与论坛组织</span>

<ol>
  <li><span class="lang-en">CVPR 2024-2026, Visual Anomaly and Novelty Detection Workshop (VAND).</span><span class="lang-zh">CVPR 2024-2026，视觉异常与新颖性检测研讨会 VAND。</span></li>
  <li><span class="lang-en">IJCAI 2024, Anomaly Detection with Foundation Models Workshop (ADFM).</span><span class="lang-zh">IJCAI 2024，基于基础模型的异常检测研讨会 ADFM。</span></li>
  <li><span class="lang-en">ICCV 2025, Anomaly Detection with Foundation Models Workshop (ADFM).</span><span class="lang-zh">ICCV 2025，基于基础模型的异常检测研讨会 ADFM。</span></li>
  <li><span class="lang-en">CVPR 2026, Anomaly Detection with Foundation Models Workshop (ADFM).</span><span class="lang-zh">CVPR 2026，基于基础模型的异常检测研讨会 ADFM。</span></li>
  <li><span class="lang-en">IEEE CASE, Special Session on Industrial Foundation Models and Applications in Smart Manufacturing.</span><span class="lang-zh">IEEE CASE，“智能制造中的工业大模型及其应用”专题。</span></li>
  <li><span class="lang-en">CSIG Donghu Forum, CVPR 2025 pre-conference "Industrial Vision" special session.</span><span class="lang-zh">CSIG “东湖论坛”前沿论文分享会 CVPR 2025 预会议“工业视觉”专场。</span></li>
  <li><span class="lang-en">YAC 2026, Special Session on Industrial Vision Intelligent Measurement and Inspection, Special Session Chair, Changsha.</span><span class="lang-zh">YAC 2026，“工业视觉智能测量与检测”专题，专题主席，长沙。</span></li>
  <li><span class="lang-en">The 3rd International Conference on 3D Vision, Perception and Applications, Robot Intelligent Inspection Forum, Forum Secretary, Suzhou.</span><span class="lang-zh">第三届国际 3D 视觉感知与应用大会，“机器人智能检测”分会，论坛秘书，苏州。</span></li>
  <li><span class="lang-en">CSIG Frontier Forum on Embodied Intelligent Perception and Inspection, Organizing Committee Chair, Guilin.</span><span class="lang-zh">CSIG 具身智能感知与检测前沿论坛，组织委员会主席，桂林。</span></li>
</ol>

<script type='text/javascript' id='clustrmaps' src='//cdn.clustrmaps.com/map_v2.js?cl=ffffff&w=300&t=tt&d=QltdrDBXR7cYztdXsLCBfSeruYl8EMVZ7i3zpSoGzP4&co=2d78ad&cmo=3acc3a&cmn=ff5353&ct=ffffff'></script>
