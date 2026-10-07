# 币安合约仓位一键查询（GitHub Pages 静态版）

纯静态网页，**不需要任何后端/本地服务**，浏览器直接调用币安接口（币安 API 已开放跨域 CORS）。

## 文件说明

| 文件 | 用途 |
|---|---|
| `index.html` | 网页本体（单文件自包含，可独立部署） |
| `README.md` | 本说明 |

> 目录下的 `_shots/` 是本地自检生成的截图，**不要上传**，只需上传 `index.html` 和 `README.md` 两个文件。

## 部署到 GitHub Pages

1. 登录 GitHub，新建一个仓库（建议**私有仓库**，虽然本页不含密钥，但保持私有更稳妥）。
2. 把 `index.html` 上传到仓库根目录（Settings → 你的仓库 → Code → upload files，或直接 push）。
3. 仓库 **Settings → Pages** → Source 选 `Deploy from a branch` → 分支选 `main`，目录选 `/ (root)` → Save。
4. 等 1～2 分钟，访问 `https://你的用户名.github.io/仓库名/` 即可使用。

> 也可以把 `index.html` 改名为 `index.html` 放在 `docs/` 目录，Pages 的目录选 `/docs`，两种方式任选其一。

## 使用步骤

1. 打开页面，点击右上角「**设置**」。
2. 填入 6 个账户（主账户 + 子账户1~5）的 **API Key / API Secret**（可只填你有密钥的账户，其他留空）。
3. 保存后点「**一键获取**」，即可看到各账户合约持仓（盈利绿 / 亏损红，按基础币跨账户对齐）。
4. 「导出 Excel」生成 `.xlsx`；勾选「获取后自动下载 Excel」可在每次获取后自动导出。

## 密钥安全（重要）

- 密钥**只保存在你本机浏览器的 localStorage**，不会写入本仓库、不会上传到 GitHub。
- 换电脑 / 换浏览器 / 清除浏览器数据后，需要重新在「设置」里填写一次。
- 不要为了省事把密钥**直接写进 index.html** 再上传——那样仓库公开时密钥就泄露了。
- 建议在币安给 API 开启 **IP 白名单**、权限只勾选「**读取**」（Enable Reading），不要开提现/交易权限。

## 使用前提

- 需要能访问 `fapi.binance.com` / `dapi.binance.com`。国内网络若无法直连，请在**浏览器或系统层面**开启代理（如 Clash）后再打开页面。
- 推荐使用最新版 Chrome / Edge（依赖浏览器内置的 WebCrypto 做 HMAC 签名）。

## 与本地服务版的区别

- 本版是纯静态：无本地服务、无 config.json，密钥存浏览器。
- 筛选列表（大宗商品/主流币/山寨币）已**内置**在页面中，修改筛选 = 修改 `index.html` 里的 `FILTER_SYMBOLS`，保存后重新上传即可。
- 交易对筛选、两段式表格、红绿盈亏、Excel 导出等交互与本地版一致。
