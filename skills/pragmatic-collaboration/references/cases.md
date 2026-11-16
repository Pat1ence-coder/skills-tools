# Communication cases / 表达案例

按当前表达问题查阅对应案例。将案例背后的原则用于当前场景，改写时保留用户提供的事实和表达目的。

Use the case that matches the wording decision. Apply the underlying principle to the current context; preserve the user's facts and purpose when rewriting.

## Concrete wording

### 中文：具体表达

描述动作时，写清检查对象：

- 原句：“完成持久化一致性核验。”
- 改写：“检查保存后的文件能否重新打开。”

阻碍会影响必需的检查时，写清缺少的依赖及其影响：

- 原句：“环境门禁待闭环。”
- 改写：“这项测试需要本地数据库。目前缺少连接配置，因此还不能确认数据能否保存。”

改写后，用户能直接理解动作或阻碍。需要用户提供配置时，再单独提出请求。

### English

When describing an action, name what will be checked:

- Before: "Complete persistence consistency verification."
- After: "Check whether the saved file can be reopened."

When reporting a blocker that affects a required check, name the dependency and its consequence:

- Before: "Environment gate pending closure."
- After: "This test needs a local database. Connection settings are missing, so saving data remains unverified."

The revised wording lets the user understand the action or blocker without translating jargon. If the user must supply the configuration, state that request separately.

## Direct concept names

### 中文：直接命名概念

背景：用陈述句说明现有材料支持的概念和工作领域。

**短语示例**

- 原句：“为什么选择这种设计”
- 改写：“设计选择的理由”

**原句**

> 现有材料对任务怎么出、设计选择怎么评、结果怎么验证都提供了具体依据.

**改写**

> 现有材料为任务生成、设计评估和结果验证提供了具体依据。

**理由**

原句用“怎么……”的问句形式罗列工作领域。改写直接写出概念，保留了材料提供具体依据的原意。使用“设计选择的理由”这样的名称后，仍须按任务要求交代具体理由。实际提问或明确提出研究问题时，可使用问句。

### English

Context: a declarative summary names concepts and areas of work supported by existing material.

**Phrase example**

- Before: "why this design was chosen"
- After: "the rationale for this design"

**Before**

> The existing material provides a concrete basis for how tasks are generated, how design choices are evaluated, and how results are verified.

**After**

> The existing material provides a concrete basis for task generation, design evaluation, and result verification.

**Why**

The original wording lists areas of work as embedded questions. The revision names them directly and preserves the claim that the material provides a concrete basis. A label such as "design rationale" still needs its supporting reasons when the task calls for them. Keep question forms when asking a real question or defining a research question.

## Unnecessary qualifications

### 中文：多余的否定补充

背景：导出错误已经修复，用户需要知道处理结果。

- 原句：“已修复导出错误，但不代表整个系统没有问题。”
- 改写：“已修复导出错误。”

删去的补充引入了用户没有要求的整体保证。影响实际使用的限制仍须直接说明，例如：“导出功能目前支持 CSV，Excel 格式尚未实现。”

### English

Context: an export error has been fixed, and the user needs the result.

- Before: "The export error is fixed, but that does not mean the entire system is free of problems."
- After: "The export error is fixed."

The removed qualification introduces a broad assurance the user did not request. A limitation that affects actual use still belongs in the report, stated directly: "Export currently supports CSV. Excel export is not implemented yet."

## Criterion gaps

### 中文：判据缺口

背景：用户需要判断某次改动是否有具体评估判据。给出的复核结果显示，现有评估规则（rubric）覆盖了配置来源统一，但缺少“按 token budget 计算 payload 上界”的判据。提交覆盖指一项改动至少有一条适用 rubric；关键行为覆盖指主要行为改动有具体判据。

**原句**

> 这次定向复核已经找到反例，但尚未逐条标注全部提交，不能据此报告总体命中率

**改写**

> 这次复核发现，现有 rubric 覆盖了配置来源统一。按 token budget 计算 payload 上界还需要具体判据。补充这项判据，并分别记录提交覆盖和关键行为覆盖。

