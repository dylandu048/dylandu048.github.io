# 文献解读站

一个基于 GitHub Pages 的静态个人主页，用于分类展示和分享学术论文的解读内容。

## 功能特性

- 按研究领域分类展示文献（自然语言处理、计算机视觉、生成模型、生物信息学、图神经网络等）
- 支持按领域筛选和关键词搜索
- 深色/浅色主题切换，自动跟随系统偏好
- 响应式设计，适配桌面端和移动端
- 纯静态 HTML/CSS/JS，无需后端服务

## 快速部署到 GitHub Pages

### 1. 创建 GitHub 仓库

1. 登录 GitHub，点击右上角 **+** → **New repository**
2. 仓库名称填写：`你的用户名.github.io`（例如 `zhangsan.github.io`）
3. 选择 **Public** 公开仓库
4. 点击 **Create repository**

### 2. 上传文件

将本项目的所有文件上传到仓库：

```bash
git clone https://github.com/你的用户名/你的用户名.github.io.git
cd 你的用户名.github.io
# 将所有文件复制到此目录
git add .
git commit -m "Initial commit: literature reading notes site"
git push origin main
```

或者直接在 GitHub 网页上上传文件。

### 3. 启用 GitHub Pages

1. 进入仓库页面，点击 **Settings**
2. 左侧菜单选择 **Pages**
3. 在 **Source** 部分选择 **Deploy from a branch**
4. 分支选择 **main**，文件夹选择 **/(root)**
5. 点击 **Save**

等待约 1-2 分钟后，访问 `https://你的用户名.github.io` 即可看到你的个人主页。

## 如何添加新的文献解读

### 方法一：复制模板（推荐）

1. 复制 `posts/post-template.html` 文件，重命名为新的文章文件名（如 `posts/your-paper.html`）
2. 修改文件中的以下内容：
   - `title` 标签中的标题
   - `article-category` 中的分类名称
   - `article-date` 中的日期
   - `h1` 中的文章标题
   - `article-authors` 中的作者和会议信息
   - `article-content` 中的解读内容
   - `article-tag` 中的标签
3. 打开 `index.html`，在 `papers` 数组中添加新文献的元数据：

```javascript
{
  id: 10,  // 确保 id 唯一
  title: "你的论文标题",
  authors: "作者名",
  venue: "会议/期刊 年份",
  category: "分类名称",  // 已有的分类会自动归类，新分类会自动创建
  date: "2024-06-15",
  tags: ["标签1", "标签2"],
  abstract: "论文摘要或简介...",
  link: "posts/your-paper.html"
}
```

### 方法二：使用已有的文章页面作为参考

参考 `posts/attention-is-all-you-need.html`、`posts/resnet.html` 或 `posts/alphafold.html` 的结构来编写新文章。

## 项目结构

```
.
├── index.html              # 主页：文献列表、搜索、分类筛选
├── posts/
│   ├── post-template.html  # 文章页面模板
│   ├── attention-is-all-you-need.html  # 示例文章
│   ├── resnet.html         # 示例文章
│   ├── alphafold.html      # 示例文章
│   └── ...                 # 更多文章
└── README.md               # 本文件
```

## 自定义建议

### 修改站点名称

编辑 `index.html` 中的 `.logo` 文字和 `<title>` 标签。

### 修改个人介绍

编辑 `index.html` 中 `.hero` 部分的 `<p>` 标签内容。

### 添加新的分类

直接在 `index.html` 的 `papers` 数组中添加新分类的文献即可，分类筛选按钮会自动生成。

### 更换主题色

编辑 CSS 中的 `--accent` 变量值（默认是蓝色 `#2563eb`）。

## 技术说明

- 本项目不使用任何外部 CSS/JS 框架，所有样式内联在 HTML 中
- 主题切换状态通过 `localStorage` 保存在本地
- 响应式布局使用原生 CSS Grid 和 Flexbox
- 完全兼容 GitHub Pages 的静态托管限制

## License

MIT
