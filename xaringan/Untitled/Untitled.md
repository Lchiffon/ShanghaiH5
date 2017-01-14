---
title: "幻灯忍者"
subtitle: "写轮眼"
author: "谢益辉"
date: "2016/12/12"
output:
  xaringan::moon_reader:
    css: zh-CN.css
    lib_dir: libs
    nature:
      highlightStyle: github
      highlightLines: true
---



background-image: url(https://upload.wikimedia.org/wikipedia/commons/b/be/Sharingan_triple.svg)

???

图片来源：[Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Sharingan_triple.svg)

---
class: center, middle

# xaringan

### /ʃæ.'riŋ.ɡæn/

---
class: inverse, center, middle

# 出发！

---

# 你好世界

首先从 [Github](https://github.com/yihui/xaringan) 安装 **xaringan** 包：


```r
if (!requireNamespace("xaringan"))
  devtools::install_github("yihui/xaringan")
```

```
## Loading required namespace: xaringan
```

--

除非你是六指琴魔，否则我建议安装 [RStudio 编辑器](https://www.rstudio.com/products/rstudio/)，它会让你做幻灯片做得飞起。

- 从菜单 `File -> New File -> R Markdown -> From Template -> Ninja Presentation (Simplified Chinese)` 创建一个新文档；

--

- 点击 `Knit` 按钮编译文档；

--

- 或者点击 [RStudio 插件](https://rstudio.github.io/rstudioaddins/)<sup>*</sup> “Infinite Moon Reader” 在 RStudio 里实时预览幻灯片（每次你保存文档的时候，它会自动重新编译）；

.footnote[[*] 如果你看不到模板或者插件，请参见 [#2](https://github.com/yihui/xaringan/issues/2)，你的某些 R 包可能崩坏了，需要重新安装。]

---
background-position: 50% 50%
class: center, bottom, inverse

### 洛阳亲友如相问，请你不要告诉他

（我是怎么做幻灯片的）

---

# 你好忍者

忍者不会停留在“你好世界”里，要用好这个 R 包，你需要了解：

1. JavaScript 库 [remark.js](https://remarkjs.com) 的语法；

1. **xaringan** 包中的选项;

**xaringan** 将 R Markdown 的查克拉注入了 **remark.js**。浏览器中的幻灯片是 remark.js 渲染出来的，而它的 Markdown 源文档是从 R Markdown 生成的（实际上主要是 **knitr**）。

---

# remark.js

关于 remark.js 的用法可参考它的[首页](https://remarkjs.com)，由于伟大的墙，你可能打不开这个页面（因为里面用了 Google 字体）。不过 [remark.js 的维基页面](https://github.com/gnab/remark/wiki) 已经有足够的信息了，你需要学习：

- 如何创建一页新的片子，主要是 Markdown 语法<sup>*</sup> 以及单页片子的属性设置；

- 如何排版，例如文本对齐；

- 如何设置整个幻灯片的选项（代码高亮样式之类的）；

- 怎样播放幻灯片（快捷键，按 `h` 键基本就知道了）；


.footnote[[*] 它和 Pandoc Markdown 语法不同，不过对做幻灯片而言，简单的语法可能也足够了。]

---
background-size: cover
class: center, bottom, inverse

### 唔，remark.js，朕很满意！

---
class: inverse, middle, center

# xaringan 包的使用

---

# xaringan

**xaringan** 包提供了一个 R Markdown 输出格式 `xaringan::moon_reader`，你可以在 R Markdown 文档的元数据中使用它，例：

```yaml
---
title: "啧啧啧，厉害啊"
author: "张三"
date: "2016年12月12日"
output:
  xaringan::moon_reader
    nature:
      autoplay: 30000
      highlightStyle: github
---
```

欲知所有可能的选项，参见 R 帮助文档 `?xaringan::moon_reader`。

---

# remark.js 与 xaringan 的区别

remark.js （左）与 **xaringan** （右）：

.pull-left[
1. 需要一个 HTML 容器文件；

1. 只能用 Markdown；

1. 若想自动播放幻灯片需要写 JavaScript；

1. 需手工配置 MathJax；

1. 用 `*` 高亮一行代码；

1. 编辑 Markdown 之后需要刷新浏览器看结果；
]

.pull-right[
1. 用 R Markdown 文档生成幻灯片；

1. Markdown 里可以嵌入 R 代码；

1. 可用 `autoplay` 选项自动播放；

1. MathJax 无需特别配置；<sup>*</sup>

1. 用 `{{}}` 高亮一行代码;

1. 用 RStudio 插件“Infinite Moon Reader”自动预览幻灯片；
]

.footnote[[*] 下一页有数学公式例子。]

---

# 数学公式

数学公式用 LaTeX 语法写在一对美元符号中间，例如 &#36;\alpha+\beta$ 会生成 $\alpha+\beta$。若要将公式单独显示为一个段落，可以用一对双重美元符号：

```
$$\bar{X}=\frac{1}{n}\sum_{i=1}^nX_i$$
```

$$\bar{X}=\frac{1}{n}\sum_{i=1}^nX_i$$

局限性：

1. 公式的源代码只能写在一行上，不能换行；

1. 起始美元符号后以及结束美元符号前不能有空格，否则不会被识别为公式；

---

# R 代码


```r
# 一个无聊的回归模型
fit = lm(dist ~ 1 + speed, data = cars)
coef(summary(fit))
```

```
#               Estimate Std. Error   t value     Pr(>|t|)
# (Intercept) -17.579095  6.7584402 -2.601058 1.231882e-02
# speed         3.932409  0.4155128  9.463990 1.489836e-12
```

```r
dojutsu = c('地爆天星', '天照', '加具土命', '神威', '須佐能乎', '無限月読')
grep('天', dojutsu, value = TRUE)
```

```
# [1] "地爆天星" "天照"
```

---

# R 图形


```r
par(mar = c(4, 4, 1, .1))
plot(cars, pch = 19, col = 'darkgray', las = 1)
abline(fit, lwd = 2)
```

![plot of chunk cars](figure/cars-1.svg)

---

# HTML 控件

我没有仔细测试 [HTML 控件](https://htmlwidgets.org)，祝你好运。下一页上有两个例子，一个地图，一个表格，目测貌似可用。

目前也不支持 Shiny 模式（即 `runtime: shiny`）。还是别把你的幻灯片搞辣么复杂吧。

---


```r
library(leaflet)
leaflet() %>% addTiles() %>% setView(-93.65, 42.0285, zoom = 17)
```

```
## Error in loadNamespace(name): there is no package called 'webshot'
```

---


```r
DT::datatable(
  head(iris, 10),
  fillContainer = FALSE, options = list(pageLength = 5)
)
```

```
## Error in loadNamespace(name): there is no package called 'webshot'
```

---

# 一些小技能

- “Infinite Moon Reader”插件默认情况下会锁住你的 R 进程，有它没你，有你没它。你可以设置一个选项，让它一边儿凉快去：

    ```r
    options(servr.daemon = TRUE)
    ```
    
    你可以把这个设置写在 `~/.Rprofile` 文件中，这样你将来所有 R 进程都不会被这个插件挡住去路。
    
    这事情背后的魔法在 [**servr**](https://github.com/yihui/servr) 包中。








---

class: center, middle

# 蟹蟹

本幻灯片由 R 包 [**xaringan**](https://github.com/yihui/xaringan) 生成；

查克拉来自于 [remark.js](https://remarkjs.com)、[**knitr**](http://yihui.name/knitr)、以及 [R Markdown](https://rmarkdown.rstudio.com)。
