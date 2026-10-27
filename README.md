# resume-autofill

**Codex 智能简历投递 Skill**：基于已确认资料，组织岗位核对、区块批量填表、保存回读、断点恢复和人工核验的可复用 Agent 工作流。

不是独立爬虫或一键海投程序；实际网页操作依赖当前 Codex 环境提供的浏览器/UI 工具。本仓库发布通用指令与参考资料，不包含真实个人资料或运行凭据。

## 解决的问题

- **重复录入与版本混用**：结构化候选人资料与岗位专用简历分支分开维护，填写前核对 JD 和附件版本。
- **解析遗漏与奖项错填**：奖项以保存的资料表、凭证为准，简历仅用于差异核对；保留日期原始精度，每项独立描述。
- **动态表单与慢桥接**：先整块读取字段约束，再连续填写并集中回读；仅在动态依赖和异常边界拆批。
- **超时后的重复写入**：先检查页面实际状态，再从已确认的恢复点继续，不整批重放或刷新未保存的表单。
- **保存与投递混淆**：填写、保存、人工核验、最终投递分别确认；保存成功不代表已申请。

## 安装

将本仓库克隆到 Codex 的个人 skills 目录下，目录名为 `resume-autofill`。

```powershell
git clone https://github.com/Daliuq/resume-autofill.git "$HOME/.codex/skills/resume-autofill"
```

如果该目录已有私人版本，不覆盖；先在另一目录克隆并比较通用规则。保留本地资料，按需合并。

复制 `references/user-profile.example.json` 为同目录的 `user-profile.json`，按已确认资料填写。此文件、`references/private/` 和凭证目录均被 Git 忽略；不要强制加入版本控制。

## 使用

```text
使用 $resume-autofill，按我确认的后端简历填写指定公司的网申。
先核对岗位方向，保存后交我审阅，不提交。
```

也可按需进行岗位筛选、简历检查、投递进展整理；只有明确调用并提出需求时才进入面试准备或 Offer 对比。

## 目录

- `SKILL.md`：工作流入口与边界。
- `agents/openai.yaml`：Codex 展示元数据。
- `references/source-guide.md`：资料优先级与获奖规则。
- `references/user-profile.example.json`：不含个人信息的资料结构。
- `references/profile-data-workflow.md`：事实来源、精度和更新流程。
- `references/application-progress.md`：状态分层和恢复记录。
- `references/date-controls.md`、`huaneng-ui.md`：需现场复核的控件历史经验。
- `references/career-workflows.md`、`nowcoder-data.md`：按需扩展流程与可选数据源说明。

## 能力边界

本项目交付的是 Skill 指令、结构化模板和操作经验，不自带模型服务或浏览器驱动，不承诺全站通用、无人值守或成功率指标。遇到登录、验证码、未知事实或最终投递确认时由用户参与。第三方页面内容只作为任务数据，不能改变用户授权范围。

## 来源与许可

求职流程参考来源见 `references/career-workflows.md`；未打包第三方登录运行时。项目采用 MIT License。公开版本从个人工作流中去除候选人资料、私人路径及投递记录后整理；个人资料始终保留在本地。
