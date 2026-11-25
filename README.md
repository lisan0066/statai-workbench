# statai-workbench
# StatAI 轻量统计与数据洞察工作台（v2.0 · AI 智能诊断版）

[![Live Demo](https://img.shields.io/badge/Live%20Demo-GitHub%20Pages-2563EB?style=flat-square)](https://lisan0066.github.io/statai-workbench/)
[![Architecture](https://img.shields.io/badge/Architecture-Pure%20Frontend%20Single--File-10B981?style=flat-square)](#技术架构)
[![Course](https://img.shields.io/badge/Course-%E4%BA%BA%E5%B7%A5%E6%99%BA%E8%83%BD%E5%9F%BA%E7%A1%80%E4%B8%8E%E5%BA%94%E7%94%A8-1E3A8A?style=flat-square)](#项目简介)

> **在线体验地址（GitHub Pages）**：https://lisan0066.github.io/statai-workbench/  
> **源代码仓库地址**：https://github.com/lisan0066/statai-workbench

---

## 一、项目简介

**StatAI** 是一款面向“AI + 数据分析”交叉场景的纯前端轻量统计与智能洞察工作台，为浙江工商大学《人工智能基础与应用》课程大作业作品。

针对传统统计工具安装门槛高、结果缺乏业务解读以及云端上传存在隐私风险等痛点，本项目采用**单文件纯前端架构**，全部统计运算与智能推理均在浏览器本地完成，支持打开即用与零配置静态托管，完整覆盖 **CSV 数据导入 → 健康度体检 → 偏度自适应智能清洗 → 双视角深度洞察与问答 → 双图表联动可视化 → 学术三线表与报告导出** 的数据分析闭环。

---

## 二、核心功能亮点

1. **多编码 CSV 导入与内置示例样本**
   - 支持本地 `.csv` 文件拖拽/选择上传，自动兼容 UTF-8 与 GBK（Excel 默认导出）编码及 RFC-4180 转义格式。
   - 页面加载自动预置 50 行 × 9 列电商用户消费示例数据（含 2 处不同分布偏态的缺失值与 3 个典型异常样本），方便快速演示。
2. **AI 智能诊断中心与健康度仪表盘**
   - 从**完整性（30%）、稳健性（25%）、分布均衡度（20%）、信息关联度（25%）**四个维度动态评估数据综合健康分（0–100 分）。
   - **缺失值偏度自适应清洗**：依据 Fisher-Pearson 无偏样本偏度 $G_1$ 自动决策（$\vert{}G_1\vert{} \ge 0.5$ 推荐中位数填补，$\vert{}G_1\vert{} < 0.5$ 推荐均值填补），支持「一键智能清洗」、动态展示清洗前后分值对比并支持随时撤回。
   - **Tukey 1.5×IQR 离群扫描**：精准定位异常行号与取值，并区分“数据录入错误”与“高价值超级 VIP 用户”给出分层建议。
3. **双视角自动报告 + 双引擎交互问答**
   - 一键切换**商业决策洞察**（Executive Summary、核心增长杠杆、Top 20% 帕累托集中度测算、P0/P1/P2 行动建议）与**学术统计解读**（样本评估、插补论证、正态性评估、多重共线性 VIF 预警、后续建模路径）。
   - 问答框默认搭载**内置离线统计推理引擎**（零配置可用），同时支持在弹窗中选配 OpenAI / DeepSeek 兼容 API（仅发送统计摘要 JSON 保护原始明细，接口异常自动降级）。
4. **双图表联动可视化与规范学术三线表**
   - **单变量直方图**：自动分组并叠加自定义 Canvas 红色均值参考虚线与偏态标签。
   - **双变量 OLS 散点回归图**：默认锁定全表相关性最强变量对，实时叠加最小二乘拟合线并展示 Pearson $r$、$R^2$ 与回归方程，琥珀色高亮 IQR 异常样本。
   - **学术规范三线表 & 明细筛选**：输出含偏度、变异系数（CV）及异常计数的三线表，支持按缺失/异常筛选明细并一键导出 `.md` 诊断报告。

---

## 三、技术架构与文件结构

- **核心技术栈**：HTML5 + 原生 JavaScript (ES6+) + Tailwind CSS (CDN) + Chart.js 4.4.4 (CDN)
- **部署特性**：零构建步骤、零后端依赖、全本地隐私运算，直接托管于 GitHub Pages。

```text
statai-workbench/
├── index.html      # StatAI v2.0 完整单文件源代码（结构、样式与统计/AI 推理引擎）
└── README.md       # 项目制作说明、使用指南与版本迭代日志
