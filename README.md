# 逃逸光点 / DRIFT

一个纯视觉、无依赖的互动解压页面。光点沿斜线持续向左上方飞行，点击、长按或按住空格会触发加速与连续音爆。

## 交互

- 左键 / 右键任意位置：触发一次脉冲加速与音爆，并从光点飘出一句短句。
- 长按左键 / 右键：进入持续过载，速度持续爬升并不断生成音爆环；光标周围会出现蓄力环，满格后显示 `MAX`。
- 空格键：单击或按住空格，效果与鼠标一致。
- 移动端：轻触触发脉冲，长按进入持续过载；长按不会选中页面内容。
- 无操作：页面会自动出现音爆环，并偶尔进行一次缓加速。

## 本地预览

直接双击 `index.html` 即可。也可以启动一个静态服务器：

```bash
python -m http.server 8000
```

然后访问 `http://localhost:8000`。

## 发布到 GitHub Pages

页面没有构建步骤，`index.html` 就是最终产物，且所有样式和脚本都内联在文件中。

1. 在 GitHub 新建一个仓库，不要初始化 README。
2. 在当前目录关联远程仓库并推送：

```bash
git remote add origin https://github.com/<你的用户名>/<仓库名>.git
git push -u origin main
```

也可以使用 GitHub CLI 创建并推送：

```bash
gh repo create <仓库名> --public --source=. --remote=origin --push
```

3. 打开仓库的 **Settings → Pages**，在 **Build and deployment** 中选择：

- Source：`Deploy from a branch`
- Branch：`main`
- Folder：`/ (root)`

保存后等待 1–2 分钟，访问：

```text
https://<你的用户名>.github.io/<仓库名>/
```

如果仓库名是 `<你的用户名>.github.io`，则访问地址为：

```text
https://<你的用户名>.github.io/
```

## 文件说明

- `index.html`：完整页面，包含 Canvas 动画、样式和交互逻辑。
- `.nojekyll`：关闭 GitHub Pages 的 Jekyll 处理。
- `preview-*.png`：仅供本地预览，已通过 `.gitignore` 排除，不会进入仓库。
