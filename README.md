# 🧠 苏泰达智能练题平台

基于 Vue 3 的手机优先在线刷题系统，支持模糊搜索、多模式练习、错题管理。

## ✨ 功能

- **📚 四种练习模式**：训练模式 / 练习模式 / 考试模式 / 错题复习
- **🔍 智能搜索**：模糊搜索 + 置信度评分，最多返回 2 条最佳匹配
- **📱 手机优先**：专为移动端优化的触控布局，选项紧凑、按钮大
- **📊 数据统计**：正确率、连续天数、分类正确率
- **📕 错题本**：自动收录错题，掌握度标记，标签分类
- **📤 题库上传**：支持 PDF / DOCX 直接上传解析
- **🔄 离线可用**：题目缓存在浏览器本地，无需每次都加载

## 🚀 快速开始

```bash
# 安装依赖
npm install

# 开发模式
npm run dev

# 生产构建
npm run build

# 预览构建结果
npm run preview
```

## 📦 部署

### GitHub Pages（推荐）

1. Push 代码到 GitHub
2. Settings → Pages → Source: GitHub Actions
3. 每次 push 自动部署

### 其他平台 (Netlify / Vercel)

- 构建命令: `npm run build`
- 发布目录: `dist`

## 🔄 更新题库

```bash
# 1. 提取 Word 题库为文本
npx mammoth 题库.docx --output-format=markdown > raw_题库.txt

# 2. 清洗 + 去重 + 分类
node tools/clean_题库.cjs

# 3. 转为网站格式
node tools/convert_questions.mjs

# 4. 构建
npm run build
```

详见 [SKILL.md](SKILL.md) 完整技能文档。

## 📁 项目结构

```
├── SKILL.md                    # 完整技能文档（清洗流程、设计规范）
├── tools/
│   ├── clean_题库.cjs          # 题库清洗脚本
│   └── convert_questions.mjs   # 格式转换脚本
├── 题库_整理版.md              # 人类可读题库
├── 题库_整理版.json            # 结构化题库
├── public/questions.json       # 网站题库（开发）
├── src/
│   ├── views/
│   │   ├── Home.vue            # 首页
│   │   ├── Practice.vue        # 刷题
│   │   ├── Search.vue          # 搜索
│   │   ├── ExamMode.vue        # 考试
│   │   ├── WrongBook.vue       # 错题本
│   │   ├── Statistics.vue      # 统计
│   │   └── Settings.vue        # 设置
│   ├── stores/
│   │   ├── questionStore.ts    # 题库状态
│   │   └── practiceStore.ts    # 练习状态
│   ├── utils/
│   │   ├── searchEngine.ts     # 搜索引擎
│   │   ├── docxParser.ts       # Word 解析
│   │   └── pdfParser.ts        # PDF 解析
│   └── types/index.ts          # 类型定义
└── index.html                  # 入口
```

## 🛠 技术栈

| 层 | 技术 |
|----|------|
| 框架 | Vue 3 + TypeScript |
| 构建 | Vite 5 |
| 路由 | Vue Router 4 |
| 状态 | Pinia |
| 搜索 | Fuse.js 7 |
| 存储 | localforage |
| 解析 | mammoth + pdfjs-dist |

## 📄 License

MIT
