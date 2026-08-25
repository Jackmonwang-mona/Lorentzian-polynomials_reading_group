# 数学 Group Project 网站模板：从修改到上线

这是一套给 directed study、reading group、research project 使用的 GitHub Pages 静态网页模板。

它只使用：

- `HTML`：负责网页内容与结构；
- `CSS`：负责颜色、排版和手机适配；
- GitHub Pages：负责免费发布网页。



---

## 1. 文件夹里有什么

```text
group-project-template/
├── index.html                  # 主页：绝大多数内容在这里修改
├── style.css                  # 样式：颜色、字号、间距、手机适配
├── README.md                  # 你正在读的中文教程
├── .nojekyll                  # 告诉 GitHub 不使用 Jekyll
├── assets/
│   ├── favicon.svg            # 浏览器标签页的小图标
│   └── social-preview.png     # 分享链接时使用的横幅图
└── materials/
    ├── index.html             # 资料页示例
    └── week-01-notes.md       # 每周 Markdown 笔记示例
```

最重要的规则：**发布时，`index.html` 必须位于 GitHub 仓库最外层。**

---

## 2. 第一次打开和预览

### 方法 A：最快的方法

1. 解压模板 ZIP。
2. 打开解压后的文件夹。
3. 双击 `index.html`。
4. 网页会直接在浏览器里打开。

这种方法足够检查文字、颜色和大部分链接。

### 方法 B：在 VS Code 中预览（推荐）

1. 打开 VS Code。
2. 选择 `File → Open Folder`。
3. 选择解压后的模板文件夹，而不是只打开一个文件。
4. 在左侧点击 `index.html`。
5. 安装 VS Code 扩展 **Live Server**。
6. 右键 `index.html`，选择 `Open with Live Server`。

以后每次保存文件，浏览器页面通常会自动刷新。

---

## 3. 第一次应该修改什么

在 VS Code 中按：

```text
Ctrl + Shift + F
```

搜索：

```text
EDIT HERE
```

模板已经把主要修改位置编号为 `EDIT HERE 1` 到 `EDIT HERE 12`。建议按下面顺序修改：

| 顺序 | 修改内容 | 在哪里 |
| --- | --- | --- |
| 1 | 项目名称、学期和一句话简介 | `index.html` 的 `EDIT HERE 1–3` |
| 2 | 下一次 meeting | `EDIT HERE 4` |
| 3 | 最新公告 | `EDIT HERE 5` |
| 4 | 项目目标和主题 | `EDIT HERE 6` |
| 5 | 导师与成员 | `EDIT HERE 7` |
| 6 | meeting 时间、地点和日程 | `EDIT HERE 8–9` |
| 7 | notes、PDF、slides 链接 | `EDIT HERE 10` |
| 8 | 联系邮箱和页脚 | `EDIT HERE 11–12` |
| 9 | 颜色 | `style.css` 最上方的 `:root` |

### 修改普通文字

例如：

```html
<h1>Geometry &amp; Dynamics Reading Group</h1>
```

只改标签中间的文字：

```html
<h1>Our Directed Study Project</h1>
```

不要删除 `<h1>` 和 `</h1>`。

### 修改链接

```html
<a href="materials/week-01-notes.md">Week 1 notes</a>
```

- `href="..."` 是点击后前往的位置；
- `Week 1 notes` 是网页上显示的文字。

外部网页链接写完整网址：

```html
<a href="https://example.com/paper.pdf">Main paper</a>
```

仓库内文件使用相对路径：

```html
<a href="materials/member-a-slides.pdf">Member A slides</a>
```

不要在内部路径前加 `/`。使用相对路径后，即使网址是
`USERNAME.github.io/REPOSITORY/`，链接也不会跳错位置。

### 添加一个成员

在 `people-grid` 中复制一整段：

```html
<article class="person-card">
  <span class="avatar" aria-hidden="true">ZW</span>
  <p class="person-role">Group member</p>
  <h3>Zemeng Wang</h3>
  <p>Hyperbolic geometry</p>
  <a href="mailto:name@example.edu">name@example.edu</a>
</article>
```

