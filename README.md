# florr 复刻版（静态站点 / GitHub Pages）

这个文件夹就是可以部署的站点：index.html 在根目录，贴图在 textures/。

## 首次部署到 GitHub Pages

1. 在 GitHub 新建仓库（Public；不要勾选自动生成 README/.gitignore，保持空仓库）。
2. 在**本目录**（deploy）执行（把地址换成你自己的仓库）：

   git remote add origin https://github.com/<用户名>/<仓库名>.git
   git branch -M main
   git push -u origin main

   第一次推送会弹窗让你登录 GitHub（或用 Personal Access Token 当密码）。

3. 仓库 Settings → Pages：Source 选 Deploy from a branch，Branch 选 main、目录选 /(root)，Save。
4. 等 1 分钟左右访问：https://<用户名>.github.io/<仓库名>/

## 以后更新

在上一级目录运行 打包部署.ps1 重新生成站点，然后：

   git add -A
   git commit -m "update"
   git push

GitHub Pages 会自动重新发布，1 分钟左右生效。贴图带了版本号 ?v=，不用怕玩家看到旧图。

## 注意

- 必须带上 textures/：少了它所有贴图 404，游戏会退回代码画的形状。
- .nojekyll 要一起提交，否则 GitHub Pages 会走 Jekyll 处理。
- 玩家进度/账号/自定义地图存在浏览器 localStorage 里，按域名隔离：换域名或换设备不通用，玩家各存各的。
- 部署是纯静态的：不需要后端、不需要构建、不需要 Node。
