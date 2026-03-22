# Eternodes 自动续期脚本

自动续期 Eternodes 服务器，支持多账号、HY2 代理、Telegram 通知。建议每 3 天运行一次。

## 环境变量配置

需要设置以下环境变量：

- PRIVATE_REPO_TOKEN （用于读取私库的 token）

- ETERNODE_BATCH_ACCOUNTS （Eternodes 账号环境变量，必须填）

```
ETERNODE_BATCH_ACCOUNTS=token|accountName,session_id,user_id,server_value,tg_token,tg_chat_id
token2|account2,session_id2,user_id2,server_value2,tg_token2,tg_chat_id2
```

### 格式说明：

每行一套数据：

1、不发 TG：token|accountName,session_id,user_id,server_value

2、发 TG：token|accountName,session_id,user_id,server_value,tg_token,tg_chat_id

3、accountName 可选，如果不提供则显示 token 前 20 位

4、token (Discord 账号 Token) 的取值方式：
- 打开 Discord 网页版 → F12 → Network → 任意请求 → Headers → authorization

5、session_id (Discord Session ID) 的取值方式：
- F12 → Network → 找一个 interactions 请求 → Payload → session_id

6、user_id 和 server_value：
- 从 Discord 消息或 API 响应中获取

- ETERNODE_HY2_PROXY_URL （可选，Hysteria2 代理 URL）

```
ETERNODE_HY2_PROXY_URL='hy2://[auth]@[host]:[port]/?sni=xxx&insecure=0&alpn=h3'
```

### 如果不设置此环境变量，脚本将使用直连模式

- SOCKS_PORT （可选，SOCKS5 端口，默认 51080）

```
SOCKS_PORT='51080'
```

### 仅在设置了 ETERNODE_HY2_PROXY_URL 时生效

## 定时任务执行时间

默认每 3 天 UTC 20:18（北京时间 04:18）执行一次

修改执行时间请编辑 eternodes-AutoRenew.yml 中的 cron 表达式
