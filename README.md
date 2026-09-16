# 建模与算法策略师

一个面向数学建模竞赛和实际建模问题的 Agent Skill。它先明确问题契约和硬约束，再比较少量结构不同的候选模型，选择与数学结构和计算规模相匹配的算法，并为结论设计可证伪的验证。

## 设计目标

- 从数据生成机制、约束和输出对象识别问题，而不是按题型关键词套模板。
- 硬门槛先于综合评分，违反题意或不可计算的方案直接淘汰。
- 先建立最低合理基线，再用最小区分实验决定是否升级模型。
- 准确区分全局最优、近似保证、局部最优和经验候选。
- 让验证方式与模型类型及结论主张匹配。
- 数值模型区分输入事实与闭合假设、守恒与经验参数、显示位数与实际精度。
- 结构对照冻结共同条件，避免把输入变化或离散误差误当作新机制影响。
- 证据已经足够决策时停止扩展，避免无效堆叠模型和指标。

## 适用场景

- 分析数学建模赛题并形式化目标、变量和约束；
- 比较预测、优化、仿真、评价或因果模型；
- 为既定模型选择求解算法并核对复杂度与正确性保证；
- 诊断现有建模方案在模型层、算法层、实现层或数据层的问题。

不适用于单纯论文排版、语言润色、制图，或模型和算法已经完全确定后的纯代码实现。

## 安装

将仓库复制到 Agent 的 skills 目录。例如 Codex：

```text
~/.codex/skills/modeling-algorithm-strategist/
```

安装后应保留如下结构：

```text
modeling-algorithm-strategist/
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    ├── model-and-algorithm-selection.md
    ├── verification-protocol.md
    ├── numerical-modeling.md
    ├── comparison-and-delivery.md
    ├── numerical-challenge-cases.md
    └── source-review-and-tests.md
```

## 使用

在支持 Skill 的 Agent 中调用：

```text
$modeling-algorithm-strategist
```

也可以直接提出自然语言请求，例如：

```text
请分析这道赛题，比较候选模型并推荐最合适的求解算法和验证方案。
```

## 内容说明

- `SKILL.md`：核心工作流程与输出规则。
- `references/model-and-algorithm-selection.md`：按数学结构选择模型与算法的参考。
- `references/verification-protocol.md`：针对不同模型和主张的验证协议。
- `references/numerical-modeling.md`：ODE/PDE、变量系数、移动边界、事件与精度的专项核查，按需加载。
- `references/comparison-and-delivery.md`：结构灵敏度、主模型选择、运行状态、缓存与独立复现。
- `references/numerical-challenge-cases.md`：维护用场景及行为判据，不冒充已完成的盲测。
- `references/source-review-and-tests.md`：公开项目调研、设计取舍与挑战测试。
- `agents/openai.yaml`：技能在兼容 Agent 中的显示信息和默认提示词。

## 许可证

本项目使用 [MIT License](LICENSE)。

