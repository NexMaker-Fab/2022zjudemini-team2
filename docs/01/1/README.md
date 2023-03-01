# 网站搭建

## 简介

我们使用了Vs code软件结合docsify来创建了我们的网站，并通过markdown语言来编辑文档，在网站建立的过程中，通过对前段知识的学习，建立了文件层级管理的意识，并通过简单的工具处理了所遇到的大量问题，提高了解决问题的能力，培养了项目管理意识。并通过小组合作更好的进行了任务分配，增进了团队协作能力。

系统：macos

## 网页搭建步骤
#### 1.注册github账号
1. **通过邮箱申请github账号**
注册一个github账号，用来存放我们的网站，新建一个项目，如下所示：
<img src="img/1/5.png">


然后如下图所示，输入自己的项目名字，后面一定要加.github.io后缀，README初始化也要勾上。
<img src="img/1/6.png">

2. **安装node.js.**

安装后可以使用命令来检查是否安装成功
检查node

```
node -v
```
3. **使用github+Docsify作为网站搭建工具**

详情参照[此网页教程](https://www.nexmaker.com/doc/1projectmanage/github&docsify.html)


#### 2.使用Docsify配合Markdown语言搭建网站
1. 全局安装  docsify-cli 工具，可以方便地创建及在本地预览生成的文档。

打开github终端并键入下列代码：
    
    npm i docsify-cli -g

2. 在项目的./docs 目录里写文档，直接通过 init 初始化项目

    docsify init ./docs

3. 通过运行 docsify serve 启动一个本地服务器，可以方便地实时预览效果。默认访问[此地址]( http://localhost:3000)
    
    docsify serve docs

更多命令行工具用法，参考 [docsify-cli](https://github.com/docsifyjs/docsify-cli) 文档。

4. 为了获得侧边栏，您需要创建自己的_sidebar.md，你也可以自定义加载的文件名。默认情况下侧边栏会通过 Markdown 文件自动生成，效果如当前的文档的侧边栏。
    首先配置 loadSidebar 选项
        <!-- index.html -->

        <script>
            window.$docsify = {
                loadSidebar: true
            }
        </script>
        <script src="//cdn.jsdelivr.net/npm/docsify/lib/docsify.min.js"></script>
    接着创建 _sidebar.md 文件，内容如下
        <!-- docs/_sidebar.md -->

        *[首页](zh-cn/)
        *[指南](zh-cn/guide)
    需要在 ./docs 目录创建 .nojekyll 命名的空文件，阻止 GitHub Pages 忽略命名是下划线开头的文件。

### 3.按文件嵌套结构创建文件夹及子目录
<img src="img/1/7.png">

1. 在vs code中建立新文件夹，将侧边栏结构按顺序嵌套在文件夹中
2. 创建一个—sidebar.md文档，编写侧边栏目录并链接在子页面中
3. 编辑各子页面内容
4. 将各子页面链接在侧边栏中

### 4.封面制作
1. 在根目录下创建-coverpage文件，在index文件中键入 

        coverpage：ture

#### 4.本地上传部署
1. 打开GitHub desktop，当我们每次做出修改时，将项目文件克隆到本地进行修改后实时上传更新即可
<img src="img/1/8.png">

<img src="img/1/9.png">

2. 每次更改后点击提交并更新
<img src="img/1/10.png">


## tips
1. 重新开启vs code时，要调出本地预览网页，需先在下方终端中输入

        docsify init

 当下方出现  Initialization succeeded! 字样时，输入
    
         docsify serve 
即可获取预览网页



[>>return](/)