# GPT-Image-2-VIP 图像生成工具

基于 [ToAPIs](https://toapis.com) 的 GPT-Image-2-VIP 图像生成前端工具，支持文生图和图生图。

## 在线访问

**https://11121211221.github.io/toapis-image-gen/**

## 功能特性

- **文生图** — 输入文本描述生成图像
- **图生图** — 上传参考图，结合提示词生成新图像
- **多任务并发** — 可同时提交多个生成任务，无需等待
- **生成记录** — 自动保存历史记录，支持查看、下载、删除
- **额度查询** — 实时查询 API Key 余额
- **消耗统计** — 每次生成自动记录消耗额度
- **明暗主题** — 支持亮色/暗色主题切换
- **自动恢复** — 刷新页面后未完成任务继续轮询

## 支持参数

| 参数 | 选项 |
|------|------|
| 宽高比 | 1:1, 3:2, 2:3, 4:3, 3:4, 16:9, 9:16, 21:9, 9:21 |
| 分辨率 | 1K, 2K, 4K |
| 质量 | Low, Medium, High |
| 数量 | 1-4 张 |

## 使用方式

1. 访问在线地址或本地打开 `index.html`
2. 在 [ToAPIs](https://toapis.com/console/token) 获取 API Key
3. 输入 API Key，填写提示词
4. 选择参数，点击「生成图像」
5. 等待完成后在右侧历史记录中查看结果

## 本地运行

```bash
# 方式一：直接双击 index.html（部分浏览器可能有跨域限制）

# 方式二：启动本地服务器
# Windows
start-server.bat

# macOS / Linux
python3 -m http.server 8080
```

然后访问 `http://localhost:8080`

## API 接口

本工具调用以下 ToAPIs 接口：

| 接口 | 方法 | 用途 |
|------|------|------|
| `/v1/images/generations` | POST | 提交图像生成任务 |
| `/v1/images/generations/{task_id}` | GET | 查询任务状态 |
| `/v1/uploads/images` | POST | 上传参考图片 |
| `/v1/balance` | GET | 查询 API Key 余额 |

## 注意事项

- 图片链接有效期 **24 小时**，请及时下载保存
- 历史记录最多保留 **100 条**，超出自动清理最旧记录
- API Key 保存在浏览器本地（localStorage），不会上传到任何服务器
- 纯前端项目，无需后端服务器

## 技术栈

- 纯 HTML / CSS / JavaScript，无任何框架依赖
- 使用 CSS Custom Properties 实现主题切换
- 使用 localStorage 持久化历史记录和设置
- 使用 Fetch API 调用 ToAPIs 接口
