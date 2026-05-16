# Login Demo

一个基于 **Vue 3 + Vite + Tailwind CSS** 构建的企业级登录页面演示项目。


> 一个简洁、响应式的登录页面，包含表单校验和优雅的 UI 设计。

## 技术栈

| 技术 | 说明 |
|------|------|
| [Vue 3](https://vuejs.org/) | 渐进式 JavaScript 框架（`<script setup>` 组合式 API） |
| [Vite](https://vitejs.dev/) | 下一代前端构建工具 |
| [Tailwind CSS](https://tailwindcss.com/) | 实用优先的 CSS 框架 |
| [PostCSS](https://postcss.org/) | CSS 处理工具 |

## 功能特性

- 响应式布局：完美适配 PC 端与移动端
- 表单校验：基于原生 JS 的账号/密码实时校验
  - 账号：非空校验 + 长度不少于 5 位
  - 密码：非空校验 + 长度 6-18 位
- 优雅的 UI 设计：符合 SaaS 企业级设计规范
- 交互动效：输入框焦点、按钮悬停/点击反馈、错误提示动画

## 快速开始

### 前置要求

- Node.js >= 18
- npm >= 8（或使用 pnpm / yarn）

### 安装依赖

```bash
npm install
```

### 启动开发服务器

```bash
npm run dev
```

浏览器访问终端提示的本地地址（默认 `http://localhost:5173`）。

### 构建生产版本

```bash
npm run build
```

构建产物默认输出到 `dist/` 目录。

### 预览生产构建

```bash
npm run preview
```

## 项目结构

```
login-demo/
├── public/                  # 静态资源
│   ├── favicon.svg
│   └── icons.svg
├── src/
│   ├── assets/              # 项目资源（图片、SVG 等）
│   ├── components/          # 组件目录
│   ├── App.vue              # 根组件（登录页面主体）
│   ├── main.js              # 应用入口
│   └── style.css            # 全局样式（Tailwind 指令）
├── index.html               # HTML 入口
├── package.json
├── vite.config.js           # Vite 配置
├── tailwind.config.js       # Tailwind CSS 配置
├── postcss.config.js        # PostCSS 配置
└── README.md
```

## 自定义指南

### 修改页面内容

编辑 [App.vue](./src/App.vue)：
- **个人信息**：修改第 72 行的姓名和学号
- **表单文案**：修改账号/密码的 placeholder 文本
- **校验规则**：调整 `validateAccount()` 和 `validatePassword()` 函数

### 修改主题样式

编辑 [tailwind.config.js](./tailwind.config.js)：
```js
theme: {
  extend: {
    colors: {
      primary: '#3b82f6',    // 自定义主色调
    },
  },
},
```

## 相关文档

- [Vue 3 文档](https://vuejs.org/guide/introduction.html)
- [Vite 文档](https://vitejs.dev/guide/)
- [Tailwind CSS 文档](https://tailwindcss.com/docs/installation)

## License

[MIT](./LICENSE)
