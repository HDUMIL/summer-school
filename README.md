# 媒体智能实验室暑期班

媒体智能实验室(Media Intelligence Laboratory, MIL) 隶属于杭州电子科技大学计算机学院。原名计算机动画与多媒体分析实验室(Computer Animation and Multimedia Analysis LAB，CAMALAB), 成立于 2014 年。每年暑期将为新入学研究生安排入门课程，进行基础内容的讲解，并培养相关科研能力。

请访问上方给出的网站链接获取详细信息。

## 维护人员文档

静态网站基于 GitHub Pages 使用 [Jekyll](https://jekyllrb.com/) 引擎渲染，使用 Liquid 语法。
未使用任何 Jekyll 主题，大部分网页内容修改只需要基础的 HTML / CSS / JS 前端知识。

### 文件夹结构

```html
_includes/                    # 存放可被重用或作为模板的 HTML 文件
  faq.html                    # 常见问题解答
  information.html            # 课程相关信息
  schedule.html               # 课程大纲时间表
  ...
  head.html                   # 网站头信息，多存放 meta 与 CSS
  header.html                 # 网站头部内容，多存放标题与导航块
  footer.html                 # 网站尾部内容，多存放网站说明信息

_layouts/                     # 渲染规则，即网页模板，默认为 defaul.html
  default.html

assets/                       # 统一用于存放静态文件资源
  css/                        # 存放 CSS 层叠样式表文件
  img/                        # 存放 Image 图像文件
  js/                         # 存放 Javascript 脚本

assignments/                  # 存放作业说明与相关文件
notebooks/                    # 存放 .ipynb 后缀的文件，常用于演示
slides/                       # 存放 PDF 格式幻灯片

_config.yml                   # 网站全局设置信息
index.html                    # 网站默认 index 主页
```

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
- 对于类似的非二进制文件，如有资源，建议使用国内服务器进行替代。
- 请勿在开源文件中，包括 Commits 等记录中泄露个人信息或者保密信息。
- 关于网页渲染机制的更多说明请查阅 Jekyll 官方文档。

## 二次使用协议

本项目使用 [MIT](./LICENSE) 协议，允许二次使用，请勿修改协议内容。
如果对当前项目的使用有任何疑问，请发送邮件到 acdoge[dot]cao[at]gmail[dot]com
