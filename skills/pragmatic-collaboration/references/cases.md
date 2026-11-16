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

### 中文：具体说明研究价值

背景：用户提供了 `verl #6974` 的评审实验描述，希望说明模型与维护者的不同处理方式能带来什么研究问题。

**原句**

> 在 verl #6974 的评审实验中，模型发现编码选项有问题后，建议加校验或补实现；维护者选择删除不需要的选项。模型识别出了缺陷，处理方式却留下不同的维护成本。这给“如何修、保留什么、简化什么”提供了实际研究样本。

**改写**

> 在 verl #6974 的评审实验中，模型发现编码选项有问题，建议增加校验或补齐实现；维护者选择删除不需要的选项。采用模型的建议，需要继续维护这个选项；删除它则缩小了维护范围。后续评审可以据此考察：模型提出修复建议时，是否会判断功能的必要性，并比较不同方案的维护成本。

**理由**

上下文为研究意图提供了具体依据，因此保留这层意思。将笼统的价值评价改成具体研究问题：模型如何考虑功能的必要性和维护成本。改写保留了两种建议和维护者的选择，并用条件句描述采用模型建议后的影响。

### English

Context: the user supplied an account of a review experiment involving `verl #6974` and wanted to explain what could be learned from the model's and maintainer's different responses. The English passages translate the supplied Chinese account and its revision.

**Before**

> In the review experiment for verl #6974, the model found a problem with an encoding option and suggested adding validation or completing the implementation. The maintainer chose to delete the unnecessary option. The model identified the defect, while the different remedies carried different maintenance costs. This provides a concrete research example for how to fix issues, what to retain, and what to simplify.

**After**

> In the review experiment for verl #6974, the model found a problem with an encoding option and suggested adding validation or completing the implementation. The maintainer chose to delete the unnecessary option. Following the model's recommendation would require continuing to maintain that option; deleting it reduces the scope of maintenance. Future reviews could examine whether a model assesses the need for a feature and compares the maintenance costs of different remedies when proposing a fix.

**Why**

The context gives the research purpose a concrete basis, so retain that purpose. Replace the broad claim that the case is useful with the specific question it motivates: how the model considers feature necessity and maintenance cost. The revision preserves both proposed remedies and the maintainer's choice, and describes the consequences of the model's recommendation conditionally.

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
