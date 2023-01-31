# GeoLite2

[![GeoLite2](../../actions/workflows/GeoLite2.yml/badge.svg)](../../actions/workflows/GeoLite2.yml)

从MindMax下载GeoLite2的数据库文件并推送到指定CDN。

# 说明

项目 **99%** 的内容都来自 [P3TERX/GeoLite.mmdb](https://github.com/P3TERX/GeoLite.mmdb)。仅增加了上传到 Cloudflare R2 的工作流（不需要可以直接 fork [P3TERX/GeoLite.mmdb](https://github.com/P3TERX/GeoLite.mmdb) 的源）


# 配置

1，访问 [Actions permissions](../../settings/actions) ，滚动到页面底部，将 `Workflow permissions` 选项修改为 `Read and write permissions` 后，点击 **Save** 按钮保存

2，点击 [Actions secrets / New secret](../../settings/secrets/actions/new)，依次添加以下内容项


| Name字段 | Secret字段 |
| ----- | ----- |
| `LICENSE_KEY` | 填写在MaxMind中注册得到的 `Licence Key`，[注册并生成Licence Key](https://dev.maxmind.com/geoip/geolite2-free-geolocation-data) |
| `CF_ACCOUNT_ID` | 参考 [Find zone and account IDs](https://developers.cloudflare.com/fundamentals/get-started/basic-tasks/find-account-and-zone-ids/)<br>**[可选]** Cloudflare 的 Account ID </br>如果不需要上传R2，则在 [.github/workflows/GeoLite2.yml](./.github/workflows/GeoLite2.yml) 文件中注释掉 `R2 Directory Upload` 相关代码</br>下同 |
| `CF_ACCESS_KEY` | 参考 [Generate an S3 Auth token](https://developers.cloudflare.com/r2/data-access/s3-api/tokens/) (下同)<br>**[可选]** 用于访问 Cloudflare R2 的 Access Key ID |
| `CF_SECRET_KEY` | **[可选]** 用于访问 Cloudflare R2 的 Secret ID |
| `R2_BUCKET` | **[可选]** Cloudflare R2 的 **存储桶名称** |
| `TELEGRAM_TOKEN` | **[可选]** Telegram Bot 的 Token</br>如需要Telegram通知需填写，不需要请注释掉流水线 `Send telegram message` 对应代码 |
| `TELEGRAM_TO` | **[可选]** Telegram 接收消息的 ID，可通过 [https://t.me/myidbot](https://t.me/myidbot) 获取 |


# 使用

直接在release中访问最新的地址，或者使用上传到了 Cloudflare R2 的 CDN 源地址（为了便捷，可将 R2 的存储桶设置为公开访问）

