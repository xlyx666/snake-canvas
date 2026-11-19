# 贪吃蛇 · Snake

一个零依赖的经典贪吃蛇小游戏，用原生 HTML + Canvas + JavaScript 写成，单文件即可运行。

![snake](https://img.shields.io/badge/build-none-brightgreen) ![snake](https://img.shields.io/badge/dependencies-0-blue) ![snake](https://img.shields.io/badge/license-MIT-orange)

## 在线试玩

直接打开 `index.html` 即可，或部署到 GitHub Pages（见下方）。

## 玩法

| 操作 | 按键 |
| --- | --- |
| 转向 | `↑` `↓` `←` `→` 或 `W` `A` `S` `D` |
| 暂停 / 继续 | `空格` |
| 开始 / 重开 | `Enter`，或点击画面中央按钮 |
| 手机 | 在棋盘上滑动，或使用右侧方向键 |

吃到食物得 10 分。撞墙或撞到自己即结束。

## 特性

- 20 × 20 网格，圆角分段蛇身，尾部渐隐，便于辨认走位
- 蛇头带朝向眼睛，食物带呼吸光晕
- 跟随系统深色模式自动换配色
- 速度三档（慢 / 标准 / 快），游戏中可随时切换
- 转向指令队列（最多缓存 2 个方向），快速连按不丢操作
- 禁止 180° 反向，判断依据为「队列最后一个待执行方向」
- 蛇尾所在格按「即将移开」处理，贴尾行走不误判死亡
- `requestAnimationFrame` + 时间累加器驱动，切后台回来不会连跳
- 按 `devicePixelRatio` 放大画布（上限 2×），高分屏不模糊
- 响应式布局，窄屏自动缩放不裁切

## 本地运行

直接双击 `index.html` 即可，无需服务器。

如需本地起服务：

```bash
python3 -m http.server 8000
# 打开 http://localhost:8000
```

## 目录结构

```
.
├── index.html          # 游戏本体，单文件
├── README.md
├── LICENSE
├── .gitignore
└── .nojekyll           # 阻止 GitHub Pages 走 Jekyll 处理
```

## 部署到 GitHub Pages

1. 把仓库推送到 GitHub。
2. 进入仓库 **Settings → Pages**。
3. **Build and deployment → Source** 选择 `Deploy from a branch`。
4. Branch 选 `main`，目录选 `/ (root)`，保存。
5. 等待约一分钟，访问 `https://<你的用户名>.github.io/<仓库名>/`。

## 自定义

想调难度，改 `index.html` 里 `<button class="pill" data-speed>` 的数值即可，单位是毫秒，数字越小越快：

```html
<button class="pill" type="button" data-speed="80">快</button>
```

想改棋盘大小，改脚本开头的常量：

```js
var COLS = 20, ROWS = 20;
```

## License

[MIT](LICENSE)
