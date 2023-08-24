# 交龙技术报告Latex示例模板
本模板修改自[SJTUThesis 示例模板](https://github.com/sjtug/SJTUThesis)

SJTUThesis 支持 XeTeX 与 LuaTeX 引擎，字符编码仅支持 UTF-8。

## 配置示例

### 配置文档类型

结项报告，技术总结报告，经验总结报告均可以使用本模板。

可以在``main.tex``文件中选择报告类型。
```
% 载入 SJTUThesis 模版
\documentclass[type=technical]{sjtuthesis}
% 选项
%   type=[project|technical|lessons],     % 可选（默认：technical），论文类型
%   zihao=[-4|5],                      % 可选（默认：-4），正文字号大小
%   lang=[zh|en],                % 可选（默认：zh），论文的主要语言
%   review,                            % 可选（默认：关闭），盲审模式
%   [twoside|oneside],                 % 可选（默认：twoside），双页或单页边距模式
%   [openright|openany],               % 可选（默认：openright），奇数页或任意页开始新章
%   math-style=[ISO|TeX],              % 可选 (默认：ISO)，数学符号样式
```
以上为``main.tex``中的代码片段，修改``type=technical``可以切换结项报告。技术总结报告，经验总结报告。其中``type=project``为结项报告，``type=lesson``为经验总结报告，``type=technical``为技术总结报告。

### 配置文档名称，车组人员名单

文档名称和车组人员名单可以在``setup.tex``中进行配置。
```
    %
    % 标题
    %
    zh / title           = {上海交通大学交龙战队2023赛季\\哨兵机器人研发技术文档},
    en / title           = {RoboMaster 2023 SJTU Jiao Loong\\ Sentry Technical documentation},
    %
    % 关键词
    %
    zh / keywords        = {哨兵机器人, 双级云台, 竖置摩擦轮, 舵轮底盘, ROS1, 2.5D导航, 状态机决策},
    en / keywords        = {sentry, dual-stage gimbal, virtical friction, swerve chassis, ROS1, 2.5-dimensional navigation, finite state machine decision module},
    %
    % 车组
    %
    zh / group         = {2023赛季哨兵组},
    en / group         = {2023 SJTU sentry group},
    % 
    % 车组负责任
    % 
    zh / leader        = {言李\hbox{\lower-0.8ex\hbox{\scalebox{1}[0.5]{斌}}\lower.1ex\hbox{\kern-1em \scalebox{1}[0.4]{贝}}}},
    en / leader        = {Yan LY},
    %
    % 项目管理
    %
    zh / manager       = {朱嘉铃},
    en / manager       = {Zhu JL},
    %
    % 机械组成员
    %
    zh / mechanic_members   = {言李\hbox{\lower-0.8ex\hbox{\scalebox{1}[0.5]{斌}}\lower.1ex\hbox{\kern-1em \scalebox{1}[0.4]{贝}}}~ 黄溱洧~ 张亦驰~ 梁睿宸},
    en / mechanic_members   = {Yan LY, Huang ZW, Zhang YC, Liang RC},
    %
    % 电控组组员
    %
    zh / ec_members         = {徐子强~ 游宇宸~ 褚家乐~ 程天纵},
    en / ec_members         = {Xu ZQ, You YC, Chu JL, Cheng TZ},
    %
    % 视觉组组员
    %
    zh / algorithm_members  = {冯临溪~ 何哲文~ 王宇轩~ 范存心},
    en / algorithm_members  = {Feng LX, He ZW, Wang YX, Fan CX},
```
以上为``setup.tex``中对于标题，车组名单，等信息的配置。

### 自定义封面
封面的定义主要集中在项目的两个地方，分别为``texmf/tex/latex/sjtutex``中的``sjtuthesis.cls``文件中和``sjtu-lang-thesis-*.def``文件中。

如果想要修改封面的校徽和交龙图标，可以找到``sjtu-lang-thesis-ch.def``的这段代码
```
\clist_map_inline:nn
  {
    { logo    }
      {
        content     =
          {
            \includegraphics [ width = 3 cm ]
              { sjtu-vi-badge- \l__sjtu_style_title_logo_color_tl .pdf }
            \includegraphics [ width = 5 cm ]
              { jiaoloong-vi-badge- \l__sjtu_style_title_jiaoloong_color_tl .pdf }
          }
      },
      ...
      ...
      ...
  }
```
以上代码声明了两个图标。

类似的，如果想要修改封面的文字内容，可以同样在``sjtu-lang-thesis-ch.def``中找到相关代码
```
\clist_map_inline:nn
  {
    ...
    ...
    ...
    { info    }
      {
        format      = \zihao { 4 } \fixedlineskip { 31.2 bp } ,
        content     =
          {
            \__sjtu_title_page_info_i:nxn { zh }
              {
                group,
                leader,
                manager,
                mechanic_members,
                ec_members,
                algorithm_members,
              }
              {
                \__sjtu_cjk_spread_box:nn { 5 em } { \heiti #1 }
                \c__sjtu_name_info_sep_zh_tl
                \__sjtu_left_aligned_box:nn {#2} {#3}
              }
          } ,
        bottom-skip = 31.2 bp
      },
    ...
    ...
    ...
  }
```
以上代码声明了封面的人员名单。

## 获取模板

### 下载模版

普通用户可以直接 `clone` 或者下载 [master.zip](https://github.com/SJTU-RoboMaster-Team/JiaoLoong-Latex-Template/archive/refs/heads/master.zip)。

```bash
git clone https://github.com/sjtug/SJTUThesis.git
```

模版更新频繁，且只维护最新版。如有问题，可以先尝试升级模版，而后根据“反馈问题”一栏进行反馈。

### Overleaf

如果需要在线 LaTeX 平台上使用（比如 [latex.sjtu.edu.cn](https://latex.sjtu.edu.cn)），您可以下载 [最新版压缩包](https://github.com/SJTU-RoboMaster-Team/JiaoLoong-Latex-Template/archive/refs/heads/master.zip)，然后上传至相应平台。请注意，Overleaf 默认使用 pdflatex 编译，您需要设置使用 XeLaTeX 编译器。

## 模板使用

如果你不熟悉 LaTeX 的编译流程，请**不要**直接使用编译器进行编译。针对不同的平台，模版提供了相应的编译脚本。在编译前，需要安装最新的 TeXLive 发行版。

### VSCode 用户

安装 “LaTeX Workshop” 后，选择 `Recipe: latexmk (xelatex)` 编译即可，并在设置中将 `latex-workshop.latex.recipe.default` 改为 `lastUsed` 以一直使用该选项编译。

### TeXStudio 用户

在TexStudio的菜单栏中，Options-Configure TeXstudio界面中，修改以下两处：

Commands-Latexmk一项修改为`latexmk -silent -synctex=1 -xelatex %`

Build-Default Compiler一项修改为`txs:///latexmk`

<details>

<summary>展开配置</summary>

<img src="https://user-images.githubusercontent.com/84025388/142163308-3d31f905-af78-40cb-bff1-851cdab04c87.png" width=500px/>

<img src="https://user-images.githubusercontent.com/84025388/142163346-63ec7b7e-932f-44c5-90c4-3b35e435545d.png" width=500px/>

</details>

### Linux 与 macOS 用户

推荐使用模版提供的 `Makefile` 进行编译，具体来说我们提供了如下几条可用的命令：

```bash
make all                      # 编译生成 main.pdf
make clean                    # 删除编译所产生的中间文件
make cleanall                 # 删除 main.pdf 和所有中间文件
make wordcount                # 论文字数统计
```

### Windows 用户

对于 Windows 用户，我们也提供了编译脚本 `Compile.bat`。可以双击直接编译，也可以在命令提示符窗口中使用脚本提供的额外功能：

```bash
.\Compile.bat thesis          # 编译生成 main.pdf
.\Compile.bat clean           # 删除编译所产生的中间文件
.\Compile.bat cleanall        # 删除 main.pdf 和所有中间文件
.\Compile.bat wordcount       # 论文字数统计
```

更多关于模板的实现细节以及使用信息，请查看使用文档 `sjtuthesis.pdf`。