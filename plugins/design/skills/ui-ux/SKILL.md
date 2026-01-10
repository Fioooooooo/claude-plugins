---
name: ui-ux
description: "UI/UX设计智能库。含50种风格、21套配色方案、50组字体组合、20种图表类型、8大技术栈（React、Next.js、Vue、Svelte、SwiftUI、React Native、Flutter、Tailwind）。支持操作：规划、构建、创建、设计、实施、评审、修复、改进、优化、增强、重构、检查UI/UX代码。适用项目：网站、落地页、仪表盘、管理后台、电商、SaaS、作品集、博客、移动应用、.html、.tsx、.vue、.svelte文件。设计元素：按钮、弹窗、导航栏、侧边栏、卡片、表格、表单、图表。风格：玻璃拟态、粘土拟态、极简主义、粗野主义、新拟态、便当网格、暗黑模式、响应式、拟物化、扁平设计。主题：配色方案、无障碍设计、动效、版式、字体排版、字体配对、间距、悬停效果、阴影、渐变。"
---

# UI/UX Pro Max - 设计智能库

可检索的UI风格数据库，包含配色方案、字体组合、图表类型、产品推荐、UX指南及技术栈最佳实践。

## 环境准备

检查Python是否安装：

```bash
python3 --version || python --version
```

若未安装，根据操作系统执行：

**macOS:**
```bash
brew install python3
```

**Ubuntu/Debian:**
```bash
sudo apt update && sudo apt install python3
```

**Windows:**
```powershell
winget install Python.Python.3.12
```

---

## 使用指南

当用户提出UI/UX需求（设计/构建/创建/实施/评审/修复/改进）时，按此流程操作：

### 步骤1：需求分析
提取关键信息：
- **产品类型**：SaaS/电商/作品集/仪表盘/落地页等
- **风格关键词**：极简/趣味/专业/优雅/暗黑模式等
- **行业领域**：医疗/金融科技/游戏/教育等
- **技术栈**：React/Vue/Next.js，默认`html-tailwind`

### 步骤2：跨维度搜索
使用`search.py`多维度检索：

```bash
python3 scripts/search.py "<关键词>" --domain <维度> [-n <结果数>]
```

**推荐搜索顺序：**
1. **产品** - 获取类型风格推荐
2. **风格** - 获取详细风格指南
3. **字体** - 获取谷歌字体组合
4. **配色** - 获取主色/辅色/背景色方案
5. **落地页** - 获取页面结构（如适用）
6. **图表** - 获取图表推荐（如适用）
7. **UX** - 获取最佳实践与反面案例
8. **技术栈** - 获取实现规范（默认html-tailwind）

### 步骤3：技术栈规范（默认html-tailwind）
未指定技术栈时默认使用：

```bash
python3 scripts/search.py "<关键词>" --stack html-tailwind
```

可选技术栈：`html-tailwind`、`react`、`nextjs`、`vue`、`svelte`、`swiftui`、`react-native`、`flutter`

---

## 搜索参考

### 可用维度
| 维度 | 用途 | 示例关键词 |
|------|------|------------|
| `product` | 产品类型推荐 | SaaS/电商/作品集/医疗/美妆/服务 |
| `style` | UI风格效果 | 玻璃拟态/极简/暗黑模式/粗野主义 |
| `typography` | 字体组合 | 优雅/趣味/专业/现代 |
| `color` | 行业配色方案 | SaaS/电商/医疗/美妆/金融科技/服务 |
| `landing` | 页面结构策略 | 首屏/客户证言/定价/社交证明 |
| `chart` | 图表类型推荐 | 趋势/对比/时间轴/漏斗/饼图 |
| `ux` | UX最佳实践 | 动效/无障碍/z-index/加载 |
| `prompt` | AI提示词 | （风格名称） |

### 可用技术栈
| 技术栈 | 侧重点 |
|--------|--------|
| `html-tailwind` | Tailwind工具类/响应式/无障碍（默认） |
| `react` | 状态管理/性能优化 |
| `nextjs` | 服务端渲染/路由优化 |
| `vue` | 组合式API/Pinia状态管理 |
| `svelte` | Runes/状态存储/SvelteKit |
| `swiftui` | 视图/状态/导航/动画 |
| `react-native` | 组件/导航/列表 |
| `flutter` | 组件/状态/布局/主题 |

---

## 工作流示例

**用户需求：** "为专业护肤服务创建落地页"

**AI操作：**

