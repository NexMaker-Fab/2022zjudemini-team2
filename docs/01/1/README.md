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
检查node。

```
node -v
```
3. **使用github+Docsify作为网站搭建工具**

详情参照[此网页教程](https://www.nexmaker.com/doc/1projectmanage/github&docsify.html)

4. **GitHub Pages 站点部署**

- 关于 GitHub Pages
GitHub Pages 是一项静态站点托管服务，它直接从 GitHub 上的仓库获取 HTML、CSS 和 JavaScript 文件，（可选）通过构建过程运行文件，然后发布网站。 
你可以在 GitHub 的 github.io 域或自己的自定义域上托管站点。
你可以创建在 Internet 上公开可用的 GitHub Pages 站点。 使用 GitHub Enterprise Cloud 的组织还可以通过管理对站点的访问控制来私下发布站点

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
2. 创建一个_sidebar.md文档，编写侧边栏目录并链接在子页面中
3. 编辑各子页面内容
4. 将各子页面链接在侧边栏中

### 4.封面制作
1. 在根目录下创建_coverpage文件，在index文件中键入 

        coverpage：ture
- 具体代码如下

```
<!-- index.html -->

<script>
  window.$docsify = {
    coverpage: true
  }
</script>
<script src="//cdn.jsdelivr.net/npm/docsify/lib/docsify.min.js"></script>
```
- 目前的背景是随机生成的渐变色，我们自定义背景色或者背景图。在文档末尾用添加图片的 Markdown 语法设置背景。

```
<!-- _coverpage.md -->
# docsify <small>3.5</small>
[GitHub](https://github.com/NexMaker-Fab/2022zjudemini-team2)
[Get Started](#quick-start)
<!-- 背景图片 -->
![](feng.JPG)
<!-- 背景色 -->
![color](#f0f0f0)
```
#### 5.从远程仓库获取更改
与远程存储库交互时，这些命令非常有用。 clone 和 fetch 将远程代码从存储库的远程 URL 下载到本地计算机，merge 用于将其他人的工作与你的工作合并在一起，而 pull 是 fetch 和 merge 的组合。
1. 克隆仓库
克隆存储库时，可以从多个不同的 URL 中进行选择。 登录到 GitHub 后，可在仓库详细信息下面找到这些 URL：
<img src="img/1/27.jpg">

运行 git clone 时，会执行以下操作：

- 创建名为 repo 的新文件夹
- 将它初始化为 Git 仓库
- 创建名为 origin 的远程存储库，指向用于克隆的 URL
- 将所有的仓库文件和提交下载到那里

#### 6.本地上传部署
1. 打开GitHub desktop，当我们每次做出修改时，将项目文件克隆到本地进行修改后实时上传更新即可
<img src="img/1/8.png">

<img src="img/1/9.png">

2. 每次更改后点击提交并更新
<img src="img/1/10.png">

3. 在vscode中提交代码到仓库
vs code打开工作区就会看到所有代码显示在这里
<img src="img/1/11.png">

点击+号，把所有文件提交到暂存区。

然后打开菜单选择--提交已暂存的
<img src="img/1/12.png">

#### 5.设置 GitHub Pages 站点的可见性
如果对 GitHub Pages 具有访问控制权限，便可以通过私密发布站点来限制访问项目站点。 只有对发布站点的仓库具有读取权限的人才可访问私密发布的站点。 
- 以私密方式发布的站点的子域
私下发布的站点与公开发布的站点位于不同的子域中。 这可确保您的 GitHub Pages 站点从发布之日起是安全的：

我们使用 TLS 证书自动保护 *.pages.github.io 的每个子域，并强制执行 HSTS 以确保浏览器始终通过 HTTPS 提供页面。
我们对以私密方式发布的站点使用独特的子域，从而确保组织中其他存储库不能在与该站点相同的来源发布内容。 这样可以保护这些站点免受“cookie 抛掷”攻击。 这也是为什么我们不在 github.com 域上托管 GitHub Pages 网站的原因。
- 更改 GitHub Pages 站点的可见性
1. 在 GitHub Enterprise Cloud 上，导航到站点的仓库。 1. 在存储库名称下，单击 “设置”。
<img src="img/1/29.jpg">

2. 在边栏的“代码和自动化”部分，单击“ 页面”。
3. 在 GitHub Pages 下，选择“GitHub Pages 可见性”下拉菜单，然后单击可见性。
<img src="img/1/26.jpg">

4. 若要查看已发布的网站，请在“GitHub Pages”下单击“ 访问网站”。
<img src="img/1/28.jpg">

## tips
1. 重新开启vs code时，要调出本地预览网页，需先在下方终端中输入

        docsify init

 当下方出现  Initialization succeeded! 字样时，输入
    
         docsify serve 
即可获取预览网页

## reference
[docsify:一个神奇的文档网站生成器。](https://www.nexmaker.com/doc/1projectmanage/github&docsify.html)<br>
[docsify使用指南](https://www.cnblogs.com/Can-daydayup/p/15413267.html)<br>
[GitHub Pages部署教程](https://docs.github.com/zh/pages/getting-started-with-github-pages/about-github-pages)<br>
[GitHub Docs](https://docs.github.com/zh)<br>
[>>return](/)