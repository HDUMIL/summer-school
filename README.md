# 媒体智能实验室暑期班

<img style="max-width:750px;" src="./assets/img/mil.png">

[实验室主页](http://mil.hdu.edu.cn/) | [课程主页](https://hdumil.github.io/summer-school/) | [GitHub 主页](https://github.com/hdumil) | [讨论区](https://github.com/hdumil/summer-school/issues)

![semester](https://img.shields.io/badge/semester-2019-blue.svg) ![build](https://img.shields.io/badge/build-passing-orange.svg) ![license](https://img.shields.io/badge/license-MIT-green.svg) ![GitHub Pages](https://img.shields.io/badge/GitHub%20Pages-Jekyll-blue.svg) ![chat on](https://img.shields.io/badge/chat%20on-issues-yellow.svg)

媒体智能实验室(Media Intelligence Laboratory, MIL) 隶属于杭州电子科技大学计算机学院。原名计算机动画与多媒体分析实验室(Computer Animation and Multimedia Analysis LAB，CAMALAB), 成立于 2014 年。实验室的研究方向为多媒体与机器学习等人工智能相关前沿领域。具体而言，包含：图像检索、跨媒体表达、人脸检测与识别、图像分类/目标识别、图像质量评价、视频理解、图像生成、深度学习等前沿课题。

每年暑期将为新入学研究生安排入门课程，进行基础内容的讲解，并培养相关科研能力。每一期暑期班的讲座内容都会有所差异，请注意当前项目对应的学期时间，你可以找到一份 [2017&2018](https://github.com/hdumil/cama_summer_school_2017) 学期的存档作为参考。

## 维护人员文档

静态网站基于 GitHub Pages 使用 [Jekyll](https://jekyllrb.com/) 引擎渲染，使用 Liquid 语法。

本项目未使用任何 Jekyll 主题，大部分网页内容修改只需要基础的 HTML / CSS / JS 前端知识。

项目允许被 Fork, 使用 Clone 建议将 `depth` 设置为 1，非管理人员发起的 PR 请求会被直接忽略。

如果对当前项目的使用有任何疑问，请发送邮件到 acdoge[dot]cao[at]gmail[dot]com

### 文件夹结构

```html
_includes/                    # 存放可被重用或作为局部模板的 HTML 文件
  faq.html                    # 常见问题解答
  information.html            # 课程相关信息
  schedule.html               # 课程大纲时间表
  ...
  head.html                   # 网站头信息，多存放 meta 与 CSS
  header.html                 # 网站头部内容，多存放标题与导航块
  footer.html                 # 网站尾部内容，多存放网站说明信息

_layouts/                     # 渲染规则，即网页模板，默认为 default.html
  default.html

assets/                       # 统一用于存放静态文件资源
  css/                        # 存放 CSS 层叠样式表文件
  img/                        # 存放 Image 图像文件
  js/                         # 存放 Javascript 脚本

assignments/                  # 存放作业说明与相关文件
notebooks/                    # 存放 .ipynb 后缀的文件，常用于助教演示
slides/                       # 存放 PDF 格式幻灯片，为讲座对应内容

_config.yml                   # 网站全局设置信息
index.html                    # 网站默认 index 主页，必须设置
```

### 如何修改课程人员信息

在 `_includes/instructor.html` 中找到“讲师”或“助教”列表：

```html
<h2 class="module-header">{类型}</h2>
```

在下方找到合适的顺序位置修改对应信息：

```html
<div class="instructor" id="{name}">
    <a href="{url}" target="_blank">
        <div class="instructorphoto">
            <img class="img-hover" src="assets/img/{name}.{jpg/png/...}">
        </div>
        <div>{名称}</div>
    </a>
    <br>
</div>
```

其中 `{name}` 为姓名信息，`{url}`为个人主页信息(如果没用可使用 `#` 代替), `{name}.{jpg/png/...}` 为需要添加到 `assets/img` 文件夹下的图片，注意分辨率不能低于 120 * 120 px, 保持图片整体为正方形比例，超过显示大小的会自动进行缩放。

### 如何修改课程大纲和时间安排

在 `_includes/schedule.html` 中 `<tbody></tbody>` 域内进行修改，例如：

```html
<tr>
    <td>第1列内容</td>
    <td>第2列内容</td>
    <td>第3列内容</td>
    <td>第4列内容</td>
    <td>第5列内容</td>
</tr>
```

以上为单行信息的修改，也可以根据情况添加新的 `<th>` 列，并设置列宽 `width` 比例：

```html
<tr class="active">
    <th style="width:10%;">类型</th>
    <th style="width:12%;">日期</th>
    <th style="width:30%;">主要内容</th>
    <th style="width:30%;">相关材料</th>
    <th style="width:18%;">备注</th>
</tr>
```

在 `<tr class="active">` 中使用 `class` 控制表格背景，

也可以在 `/assets/css/main.css`中自定义新样式，

目前已经提供的有 `active` , `info` , `warning` 与  `danger`.

为了更好的控制样式，如单元格合并居中等，时间表不推荐使用 Markdown 语法。

### 其它维护说明

Jekyll 引擎支持以 Markdown 语法进行渲染，即使用 `.md` 文件代替 `.html` 文件。
想要触发模板渲染机制，请使用 YAML 头写法，例如：

```YAML
---
layout: default
---
```

默认网页渲染格式参考 `default.html` 文件：

```html
<!DOCTYPE html>
<html>
<html lang="{{ page.lang | default: site.lang | default: "zh" }}"></html>

{% include head.html %}

<body>

    {% include header.html %}

    <div class="page-content">
        <div class="wrap">
            {{ content }}
        </div>
    </div>

    {% include footer.html %}

    <!-- JavaScript -->
    <script src="{url}.js"></script>
</body>

</html>
```

注意事项：

- 由于 GitHub 服务器在国内不稳定，CSS / JS 文件尽可能使用国内 CDN 进行加速。
- JS 文件通常在 `_layouts` 网页源码内 `footer.html` 后按需调用，加快访问速度。
- 由于图片为非二进制文件容易影响 `git` 体积，建议使用稳定图床，或通过 TinyJPG 网站压缩后上传。
- 对于类似的非二进制文件，如有存储资源，建议使用国内服务器进行替代，或提供镜像下载源。
- 请勿在开源文件中，包括 Commits 等记录中泄露个人信息或者保密信息。
- 关于网页渲染机制的更多说明请查阅 Jekyll 官方文档。

### 进阶使用

你可以根据实际情况，设计一些新的页面或渲染模板以加强互动性和丰富性，参考 Jekyll Themes.

甚至可以完全脱离 Jekyll 引擎范围，自由地开发新的静态页面(但是不推荐这样做)。

## 使用协议

本项目使用 [MIT](./LICENSE) 协议，允许二次使用，请勿擅自修改协议内容。