然后改缩写、姓名、方向和邮箱。删除成员时，也要删除完整的 `<article> ... </article>`。

### 添加一周日程

在表格的 `<tbody>` 中复制一整段：

```html
<tr>
  <td>Oct 9</td>
  <td>Member B</td>
  <td>Cycle transformations</td>
  <td><a href="materials/week-06-notes.pdf">Week 6</a></td>
  <td><span class="status status-planned">Planned</span></td>
</tr>
```

状态样式已经准备好：

- `status-complete`：已经完成；
- `status-next`：下一次 meeting；
- `status-planned`：之后的计划。

同一时刻最好只保留一个 `status-next`。

### 添加 PDF 或 slides

1. 把文件名改成简单的英文，例如 `week-03-notes.pdf`。
2. 把文件放进 `materials` 文件夹。
3. 在 `index.html` 中加入：

```html
<a href="materials/week-03-notes.pdf">Week 3 notes</a>
```

文件名建议只使用小写英文字母、数字和连字符 `-`，不要使用空格。

### 修改颜色

打开 `style.css`，最上方可以看到：

```css
:root {
  --paper: #f7f4ed;
  --navy: #173b5f;
  --burgundy: #8f2945;
}
```

先只改这三个颜色，保存后观察变化。如果页面变得难以阅读，就按 `Ctrl + Z` 撤销。

---

## 4. 第一次发布到 GitHub Pages：完全不用命令行

### 第一步：创建空仓库

1. 登录 GitHub。
2. 点击右上角 `+`，选择 `New repository`。
3. `Repository name` 可以填 `directed-study` 或 `geometry-reading-group`。
4. 如果使用 GitHub Free，建议先选择 `Public`。
5. 为了避免和模板文件冲突，暂时不要勾选自动创建 README、`.gitignore` 或 License。
6. 点击 `Create repository`。

### 第二步：上传模板内容

1. 在空仓库页面点击 `uploading an existing file`；如果仓库已经有文件，点击 `Add file → Upload files`。
2. 打开你解压后的模板文件夹。
3. 选中**文件夹里面的全部内容**并拖进 GitHub 页面。
4. 确认 GitHub 顶层直接出现 `index.html`、`style.css`、`assets` 和 `materials`。
5. 在提交说明中填写 `Add group project website`。
6. 点击 `Commit changes`。

常见错误：把外层 `group-project-template` 文件夹整体套在仓库里，结果变成
`group-project-template/index.html`。这种结构会导致 Pages 找不到首页。

### 第三步：打开 Pages

1. 进入仓库的 `Settings`。
2. 在左侧找到 `Pages`。
3. 在 `Build and deployment` 下，把 `Source` 设为 `Deploy from a branch`。
4. `Branch` 选择 `main`。
5. 文件夹选择 `/(root)`。
6. 点击 `Save`。

GitHub 官方说明，第一次或一次更新最多可能需要约 10 分钟才发布完成。

### 第四步：找到网址

如果：

```text
用户名：jackmonwang-mona
仓库名：directed-study
```

网页地址通常是：

```text
https://jackmonwang-mona.github.io/directed-study/
```

这是 **project site** 的正常格式，仓库名会出现在网址后面。

只有当仓库名称本身严格叫：

```text
jackmonwang-mona.github.io
```

地址才会是：

```text
https://jackmonwang-mona.github.io/
```

---

## 5. 以后怎样更新网页

### 小修改：直接在 GitHub 网页中完成

1. 打开仓库。
2. 点击 `index.html`。
3. 点击右上方铅笔图标。
4. 修改文字。
5. 点击 `Commit changes`。

Pages 会自动重新发布。

### 正式方法：VS Code + GitHub Desktop

适合持续整个学期更新。

