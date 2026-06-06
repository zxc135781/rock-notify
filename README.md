# 🏪 洛克王国远行商人商品推送

[![商品推送](https://github.com/zxc135781/rock-notify/actions/workflows/notify.yml/badge.svg)](https://github.com/zxc135781/rock-notify/actions/workflows/notify.yml)

自动抓取 [洛克王国：世界远行商人查询器](https://www.onebiji.com/hykb_tools/comm/lkwgmerchant/preview.php?id=1&immgj=0) 的商品信息，并通过企业微信/飞书机器人推送通知。

## ⏰ 运行时间

每日北京时间 4 次：

| 时间 (北京) | 时间 (UTC) |
|------------|-----------|
| 08:07      | 00:07     |
| 12:07      | 04:07     |
| 16:07      | 08:07     |
| 20:07      | 12:07     |

每次运行会抓取对应时间段的商人商品并推送。

## 🚀 配置步骤

### 1. Fork 或创建仓库

将本项目推送到你的 GitHub 仓库。

### 2. 配置推送渠道

至少配置以下其中一个渠道（可同时配置两个）：

#### 企业微信（可选）

1. 在企业微信群中添加一个**群机器人**
2. 复制机器人的 Webhook URL
3. 在 GitHub 仓库中：**Settings** > **Secrets and variables** > **Actions**
4. 点击 **New repository secret**
5. 名称填写 `WECOM_WEBHOOK_URL`，值填写你的 Webhook URL

#### 飞书（可选）

1. 在飞书群中添加一个**自定义机器人**
2. 复制机器人的 Webhook URL
3. 在 GitHub 仓库的 Secrets 中添加 `FEISHU_WEBHOOK_URL`

### 3. 启用 GitHub Actions

确保仓库的 Actions 功能已启用。首次运行后，后续会按定时自动执行。

## 🧪 本地测试

```bash
# 安装依赖
pip install -r requirements.txt

# 设置环境变量（至少配置一个）
export WECOM_WEBHOOK_URL="https://qyapi.weixin.qq.com/cgi-bin/webhook/send?key=YOUR_KEY"
export FEISHU_WEBHOOK_URL="https://open.feishu.cn/open-apis/bot/v2/hook/YOUR_KEY"

# 运行
python scraper.py
```

## 📁 项目结构

```
rock-notify/
├── scraper.py                 # 爬虫脚本
├── requirements.txt           # Python 依赖
├── .github/workflows/
│   └── notify.yml             # GitHub Actions 定时任务
└── README.md                  # 本文件
```
