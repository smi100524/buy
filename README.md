# 食堂采购系统（GitHub 部署版）

一个单文件网页版食堂采购系统：每日采购表、台账、统计、Excel 导出，已内置 **2026 年 6 月真实数据**。
打开后需要输入**访问密码**才能使用；第一次输入后**本机免密**，之后直接进入。

## 默认密码
- **默认访问密码：`123456`**
- 上线后请立即在「系统设置 → 访问密码」中修改（输入当前密码 + 新密码即可）

## 一、部署到 GitHub Pages（网页上传方式，最简单）
1. 登录 [github.com](https://github.com)，点右上角 **+ → New repository**
   - Repository name 随意（如 `canteen`），选 **Public**（公开）或 Private（私有，仍可开 Pages）
   - 直接 **Create repository**
2. 进入新仓库 → 点 **Add file → Upload files**
   - 把本文件夹里的 `index.html`、`README.md` 拖进去
   - 再点 **Add file → Upload files**，把 `.github` 文件夹也拖进去（里面有自动发布脚本，非必需）
   - 点 **Commit changes**
3. 仓库 **Settings → Pages**（左侧菜单）
   - Source 选择 **Deploy from a branch**
   - Branch 选 `main`，目录选 `/ (root)`，点 **Save**
4. 等待 1~2 分钟，访问：
   `https://你的用户名.github.io/仓库名/`
   （例如用户名 `zhangsan`、仓库 `canteen` → `https://zhangsan.github.io/canteen/`）

> 有 Git 基础的话，也可以把整个文件夹 `git push` 到仓库，仓库里的 `.github/workflows/deploy.yml` 会自动帮你发布到 Pages。

## 二、使用说明
- 打开网址 → 输入密码 `123456`（可勾选"记住本机"）→ 进入系统
- 「每日采购表」：选日期 + 职员/员工，顶部数据环比，下方明细可增删改，支持导出当日 Excel
- 「采购台账 / 统计报表 / 食材库 / 系统设置」：查看与管理
- 点顶栏「🔒」可随时锁屏

## 三、重要说明（请务必了解）
1. **密码属于"前端限制"**：代码里用 SHA-256 校验密码，适合内部使用、防止误操作。
   GitHub Pages 是纯静态托管，网页源代码公开可见，无法做到银行级安全。如需更强安全，需要服务端。
2. **数据保存在访问者的浏览器里**（localStorage）：
   - 同一台电脑、同一个浏览器：输一次密码即免密，录入的数据会保留
   - 换电脑 / 换浏览器 / 清除浏览器数据：各自独立，看不到另一台录入的数据
3. **"同一 IP 免密 + 多台电脑共享同一份数据"** 需要一个小服务器（服务端记录 IP 并存放公共数据）。
   如果您需要这个效果（例如食堂里多台电脑同时用、数据互通），告诉我，我可以再做一版"服务版"部署方案（可免费托管在 Render/Railway 等平台）。