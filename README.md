# 口算100题 · 小学1-3年级数学口算练习工具

> 永久免费、无广告、零依赖的单文件 HTML 工具。打开即用，无需下载安装。

## 这是什么

一个面向中国小学 1-3 年级学生家长的口算练习工具。100 道加减乘除随机出题，自动批改、错题订正循环、A4 打印、历史记录全都有。一份 HTML 文件搞定全部功能，可以本地打开，也可以部署到 GitHub Pages 免费让全网访问。

## 包含的文件

| 文件 | 说明 |
|------|------|
| `index.html` | 产品落地页（中文，家长视角，含赞赏码占位） |
| `math-practice.html` | 核心工具：100 道口算练习（不要修改） |
| `gomoku.html` | 五子棋小游戏（赠品引流用，不要修改） |
| `timer.html` | 倒计时工具（赠品引流用，不要修改） |
| `README.md` | 本文件 |
| `小红书引流文案.md` | 5 条小红书种草文案 |
| `变现方案.md` | 变现路径分析 |

## 核心功能

- 🎲 **随机出题** — 每次练习都是全新 100 题，加/减/乘/除各 25 道打乱顺序
- ✅ **自动批改** — 提交即出：正确数 / 错误数 / 未答数 / 得分 / 用时
- 📝 **错题订正循环** — 自动收集错题进入订正区，做对为止，可多轮订正
- 🖨️ **A4 一键打印** — 专门优化打印样式，隐藏按钮，一页整齐 100 题
- 📚 **历史记录** — 自动保存最近 20 次练习成绩、用时、错题详情（localStorage）
- 📡 **离线可用** — 纯网页，无需注册、无需安装、断网也能用

## 题目难度范围

| 运算 | 范围 | 说明 |
|------|------|------|
| 加法 | 100-999 + 100-999 | 结果不超 1000 |
| 减法 | 200-999 - 100-? | 不出现负数 |
| 乘法 | 100-999 × 2-9 | 结果不超 1000 |
| 除法 | ? ÷ 2-9 | 结果整除，11-499 |

适合小学 1-3 年级。

## 本地使用

直接双击 `index.html` 或 `math-practice.html` 用浏览器打开即可，无需任何环境。

## 部署到 GitHub Pages（免费上线）

让全网家长通过一个网址访问你的工具，全程免费。

### 前置准备

1. 注册 GitHub 账号（[github.com](https://github.com)）
2. 安装 Git 和 GitHub CLI（`gh`）
   - Windows 下载：[git-scm.com](https://git-scm.com)、[cli.github.com](https://cli.github.com)
3. 在终端登录 GitHub：
   ```bash
   gh auth login
   ```
   按提示选 `GitHub.com` → `HTTPS` → `Login with a web browser`，浏览器授权即可。

### 部署步骤

```bash
# 1. 进入项目目录
cd D:/开发/earn/edu-tools-kit

# 2. 初始化 git 仓库
git init
git add .
git commit -m "初始化：口算100题工具包"

# 3. 在 GitHub 创建公开仓库并推送（仓库名随意，比如 math-practice）
gh repo create math-practice --public --source=. --push

# 4. 开启 GitHub Pages（用 main 分支根目录作为页面源）
# 方法一：gh CLI（推荐）
gh api -X POST /repos/{owner}/math-practice/pages \
  -f "source[branch]=main" -f "source[path]=/"

# 方法二：网页操作
# 打开 https://github.com/你的用户名/math-practice/settings/pages
# Source 选 "Deploy from a branch"，Branch 选 main / root，Save
```

### 访问地址

部署成功后（一般 1-2 分钟），访问：

```
https://你的用户名.github.io/math-practice/
```

落地页会自动加载，点「立即练习」即可进入工具页。

### 更新内容

以后改了代码，只需要：

```bash
git add .
git commit -m "更新说明"
git push
```

GitHub Pages 会自动重新部署，1-2 分钟后访问到的就是最新版。

## 替换赞赏码（重要）

落地页 `index.html` 的「支持作者」区目前是占位符。要真正收赞赏，需要：

1. **微信**：打开「微信 → 我 → 服务 → 收付款 → 二维码收款」，截图保存为 `wechat-qr.jpg`，放到 `edu-tools-kit/` 目录
2. **支付宝**：打开「支付宝 → 收钱码」，截图保存为 `alipay-qr.jpg`
3. 编辑 `index.html`，找到这段注释：
   ```html
   <!-- ★★★ 赞赏码位置：用户需替换为真实收款码 ★★★ -->
   ```
   把下面的占位 `<div class="donate-code-img">...</div>` 替换为：
   ```html
   <img src="wechat-qr.jpg" alt="微信赞赏码"
        style="width:180px;height:180px;border-radius:12px;">
   ```
4. 重新 push 即可生效。

不想收赞赏就整段 `.donate-codes` 删掉，不影响其他功能。

## 替换 GitHub 链接

`index.html` 底部 footer 的 GitHub 链接目前是占位的 `https://github.com`。部署后改成你自己的仓库地址：

```html
<a href="https://github.com/你的用户名/math-practice" ...>GitHub 源码</a>
```

## 关于变现

详见 [`变现方案.md`](./变现方案.md)。简要推荐路径：

1. **首要**：小红书发种草笔记引流 → 落地页免费试用 → 赞赏码收红包（最低门槛，AI 可全自动）
2. **进阶**：闲鱼挂"可定制版口算练习工具"卖 5-15 元（需你提供闲鱼账号）
3. **规模化**：给家教/培训机构批量授权（需主动 BD，单价 50-200 元）

## 技术栈

- 纯 HTML + CSS + 原生 JavaScript
- 零依赖、零框架、零打包工具
- 单文件可直接打开，无需服务器
- localStorage 持久化历史记录

## 免责声明

- 本工具仅供学习交流使用
- 不收集任何用户数据，所有数据存于本地浏览器
- 不保证题目 100% 准确，请家长陪同使用
- 完全开源，可自由修改、分发

## License

MIT
