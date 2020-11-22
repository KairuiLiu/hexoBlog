---
title: LaTeX学习笔记(刘大成版)
date: 2020-10-31 00:00:08
toc: true
description: 看了B站西北农林科技大学的视频，想通过刘大成的LaTeX教程完善一下(估计要烂尾)
categories:
  - [杂七杂八的,LaTeX]
  - [工具,LaTeX]
tags:
  - LaTeX
---

## 1.$\LaTeX$的概述与安装

$\LaTeX$ 是对$\TeX$ 的一种封装，所以我们先从$\TeX$ 说起，$\TeX$ 的发明是因为在很久以前计算机照排太差劲了，远远输于手工照排，有一个教授感觉这实在是太影响写作心情了，于是在他的同事学生的帮助下八年搞了一个$\TeX$ 的排版工具，但是这个实在是不易于使用，所以又一个教授写了一个$\LaTeX$ 这个就相对好用了，不过也由于此，他主要用于个人排版，而不用于专业印刷排版 

### 1.1 $\LaTeX$ 的版本

$\LaTeX$ 有许多版本，例如$\mathbb{C}TeX$(不标准的写法) 和 $\TeX\,live$ 

#### 1.1.1 $\mathbb{C}TeX$

这是一个过气的中文$\TeX$ 版本，由中科院吴凌云(纪念大佬)维护的版本，包含了 WinEdt 做编辑器，SyumatraPDF做预览器，包含了很多常用的中文字体

#### 1.1.2  $\TeX\,live$ 

支持跨系统的发行版，首先需要下载 $\TeX\,live$ 的安装程序(当然可以使用网络安装，但是网络要求太高了qwq，三点几G的文件，断下网就凉凉了)

1. 进入官网 http://www.tug.org/texlive/ 
2. 找到**How to acquire TeX Live:** download, on DVD, other methods.，选择**on DVD**
3. 点开最下面的 **Information about downloading the TeX Live ISO image and burning your own DVD is available separately, as well as other ways to acquire TeX Live.**的**downloading the TeX Live ISO image and burning your own DVD is available separately**
4. 选择**download from a nearby CTAN mirror; or**的**download from a nearby CTAN mirror** 你就可以进入离你最近的镜像网站了(斜了门了，在重庆最近的镜像是清华的，在山西最近的镜像是重庆大学的)找到最新的ISO镜像文件，下载下来
5. 如果是win8+的系统，双击下载的iso会自动加载虚拟光驱(所以装完了记得弹出)，选择**install-tl-advanced.bat**开始安装，一路下一步即可，$\LaTeX$会自动注册环境变量，然后就安装完成了

至于Linux用户，还是看原书吧

#### 1.1.3 $\TeX\,live$ 的附属软件

1. TeXworks editor: 文件编辑器
2. DVIOUT DVI viewer: DVI文件预览器
3. PS_View: PostScrip文件查看器
4. TeX Live command line: 命令提示符
5. TeX Live documentation: 帮助文件链接
6. TeXdoc GUI: 文档列表
7. TeX Live Manager: TeX Live 的管理工具

好的，以上软件我们基本不用

### 1.2 $\LaTeX$ 涉及到的奇奇怪怪的格式

1. .aux/.bl/.synctex.gz 编译辅助文件，暂时不管
2. .tex 源文件
3. .sty style文件
4. PS格式文件：全称"PostScript"文件，不是Photoshop的psd，同出Adobe公司，的一种页面描述语言，很多软件可以画出其文件的内容，他在专业排版中很常见，但是在个人排版中pdf更为流行
5. esp文件: 位图图片文件，可以轻松转换为png或bmp文件

### 1.3 常用的编辑器

