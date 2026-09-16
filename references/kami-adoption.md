# Kami 方法整合边界

本文件记录 `lvsea-resume` 对 `tw93/kami` 的语义采用，不是 Kami 源码、模板或资源的镜像。它服务于当前 Skill 的一页 A4 简历场景；如果未来要引入 Kami 的其他文档类型，应另行建立意图、模板和验证契约。

## 来源与审阅边界

- 来源类型：公开 GitHub Skill 仓库。
- 来源：<https://github.com/tw93/kami>。
- 审阅提交：`0847a06355b4fd62438c9fac38652dbbffeec7c4`（本次浅克隆的 `main`）。
- 许可证：Kami 为 MIT；本仓库仅采用方法语义，没有复制 Kami 的代码、模板、字体、图片或脚本。
- 已读高信号材料：根 `README.md`、`skills/kami/SKILL.md`、`CHEATSHEET.md`、`references/resume-writing.md`、`references/writing.md`、`references/production.md`、`references/design.md`、`references/anti-patterns.md`、`references/schemas/resume.json`、`LICENSE`。
- 未读或明确不采用：Kami 的 landing page、slides、diagram、math、MCP 运行路径及完整模板/资产目录；它们不属于本仓库的一页简历边界。

## 来源边界

### Read from source

- 多来源简历先做 claim-level truth pass；冲突的所有权、范围、单位、日期和数字不能静默合并。
- 简历项目使用 Role / Actions / Impact 三部分组织：角色说明位置，动作说明具体做法，影响说明可观察结果。
- 所有权词应与可辩护的责任边界匹配，不把所有项目都写成 `主导`。
- 没有支持的数字、统计和结果要标记缺口或询问，不用模板空位制造内容。
- 机械检查之后需要一次脱离作者意图的招聘者复核，检查跨行重复、过程冒充结果和证据越界。

### Inferred

- 这些机制与 `lvsea-resume` 的 YAML-first 内容阶段兼容，主要补强事实边界和项目表达，不需要引入 Kami 的构建器。
- 一页简历需要把 Role / Actions / Impact 压缩进既有 `projects[].role`、`projects[].bullets` 和 `experience[].items[].body`，而不是复制 Kami 的两页卡片结构；多来源状态可记录在 Schema 新增的私有 `source_ledger` / `claim_ledger` 中。

### User-provided

- 目标仓库是 `lhylvsea/lvsea-resume`；用户要求以本仓库为整合目标，并明确点名使用 `$lvsea-zao-skill`。
- 目标运行时仍以现有 Agent Skill 入口、12 套官方模板和一页 A4 输出为准。

### Unavailable / Dry-run

- 未执行真实候选人的 provider 写作、人工招聘者盲评或用户满意度测试；这些证据属于 `missing evidence`。
- 未把 Kami 的两页模板或字体在本仓库中渲染；因此不能声称已获得 Kami 的视觉效果或两页平衡能力。

## Keep / Adapt / Reject / Invent

| 决策 | Kami 机制 | `lvsea-resume` 落点 | 取舍理由 |
|---|---|---|---|
| keep | 多来源 claim-level truth pass | `SKILL.md` 来源边界、`copy-optimize.md` source pass | 直接降低角色、单位和数字误写风险 |
| keep | Role / Actions / Impact 项目结构 | `SKILL.md` 3.5、`copy-optimize.md`、QA 清单 | 能与现有一页模板的项目行兼容 |
| keep | 最低真实所有权词 | `SKILL.md` 3.5、`copy-optimize.md` | 防止把协作贡献升级成主导成果 |
| keep | 缺失证据和无结果时停机/询问 | 来源边界、`ask` / `do-not-claim`、QA 清单 | 比生成泛化成就更可复核 |
| adapt | Kami 的 content IR / execution contract | 继续以 `raw.data.yaml` → `resume.data.yaml` 为唯一内容链，在流程中锁定受众、岗位、页数、模板和验收项 | 再增加 `content.json` 会破坏现有双层 YAML 约定 |
| adapt | 跨文档的 density / visual review | 仅吸收一页的招聘者复核、内容重复和证据检查；保留现有 PDF、字体、底部留白和截图门禁 | Kami 的多页密度规则不适用于一页硬门槛 |
| reject | Kami 两页 resume schema 与 resume template | 不进入 12 模板 allowlist | 直接引入会冲突于本仓库的一页 A4 契约 |
| reject | Kami 暖色纸张、字体、landing/slides/diagram/MCP 构建器 | 不复制模板、资产、依赖和脚本 | 与本仓库的目标、许可证边界和运行时不同 |
| reject | 非阻塞更新检查、通用文档输出路由 | 不增加联网、缓存或额外权限 | 本次只维护简历 Skill，不扩大运行权限 |
| invent | 一页模板中的 Role / Actions / Impact 映射与前向重测 | 本文件、`evals/kami-integration-cases.md`、SKILL/QA规则 | 这是面向目标仓库的兼容连接，不是上游原样机制 |

## 维护边界

- `SKILL.md` 负责运行时路由和硬门槛；长方法留在 `references/`。
- `reports/` 只记录来源、取舍和验证证据，不放候选人原始材料、私有路径、凭据或个人简历。
- 如果未来复制 Kami 的代码或资产，必须新增明确的第三方归属、许可证副本和文件级来源；不能把当前的“语义采用”描述继续当作代码镜像。
