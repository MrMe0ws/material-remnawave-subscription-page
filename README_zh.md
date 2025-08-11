[Русская версия](README.md) | [English Version](README_en.md) | [中文版](README_zh.md) | [نسخه فارسی](README_fa.md)

# Material Remnawave 订阅页面

此存储库包含 Remnawave 代理面板订阅页面的源代码，采用现代 Material Design 3 风格设计。该页面为用户提供方便的订阅信息访问、连接说明和链接。代码在 Claude Sonnet 4 AI 模型的帮助下编写。

## 主要特性

* **Material 3 设计：** 根据最新的 Material Design 3 原则开发的现代直观用户界面。

* **深色和浅色主题支持：** 自动或手动在浅色和深色主题之间切换，适合任何光照条件下的舒适使用。

* **灵活的应用配置：** 支持用于连接的标准推荐应用程序列表，以及通过[可自定义的 `app-config.json`](https://remna.st/docs/install/remnawave-subscription-page#custom-app-configjson-custom-apps) 文件轻松集成第三方客户端。
* * **自定义组**  
通过集成文件向应用程序部分添加额外组的能力，[例如，`TV 部分`](https://github.com/legiz-ru/my-remnawave/blob/main/sub-page/multiapp/app-config.json)。

* **单独链接复制：** 除了主要订阅链接外，还可以直接从页面复制单独链接（例如 `vless://`、`trojan://`）。

* **多语言支持：** 页面支持俄语、英语、波斯语和中文，具有自动浏览器语言检测功能。

## 屏幕截图

<div align="center">
  <img src="./screenshots/apps-sections-select.jpg" width="66%" />
  <img src="./screenshots/apps-sections.jpg" width="66%" />
  <img src="./screenshots/user-status-sections.jpg" width="66%" />
  <img src="./screenshots/settings-sections.jpg" width="66%" />
  <img src="./screenshots/sub-links-sections.jpg" width="66%" />
</div>

## 安装

1. **下载页面文件：**
   使用 `curl` 将 `index.html` 文件下载到您的 `docker-compose.yml` 所在的同一目录：

   ```bash
   curl -o index.html https://raw.githubusercontent.com/legiz-ru/material-remnawave-subscription-page/refs/heads/main/index.html
   ```

2.  **配置 Docker Compose：**
    通过在 `remnawave-subscription-page` 容器中挂载 `volumes`，在您的 `docker-compose.yml` 中指定下载的 `index.html` 的路径。

    标准安装示例：

    ```yaml
    services:
      remnawave-subscription-page:
        volumes:
          - ./index.html:/opt/app/frontend/index.html
    ```

    如果您计划使用[自定义应用程序列表](https://remna.st/docs/install/remnawave-subscription-page#custom-app-configjson-custom-apps)（`app-config.json`），请添加相应的 `volume`：

    ```yaml
    services:
      remnawave-subscription-page:
        image: remnawave/subscription-page:latest
        volumes:
          - ./index.html:/opt/app/frontend/index.html
          - ./app-config.json:/opt/app/frontend/assets/app-config.json
    ```

    您可以使用我的自定义应用程序列表之一，可在以下位置获得：[自定义应用列表](https://github.com/legiz-ru/my-remnawave/blob/main/README.md#remnawave-subscription-page-%D1%81lient-configuration)

3.  **重启容器：**
    要应用更改，请重启您的 Docker 容器：

    ```bash
    docker compose down remnawave-subscription-page && docker compose up -d remnawave-subscription-page
    ```

## 联系方式

  * [Telegram 频道](https://t.me/legiz_trashbag)

## 支持项目

如果您喜欢这个项目并想支持其开发，您可以进行捐赠：

  * [Telegram 上的 Tribute](https://t.me/tribute/app?startapp=drzu)
  * [TON USDT: `UQAGQTQZYCx5TWj5cmTLpo7164PFsXqZZJ6t6x88n7sHW9gU`]