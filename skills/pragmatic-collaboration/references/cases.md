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

**解释模型比较结果**

- **原句**　“题目完全相同，但回复长度差异会影响对架构差异的归因。”
- **改写**　“两个模型回答了同一道题，回复长度不同。仅凭这次比较，还难以判断结果差异有多少来自模型架构。”

“影响”可以照常使用。这句里的“归因”省略了要解释的对象。改写先交代两个模型的回复长度不同，再写明哪项判断仍有困难。如果上下文给出了具体指标，就用指标名替换“结果差异”。

### English

When describing an action, name what will be checked:

- Before: "Complete persistence consistency verification."
- After: "Check whether the saved file can be reopened."

When reporting a blocker that affects a required check, name the dependency and its consequence:

- Before: "Environment gate pending closure."
- After: "This test needs a local database. Connection settings are missing, so saving data remains unverified."

The revised wording lets the user understand the action or blocker without translating jargon. If the user must supply the configuration, state that request separately.

**Explaining a model comparison**

- **Before** “The prompts were identical, but differences in response length affect the attribution of architectural differences.”
- **After** “The two models answered the same question and produced answers of different lengths. From this comparison alone, it is hard to tell how much of the difference in results comes from model architecture.”

“Affect” is fine here. “Attribution” leaves out which result needs explaining. The revision gives the observation first, then states what remains difficult to judge. When the metric is known, name it in place of “results.”

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

## Numerical differences and causal evidence

### 中文：解释数值差异与证据强度

背景：用户提供了单卡断点续训的初步汇报，以及后续补充的逐步观测和权重比较。案例依据这些材料整理，重点是说明恢复了哪些内容、数值分歧出现在什么位置，以及哪些解释已经得到支持。

**原回复中的结论**

> 单卡断点续训验证通过。
>
> 最终权重存在数值波动。以连续训练后 8 步的权重更新量为基准，连续训练与第一次恢复的最终权重差异为 26.8%，两次独立恢复之间为 32.8%。相同起点重复运行也出现了同量级波动，当前配置能准确恢复训练状态，但后续更新不能逐位复现。

**问题**

“验证通过”没有说明验收范围，“数值波动”没有说明差异是否可接受。读者还需要了解差异最早出现的位置、百分比的参照、精度转换的影响，以及原因解释的证据强度。

**改写示例**

已检查的断点内容和续训位置恢复一致，后续训练出现了数值分歧。权重差异比例的放大已有部分解释，最初梯度范数差异的具体原因仍需定位。

本次用 Qwen3.5-4B 评分的 128 条 GSM8K 轨迹训练 Qwen3.5-0.8B，连续运行 16 步，并从第 8 步的检查点独立恢复两次。

**恢复后的起点与进度**

第 9 步更新前，三次运行的 383 个模型参数张量和 690 个 Adam 状态张量逐项一致。两次恢复读到了与连续训练相同的 8 条样本，第 9 步的学习率均为 1.5e-6，loss 均为 0.214940235。这些结果支持模型参数、已检查的优化器状态和续训位置正确衔接。

第 9–16 步的样本顺序、学习率和 Adam 步数也逐步一致。连续运行完整使用了 128 条样本，每条恰好一次。

**后续数值分歧**

最早可见的差异出现在第 9 步的梯度范数，第 10 步的 loss 随后也出现差异：

| 观测项 | 第一次恢复 | 第二次恢复 |
|---|---|---|
| 第 9 步梯度范数 | 20.5148525 | 20.5146503 |
| 第 10 步 loss | 0.230014 | 0.229259 |

第 16 步权重的比较结果如下。百分比以连续训练从第 8 步到第 16 步的净更新量为分母，每列的分子和分母均使用相应精度的权重计算：

| 比较对象 | Adam 实际更新的 FP32 主权重 | 模型使用的权重，绝大多数为 BF16 |
|---|---|---|
| 连续训练与第一次恢复 | 8.6% | 26.8% |
| 连续训练与第二次恢复 | 12.9% | 32.2% |
| 第一次恢复与第二次恢复 | 13.0% | 32.8% |

这些比例衡量不同运行之间的最终权重差异相当于本轮净更新量的多少。FP32 主权重用于 Adam 更新，模型权重采用的精度不同，因此两列需要分别解释。

**已有依据的解释与工作假设**

精度转换可以解释差异比例增大这一部分。两次恢复的 FP32 主权重已有相当于净更新量 13.0% 的差异；将这些主权重转换为模型使用的精度后，可以复现 32.8%。两个接近的 FP32 值可能位于 BF16 舍入边界的两侧，转换后相对差异随之放大。

对最初的梯度范数差异，当前工作假设是 GPU 反向计算或梯度归约存在非确定性。本次运行关闭了确定性模式，这为该假设提供了线索；具体算子仍需定位。

**异常性判断与后续处理**

目前可以验收已检查的断点内容和续训位置。训练数值确实发生了分歧，待判定的是恢复操作是否额外放大了当前配置下的重复运行差异。

两次恢复彼此的差异，与各自偏离连续训练的差异处于同一量级。结合恢复起点的参数、Adam 状态和样本一致的结果，当前排查重点是续训计算过程的重复性。

