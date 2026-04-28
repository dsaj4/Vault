# IMA 技能安装记录

## 安装信息

- 技能名称：`ima-skill`
- 版本：`1.1.7`
- 下载地址：`https://app-dl.ima.qq.com/skills/ima-skills-1.1.7.zip`
- 压缩包 SHA256：`BD5878416AED4C358DEB2B9BC34DFD7602A0DA9D9602582227794791289F73B2`
- 安装位置：`C:\Users\Administrator\.codex\skills\ima-skill`
- 安装时间：2026-04-28

## 审查结论

- 文件已逐项审查：`SKILL.md`、`ima_api.cjs`、`meta.json`、`knowledge-base/`、`notes/`。
- 主要网络目标：`https://ima.qq.com` 与腾讯云 COS 域名 `*.myqcloud.com`。
- 主要权限需求：读取用户指定上传的文件；读取 IMA 凭证；向 IMA/COS 发起 API 请求。
- 未发现混淆代码、任意命令执行、读取 SSH/AWS/浏览器凭证、系统级修改等高危行为。
- 风险级别：中等。原因是该技能需要用户提供 IMA OpenAPI Client ID 与 API Key，并可按用户指令上传文件到 IMA 知识库。

## 当前配置状态

- 尚未检测到本机凭证文件：
  - `~/.config/ima/client_id`
  - `~/.config/ima/api_key`
- 后续如需实际同步到 IMA，需要先从 `https://ima.qq.com/agent-interface` 获取凭证并配置。

## 凭证配置方式

推荐使用配置文件：

```bash
mkdir -p ~/.config/ima
echo "your_client_id" > ~/.config/ima/client_id
echo "your_api_key" > ~/.config/ima/api_key
```

也可以使用环境变量：

```bash
export IMA_OPENAPI_CLIENTID="your_client_id"
export IMA_OPENAPI_APIKEY="your_api_key"
```

兼容环境变量：

```bash
export IMA_CLIENT_ID="your_client_id"
export IMA_API_KEY="your_api_key"
```
