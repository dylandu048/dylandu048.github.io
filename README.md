# Dive into AI

一个深色主题的技术文献分析展示网站，专注于 AI 芯片与大模型优化领域。纯前端实现，可一键部署到 GitHub Pages。

## 功能特性

- **深色科技风格**：以 `#0A0E17` 为基底，搭配紫蓝渐变强调色和领域专属霓虹色标
- **Hero 统计面板**：文献总量、近7天新增、技术领域数，顶部渐变装饰线
- **领域筛选**：全部 + 5 个技术领域（AI芯片、互联技术、大模型优化、模型压缩、推理引擎）
- **实时搜索**：按标题、摘要、领域关键词实时过滤
- **星级评分**：每篇文献配有 5 星级 AI 置信度评分（支持半星）
- **Glow 悬停效果**：卡片悬停时顶部浮现领域色霓虹光条，边框发出柔和辉光
- **卡片跳转**：点击卡片即在新标签页打开对应的文献/项目链接
- **背景网格**：页面背景带有极淡的紫蓝色网格线，营造数据中心氛围
- **响应式布局**：PC 3 列、平板 2 列、手机 1 列的自适应网格

## 快速部署

### 1. 创建 GitHub 仓库

1. 登录 GitHub → **New repository**
2. 仓库名：`你的用户名.github.io`
3. 选择 **Public**
4. 点击 **Create repository**

### 2. 上传文件

```bash
git clone https://github.com/你的用户名/你的用户名.github.io.git
cd 你的用户名.github.io
cp /path/to/index.html .
cp /path/to/README.md .
git add .
git commit -m "Add Dive into AI literature hub"
git push origin main
```

### 3. 启用 Pages

仓库 → **Settings** → **Pages** → Source 选 **main** 分支，**/(root)** → Save。

约 1-2 分钟后访问 `https://你的用户名.github.io`。

## 添加/修改文献

所有数据在 `index.html` 底部的 `articles` 数组中：

```javascript
{
  id: 13,                          // 唯一递增 ID
  title: "论文标题",                // 文章标题
  summary: "概述/摘要...",           // 文章概述（2-3行最佳）
  field: "AI芯片",                  // 显示用领域名称
  fieldSlug: "chip",                // 领域标识：chip / interconnect / llm / compress / inference
  venue: "Hot Chips 2024",          // 会议/期刊/来源
  year: 2024,                       // 发表年份
  score: 0.94,                      // AI 置信度（0.0 ~ 1.0）
  link: "https://example.com/..."   // 点击卡片后跳转的 URL
}
```

### 添加新领域

1. 在 `fieldConfig` 中添加配置：

```javascript
quantum: { label: "量子计算", color: "#06B6D4" }
```

2. 在 CSS 中添加领域样式：

```css
.field-quantum { --field: #06B6D4; --field-glow: rgba(6,182,212,0.25); --field-bg: rgba(6,182,212,0.1); }
```

3. 在 `getFieldClass` 函数中添加映射：

```javascript
quantum: "field-quantum"
```

4. 在 `renderFilters` 的 `fields` 数组中追加新领域

## 技术说明

| 项目 | 说明 |
|------|------|
| 样式方案 | 纯内联 CSS，无外部样式库 |
| 字体 | Inter（Google Fonts）+ 系统无衬线回退 |
| 布局 | CSS Grid + Flexbox |
| 交互 | 原生 JavaScript，无框架依赖 |
| 外部资源 | 仅 Google Fonts（Inter） |
| 兼容性 | 现代浏览器（Chrome, Firefox, Safari, Edge） |

## 自定义主题

| CSS 变量 | 默认值 | 说明 |
|----------|--------|------|
| `--bg-base` | `#0A0E17` | 页面背景 |
| `--bg-card` | `#161B22` | 卡片背景 |
| `--accent` | `#6366F1` | 主色调（靛蓝紫） |
| `--text-primary` | `#E5E7EB` | 主文字 |
| `--border-standard` | `rgba(255,255,255,0.08)` | 标准边框 |

修改这些变量即可快速调整整体风格。

## License

MIT