下一步补充同一起点、同一批数据的重复不中断训练对照，采用相同口径比较 FP32 主权重和模型权重的差异范围。这组对照将用于判断恢复操作是否引入额外偏差，再决定后续训练的数值一致性是否符合本次验收要求。

**改写依据**

改写将恢复一致性、后续数值分歧和异常性判断分别说明。逐步观测解释了“接上第 9 步”的具体含义；分母和权重精度解释了百分比；转换后能复现 32.8% 支持精度放大的解释；GPU 计算非确定性仍明确标为假设。所缺的不中断训练对照直接影响异常性判断，因此需要交代其用途。新增数值和配置事实均来自用户补充的材料。

### English

Context: the user supplied an initial report on single-GPU checkpoint resumption, followed by step-level observations and weight comparisons. This case uses that material to explain the restored state, the observed divergence, and the strength of each explanation.

**Original conclusion**

> Single-GPU checkpoint resumption validation passed.
>
> Final weights show numerical variation. Relative to the weight update over the last 8 uninterrupted training steps, the final difference between uninterrupted training and the first resumed run is 26.8%, and the difference between two independent resumed runs is 32.8%. Repeated runs from the same starting point also show variation of the same order. The configuration accurately restores training state, but subsequent updates are not bitwise reproducible.

**Problem**

"Validation passed" leaves the acceptance scope unclear, and "numerical variation" does not explain acceptability. The reader needs the earliest observed divergence, the denominator of the percentages, the effect of precision conversion, and the evidence supporting the proposed causes.

**Revised example**

The checked checkpoint contents and resumption position match, while subsequent training shows numerical divergence. Part of the increase in the relative weight difference has an explanation; the specific cause of the initial gradient-norm divergence remains to be identified.

Qwen3.5-0.8B was trained for 16 uninterrupted steps on 128 GSM8K trajectories scored by Qwen3.5-4B. Two independent runs resumed from the step-8 checkpoint.

**Restored starting point and progress**

Before the step-9 update, all 383 model parameter tensors and 690 Adam state tensors matched across the three runs. Both resumed runs read the same 8 samples as uninterrupted training. The step-9 learning rate was 1.5e-6 and the loss was 0.214940235 in all three runs. These observations support correct restoration of the model parameters, checked optimizer state, and resumption position.

Sample order, learning rates, and Adam step counts also matched at each step from 9 through 16. The uninterrupted run used all 128 samples exactly once.

**Subsequent numerical divergence**

The earliest visible difference was in the step-9 gradient norm, followed by a difference in step-10 loss:

| Observation | First resumed run | Second resumed run |
|---|---|---|
| Step-9 gradient norm | 20.5148525 | 20.5146503 |
| Step-10 loss | 0.230014 | 0.229259 |

The step-16 weight comparisons are below. Each percentage uses the uninterrupted run's net update from step 8 to step 16 as its denominator. Within each column, the numerator and denominator use weights at the corresponding precision:

| Runs compared | FP32 master weights updated by Adam | Model weights, mostly BF16 |
|---|---|---|
| Uninterrupted and first resumed run | 8.6% | 26.8% |
| Uninterrupted and second resumed run | 12.9% | 32.2% |
| First and second resumed runs | 13.0% | 32.8% |

These ratios express the final difference between runs relative to this training segment's net update. Adam updates the FP32 master weights, while the model uses weights at a different precision, so each column needs its own interpretation.

**Supported explanation and working hypothesis**

Precision conversion explains part of the increase in the relative difference. The two resumed runs' FP32 master weights already differ by 13.0% of the reference net update. Converting those master weights to the model's precision reproduces 32.8%. Two nearby FP32 values can fall on opposite sides of a BF16 rounding boundary, amplifying the relative difference after conversion.

The working hypothesis for the initial gradient-norm divergence is nondeterminism in GPU backward computation or gradient reduction. Deterministic mode was disabled in this run, which provides a clue for that hypothesis; the specific operator remains to be identified.

**Acceptability judgment and next action**

The checked checkpoint contents and resumption position can be accepted. Numerical divergence has been observed. The unresolved question is whether resumption adds variation beyond the configuration's repeat-run behavior.

The difference between the two resumed runs is of the same order as each run's difference from uninterrupted training. Together with the matching starting parameters, Adam state, and samples, this directs the next investigation toward reproducibility during continued computation.

Next, add repeated uninterrupted controls using the same starting point and data, and compare FP32 master-weight and model-weight variation using the same metrics. These controls provide a baseline for judging whether resumption introduces additional deviation and whether subsequent training's numerical consistency meets the acceptance requirements.

**Why**

The revision separates restoration consistency, later divergence, and acceptability. Step-level observations explain what resuming at step 9 means. The denominator and weight precision explain the percentages. Reproducing 32.8% through conversion supports the precision-related amplification, while GPU nondeterminism remains explicitly a hypothesis. The missing uninterrupted controls directly affect the acceptability judgment, so their purpose belongs in the explanation. All added measurements and configuration facts come from the user's supplementary material.