**理由**

原句把注意力转向用户未要求的总体统计，并暗示还要扩大复核范围。改写直接指出判据缺口和解决方向。用户确实需要总体命中率时，覆盖不完整会影响判断，必须说明。

### English

Context: the user is assessing whether a particular change has concrete evaluation criteria. The supplied review identifies coverage for a shared configuration source and a missing criterion for calculating a payload upper bound from a token budget. Commit coverage means that at least one rubric applies to a change; key-behavior coverage means that its primary behavior change has a concrete criterion.

**Before**

> This targeted review found a counterexample, but not every commit has been annotated, so we cannot report the overall hit rate.

**After**

> This review found that the rubric covers the shared configuration source. The calculation of the payload upper bound from the token budget needs an explicit criterion. Add that criterion, and record commit coverage and key-behavior coverage separately.

**Why**

The original ending shifts attention to an unrequested aggregate metric and implies a larger review. The revision identifies the criterion gap and the action that resolves it. If the user actually needs an overall rate, incomplete coverage affects that judgment and must be explained.

## Motivation

### 中文：交代动机

> 用户连续点击会重复提交订单，因此在请求完成前禁用提交按钮。

这句话把已观察到的问题与所选动作联系起来，直接说明改动的用途，省去笼统的“体验得到改善”评价。

### English

> Repeated clicks submit duplicate orders, so disable the submit button until the request finishes.

This sentence connects an observed problem to the chosen action. It explains why the change is useful without a separate statement claiming that the experience was improved.

## Research value

### 中文：研究价值与句子衔接

背景：用户提供了 `verl #6974` 的评审实验描述，希望说明模型与维护者的不同处理方式能带来什么研究问题，并让选择与维护影响的叙述衔接自然。

**原句：研究价值笼统**

> 在 verl #6974 的评审实验中，模型发现编码选项有问题后，建议加校验或补实现；维护者选择删除不需要的选项。模型识别出了缺陷，处理方式却留下不同的维护成本。这给“如何修、保留什么、简化什么”提供了实际研究样本。

**原句：选择与影响分离**

> 在 verl #6974 的评审实验中，模型发现编码选项有问题，建议增加校验或补齐实现；维护者选择删除不需要的选项。采用模型的建议，仍需维护这个选项；删除它则缩小了维护范围。

**改写**

> 在 verl #6974 的评审实验中，模型发现编码选项有问题，建议增加校验或补齐实现。这两种方案都会保留该选项，后续还需要维护相应逻辑。维护者则选择删除不需要的选项，从而缩小维护范围。后续评审可以据此考察：模型提出修复建议时，是否会判断功能的必要性，并比较不同方案的维护成本。

**理由**

上下文为研究意图提供了具体依据，因此保留这层意思。将笼统的价值评价改成具体研究问题：模型如何考虑功能的必要性和维护成本。改写保留了两种建议和维护者的选择，并将模型建议的维护影响表述为预期。

衔接问题来自叙述顺序：先列出两方的选择，再回头分别解释影响，导致叙述来回切换。改写先说明模型的方案及其维护影响，再说明维护者的选择及其影响，让读者顺着因果关系理解两种处理方式。

### English

Context: the user supplied an account of a review experiment involving `verl #6974` and wanted to explain its research value while connecting each choice to its maintenance consequences. The English passages translate the supplied Chinese examples and their revision.

**Before: vague research value**

> In the review experiment for verl #6974, the model found a problem with an encoding option and suggested adding validation or completing the implementation. The maintainer chose to delete the unnecessary option. The model identified the defect, while the different remedies carried different maintenance costs. This provides a concrete research example for how to fix issues, what to retain, and what to simplify.

**Before: choices separated from consequences**

> In the review experiment for verl #6974, the model found a problem with an encoding option and suggested adding validation or completing the implementation; the maintainer chose to delete the unnecessary option. Following the model's recommendation would still require maintaining that option; deleting it reduces the scope of maintenance.