1. Tex Studio
2. Vscode(使用方法见博客:[VScode使用全指南 (环境配置，插件推荐，美化) (C++,Python,LaTeX,R...)](https://blog.csdn.net/Liukairui/article/details/104603184))

## 2. 第一次尝试

1. 要使用中文请使用`\documentclass[*UTF8*]{ctexart}`

2. 图片请使用`\usepackage{graphicx}`

3. H浮动体使用 `\usepackage{float}`

4. 使用eqref请使用 

   ```
   \usepackage{amsmath}
   \eqref{XXX}bl
   ```

5. 自定义定理：

   ```
   \newtheorem{thm}{定理}
       \begin{*thm*}[勾股定理]
            直角三角形$\angle ABC = \pi / 2$
         \end{*thm*}
   ```

   效果为:

   ```
   定理1 (勾股定理)直角三角∠ABC=π/2
   ```

6. 标题，作者，日期

   ```
   \newtheorem{thm}{定理}
   \title{杂谈勾股定理}
   \author{张三}
   \date{\today}
   ```

7. 参考文献相关,bib使用见后文

   ```
   % 格式：
   % plain，按字母的顺序排列，比较次序为作者、年度和标题.
   % unsrt，样式同plain，只是按照引用的先后排序.
   % alpha，用作者名首字母+年份后两位作标号，以字母顺序排序.
   % abbrv，类似plain，将月份全拼改为缩写，更显紧凑.
   % ieeetr，国际电气电子工程师协会期刊样式.
   % acm，美国计算机学会期刊样式.
   % siam，美国工业和应用数学学会期刊样式.
   % apalike，美国心理学学会期刊样式.
   \bibliographystyle{plain}
   
   % rf为bib文件
   \bibliography{rf}
   
   %引用
   \cref{王一晴2020}
   
   % 注意：文中不引用就不显示，以下在\bibliography{rf}之前达到正文不显示但可以出现在ref中
   \nocite{王一晴2020}
   
   
   ```

8. 设置摘要

   ```
   \begin{abstract}
           这是一杯关于勾股定理的小短文
   \end{abstract}
   ```

9. 显示首页`\maketitle`

10. 显示目录`\tableofcontents`

11. 小节

    ```
    \section{杂谈勾股定理}
    \subsection{杂谈勾股定理}
    \subsubsection{杂谈勾股定理}
    ```

12. 设置引文环境

    ```
    \begin{quote}
        \zihao{-5}\kaishu
        勾三股四玄五
    \end{quote}
    ```

13. 时间的短横线(1个c的距离)`我国的公元前7--6世纪`

14. 公式环境

    ```
    % 行间公式有标号
    \begin{equation}
        a(b+c)=ab+ac
    \end{equation}
    % 行间公式无标号1
    \begin{equation*}
        a(b+c)=ab+ac
    \end{equation*}
    % 行间公式无标号2
    \[
        a(b+c)=ab+ac
    \]
    % 行间公式无标号3
    $$
        a(b+c)=ab+ac
    $$
    % 行间公式加Lable
    \begin{equation}\label{1}
        a(b+c)=ab+ac
    \end{equation}
    % 行内公式1
    \(a(b+c)=ab+ac\)
    % 行内公式1
    $a(b+c)=ab+ac$
    ```

15.  图片环境
	    ```
	   \begin{figure}[ht]
        \centering
        %放缩因子有width,height,scale...
        \includegraphics[scale=0.6]{xiatu}
        %注意上下
        \caption{仿制的弦图}
        \label{fig:xiatu}
 	   \end{figure}
 	   ```
17. 表格环境
    ```
    \begin{table}[H]
    %注意|与lrc
        \begin{tabular}{|rrr|}
        	% 横线
            \hline
            % &用于对齐
            直角边 $a$ & 直角边 $a$ & 斜边 $a$\\
            \hline
            3&4&5\\
            5&12&13\\
            \hline
        \end{tabular}%
    \end{table}
    ```
    
18. 参考文献管理

    首先我们可以直接写，例如

    ```
    \begin{thebibliography}{99}
    	\addcontentsline{toc}{section}{References}
    	\bibitem{1}Elisa T. Lee, Oscar T. Survival Analysis in Public Health Research. \emph{Go. 	
    	College of Public Health}, 1997(18):105-134.
    	\bibitem{2}Wikipedia: Proportional hazards model. 2017.11.26. 			  
        \texttt{\\https://en.wikipedia.org/wiki/Proportional\_{}hazards\_{}model}
    \end{thebibliography}
    ```

    也可使用文件管理器将参考文献单独写一个文件，这里首推管理器为**JabRef**，好用，免费。注意：**请下载官方版！！**官网已经更新到5.0版本了但是国内都是4.2左右的，就连SourceForge都是2017的版本，界面简直没法比！！

    首先打开官网：www.jabref.org/

    往下翻，有一个下载发行版还是源文件，选download latest release，然后选择对应版本即可

    服务器在国外，所以下载很慢，自行处理┓(;´_｀)┏

    软件很好用，就是没有中文的，生成之后直接保存到工作文件夹下即可
 18. 修改页面页边距
	    ```
 	   \usepackage{geometry}
 	   \geometry{a6paper,centering,scale=0.8}
 	   % A6纸  居中  长宽为页面宽度0.8倍
 	   ```

19. 修改表格标题格式

    ```
    \usepackage[format=hang,font=small,textfont=it]{caption}
    % 图标标题悬挂对齐，左突出，小字号，斜体(中文楷书)
    ```

20. 自定义目录

    ```
    \usepackage[nottoc]{tocbiblind}
    ```

21. 自定义环境，$\LaTeX$ 的思想是格式与内容分离，所以一般不用

    ```
    \begin{quote}
        \zihao{-10}\kaishu
        勾三股四玄五
    \end{quote}
    ```

    一般写为

    ```
    \newenvironment{myquote}
        {\begin(quote)\kaishu\zihao{-5}}
        {\end{quote}}
    \begin{myquote}
        勾三股四玄五
    \end{myquote}
    ```


## 3. 文本的组织

### 3.1 符号的组织

#### 3.1.1重音符号

```
\"a
\'a
\`a
\^a
\ae
```

效果为

```
ä á à â æ
```

还有很多，见后面的参考手册

当然因为我们用的是UTF-8所以直接输入法输入即可

#### 3.1.2连词的处理

例如fi会直接连在一起，处理方法如下,{}与\/均可

```
fififififififififiifiiiiff{}ffff\/ffffiiii
```

效果如图

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200319005408911.png)

#### 3.1.3引号

Tab上面那个在英文状态下是引号的左半边，Enter左边的是后面的，中间写就是单引号(第一行)，双引号就是写双倍(第二行)，对于单双引号在一起的时候在分割地方加上`\,`

```
`hi'
``''
`\,``'\,''
```

效果如图

![](https://img-blog.csdnimg.cn/20200319005422625.png)

#### 3.1.4 时间的短杠,破折号和波浪号

两个是时间的短杠，三个是破折号，\sim是波浪

```
wtat it is a---hokl--JIKL
$\sim$
```

效果如图

![](https://img-blog.csdnimg.cn/20200319005441656.png)

#### 3.1.5 三个省略号

- `\ldots`是$\ldots$他会自动权衡这几个点之间的距离，点和文字之间的距离
- `\cdots`是$\cdots$唯一和ldots不同的是在中间
- `\dots` 是 amsmath 命令用来试图帮你在 \ldots 和 \cdots 中自动做决断的

```
aaaaaa\ldots aaaaaaaa\dots aaaaaa$\cdots$ aaaaaaaaa
```

效果如图

![](https://img-blog.csdnimg.cn/20200319005454151.png)

#### 3.1.6 命令与文字的关系

命令与文字之间的空格是会被忽略掉，latex会自动调整间距，也可以手动用`\ ` 加空格

```
It is \LaTeX aws!
    
It is \LaTeX  aws!
    
It is \LaTeX\ \ \ aws!
```

效果如图

![](https://img-blog.csdnimg.cn/20200319005509296.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0xpdWthaXJ1aQ==,size_16,color_FFFFFF,t_70)

#### 3.1.7 中文与英文之间的间距

中英文之间会自动加间距，手打空格无效，也有规避方法，就是让latex不认为中文是中文，而是一个普通latex对象，就是给中文加一个单独的box放着

```
中文与English的排版

中文与 English 的排版

\mbox{盒子与}English的排版
```

![](https://img-blog.csdnimg.cn/20200319005522768.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0xpdWthaXJ1aQ==,size_16,color_FFFFFF,t_70)

还有一个方法是用CJK

```
\CJKsetecglue{}
    中文与CJK
```

![](https://img-blog.csdnimg.cn/20200319005530812.png)

#### 3.1.8 幻影空格

通过幻影空格我们可以**占着茅坑不拉屎**，占多大的茅坑呢？与给的参数的长度决定

```
终极奥义，\phantom{隐身}!

终极奥义，隐身!
```

效果

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200319005541772.png)

这是给他水平方向空了，垂直也可以空，是`\vphantom`

#### 3.1.9 换行

1. 双反斜线换行：用双反斜线空格，这样会不会认为另起一段，所以下一段不会像第一段一样开头空两格

   ```
   双反斜线测试 双反斜线测试 双反斜线测试 双反斜线测试 双反斜线测试 双反斜线测试 双反斜线测试 双反斜线测试 双反斜线测试 双反斜线测试 \\双反斜线测试 双反斜线测试 双反斜线测试 双反斜线测试 双反斜线测试 双反斜线测试 双反斜线测试 双反斜线测试 双反斜线测试 双反斜线测试 
   ```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200319005557571.png)

2. 空一行换行：认为是另起一段

   ```
   双换行测试 双换行测试 双换行测试 双换行测试 双换行测试 双换行测试 双换行测试 双换行测试 双换行测试 双换行测试 双换行测试 双换行测试 
   
   双换行测试 双换行测试 双换行测试 双换行测试 双换行测试 双换行测试 双换行测试 双换行测试 双换行测试 双换行测试 双换行测试 双换行测试 
   ```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200319005605529.png)

3. \linebreak 换行，默认写一个\linebreak就可以了

   ```
   linebreak 测试 linebreak 测试 linebreak 测试 linebreak 测试 linebreak 测试 linebreak 测试 linebreak 测试 \linebreak
   linebreak 测试 linebreak 测试 linebreak 测试 linebreak 测试 linebreak 测试 linebreak 测试 linebreak 测试 linebreak 测试 
   ```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200319005613235.png)

可以看到三者区别就是

- `\\`是前一段断尾正常写，下一段无空格
- 空格是两段段断尾正常写，下一段有空格
- `\linebreak` 是第一段断尾**分散对齐**，下一段无空格

4. `\\`的扩展用法:给一个2cm的空行 

```
\\[2cm] 
```

![](https://img-blog.csdnimg.cn/20200319005626283.png)

5. linebreak的扩展用法:

   ```
   \linebreak[0-4，数越大建议力度越大]
   ```

#### 3.1.10 特殊符号

示例：

```
    \S 
    \dag
    \ddag
    \P
    \copyright
    \textregistered
    \texttrademark
    \pounds
    \textbullet
```

![](https://img-blog.csdnimg.cn/20200319005636647.png)

不包含text的还可以用于数学环境，有text的可以加入但是会报错`Command \textregistered invalid in math mode.`

```
\(
        \S 
        \dag
        \ddag
        \P
        \copyright
        \pounds
\)
```

效果[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-eid1j8q4-1584550369596)![](https://img-blog.csdnimg.cn/20200319005648650.png)

注意\pound从欧元变为了美元

特殊符号扩展包：`\usepackage{textcomp}`

示例

```
\usepackage{textcomp}
\texteuro
\textperthousand
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200319005658145.png)

实际上可以直接输入

```
§†‡¶©®™\$•
```

也可以使用\symbol直接输入编号得到符号，示例：

```
\symbol{25289}\symbol{27888}\symbol{36203}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200319005715387.png)

与python的ord(拉)的结果一样

**实际上，具体的标志可以查询长达358页的Pakin的参考手册**

简易版：https://math.uoregon.edu/wp-content/uploads/2014/12/compsymb-1qyb3zd.pdf

标准版：http://tug.ctan.org/info/symbols/comprehensive/symbols-letter.pdf

### 3.2 字体样式

**字体族：**有罗马样式(边角带勾的)，无衬线样式(没有带勾角的)，打字机字体(等宽)

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200319005816865.png)

**字体形状：**有直体(正常)，意大利体(斜体连笔)，斜体(斜的)，粗体

注意的是例如书名等理论上是用斜体，但实际上是用意大利，这是由于1.好看2.斜体支持不好(详见《西文排版》)

有两种声明形式

1. \命令让后面的全应用
2. \ { }让括号内的应用

我为了测试方便写在了quote里面，实际不需要

```
\begin{quote}
        \rmfamily This is Roma Family front family 罗马体\\
        \sffamily This is sans serif Family front family 无衬线 \\
        \ttfamily This is Typing front family 打字机\\
        \textrm{This is Roma Family front family 罗马体} \\
        \textsf{This is sans serif Family front family 无衬线} \\
        \texttt{This is Typing front family 打字机} \\
    \end{quote}

    \begin{quote}
        \upshape upfront upfront upfront 直立 \\
        \itshape itshape itshape itshape 意大利体 \\
        \slshape slshape slshape slshape 斜体 \\
        \scshape scshape scshape scshape 小型大写 \\
        \normalfont normalfontnormalfont 正常字体 \\
        \textup{textup textup textup 直立} \\
        \textit{textit textit textit 意大利体} \\
        \textsl{textsl textsl textsl 斜体} \\
        \textsc{textsc textsc textsc 小型大写} \\
        \textnormal{textnormal textnormal textnormal 正常字体}\\
    \end{quote}
```

效果

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200319005800907.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0xpdWthaXJ1aQ==,size_16,color_FFFFFF,t_70)

**字体样式的矫正**：啦啦啦啦啦啦




---
## $\LaTeX$各种报错的方法
1. Error Page XXX on XXX not ...
	这是vscode配置问题，settings.json文件加入
	```
	"latex-workshop.latex.recipes": [
      {
        "name": "xelatex",
        "tools": [
          "xelatex"
        ]
      },
      {
        "name": "xelatex -> bibtex -> xelatex*2",
        "tools": [
          "xelatex",
          "bibtex",
          "xelatex",
          "xelatex"
        ]
      }
    ],
    "latex-workshop.latex.tools": [
      {
        "name": "latexmk",
        "command": "latexmk",
        "args": [
          "-synctex=1",
          "-interaction=nonstopmode",
          "-file-line-error",
          "-pdf",
          "%DOC%"
        ]
      },
      {
        "name": "xelatex",
        "command": "xelatex",
        "args": [
          "-synctex=1",
          "-interaction=nonstopmode",
          "-file-line-error",
          "%DOC%"
        ]
      },
      {
        "name": "bibtex",
        "command": "bibtex",
        "args": [
          "%DOCFILE%"
        ]
      }
    ],
	```
2. vscode自动保存烦人？
	这是vscode配置问题，settings.json文件加入
	```javascript
	//auto compress
	    "latex-workshop.latex.autoBuild.run": "never",
	```
3. Missing } inserted.
	1.在数学区出现美元符号
	2.多写了},比如
	```javascript
	\newenvironment{lalalalala}
    	{\begin{quote}\kaishu\zihao{-5}}
	    {\end{quote}}
	```
	写成了
	```javascript
	\newenvironment{lalalalala}{
    	{\begin{quote}\kaishu\zihao{-5}}
	    {\end{quote}}
	}
	```
	4.There's no line here to end.
		前面是不是多加了`\\`
		

