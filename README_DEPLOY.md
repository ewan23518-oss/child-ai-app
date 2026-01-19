# 🚀 如何部署 AI 游乐场 (并生成手机 App)

想让这个 App 随时随地都能用，不用依赖家里的电脑？
最好的方法是把它部署到云端服务器 (**Vercel**)！

## 第一步：准备代码
1. 注册一个 [GitHub](https://github.com/) 账号（如果还没有）。
2. 在 GitHub 上创建一个新仓库，名字叫 `child-ai-app`。
3. 把你现在的代码上传到这个仓库（如果你不会用 Git 命令行，可以用 VS Code 左侧的 Source Control 按钮发布）。

## 第二步：部署到 Vercel (完全免费)
1. 访问 [Vercel](https://vercel.com/) 并用 GitHub 账号登录。
2. 点击 **"Add New..."** -> **"Project"**。
3. 在列表里找到刚才创建的 `child-ai-app`，点击 **"Import"**。
4. **关键步骤：配置环境变量 (Environment Variables)**
   在部署页面的 "Environment Variables" 区域，点击展开，添加以下变量：
   
   | Name | Value | 说明 |
   |Data|---|---|
   | `OPENAI_API_KEY` | `AIzaSy...` (你的 Key) | 必填 |
   | `OPENAI_BASE_URL` | `https://generativelanguage.googleapis.com/v1beta/openai/` | 必填 |
   | `OPENAI_MODEL` | `gemini-2.5-flash-lite` | 必填 |

   > **注意**：不要在 Vercel 上添加 `HTTPS_PROXY`，因为 Vercel 的服务器在国外，可以直接访问 Gemini API，不需要代理！

5. 点击 **"Deploy"** 按钮。
6. 等待约 1-2 分钟，屏幕上会放烟花 🎉，恭喜你部署成功！
7. 你会得到一个网址，比如 `https://child-ai-app-three.vercel.app`。

## 第三步：在手机上安装 (无需打包 APK)
现在的 Web 技术非常强大，你不需要专门打包 APK 也能像 App 一样使用。

1. **拿出手机**（安卓或 iPhone 都可以，不需要连家里的 Wi-Fi，用 4G/5G 也能上）。
2. 打开手机浏览器，访问刚才 Vercel 生成的网址。
3. **添加到桌面**：
   - **安卓 (Chrome)**: 点击右上角菜单 -> "添加到主屏幕" (Add to Home Screen)。
   - **iPhone (Safari)**: 点击底部分享按钮 -> "添加到主屏幕"。
4. 你的桌面上会出现一个紫色的 **"AI 游乐场"** 图标。
5. 点击它，它会全屏运行，看起来和原生 App 一模一样！

---

## 常见问题
**Q: 为什么不需要代理了？**
A: 因为 Vercel 的服务器在海外，它们访问 Google (Gemini) 的网络是通畅的。

**Q: 我的数据存在哪里？**
A: 目前版本的数据（关卡、故事）是直接写在代码里的 JSON 文件，部署上去就能用，非常稳定。

**Q: 真的不能打包成 APK 吗？**
A: 如果你一定要 APK 文件，可以使用在线工具（如 `web2apk`），把你的 Vercel 网址填进去，它会自动生成一个 APK 给你下载。但其实直接用“添加到主屏幕”体验更好，更新也更方便（你更新代码，手机上自动就更新了）。
