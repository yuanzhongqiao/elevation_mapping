<div class="Box-sc-g0xbh4-0 bJMeLZ js-snippet-clipboard-copy-unpositioned" data-hpc="true"><article class="markdown-body entry-content container-lg" itemprop="text"><div class="markdown-heading" dir="auto"><h1 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">以机器人为中心的高程测绘</font></font></h1><a id="user-content-robot-centric-elevation-mapping" class="anchor" aria-label="永久链接：以机器人为中心的高程测绘" href="#robot-centric-elevation-mapping"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">概述</font></font></h2><a id="user-content-overview" class="anchor" aria-label="固定链接：概述" href="#overview"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这是为移动机器人的高程测绘而开发的</font></font><a href="http://www.ros.org" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">ROS</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">包。该软件专为配备姿态估计（例如 IMU 和里程计）和距离传感器（例如结构光（Kinect、RealSense）、激光测距传感器、立体摄像头）的机器人的（本地）导航任务而设计。所提供的高程图仅限于机器人周围，并反映了通过机器人运动（以机器人为中心的测绘）而聚集的姿态不确定性。该方法被开发用于明确处理机器人姿态估计的漂移。</font></font></p>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这是研究代码，预计它会经常变化，并且不适用于任何特定用途。</font></font></p>
<p dir="auto"><font style="vertical-align: inherit;"></font><a href="/ANYbotics/elevation_mapping/blob/master/LICENSE"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">源代码根据BSD 3-Clause 许可证</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">发布</font><font style="vertical-align: inherit;">。</font></font></p>
<p dir="auto"><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">作者：Péter Fankhauser</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">
合著者：Maximilian Wulf</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">
所属机构：</font></font><a href="https://www.anybotics.com/" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">ANYbotics</font></font></a><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">
维护者：Maximilian Wulf，</font></font><a href="mailto:mwulf@anybotics.com"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">mwulf@anybotics.com</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，Magnus Gärtner，</font></font><a href="mailto:mgaertner@anybotics.com"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">mgaertner @anybotics.com</font></font></a><br></strong></p>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">该项目最初是在苏黎世联邦理工学院（自主系统实验室和机器人系统实验室）开发的。</font></font></p>
<p dir="auto"><a href="https://www.anymal-research.org/" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这项工作是 ANYmal Research 的一部分，ANYmal Research 是一个致力于推动足式机器人技术的社区。</font></font></a></p>
<p dir="auto"><a target="_blank" rel="noopener noreferrer" href="/ANYbotics/elevation_mapping/blob/master/elevation_mapping_demos/doc/elevation_map.jpg"><img alt="海拔地图示例" src="/ANYbotics/elevation_mapping/raw/master/elevation_mapping_demos/doc/elevation_map.jpg" width="700" style="max-width: 100%;"></a></p>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用中的高程测绘软件的视频：</font></font></p>
<p dir="auto"><a alt="StarlETH Kinect 高程测绘" href="https://www.youtube.com/watch?v=I9eP8GrMyNQ" rel="nofollow"><img src="/ANYbotics/elevation_mapping/raw/master/elevation_mapping_demos/doc/starleth_kinect.jpg" align="left" width="180" style="max-width: 100%;"></a>
<a alt="ANYmal 户外地形测绘" href="https://www.youtube.com/watch?v=iVMsQPTM65M" rel="nofollow"><img src="/ANYbotics/elevation_mapping/raw/master/elevation_mapping_demos/doc/anymal_forrest.jpg" align="left" width="180" style="max-width: 100%;"></a>
<a alt="ANYmal 崎岖地形运动规划器" href="https://www.youtube.com/watch?v=CpzQu25iLa0" rel="nofollow"><img src="/ANYbotics/elevation_mapping/raw/master/elevation_mapping_demos/doc/anymal_locomotion_planner.jpg" align="left" width="180" style="max-width: 100%;"></a>
<a alt="ANYmal 户外爬楼梯" href="https://www.youtube.com/watch?v=vSveQrJLRTo" rel="nofollow"><img src="/ANYbotics/elevation_mapping/raw/master/elevation_mapping_demos/doc/anymal_outdoor_stairs.jpg" width="180" style="max-width: 100%;"></a></p>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">引用</font></font></h2><a id="user-content-citing" class="anchor" aria-label="永久链接：引用" href="#citing"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">以下论文（可</font></font><a href="https://doi.org/10.3929/ethz-b-000272110" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在此处</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">获取）介绍了此软件中使用的以机器人为中心的高程测绘方法。如果您在学术背景下使用此作品，请引用以下出版物：</font></font></p>
<ul dir="auto">
<li>
<blockquote>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">P. Fankhauser、M. Bloesch 和 M. Hutter，
 </font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">《具有不确定定位的移动机器人的概率地形测绘》</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，载于《IEEE 机器人与自动化快报》（RA-L），第 3 卷，第 4 期，第 3019-3026 页，2018 年。（</font></font><a href="http://dx.doi.org/10.1109/LRA.2018.2849506" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">PDF</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">）</font></font></p>
