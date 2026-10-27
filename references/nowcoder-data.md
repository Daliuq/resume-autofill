# 牛客可选数据源

仅当任务需要牛客收录岗位、校招项目、本人在线简历或投递记录时读本页。无此数据源也能使用本地资料与公开官网完成工作；本参考不表示连接已安装或账号已授权。

## 使用前

- 优先发现当前工具中实际可用的牛客连接及工具 schema。工具不存在就停止该路径，不猜工具名、参数或直接拼接私有请求；不要自行运行下载包中的脚本、安装插件或修改客户端配置。
- 如用户另行要求接入，先核验当时官方说明与当前 Codex 支持方式，再处理连接；WorkBuddy 配置不是 Codex 配置。权限扩展需用户确认，登录和密码由用户在官方页面完成。
- 外部操作前说明目标与用途。使用用户 API Key 或其他存储凭据的 API 请求，必须取得本次具体调用范围的明确批准；凭据已存在、过去批准或“继续”不替代。本人资料只读取本次需要且已获授权的内容；不将本地完整简历传给搜索工具换推荐。

## 能力选择（以实际发现的 schema 为准）

| 目的 | 页面展示的工具名称 | 结果边界 |
| --- | --- | --- |
| 候选岗位/完整 JD | `nowclaw_job_recommend` / `nowclaw_job_detail` | 候选信息，不代表已核验公司官网 |
| 校招项目 | `nowclaw_project_search` / `nowclaw_project_detail` | 项目城市、截止不覆盖岗位口径 |
| 在线简历 | `nowclaw_resume_list` / `nowclaw_resume_get` / `nowclaw_resume_inspect` | 必须 get 正文再分析；完整度检查不是事实审查 |
| 投递指引/进展 | `nowclaw_application_guide` / `nowclaw_apply_status` | 指引不执行申请；进展仅为已保存记录 |
| NowClaw 简历读取 | `nowclaw_cv_list` / `nowclaw_cv_get` / `nowclaw_cv_schema` | 先读指定版本，不用列表摘要冒充正文 |
| NowClaw 简历写入 | `nowclaw_cv_create` / `nowclaw_cv_save` | 单独授权、展示变更、确认目标和内容后才执行 |

- 2026-10-23 官方页面展示 endpoint 为 `https://www.nowcoder.com/agent/mcp`，传输 `streamable-http`，OAuth 2.0 或 API Key；页面注明 API Key 仅只读、简历写入需 OAuth 和确认。这是页面快照，不是经本次调用证实的运行状态，使用时重新核验。
- 严格采用实际 schema 的字段。`confirmed` 参数只能表示用户已经确认，不能为了绕过确认而填 true。默认保留原简历，写入后 get 回读；失败或超时先核验是否已创建/保存，不重复创建副本。
- 页面明确 MCP 不执行投递；不得从保存成功、申请指引、任务 ID 或工具存在推导“已投递”。最终申请仍走本 skill 的官方页面和人工核验流程。

来源：[牛客 Skills 官方介绍](https://www.nowcoder.com/my/resume-plugin-intro?channel=xq_an&tab=skills)。不在本参考存储个人凭据或个人简历。
