# AI-Skills

跨项目复用的 WorkBuddy 资产库：专家包、技能、治理模板。

当前只装了治理相关的东西，后续要加别的按目录分类放。

## 目录

| 路径 | 内容 |
| --- | --- |
| `experts/governance-council/` | 三省六部治理团（Team 型专家包，7 角色） |
| `templates/` | 项目宪法与治理文档的最小模板 |

## 治理团怎么用

### 1. 装专家包

把 `experts/governance-council/` 整个目录复制到：

```
~/.workbuddy/plugins/marketplaces/my-experts/plugins/governance-council/
```

然后在 `~/.workbuddy/plugins/marketplaces/my-experts/.codebuddy-plugin/marketplace.json`
的 `plugins` 数组里加一条：

```json
{
  "name": "governance-council",
  "source": "./plugins/governance-council",
  "description": "跨项目六部治理团"
}
```

重启 WorkBuddy，专家列表里就能看到「三省六部治理团」。

### 2. 给项目写宪法（必做）

治理团**不自带任何项目规则**。它开工第一步会去找项目的
`docs/governance/CONSTITUTION.md`，找不到就停下并提示你补——
**它不会自己编一套默认值然后开干**，这是刻意设计的。

用 `templates/CONSTITUTION.template.md` 起手，填完落地到：

```
<项目根>/docs/governance/CONSTITUTION.md
```

### 3. 开始用

在装了专家包的工作区里选「三省六部治理团」，说一句：

> 给当前项目加个功能，走完整流程

## 设计取舍（为什么做成这样）

| 取舍 | 选择 | 代价 |
| --- | --- | --- |
| 通用 vs 专用 | 做成通用，项目事实运行时读宪法 | 每个新项目要写一份宪法，约 15 分钟 |
| 决策权归属 | L0 部内、L1 跨部自行消化，**只有 L2 上报人** | 部内决策质量依赖 agent 自律 |
| 起草 vs 审批 | 中书省起草、门下省封驳，不是同一方 | 流程比单 agent 直接干要慢 |
| 验收独立性 | 刑部独立于研发，持上线否决权 | 可能卡在细节上反复 |

## 其他

- 本库只放**通用资产**。项目专属的技能（如某个项目的 `mf-*` 技能）放各自项目仓库，不要塞进来。
