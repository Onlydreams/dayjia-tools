# AGENTS.md

> 作用范围：本文件所在目录及其子目录。

## 项目上下文

- 本仓库是 `tool.dayjia.com` 的静态工具站点。
- 根目录 `index.html` 是工具集合入口。
- 每个工具应放在独立子目录中，例如 `down-jacket-helper/`。
- 当前仓库没有 `package.json`、Vite 配置或源码目录；`down-jacket-helper/assets/` 中的文件是已构建的静态产物。

## 工作原则

- 默认使用简体中文沟通；代码、文件名、命令和技术术语可保留英文。
- 只做当前任务需要的最小改动，不主动重构、搬迁目录或引入新工具链。
- 不要覆盖或回退用户已有的未提交改动。
- 不要在仓库中写入密钥、Token、密码或真实环境变量值。
- 未经明确要求，不要修改本文件、全局规则或其他 agent 配置文件。

## 静态站点约定

- 保持 HTML 可直接静态托管，不依赖服务端逻辑。
- 保持中文页面使用 `lang="zh-CN"`。
- 页面标题、`meta description`、`canonical`、入口链接和可访问性标签要与实际工具内容一致。
- 根入口新增工具时，同步更新：
  - `index.html` 的工具列表；
  - `sitemap.xml` 的 URL 和 `lastmod`；
  - 必要时检查 `robots.txt`。
- 每个工具目录应可通过 `/工具目录名/` 直接访问。
- 避免引入外部 CDN、统计脚本、追踪脚本或第三方资源；确需引入时先说明原因和风险。

## 产物与源码

- 如果任务涉及 `down-jacket-helper/assets/` 这类构建产物，先确认是否有对应源码来源。
- 有源码时，优先改源码并重新生成产物。
- 没有源码且用户要求直接改当前仓库时，只做局部、可验证的静态产物修改，并在最终说明这一点。
- 不要无故改动带 hash 的资源文件名；如果文件名变更，必须同步更新引用它的 HTML。

## 验证

- 对 HTML、CSS、JS 改动，至少做静态检查：确认目标文件存在、引用路径正确、关键页面可打开。
- 如需本地预览，可在仓库根目录运行：

```bash
python3 -m http.server 8000
```

- 重点验证：
  - `http://localhost:8000/`
  - `http://localhost:8000/down-jacket-helper/`
- 如果无法运行本地服务或浏览器验证，最终回复中说明原因和剩余风险。

## Git 约定

- 修改前查看 `git status --short`，识别用户已有改动。
- 不使用 `git reset --hard`、`git checkout --` 等破坏性命令，除非用户明确要求。
- 提交信息保持简短明确，例如 `docs: add agent instructions` 或 `deploy: update tool entry`。