1. 安装并登录 GitHub Desktop。
2. 在 GitHub 仓库页面点击 `Code → Open with GitHub Desktop`，把仓库 clone 到电脑。
3. 用 VS Code 打开 clone 下来的整个文件夹。
4. 修改并保存文件。
5. 回到 GitHub Desktop，在左下角写简短说明，例如 `Update week 4 schedule`。
6. 点击 `Commit to main`。
7. 点击 `Push origin`。

三个词的区别：

- **Commit**：在本地做一次有说明的版本快照；
- **Push**：把本地 commit 发送到 GitHub；
- **Pages**：把 GitHub 中的最新网页版本发布到公开网址。

---

## 6. 小组成员怎样共同维护

### 邀请成员

仓库负责人进入：

```text
Settings → Collaborators → Add people
```

搜索成员的 GitHub 用户名并发送邀请。对方接受后即可协作。

### 两种协作强度

#### 初级方式：一名网页负责人

- 每位成员把 notes、slides 或需要修改的信息发给负责人；
- 负责人统一更新 `main`；
- 最不容易发生冲突，适合刚开始的 2–5 人小组。

#### 推荐方式：branch + pull request

当多人都会 Git 后：

1. 每个人为自己的任务新建 branch，例如 `week-04-notes`。
2. 在自己的 branch 中修改和 commit。
3. Push 后创建 Pull Request。
4. 由 coordinator 检查预览和文字。
5. 确认后 merge 到 `main`。

Pull Request 的意义是：**先提出修改并让组员审阅，再合并进正式网页。**

建议分工：

| 内容 | 负责人 |
| --- | --- |
| 首页介绍和学期信息 | Coordinator |
| Weekly schedule | 当周主持人或 Coordinator |
| 每周 notes | 当周报告人 |
| Reading list | 全组确认、一人维护 |
| 最终 slides | 每位报告人上传自己的文件 |

---

## 7. 常见问题

### Pages 显示 404

依次检查：

1. 仓库最外层是否直接存在 `index.html`；
2. `Settings → Pages` 是否选择 `main` 和 `/(root)`；
3. 是否已经点击 `Save`；
4. 是否等待了几分钟；
5. GitHub 仓库的 `Actions` 页面里是否有失败的 Pages workflow。

### 页面有文字但没有样式

检查：

- `index.html` 和 `style.css` 是否在同一层；
- `index.html` 中是否仍然写着 `<link rel="stylesheet" href="style.css">`；
- 上传时是否漏掉 `style.css`。

### 修改后网页没有变化

1. 确认修改已经 commit 并 push 到 `main`；
2. 等待 Pages 完成新一次发布；
3. 在浏览器按 `Ctrl + F5` 强制刷新。

### 点击内部文件后 404

- 核对文件名的大小写；GitHub 区分 `Week-01.pdf` 和 `week-01.pdf`；
- 核对链接中的文件夹，例如 `materials/week-01.pdf`；
- 不要在相对路径最前面加 `/`。

### 是否可以放私人材料

不要。GitHub Pages 网页通常是公开可访问的。不要上传：

- 密码、API key、身份证件；
- 未经允许公开的学生信息；
- 不希望公开的草稿或邮箱；
- 有版权限制、不能公开分发的教材 PDF。

如果不想公开个人邮箱，可以删除成员卡片中的邮箱行，只留下项目统一联系邮箱。

---

## 8. 官方参考

- [GitHub Pages Quickstart](https://docs.github.com/pages/quickstart)
- [配置 Pages 发布来源](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site)
- [通过网页上传文件](https://docs.github.com/en/repositories/working-with-files/managing-files/adding-a-file-to-a-repository)
- [邀请仓库协作者](https://docs.github.com/articles/inviting-collaborators-to-a-personal-repository)
- [GitHub Flow：branch 与 pull request](https://docs.github.com/en/get-started/using-github/github-flow)

完成第一次发布后，下一次练习建议只做一件事：把一个成员卡片改成真实信息，commit，并观察 Pages 自动更新。