</blockquote>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>  @article{Fankhauser2018ProbabilisticTerrainMapping,
    author = {Fankhauser, P{\'{e}}ter and Bloesch, Michael and Hutter, Marco},
    doi = {10.1109/LRA.2018.2849506},
    title = {Probabilistic Terrain Mapping for Mobile Robots with Uncertain Localization},
    journal = {IEEE Robotics and Automation Letters (RA-L)},
    volume = {3},
    number = {4},
    pages = {3019--3026},
    year = {2018}
  }
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 tooltipped-no-delay d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="  @article{Fankhauser2018ProbabilisticTerrainMapping,
    author = {Fankhauser, P{\'{e}}ter and Bloesch, Michael and Hutter, Marco},
    doi = {10.1109/LRA.2018.2849506},
    title = {Probabilistic Terrain Mapping for Mobile Robots with Uncertain Localization},
    journal = {IEEE Robotics and Automation Letters (RA-L)},
    volume = {3},
    number = {4},
    pages = {3019--3026},
    year = {2018}
  }" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
</li>
<li>
<blockquote>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">P. Fankhauser、M. Bloesch、C. Gehring、M. Hutter 和 R. Siegwart，
 </font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">《具有不确定性估计的以机器人为中心的高程测绘》</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，国际攀爬和行走机器人会议 (CLAWAR)，2014 年。（</font></font><a href="http://dx.doi.org/10.3929/ethz-a-010173654" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">PDF</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">）</font></font></p>
</blockquote>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>  @inproceedings{Fankhauser2014RobotCentricElevationMapping,
    author = {Fankhauser, P\'{e}ter and Bloesch, Michael and Gehring, Christian and Hutter, Marco and Siegwart, Roland},
    title = {Robot-Centric Elevation Mapping with Uncertainty Estimates},
    booktitle = {International Conference on Climbing and Walking Robots (CLAWAR)},
    year = {2014}
  }
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 tooltipped-no-delay d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="  @inproceedings{Fankhauser2014RobotCentricElevationMapping,
    author = {Fankhauser, P\'{e}ter and Bloesch, Michael and Gehring, Christian and Hutter, Marco and Siegwart, Roland},
    title = {Robot-Centric Elevation Mapping with Uncertainty Estimates},
    booktitle = {International Conference on Climbing and Walking Robots (CLAWAR)},
    year = {2014}
  }" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
</li>
</ul>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">安装</font></font></h2><a id="user-content-installation" class="anchor" aria-label="固定链接：安装" href="#installation"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<div class="markdown-heading" dir="auto"><h3 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">依赖项</font></font></h3><a id="user-content-dependencies" class="anchor" aria-label="永久链接：依赖项" href="#dependencies"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">该软件基于机器人操作系统 ( </font></font><a href="http://www.ros.org" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">ROS</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> ) 构建，需要先</font></font><a href="http://wiki.ros.org" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">安装</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。此外，以机器人为中心的高程测绘依赖于以下软件：</font></font></p>
<ul dir="auto">
<li><a href="https://github.com/anybotics/grid_map"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Grid Map</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（移动机器人的网格图库）</font></font></li>
<li><a href="http://github.com/anybotics/kindr"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">kindr</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（机器人运动学和动力学库），</font></font></li>
<li><a href="https://github.com/anybotics/kindr_ros"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">kindr_ros</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（kindr 的 ROS 包装器），</font></font></li>
<li><a href="http://pointclouds.org/" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">点云库（PCL）</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（点云处理），</font></font></li>
<li><a href="http://eigen.tuxfamily.org" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Eigen</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（线性代数库）。</font></font></li>
</ul>
<div class="markdown-heading" dir="auto"><h3 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">建筑</font></font></h3><a id="user-content-building" class="anchor" aria-label="固定链接：建筑" href="#building"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">为了安装以机器人为中心的高程测绘，请将此存储库中的最新版本克隆到您的 catkin 工作区并使用 ROS 编译包。</font></font></p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>cd catkin_workspace/src
git clone https://github.com/anybotics/elevation_mapping.git
cd ../
catkin config --cmake-args -DCMAKE_BUILD_TYPE=Release
catkin build
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 tooltipped-no-delay d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="cd catkin_workspace/src
git clone https://github.com/anybotics/elevation_mapping.git
cd ../
catkin config --cmake-args -DCMAKE_BUILD_TYPE=Release
catkin build" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<div class="markdown-heading" dir="auto"><h3 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">单元测试</font></font></h3><a id="user-content-unit-tests" class="anchor" aria-label="固定链接：单元测试" href="#unit-tests"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用以下工具构建测试</font></font></p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>roscd elevation_mapping
catkin build --catkin-make-args run_tests -- --this
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 tooltipped-no-delay d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="roscd elevation_mapping
catkin build --catkin-make-args run_tests -- --this" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用以下方法运行测试</font></font></p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code> rostest elevation_mapping elevation_mapping.test -t
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 tooltipped-no-delay d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value=" rostest elevation_mapping elevation_mapping.test -t" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">基本用法</font></font></h2><a id="user-content-basic-usage" class="anchor" aria-label="固定链接：基本用法" href="#basic-usage"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">为了让 Robot-Centric Elevation Mapping 与您的机器人一起运行，您需要调整一些参数。最简单的方法是从包中复制并调整您需要更改的所有参数文件</font></font><code>elevation_mapping_demos</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（例如</font></font><code>simple_demo</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">示例）。这些具体是文件夹中的参数文件</font></font><code>config</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和启动文件</font></font><code>launch</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>
<div class="markdown-heading" dir="auto"><h3 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">TurtleBot3 华夫饼模拟</font></font></h3><a id="user-content-turtlebot3-waffle-simulation" class="anchor" aria-label="永久链接：TurtleBot3 华夫饼模拟" href="#turtlebot3-waffle-simulation"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">提供了一个运行示例，利用 Turtlebot3 模拟环境。此示例可用于测试高程测绘，作为进一步集成的起点。</font></font></p>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">首先，需要安装 Turtlebot3 模拟依赖项：</font></font></p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>sudo apt install ros-melodic-turtlebot3*
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 tooltipped-no-delay d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="sudo apt install ros-melodic-turtlebot3*" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">可以使用以下命令启动高程测绘演示和 turtlebot3 模拟：</font></font></p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>roslaunch elevation_mapping_demos turtlesim3_waffle_demo.launch
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 tooltipped-no-delay d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="roslaunch elevation_mapping_demos turtlesim3_waffle_demo.launch" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">要使用键盘控制机器人，需要打开一个新的终端窗口（记得获取 ROS 环境）。然后运行</font></font></p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>export TURTLEBOT3_MODEL=waffle
roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 tooltipped-no-delay d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="export TURTLEBOT3_MODEL=waffle
roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">可以通过按键</font></font><code>a</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">、</font></font><code>w</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">、</font></font><code>d</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">、向机器人发送速度输入</font></font><code>x</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。要完全停止机器人，请按</font></font><code>s</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>
<div class="markdown-heading" dir="auto"><h3 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">简单演示和地面实况演示</font></font></h3><a id="user-content-simple-demo--ground-truth-demo" class="anchor" aria-label="永久链接：简单演示和地面实况演示" href="#simple-demo--ground-truth-demo"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">.ply 发布为静态点云，elevation_mapping 订阅它并发布高程图。您可以通过 rviz 对其进行可视化。对于可视化，请选择</font></font><code>/elevation_mapping/elevation_map_raw</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>
<p dir="auto"><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">注意</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：您可能需要切换 grid_map_plugin 的可见性以将其可视化。</font></font></p>
<div class="highlight highlight-source-shell notranslate position-relative overflow-auto" dir="auto"><pre>roslaunch elevation_mapping_demos ground_truth_demo.launch</pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 tooltipped-no-delay d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="roslaunch elevation_mapping_demos ground_truth_demo.launch" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">虽然地面实况演示估算了地图框架中的高度，但简单演示设置了更现实的部署场景。在这里，elevation_map 配置为跟踪基准框架。首先，我们建议尝试一下并可视化其他已发布的主题，例如，</font></font><code>/elevation_mapping/elevation_map_raw</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">并将高度层更改为另一个层，例如</font></font><code>elevation_inpainted</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">节点</font></font></h2><a id="user-content-nodes" class="anchor" aria-label="永久链接：节点" href="#nodes"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<div class="markdown-heading" dir="auto"><h3 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">节点：elevation_mapping</font></font></h3><a id="user-content-node-elevation_mapping" class="anchor" aria-label="永久链接：节点：elevation_mapping" href="#node-elevation_mapping"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这是主要的以机器人为中心的高程测绘节点。它使用距离传感器测量值以及机器人的姿势和协方差来生成带有方差估计的高程图。</font></font></p>
<div class="markdown-heading" dir="auto"><h4 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">订阅主题</font></font></h4><a id="user-content-subscribed-topics" class="anchor" aria-label="固定链接：已订阅主题" href="#subscribed-topics"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<ul dir="auto">
<li>
<p dir="auto"><strong><code>/points</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（</font></font><a href="http://docs.ros.org/api/sensor_msgs/html/msg/PointCloud2.html" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">传感器消息/PointCloud2</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">）</font></font></p>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">距离测量。</font></font></p>
</li>
<li>
<p dir="auto"><strong><code>/pose</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（</font></font><a href="http://docs.ros.org/api/geometry_msgs/html/msg/PoseWithCovarianceStamped.html" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">geometry_msgs/PoseWithCovarianceStamped</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">）</font></font></p>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">机器人的姿势和协方差。</font></font></p>
</li>
<li>
<p dir="auto"><strong><code>/tf</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（</font></font><a href="http://docs.ros.org/kinetic/api/tf/html/msg/tfMessage.html" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">tf/tfMessage</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">）</font></font></p>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">變化樹。</font></font></p>
</li>
</ul>
<div class="markdown-heading" dir="auto"><h4 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">已发布主题</font></font></h4><a id="user-content-published-topics" class="anchor" aria-label="固定链接：已发布主题" href="#published-topics"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<ul dir="auto">
<li>
<p dir="auto"><strong><code>elevation_map</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（</font></font><a href="https://github.com/anybotics/grid_map/blob/master/grid_map_msgs/msg/GridMap.msg"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">grid_map_msgs/GridMap</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">）</font></font></p>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">整个（融合）海拔地图。它会定期发布（参见</font></font><code>fused_map_publishing_rate</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">参数）或在</font></font><code>trigger_fusion</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">调用服务后发布。</font></font></p>
</li>
<li>
<p dir="auto"><strong><code>elevation_map_raw</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（</font></font><a href="https://github.com/anybotics/grid_map/blob/master/grid_map_msgs/msg/GridMap.msg"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">grid_map_msgs/GridMap</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">）</font></font></p>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">融合步骤之前的整个（原始）高程图。</font></font></p>
</li>
</ul>
<div class="markdown-heading" dir="auto"><h4 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">服务</font></font></h4><a id="user-content-services" class="anchor" aria-label="固定链接：服务" href="#services"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<ul dir="auto">
<li>
<p dir="auto"><strong><code>trigger_fusion</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（</font></font><a href="http://docs.ros.org/api/std_srvs/html/srv/Empty.html" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">std_srvs/空</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">）</font></font></p>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">触发整个海拔地图的融合过程并发布。例如，您可以使用以下命令从控制台触发地图融合步骤</font></font></p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>  rosservice call /elevation_mapping/trigger_fusion
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 tooltipped-no-delay d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="  rosservice call /elevation_mapping/trigger_fusion" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
</li>
<li>
<p dir="auto"><strong><code>get_submap</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（</font></font><a href="https://github.com/anybotics/grid_map/blob/master/grid_map_msgs/srv/GetGridMap.srv"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">grid_map_msgs/获取网格地图</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">）</font></font></p>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">获取请求位置和大小的融合高程子图。例如，您可以获取 odom 框架中描述的位置 (-0.5, 0.0) 和大小 (0.5, 1.2) 处的融合高程子图，并使用以下命令将其从控制台保存到文本文件中</font></font></p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>  rosservice call -- /elevation_mapping/get_submap odom -0.5 0.0 0.5 1.2 []
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 tooltipped-no-delay d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="  rosservice call -- /elevation_mapping/get_submap odom -0.5 0.0 0.5 1.2 []" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
</li>
<li>
<p dir="auto"><strong><code>get_raw_submap</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（</font></font><a href="https://github.com/anybotics/grid_map/blob/master/grid_map_msgs/srv/GetGridMap.srv"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">grid_map_msgs/获取网格地图</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">）</font></font></p>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">获取请求位置和大小的原始海拔子图。例如，您可以获取 odom 框架中描述的位置 (-0.5, 0.0) 和大小 (0.5, 1.2) 处的原始海拔子图，并使用以下命令将其从控制台保存到文本文件中</font></font></p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>  rosservice call -- /elevation_mapping/get_raw_submap odom -0.5 0.0 0.5 1.2 []
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 tooltipped-no-delay d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="  rosservice call -- /elevation_mapping/get_raw_submap odom -0.5 0.0 0.5 1.2 []" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
</li>
<li>
<p dir="auto"><strong><code>clear_map</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（</font></font><a href="http://docs.ros.org/api/std_srvs/html/srv/Empty.html" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">std_srvs/空</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">）</font></font></p>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">启动清除整个地图以进行重置。使用以下命令触发地图清除</font></font></p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>  rosservice call /elevation_mapping/clear_map
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 tooltipped-no-delay d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="  rosservice call /elevation_mapping/clear_map" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
</li>
<li>
<p dir="auto"><strong><code>masked_replace</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（[grid_map_msgs/设置网格地图]）</font></font></p>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">允许通过服务调用设置海拔地图的各个图层。图层蒙版可用于仅设置某些单元格，而不是整个地图。蒙版中包含 NAN 的单元格未设置，所有其他单元格均已设置。如果未提供图层蒙版，则整个地图将设置在两个地图的交集中。提供的地图的大小和位置可能与将要更改的地图不同。将海拔图层中标有蒙版的一些单元格设置为 0.5 的示例服务调用是</font></font></p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>  rosservice call /elevation_mapping/masked_replace "map:
    info:
      header:
        seq: 3
        stamp: {secs: 3, nsecs: 80000000}
        frame_id: 'odom'
      resolution: 0.1
      length_x: 0.3
      length_y: 0.3
      pose:
        position: {x: 5.0, y: 0.0, z: 0.0}
        orientation: {x: 0.0, y: 0.0, z: 0.0, w: 0.0}
    layers: [elevation,mask]
    basic_layers: [elevation]
    data:
    - layout:
        dim:
        - {label: 'column_index', size: 3, stride: 9}
        - {label: 'row_index', size: 3, stride: 3}
        data_offset: 0
      data: [0.5, 0.5, 0.5, 0.5, 0.5, 0.5, 0.5, 0.5, 0.5]
    - layout:
        dim:
        - {label: 'column_index', size: 3, stride: 9}
        - {label: 'row_index', size: 3, stride: 3}
        data_offset: 0
      data: [0, 0, 0, .NAN, .NAN, .NAN, 0, 0, 0]
    outer_start_index: 0
    inner_start_index: 0"
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 tooltipped-no-delay d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="  rosservice call /elevation_mapping/masked_replace &quot;map:
    info:
      header:
        seq: 3
        stamp: {secs: 3, nsecs: 80000000}
        frame_id: 'odom'
      resolution: 0.1
      length_x: 0.3
      length_y: 0.3
      pose:
        position: {x: 5.0, y: 0.0, z: 0.0}
        orientation: {x: 0.0, y: 0.0, z: 0.0, w: 0.0}
    layers: [elevation,mask]
    basic_layers: [elevation]
    data:
    - layout:
        dim:
        - {label: 'column_index', size: 3, stride: 9}
        - {label: 'row_index', size: 3, stride: 3}
        data_offset: 0
      data: [0.5, 0.5, 0.5, 0.5, 0.5, 0.5, 0.5, 0.5, 0.5]
    - layout:
        dim:
        - {label: 'column_index', size: 3, stride: 9}
        - {label: 'row_index', size: 3, stride: 3}
        data_offset: 0
      data: [0, 0, 0, .NAN, .NAN, .NAN, 0, 0, 0]
    outer_start_index: 0
    inner_start_index: 0&quot;" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
</li>
<li>
<p dir="auto"><strong><code>save_map</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（</font></font><a href="https://github.com/ANYbotics/grid_map/blob/master/grid_map_msgs/srv/ProcessFile.srv"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">grid_map_msgs/ProcessFile</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">）</font></font></p>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">将当前融合网格图和原始网格图保存到 rosbag 文件中。字段</font></font><code>topic_name</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">必须是基本名称，即没有前导斜杠字符 (/)。如果字段</font></font><code>topic_name</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">为空，则</font></font><code>elevation_map</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">默认使用。具有默认主题名称的示例</font></font></p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>  rosservice call /elevation_mapping/save_map "file_path: '/home/integration/elevation_map.bag' topic_name: ''"
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 tooltipped-no-delay d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="  rosservice call /elevation_mapping/save_map &quot;file_path: '/home/integration/elevation_map.bag' topic_name: ''&quot;" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
</li>
<li>
<p dir="auto"><strong><code>load_map</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（</font></font><a href="https://github.com/ANYbotics/grid_map/blob/master/grid_map_msgs/srv/ProcessFile.srv"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">grid_map_msgs/ProcessFile</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">）</font></font></p>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">从 rosbag 文件加载融合网格图和原始网格图。字段</font></font><code>topic_name</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">必须是基本名称，即没有前导斜杠字符 (/)。如果字段</font></font><code>topic_name</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">为空，则</font></font><code>elevation_map</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">默认使用。具有默认主题名称的示例</font></font></p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>  rosservice call /elevation_mapping/load_map "file_path: '/home/integration/elevation_map.bag' topic_name: ''"
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 tooltipped-no-delay d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="  rosservice call /elevation_mapping/load_map &quot;file_path: '/home/integration/elevation_map.bag' topic_name: ''&quot;" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
</li>
<li>
<p dir="auto"><strong><code>reload_parameters</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（[std_srvs/触发器]）</font></font></p>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">触发所有高程映射参数的重新加载，可用于在线重新配置参数。示例用法：</font></font></p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>  rosservice call /elevation_mapping/reload_parameters {}
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 tooltipped-no-delay d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="  rosservice call /elevation_mapping/reload_parameters {}" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
</li>
<li>
<p dir="auto"><strong><code>disable_updates</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（</font></font><a href="http://docs.ros.org/api/std_srvs/html/srv/Empty.html" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">std_srvs/空</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">）</font></font></p>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">停止使用传感器输入更新海拔地图。使用以下方式触发更新停止：</font></font></p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>  rosservice call /elevation_mapping/disable_updates {}
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 tooltipped-no-delay d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="  rosservice call /elevation_mapping/disable_updates {}" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
</li>
<li>
<p dir="auto"><strong><code>enable_updates</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（</font></font><a href="http://docs.ros.org/api/std_srvs/html/srv/Empty.html" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">std_srvs/空</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">）</font></font></p>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">开始使用传感器输入更新海拔地图。触发更新时，请先输入</font></font></p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>  rosservice call /elevation_mapping/enable_updates {}
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 tooltipped-no-delay d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="  rosservice call /elevation_mapping/enable_updates {}" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
</li>
</ul>
<div class="markdown-heading" dir="auto"><h4 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">参数</font></font></h4><a id="user-content-parameters" class="anchor" aria-label="永久链接：参数" href="#parameters"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<ul dir="auto">
<li>
<p dir="auto"><strong><code>DEPRECATED point_cloud_topic</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（字符串，默认值：“/points”）</font></font></p>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">距离测量主题的名称。请改用 input_sources。</font></font></p>
</li>
<li>
<p dir="auto"><strong><code>input_sources</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（输入源列表，默认值：无）</font></font></p>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您可以在这里指定高程映射的输入，目前支持“点云”输入。</font></font></p>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">示例配置：</font></font></p>
<div class="highlight highlight-source-yaml notranslate position-relative overflow-auto" dir="auto"><pre><span class="pl-ent">input_sources</span>:
    <span class="pl-ent">front</span>: <span class="pl-c"><span class="pl-c">#</span> A name to identify the input source</span>
      <span class="pl-ent">type</span>: <span class="pl-s">pointcloud </span><span class="pl-c"><span class="pl-c">#</span> Supported types: pointcloud</span>
      <span class="pl-ent">topic</span>: <span class="pl-s">/lidar_front/depth/points</span>
      <span class="pl-ent">queue_size</span>: <span class="pl-c1">1</span>
      <span class="pl-ent">publish_on_update</span>: <span class="pl-s">true </span><span class="pl-c"><span class="pl-c">#</span> Wheter to publish the elevation map after a callback from this source. </span>
    <span class="pl-ent">rear</span>:
      <span class="pl-ent">type</span>: <span class="pl-s">pointcloud</span>
      <span class="pl-ent">topic</span>: <span class="pl-s">/lidar_rear/depth/points</span>
      <span class="pl-ent">queue_size</span>: <span class="pl-c1">5</span>
      <span class="pl-ent">publish_on_update</span>: <span class="pl-c1">false</span></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 tooltipped-no-delay d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="input_sources:
    front: # A name to identify the input source
      type: pointcloud # Supported types: pointcloud
      topic: /lidar_front/depth/points
      queue_size: 1
      publish_on_update: true # Wheter to publish the elevation map after a callback from this source. 
    rear:
      type: pointcloud
      topic: /lidar_rear/depth/points
      queue_size: 5
      publish_on_update: false" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">不能使用空数组配置任何输入源：</font></font></p>
<div class="highlight highlight-source-yaml notranslate position-relative overflow-auto" dir="auto"><pre><span class="pl-ent">input_sources</span>: <span class="pl-s">[]</span></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 tooltipped-no-delay d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="input_sources: []" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
</li>
<li>
<p dir="auto"><strong><code>robot_pose_topic</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（字符串，默认值：“/robot_state/pose”）</font></font></p>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">机器人姿势和协方差主题的名称。</font></font></p>
</li>
<li>
<p dir="auto"><strong><code>base_frame_id</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（字符串，默认值：“/robot”）</font></font></p>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">机器人基础 tf 框架的 id。</font></font></p>
</li>
<li>
<p dir="auto"><strong><code>map_frame_id</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（字符串，默认值：“/map”）</font></font></p>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">高程图的tf框的id。</font></font></p>
</li>
<li>
<p dir="auto"><strong><code>track_point_frame_id</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（字符串，默认值：“/robot”）</font></font></p>
<p dir="auto"><font style="vertical-align: inherit;"></font><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">高程图随着机器人跟随轨迹点</font></font></em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">移动</font><font style="vertical-align: inherit;">。这是定义轨迹点的 tf 框架的 id。</font></font></p>
</li>
<li>
<p dir="auto"><strong><code>track_point_x</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，，</font></font><strong><code>track_point_y</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（</font></font><strong><code>track_point_z</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">双精度，默认值：0.0，0.0，0.0）</font></font></p>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">高程图随着机器人沿着</font></font><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">轨迹点</font></font></em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">移动。这是轨迹点在 中的位置</font></font><code>track_point_frame_id</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>
</li>
<li>
<p dir="auto"><strong><code>robot_pose_cache_size</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（int，默认值：200，最小值：0）</font></font></p>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">机器人姿势缓存的大小。</font></font></p>
</li>
<li>
<p dir="auto"><strong><code>min_update_rate</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（双精度，默认值：2.0）</font></font></p>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">根据新测量值或机器人姿势估计值更新高程图的最小更新率（以赫兹为单位）。</font></font></p>
</li>
<li>
<p dir="auto"><strong><code>fused_map_publishing_rate</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（双精度，默认值：1.0）</font></font></p>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">发布整个（融合）海拔地图的费率。</font></font></p>
</li>
<li>
<p dir="auto"><strong><code>relocate_rate</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（双精度，默认值：3.0）</font></font></p>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">检查海拔图以根据跟踪点进行重新定位的速率（以赫兹为单位）。</font></font></p>
</li>
<li>
<p dir="auto"><strong><code>length_in_x</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，</font></font><strong><code>length_in_y</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（双精度，默认值：1.5，最小值：0.0）</font></font></p>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">海拔地图的尺寸&ZeroWidthSpace;&ZeroWidthSpace;（以米为单位）。</font></font></p>
</li>
<li>
<p dir="auto"><strong><code>position_x</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，</font></font><strong><code>position_y</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（双精度，默认值：0.0）</font></font></p>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">高程图中心在高程图框架中的位置。此参数设置生成的高程图与其发布框架之间的平面位置偏移（ ）。仅在未</font><font style="vertical-align: inherit;">使用任何参数</font></font><code>map_frame_id</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">时才有用。</font></font><code>track_point_frame_id</code><font style="vertical-align: inherit;"></font></p>
</li>
<li>
<p dir="auto"><strong><code>resolution</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（双精度，默认值：0.01，最小值：0.0）</font></font></p>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">高程图的分辨率（以米/单元格为单位的单元格大小）。</font></font></p>
</li>
<li>
<p dir="auto"><strong><code>min_variance</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，</font></font><strong><code>max_variance</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（双精度，默认值：9.0e-6，0.01）</font></font></p>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">海拔图方差数据的最小值和最大值。</font></font></p>
</li>
<li>
<p dir="auto"><strong><code>mahalanobis_distance_threshold</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（双倍，默认值：2.5）</font></font></p>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">高程图中的每个单元格的高度值都存在不确定性。根据现有高度分布和新测量值的马哈拉诺比斯距离，传入的数据将与现有估计值融合、覆盖或忽略。此参数确定马哈拉诺比斯距离的阈值，从而决定传入测量值的处理方式。</font></font></p>
</li>
<li>
<p dir="auto"><strong><code>sensor_processor/ignore_points_above</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（双精度，默认值：inf）深度传感器引入的点高度的硬阈值。在数据收集步骤中，高度超过此阈值的点将不被视为有效。</font></font></p>
</li>
<li>
<p dir="auto"><strong><code>sensor_processor/ignore_points_below</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（双精度，默认值：-inf）深度传感器引入的点高度的硬阈值。在数据收集步骤中，高度低于此阈值的点将不被视为有效。</font></font></p>
</li>
<li>
<p dir="auto"><strong><code>multi_height_noise</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（双精度，默认值：9.0e-7）</font></font></p>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">噪声添加到高于该特定位置的当前海拔图的测量值中。仅当某个点超过马哈拉诺比斯距离阈值时，才会执行此噪声添加过程。较高的值有助于更快地适应动态环境（例如移动物体），但可能会导致高度估计中出现更多噪声。</font></font></p>
</li>
<li>
<p dir="auto"><strong><code>min_horizontal_variance</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，</font></font><strong><code>max_horizontal_variance</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（双精度，默认值：pow（分辨率/2.0, 2），0.5）</font></font></p>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">高程图水平方差数据的最小值和最大值。</font></font></p>
</li>
<li>
<p dir="auto"><strong><code>enable_visibility_cleanup</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（布尔值，默认值：true）</font></font></p>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">启用/禁用一个单独的线程，该线程通过源自传感器框架的光线追踪从地图中删除不再可见的元素。</font></font></p>
</li>
<li>
<p dir="auto"><strong><code>visibility_cleanup_rate</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（双精度，默认值：1.0）</font></font></p>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">执行可见性清理的速率（以赫兹为单位）。</font></font></p>
</li>
<li>
<p dir="auto"><strong><code>enable_continuous_cleanup</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（布尔值，默认值：false）</font></font></p>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">启用/禁用海拔地图的连续清理。如果启用，则每次收到新的传感器数据时，海拔地图将被清除，并仅使用来自传感器的最新数据进行填充。启用连续清理后，可见性清理将自动禁用，因为在这种情况下不需要。</font></font></p>
</li>
<li>
<p dir="auto"><strong><code>num_callback_threads</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（整数，默认值：1，最小值：1）用于处理回调的线程数。线程越多，吞吐量越高，但资源占用也越多。</font></font></p>
</li>
<li>
<p dir="auto"><strong><code>postprocessor_pipeline_name</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（字符串，默认值：postprocessor_pipeline）</font></font></p>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">用于后处理的要执行的管道的名称。它期望将管道配置加载到此名称下的节点的私有命名空间中。例如：</font></font></p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>  &lt;node pkg="elevation_mapping" type="elevation_mapping" name="elevation_mapping" output="screen"&gt;
      ...
      &lt;rosparam command="load" file="$(find elevation_mapping_demos)/config/postprocessor_pipeline.yaml" /&gt;
  &lt;/node&gt;
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 tooltipped-no-delay d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="  <node pkg=&quot;elevation_mapping&quot; type=&quot;elevation_mapping&quot; name=&quot;elevation_mapping&quot; output=&quot;screen&quot;>
      ...
      <rosparam command=&quot;load&quot; file=&quot;$(find elevation_mapping_demos)/config/postprocessor_pipeline.yaml&quot; />
  </node>" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">管道是 grid_map_filter 链，</font><font style="vertical-align: inherit;">有关更多信息，请参阅 grid_map_demos/filters_demo.yaml 和</font></font><a href="http://wiki.ros.org/filters" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">ros/filters 。</font></font></a><font style="vertical-align: inherit;"></font></p>
</li>
<li>
<p dir="auto"><strong><code>postprocessor_num_threads</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（整数，默认值：1，最小值：1）</font></font></p>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">用于异步后处理的线程数。线程越多，吞吐量越高，但资源使用量也越多。</font></font></p>
</li>
<li>
<p dir="auto"><strong><code>scanning_duration</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（双精度，默认值：1.0）</font></font></p>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">用于可见性清理的传感器扫描持续时间（以秒为单位）。将其大致设置为两次连续完整扫描之间的持续时间（例如，对于 30 Hz 的 ToF 相机，设置为 0.033 秒；对于旋转激光扫描仪，设置为 3 秒）。根据扫描的密集程度或稀疏程度，增加或减少扫描持续时间。较小的值会导致更快的动态对象移除，较大的值有助于减少错误的地图清理。</font></font></p>
</li>
<li>
<p dir="auto"><strong><code>sensor_cutoff_min_depth</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，</font></font><strong><code>sensor_cutoff_max_depth</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（双精度，默认值：0.2，2.0）</font></font></p>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">距离传感器测量长度的最小值和最大值。此间隔之外的测量将被忽略。</font></font></p>
</li>
<li>
<p dir="auto"><strong><code>sensor_model_normal_factor_a</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，</font></font><strong><code>sensor_model_normal_factor_b</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，</font></font><strong><code>sensor_model_normal_factor_c</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，</font></font><strong><code>sensor_model_lateral_factor</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（双倍的）</font></font></p>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">传感器噪声模型的数据。</font></font></p>
</li>
<li>
<p dir="auto"><strong><code>initialize_elevation_map</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（布尔值）
 </font></font><strong><code>initialization_method</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，（整数），
 </font></font><strong><code>length_in_x_init_submap</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（双精度，m），
 </font></font><strong><code>length_in_y_init_submap</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（双精度，m），
 </font></font><strong><code>init_submap_height_offset</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（双精度，m），
 </font></font><strong><code>init_submap_variance</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（双精度），
 </font></font><strong><code>target_frame_init_submap</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（字符串）</font></font></p>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果启用（</font></font><code>initialize_elevation_map</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：true），则</font><font style="vertical-align: inherit;">在 的原点附近</font><font style="vertical-align: inherit;">以 的高度偏移初始化一个大小为 ( </font><font style="vertical-align: inherit;">, )</font></font><code>initialization_method</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的平面 ( ：0) </font><font style="vertical-align: inherit;">。方差设置为</font><font style="vertical-align: inherit;">。</font></font><code>submap_length_x</code><font style="vertical-align: inherit;"></font><code>submap_length_y</code><font style="vertical-align: inherit;"></font><code>init_submap_height_offset</code><font style="vertical-align: inherit;"></font><code>target_frame_init_submap</code><font style="vertical-align: inherit;"></font><code>init_submap_variance</code><font style="vertical-align: inherit;"></font></p>
</li>
<li>
<p dir="auto"><strong><code>increase_height_alpha</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（双精度，默认值：0.0，最小值：0.0，最大值：0.99）</font></font></p>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">elevation = increase_height_alpha * previous_z + (1.0 - increase_height_alpha) * new_measured_z 凸组合参数，用于形成分布点之外的新融合高度观测值。对于尚未观察到的单元格，高度高于上限马哈拉诺比斯阈值的观测值会</font></font><code>scanning_duration</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">
触发高度估计的重新初始化。重新初始化被参数化为先前高度估计和观测值的凸组合：</font></font></p>
<ul dir="auto">
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">0.0：新的观察将用于初始化新模式，先前的数据被丢弃。</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">1.0：当前扫描中更高、超出分布的点的新观察结果不予考虑。先前的观察结果将保留为模式。</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">介于两者之间：值越高，对现有的先前估计的偏差越大。将形成高度和估计值与测量值之间的方差的凸组合，以初始化新的高斯高度分布。</font></font></li>
</ul>
</li>
</ul>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">更新日志</font></font></h2><a id="user-content-changelog" class="anchor" aria-label="永久链接：变更日志" href="#changelog"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">查看</font></font><a href="/ANYbotics/elevation_mapping/blob/master/CHANGELOG.rst"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">变更日志</font></font></a></p>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">错误和功能请求</font></font></h2><a id="user-content-bugs--feature-requests" class="anchor" aria-label="固定链接：错误和功能请求" href="#bugs--feature-requests"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">请使用</font></font><a href="https://github.com/anybotics/elevation_mapping/issues"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">问题跟踪器</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">报告错误并请求功能。</font></font></p>
</article></div>