**After**

> In the review experiment for verl #6974, the model found a problem with an encoding option and suggested adding validation or completing the implementation. Both approaches would retain the option and require continued maintenance of its logic. The maintainer chose to delete the unnecessary option, reducing the scope of maintenance. Future reviews could examine whether a model assesses the need for a feature and compares the maintenance costs of different remedies when proposing a fix.

**Why**

The context gives the research purpose a concrete basis, so retain that purpose. Replace the broad claim that the case is useful with the specific question it motivates: how the model considers feature necessity and maintenance cost. The revision preserves both proposed remedies and the maintainer's choice, and presents the maintenance effects of the model's recommendation as expected consequences.

The flow problem comes from listing both choices before returning to explain their consequences, which makes the narrative switch back and forth. The revision groups the model's proposals with their maintenance implications, then presents the maintainer's choice and its effect. This order keeps each causal connection together.

## Interpreting metrics

### 中文：解读指标

假设验收目标为导出成功率至少 99%，本次测量包含 100 次导出，其中 92 次成功。

**推荐表述**

> 100 次导出中有 92 次成功，成功率为 92%，比验收目标低 7 个百分点。下一步先查看 8 次失败的日志，判断是否存在共同原因，再确定修复方法。

样本、目标和下一步行动让数值能够支持判断。使用这种写法时，数值和目标必须有当前任务中的依据。

### English

Assume the acceptance target is an export success rate of at least 99%, and the measured sample contains 92 successful exports out of 100 attempts.

**Preferred wording**

> Of 100 export attempts, 92 succeeded. The success rate is 92%, which is 7 percentage points below the acceptance target. Next, inspect the logs from the 8 failed attempts for a common cause before choosing a fix.

The sample, target, and next action make the number useful for a decision. Use values and targets supported by the actual task when applying this pattern.

## Self-contained technical explanations

### 中文：自足的技术说明

背景：用户提供了一份关于 Relax 的调研说明，其中包含源码对照数量、局部函数复现结果和两个缺陷案例。读者需要理解这些记录对评测的用途，即使没有参与调查过程。

**原句**

> Relax 已有 15 条源码前后对照，其中 3 条完成局部行为复现。例如，缺少 expected 时从误判 PASS 改为 FAIL，两个入口对同一模型别名从处理不一致改为一致。这些条目有明确输入和预期输出，可以通过执行代码判定。

**问题**

原句省略了工具用途、变量含义、故障后果和实验范围。读者看到了数量和状态变化，却缺少理解变化及其评估用途的背景。

**改写示例**

这份材料整理了 15 个评审问题的修改前后代码。其中 3 个已执行实际函数，并记录输入输出。这些源码对照和执行记录可用于构造任务专用测试，并检查测试能否识别历史缺陷。

**缺少参考结果时误报通过**

Relax 的轨迹重放工具保存训练中的数据和计算结果，随后重新计算，并将新结果与保存的结果比较。`expected` 是保存的参考结果，`actual` 是重新计算的结果，例如某个样本的奖励值（reward）。

旧实现缺少参考结果时，仍然可能返回 `PASS`。工具没有完成比较，却向调用方报告验证通过。

对相同输入分别执行修改前后的比较函数，得到以下结果：

| 保存的参考结果（`expected`） | 重算结果（`actual`） | 修改前 | 修改后 |
|---|---|---|---|
| 1 | 1 | PASS | PASS |
| 2 | 1 | FAIL | FAIL |
| 缺失 | 1 | PASS | FAIL |

对应的评分要求是：缺少必需的参考结果时，验证工具必须拒绝报告通过。向待评测实现提供缺少参考结果的输入，检查返回状态，就能发现误报成功的问题。

**两个入口的选模结果不一致**

统一推理服务需要根据请求中的模型名称选择实际部署的模型。本例只部署了默认模型 `m1`，客户端请求的名称是 `served-name`。该项目的单模型兼容策略允许将 `served-name` 映射到默认模型 `m1`。

