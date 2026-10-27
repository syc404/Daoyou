# 本站部署修改

修改日期：2026-10-27。

本版本基于 ChurchTao/Daoyou（提交 4cd2399788e151cb4abf06acad2815164a3127a2）修改，继续采用仓库 LICENSE 中的 GNU GPL v3.0。原作者及第三方版权、许可证声明保留。本站独立维护，地址为 https://game.hantieyi.cn 。

- 新增 `/web` 静态官网，包含游戏介绍、本站联系方式、备案链接和部署版本源码下载。
- 登录及注册页面显示本站域名、官网入口及备案号。
- 移除登录、注册和账号设置中的 GitHub 登录/绑定展示，保留已有邮箱认证流程。
- API 非接口路径的回退跳转改为本站游戏入口。
- Service Worker 对 `/web` 使用网络请求，避免官网被当成游戏应用壳缓存。
- 官网页脚不展示本站源码链接，源码获取入口位于“开源项目关系”折叠说明中。

构建命令：`pnpm install --frozen-lockfile`，`pnpm run build`。运行时及包管理器版本以 package.json 和 docker/Dockerfile.app 为准。前端产物为 apps/web/dist，API 产物为 apps/api/dist。

`/web` 由 Nginx 静态站点提供；游戏路由继续使用 SPA 回退，`/api/` 继续反向代理至原 API 服务。此修改不包含数据库结构变更。

发布时将本仓库部署对应的源码归档放到 `/web/source/daoyou-source.tar.gz`，并将 LICENSE 复制到 `/web/LICENSE.txt`。源码归档不应包含 `.env`、私钥、数据库数据、访问令牌或生产日志。