```bash
# 1. 搜索产品类型
python3 scripts/search.py "beauty spa wellness service" --domain product

# 2. 搜索风格（美妆行业/优雅风格）
python3 scripts/search.py "elegant minimal soft" --domain style

# 3. 搜索字体组合
python3 scripts/search.py "elegant luxury" --domain typography

# 4. 搜索配色方案
python3 scripts/search.py "beauty spa wellness" --domain color

# 5. 搜索页面结构
python3 scripts/search.py "hero-centric social-proof" --domain landing

# 6. 搜索UX规范
python3 scripts/search.py "animation" --domain ux
python3 scripts/search.py "accessibility" --domain ux

# 7. 搜索技术栈规范（默认html-tailwind）
python3 scripts/search.py "layout responsive" --stack html-tailwind
```

**最后：** 综合所有搜索结果实现设计方案。

---

## 优化技巧

1. **关键词具体化** - 用"医疗SaaS仪表盘"而非"应用"
2. **多次搜索** - 不同关键词揭示不同维度
3. **组合维度** - 风格+字体+配色=完整设计系统
4. **必查UX** - 搜索"动效"、"z-index"等常见问题
5. **技术栈标志** - 获取实现规范
6. **迭代优化** - 首次不匹配时尝试变体关键词

---

## 专业UI通用准则

### 图标与视觉元素
| 准则 | 推荐做法 | 避免做法 |
|------|----------|----------|
| **禁用表情图标** | 使用SVG图标（Heroicons/Lucide） | 用🎨🚀⚙️等表情替代 |
| **稳定悬停态** | 使用颜色/透明度过渡 | 使用导致布局偏移的缩放 |
| **正确品牌标识** | 从Simple Icons获取官方SVG | 使用猜测或不规范路径 |
| **统一图标尺寸** | 固定viewBox(24x24)配合w-6 h-6 | 混用随机尺寸 |

### 交互与光标
| 准则 | 推荐做法 | 避免做法 |
|------|----------|----------|
| **指针光标** | 为可点击元素添加cursor-pointer | 交互元素保持默认光标 |
| **悬停反馈** | 提供颜色/阴影/边框变化 | 无交互状态提示 |
| **平滑过渡** | 使用transition-colors duration-200 | 瞬时切换或过渡缓慢(>500ms) |

### 深浅模式对比
| 准则 | 推荐做法 | 避免做法 |
|------|----------|----------|
| **浅色玻璃卡片** | 使用bg-white/80及以上透明度 | 使用bg-white/10（过透） |
| **浅色文本对比** | 正文使用slate-900(#0F172A) | 使用slate-400(#94A3B8) |
| **浅色辅助文本** | 最小使用slate-600(#475569) | 使用gray-400及以上浅色 |
| **边框可见性** | 浅色模式使用border-gray-200 | 使用border-white/10（不可见） |

### 布局与间距
| 准则 | 推荐做法 | 避免做法 |
|------|----------|----------|
| **悬浮导航栏** | 添加top-4 left-4 right-4边距 | 紧贴top-0 left-0 right-0 |
| **内容内边距** | 预留固定导航栏高度 | 内容被固定元素遮挡 |
| **统一最大宽度** | 采用相同max-w-6xl/max-w-7xl | 混用不同容器宽度 |

---

## 交付前检查清单

### 视觉质量
- [ ] 禁用表情图标（使用SVG替代）
- [ ] 所有图标来源统一（Heroicons/Lucide）
- [ ] 品牌标识验证通过（Simple Icons）
- [ ] 悬停态不引发布局偏移
- [ ] 直接使用主题色（bg-primary）而非var()包裹

### 交互体验
- [ ] 所有可点击元素含cursor-pointer
- [ ] 悬停态提供明确视觉反馈
- [ ] 过渡效果流畅（150-300ms）
- [ ] 键盘导航焦点状态可见

### 深浅模式
- [ ] 浅色模式文本对比度达标（≥4.5:1）
- [ ] 玻璃元素在浅色模式可见
- [ ] 边框双模式可见
- [ ] 交付前双模式测试

### 布局规范
- [ ] 悬浮元素距边缘间距合理
- [ ] 无内容被固定导航遮挡
- [ ] 适配320px/768px/1024px/1440px
- [ ] 移动端无水平滚动

### 无障碍设计
- [ ] 所有图片含alt文本
- [ ] 表单输入含关联标签
- [ ] 不以颜色作为唯一状态标识
- [ ] 遵守prefers-reduced-motion设置