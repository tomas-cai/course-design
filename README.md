# 课程开发三 Skill 体系

> 把课程当作产品做——从发现培训商机、到设计开发、再到质量评审，全流程覆盖。

三个独立 Skill 通过**文件命名约定**协作：

| Skill | 做什么 | 触发词 | 产出物 |
|:---|:---|:---|:---|
| **course-discovery** | 探索培训方向 | 培训需求发现、头脑风暴课程机会 | `00-培训需求spec.md` |
| **course-design** | 开发课程 | 开发课程、设计培训方案 | `01~05` 阶段文件 |
| **course-review** | 评审课程质量 | 审阅课程、质量检查 | 评审报告 |

---

## 核心理念

### 六维嵌套模型（course-design 的理论基础）

| 层次 | 维度 | 解决的问题 |
|:---|:---|:---|
| **流程层** | ADDIE | 项目管控 |
| **质量层** | 迪克-凯瑞 | 内容对齐 |
| **精度层** | 布卢姆目标分类法 | 目标精度 |
| **体验层** | LXD + 产品思维 | 学习动机与完课率 |
| **敏捷层** | SAM/AGILE | 内容时效性 |
| **评估层** | 柯氏四级 | 效果闭环 |

### 课程即产品的核心概念

- **痛点**：学习者的真实困难、焦虑、挫败
- **惊叫点**：让学习者发出"原来如此！"的顿悟时刻
- **爽点**：让学习过程顺畅、有掌控感的细节体验

---

## 三 Skill 协作流程

```
用户说"我想看看有什么培训机会"
        │
        ▼
  course-discovery Skill
  ├── 信号采集（市场/用户/组织）
  ├── 信号聚类 → 痛点提取
  ├── 商机评估（五维评分）
  └── 课程假设形成
        │
        │  产出 00-培训需求spec.md
        ▼
用户说"帮我开发这门课"
        │
        ▼
  course-design Skill
  ├── Phase 01 分析（需求拆解→画像→能力诊断）
  ├── Phase 02 设计（目标→情绪曲线→对齐）
  ├── Phase 03 开发（大纲→手册→案例→测评→课件）
  ├── Phase 04 实施（前置测评→随堂验证）
  └── Phase 05 评估（柯氏→痛点复盘→迭代计划）
        │
        │  产出 01~05 文件
        ▼
用户说"审一下这个课程的质量"
        │
        ▼
  course-review Skill
  ├── 结构完整性检查
  ├── 内部一致性检查（跨阶段信息追踪）
  ├── 内容深度评估（L1-L4 分级）
  ├── 可教性检查（模拟明天上课）
  └── 风险评估（识别 3 个最大风险点）
        │
        └── 产出评审报告
```

### 协作机制

三个 Skill 不需要互相导入或引用内部逻辑。协作完全依赖**文件命名约定**：

| 文件 | 由谁产出 | 被谁消费 |
|:---|:---|:---|
| `00-培训需求spec.md` | course-discovery | course-design（Phase 01 前置输入） |
| `01-需求定位报告.md` → `05-评估报告.md` | course-design | course-review（扫描评审） |
| 评审报告 | course-review | 交付物持有者 |

任意 Skill 产生的输出文件均可被其他 Skill 消费。

---

## 产出物流（Artifact Chain）

以 course-design 为核心，每个阶段产出唯一的标准化文件：

```
<course-project-root>/
│
├── 00-培训需求spec.md            ← 来自 course-discovery → Phase 01 读取
│
├── 01-需求定位报告.md            ← Phase 01 产出 → Phase 02 读取
├── 02-课程设计方案.md            ← Phase 02 产出 → Phase 03 读取
├── 03-教学材料包/                ← Phase 03 产出 → Phase 04 读取
│   ├── 00-课程大纲.md
│   ├── 01-学员手册.md
│   ├── 02-讲师手册.md
│   ├── 03-实操案例.md
│   ├── 04-测评方案.md
│   └── 05-课程课件
├── 04-实施记录与反馈.md          ← Phase 04 产出 → Phase 05 读取
└── 05-评估报告与迭代计划.md      ← Phase 05 产出（完结）
```

每个产出物是自包含的 Markdown 文件，含元数据头和内容正文。下一阶段读取它就能知道上一阶段做了什么决策。

---

## 目录结构

```
skills/
│
├── course-discovery/              培训需求发现
│   ├── SKILL.md                   工作流（信号采集→聚类→商机→假设）
│   ├── agents/openai.yaml
│   └── references/
│       └── discovery-methodology.md  详细方法论
│
├── course-design/                  课程开发
│   ├── SKILL.md                   工作流（入口逻辑 + 五阶段指令）
│   ├── agents/openai.yaml
│   └── references/
│       ├── overview.md            六维模型完整理论
│       ├── phase-01-analysis.md   分析方法论
│       ├── phase-02-design.md     设计方法论 + 子模块叙事弧
│       ├── phase-03-development.md 开发方法论 + 跨模块技能
│       ├── phase-04-implementation.md 实施方法论
│       ├── phase-05-evaluation.md 评估方法论
│       ├── common-tools.md        布卢姆动词手册 + 敏捷验证 + 质量清单
│       └── pm-ai-adaption.md      PM+AI 课程适配规则
│
└── course-review/                  项目评审
    ├── SKILL.md                   工作流（五维评审模型）
    ├── agents/openai.yaml
    └── references/
        └── review-methodology.md   评审详细检查项
```

---

## 使用方式

在 Codex 中触发对应 Skill：

| 你说 | Codex 加载 |
|:---|:---|
| "帮我探索一下培训方向" | → course-discovery |
| "开发一门课程，主题是 XXX，面向 XXX" | → course-design |
| "审阅这个课程项目的质量" | → course-review |
| "我已有需求分析报告，从设计阶段开始" | → course-design（中间切入） |

---

## 适用场景

- **通用课程开发**：技能课、认知课、思维课均可
- **PM + AI 方向**：有专门适配规则（判断类能力、案例驱动测评、内容时效性分层）
- **标准化技能培训**：无需过度使用体验设计层，但方法论框架同样适用

---

## 课程项目库

本仓库不包含实际课程产出物。通过本 Skill 开发的课程应存放在其他目录：

```
/path/to/courses/
├── pm-ai-prototyping/            ← 示例：PM+AI 原型设计
│   ├── 01-需求定位报告.md
│   └── ...
└── graduate-ai-pm/               ← 示例：AI 产品落地实战
    ├── 00-培训需求spec.md
    ├── 01-需求定位报告.md
    └── ...
```

---

## 快速开始

```bash
# 克隆本仓库
git clone https://github.com/tomas-cai/course-design.git

# 注册到 Codex（软链接）
ln -s $(pwd)/course-discovery ~/.codex/skills/course-discovery
ln -s $(pwd)/course-design ~/.codex/skills/course-design
ln -s $(pwd)/course-review ~/.codex/skills/course-review

# 在 Codex 中使用
# "用 course-design 帮我开发一门课，主题是 AI 产品设计"
```

---

## 许可

MIT