这项兼容规则原先只在内部执行器中处理，修改后集中到公共选模函数。给两处逻辑提供相同的部署信息和请求名称，结果如下：

| 选模入口 | 修改前 | 修改后 |
|---|---|---|
| 内部执行器 | 选中 `m1` | 选中 `m1` |
| 公共选模函数 | 拒绝：未知模型 | 选中 `m1` |

对应的评分要求是：在这个单模型兼容场景下，两处逻辑都必须选中 `m1`。向两处提供相同输入，以两者都返回预期模型作为通过条件，可以发现只修复一条调用路径的问题。

**改写依据**

改写保留了统计结果，并说明每个数量的含义：15 个问题有源码前后对照，其中 3 个有函数执行记录。工具用途和术语解释帮助读者理解检查目的；输入输出对照说明触发条件、行为变化和故障后果；评分要求将这些记录连接到具体评测任务。

说明围绕当前结论展开。用户明确熟悉的概念可直接使用，专业经验或前序参与不能代替理解这次结果所需的实现背景。

### English

Context: the user supplied a research summary about Relax containing counts of source comparisons, local function reproductions, and two defect examples. The reader needs to understand how these records support evaluation, even without participating in the investigation.

**Before**

> Relax already has 15 before-and-after source comparisons, 3 of which have local behavior reproductions. For example, a missing expected changes from an incorrect PASS to FAIL, and two entry points change from inconsistent to consistent handling of the same model alias. These entries have explicit inputs and expected outputs and can be judged by executing code.

**Problem**

The original omits the tool's purpose, the variables' meanings, the consequences of the defects, and the scope of the experiments. Counts and status changes alone leave the reader without enough context to interpret the findings or their evaluation use.

**Revised example**

The material contains before-and-after code for 15 review issues. For 3 of those issues, actual functions have been executed and their inputs and outputs recorded. These source comparisons and execution records can support task-specific tests and checks of whether those tests detect historical defects.

**Reporting success without a reference result**

Relax's trajectory replay tool saves data and computed results during training, then repeats the computation and compares the new results with the saved ones. `expected` is the saved reference result; `actual` is the recomputed result, such as the reward for a sample.

The old implementation could return `PASS` when the reference result was missing. It reported successful verification to the caller even though no comparison had been completed.

Executing the old and new comparison functions with the same inputs produced these results:

| Saved reference (`expected`) | Recomputed result (`actual`) | Before | After |
|---|---|---|---|
| 1 | 1 | PASS | PASS |
| 2 | 1 | FAIL | FAIL |
| Missing | 1 | PASS | FAIL |

The scoring requirement is that a verification tool must refuse to report success when a required reference result is missing. Supply an input without that reference and inspect the returned status to detect a false success report.

**Inconsistent model selection across two entry points**

The unified inference service selects a deployed model using the model name in a request. In this example, `m1` is the only deployed model and is configured as the default. The client requests `served-name`. The project's single-model compatibility policy permits mapping `served-name` to the default model, `m1`.

Previously, only the internal executor applied this compatibility rule. The change centralizes it in the public model-selection function. With the same deployment information and requested name, the results are:

| Selection entry point | Before | After |
|---|---|---|
| Internal executor | Selects `m1` | Selects `m1` |
| Public model-selection function | Rejects the request as an unknown model | Selects `m1` |

The scoring requirement is that both paths must select `m1` in this single-model compatibility scenario. Provide the same input to both paths and require both to return the expected model. This exposes a fix that updates only one call path.

**Why**

The revision retains the statistics and defines their units: 15 issues have before-and-after source comparisons, and 3 of them have function execution records. The tool description and term definitions establish the purpose of the checks. The input/output comparisons explain triggers, behavior changes, and consequences. The scoring requirements connect these records to specific evaluation tasks.

The explanation stays focused on the current conclusion. Explicitly familiar concepts can be used directly; professional expertise or earlier involvement does not replace the implementation context needed to understand this result.
