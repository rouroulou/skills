# skills

rouroulou 的个人 [Claude Code](https://claude.com/claude-code) skills 集合，以 plugin marketplace 形式发布。

## 安装

在 Claude Code 中执行：

```
/plugin marketplace add rouroulou/skills
/plugin install feature-test@rouroulou-skills
```

或在桌面端 **Customize → Plugins → Add marketplace** 中填入本仓库地址 `https://github.com/rouroulou/skills.git` 并 Sync。

也可以不走插件体系，直接把某个 skill 拷贝为个人 skill：

```bash
git clone https://github.com/rouroulou/skills.git
cp -r skills/skills/feature-test ~/.claude/skills/
```

## Skills 列表

### feature-test — 功能测试 + 体验审计一体化流程

对指定功能模块执行一次完整的测试闭环，适用于功能开发完成后的系统性验收：

1. **文档驱动生成用例** — 自动定位项目中的功能文档（PRD/方案），通读后生成两类测试用例：
   - A 类·功能连通性：核心流程 happy path 全链路（页面可达、数据加载、表单提交、状态流转）
   - B 类·极端场景：空态、极值、非法输入、慢响应/报错、权限越权、多语言切换、重复提交、窄屏响应式等 8 个维度
2. **真实环境执行** — 在本地 dev 服务器上用浏览器工具逐条跑用例（禁止只读代码下结论），每条用例记录通过/失败及证据
3. **双审计** — 依次调用 `/frontend-design-audit`（代码层可用性审计）与 `/ux-audit`（真实用户走查）
4. **结构化报告** — 落盘到 `docs/test-reports/`，问题按 **P0 阻塞 / P1 严重 / P2 一般 / P3 优化** 划分，每个问题强制四段式：
   现象（含复现步骤与证据）→ 原因分析（定位到 `file:line` 根因）→ 行业通用做法（具体到 Stripe/Vercel/Linear 等同类产品的处理方式）→ 结合项目技术栈的最小改动修复方案

**触发方式**：`/feature-test <模块名>`，或直接说"测试一下 XX 功能"、"验收 XX"、"跑一遍 QA"。

**环境要求**：项目可在本地启动 dev 服务器；环境中装有 `frontend-design-audit` 与 `ux-audit` 两个审计 skill（缺失时会在报告中注明跳过）。

## 仓库结构

```
.
├── .claude-plugin/
│   └── marketplace.json   # 插件市场清单
├── skills/
│   └── feature-test/
│       └── SKILL.md       # skill 定义
└── README.md
```

## License

MIT
