# mmPlayer

模仿 QQ 音乐网页版界面，采用 `flexbox` 和 `position` 布局；
mmPlayer 虽然是响应式，但主要以 PC 端为主，移动端只做相应适配；


> api：一个开源的[网易云音乐 NodeJS 版 API](https://binaryify.github.io/NeteaseCloudMusicApi)（有 api 才有动力写！！！）
>
> [在线演示地址](https://netease-music.fe-mm.com/)
>
> [React 移动端版本（高仿网易云音乐）](https://github.com/maomao1996/react-music)
>


## 免责声明

本站音频文件来自各网站接口

音频版权来自各网站，本站只提供数据查询服务，不提供任何音频存储和贩卖服务

本项目仅为前端练手项目，请勿用作商业用途，请勿通过本项目下载盗版歌曲资源，否则后果自负！

## 安装与使用

### 检查 node 版本

```sh
# 查看 node 版本，确保 node 版本高于 12 版本
node -v
```

[Node.js 中文网](http://nodejs.cn/)

### mmPlayer

```sh
# 下载 mmPlayer
git clone https://github.com/maomao1996/Vue-mmPlayer

# 进入 mmPlayer 播放器目录
cd Vue-mmPlayer

# 安装依赖 推荐使用 yarn
npm install

# 本地运行 mmPlayer
npm run serve

# 编译打包
npm run build
```

### 后台 api 服务（本地开发）

[网易云音乐 NodeJS 版 API](https://binaryify.github.io/NeteaseCloudMusicApi)

```sh
# 下载 NeteaseCloudMusicApi
git clone --depth=1 https://github.com/Binaryify/NeteaseCloudMusicApi

# 进入 NeteaseCloudMusicApi 后台服务目录
cd NeteaseCloudMusicApi

# 安装依赖
npm install

# 运行后台 api 服务 访问 http://localhost:3000
node app.js
```

### 注意点

**运行 mmPlayer 后无法获取音乐请检查后台 `api` 服务是否启动(即控制台请求报 404)**

**线上部署不是直接将整个项目丢到服务器，再去运行 `npm run serve` 命令**

**项目打包前 `VUE_APP_BASE_API_URL` 必须改后台 `api` 服务地址为线上地址，不能是本地地址**

### 关于项目线上部署

最近有不少小伙伴部署出了问题，我在这说明下

- 后台 `api` 服务线上部署

  - 你需要将 [NeteaseCloudMusicApi](https://binaryify.github.io/NeteaseCloudMusicApi) 下载
  - 然后将下载的文件上传至服务器
  - 再通过 `pm2` 去启动服务(`pm2` 安装和相关命令网上有很多，这里不再赘述)
  - 最后通过服务器 `ip` + 端口号访问验证 `api` 服务是否启动成功

- `mmPlayer` 线上部署

  - 首先要注意的是
  - 先将 `.env` 文件的 `VUE_APP_BASE_API_URL` 修改成上一步启动的后台 `api` 服务地址(服务器 `ip` + 端口号或者你绑定的域名)
  - 然后先在本地运行 `npm run build` 命令，会打包在生成一个 `dist` 文件
  - 最后将打包的 `dist` 文件上传到你的网站服务器目录即可


## 技术栈

- [Vue Cli（Vue 脚手架工具）](https://cli.vuejs.org/zh/)
- [Vue（核心框架）](https://cn.vuejs.org/)
- [Vue Router（页面路由）](https://router.vuejs.org/zh/)
- [Vuex（状态管理）](https://vuex.vuejs.org/zh/)
- ES 6 / 7 （JavaScript 语言的下一代标准）
- Less（CSS 预处理器）
- Axios（网络请求）
- FastClick（解决移动端 300ms 点击延迟）

## 项目结构目录图（使用 tree 生成）

<details>
<summary>展开查看</summary>
<pre><code>
├── public                                          // 静态资源目录
│   └─index.html                                    // 入口 html 文件
├── screenshots                                     // 项目截图
├── src                                             // 项目源码目录
│   ├── api                                         // 数据交互目录
│   │   └── index.js                                // 获取数据
│   ├── assets                                      // 资源目录
│   │   └── background                              // 启动背景图目录
│   │   └── img                                     // 静态图片目录
│   ├── base                                        // 公共基础组件目录
│   │   ├── mm-dialog
│   │   │   └── mm-dialog.vue                       // 对话框组件
│   │   ├── mm-icon
│   │   │   └── mm-icon.vue                         // icon 组件
│   │   ├── mm-loading
│   │   │   └── mm-loading.vue                      // 加载动画组件
│   │   ├── mm-no-result
│   │   │   └── mm-no-result.vue                    // 暂无数据提示组件
│   │   ├── mm-progress
│   │   │   └── mm-progress.vue                     // 进度条拖动组件
│   │   └── mm-toast
│   │        ├── index.js                           // mm-toast 组件插件化配置
│   │        └── mm-toast.vue                       // 弹出层提示组件
│   ├── components                                  // 公共项目组件目录
│   │   ├── lyric
│   │   │   └── lyric                               // 歌词和封面组件
│   │   └── mm-header
│   │   │   └── mm-header.vue                       // 头部组件
│   │   ├── music-btn
│   │   │   └── music-btn.vue                       // 按钮组件
│   │   ├── music-list
│   │   │    └── music-list.vue                     // 列表组件
│   │   └── volume
│   │        └── volume.vue                         // 音量控制组件
│   ├── pages                                       // 页面组件目录
│   │   ├── comment
│   │   │   └── comment.vue                         // 评论
│   │   ├── details
│   │   │   └── details.vue                         // 排行榜详情
│   │   ├── historyList
│   │   │   └── historyList.vue                     // 我听过的（播放历史）
│   │   ├── playList
│   │   │   └── playList.vue                        // 正在播放
│   │   ├── search
│   │   │   └── search.vue                          // 搜索
│   │   ├── topList
│   │   │   └── topList.vue                         // 排行榜页面
│   │   ├── userList
│   │   │   └── userList.vue                        // 我的歌单
│   │   ├── mmPlayer.js                             // 播放器事相关件绑定
│   │   └── music.vue                               // 播放器主页面
│   ├── router
│   │   └── index.js                                // 路由配置
│   ├── store                                       // vuex 的状态管理
│   │   ├── actions.js                              // 配置 actions
│   │   ├── getters.js                              // 配置 getters
│   │   ├── index.js                                // 引用 vuex，创建 store
│   │   ├── mutation-types.js                       // 定义常量 mutations 名
│   │   ├── mutations.js                            // 配置 mutations
│   │   └── state.js                                // 配置 state
│   ├── styles                                      // 样式文件目录
│   │   ├── index.less                              // mmPlayer 相关基础样式
│   │   ├── mixin.less                              // 样式混合
│   │   ├── reset.less                              // 样式重置
│   │   └── var.less                                // 样式变量（字体大小、字体颜色、背景颜色）
│   ├── js                                          // 数据交互目录
│   │   ├── hack.js                                 // 修改 nextTick
│   │   ├── mixin.js                                // 组件混合
│   │   ├── song.js                                 // 数据处理
│   │   ├── storage.js                              // localStorage 配置
│   │   └── util.js                                 // 公用 js 方法
│   ├── App.vue                                     // 根组件
│   ├── config.js                                   // 基本配置
│   └── main.js                                     // 入口主文件
└── vue.config.js                                   // vue-cli 配置文件

</code></pre>

</details>

## 功能

- 播放器
- 快捷键操作
- 歌词滚动
- 正在播放
- 排行榜
- 歌单详情
- 搜索
- 播放历史
- 查看评论
- 同步网易云歌单

<details>
<summary>点击查看</summary>

### PC

#### 正在播放

![正在播放](https://cdn.jsdelivr.net/gh/maomao1996/Vue-mmPlayer/screenshots/1.jpg)

#### 排行榜

![排行榜](https://cdn.jsdelivr.net/gh/maomao1996/Vue-mmPlayer/screenshots/2.jpg)

#### 搜索

![搜索](https://cdn.jsdelivr.net/gh/maomao1996/Vue-mmPlayer/screenshots/3.jpg)

#### 我的歌单

![我的歌单](https://cdn.jsdelivr.net/gh/maomao1996/Vue-mmPlayer/screenshots/4.jpg)

#### 我听过的

![我听过的](https://cdn.jsdelivr.net/gh/maomao1996/Vue-mmPlayer/screenshots/5.jpg)

#### 歌曲评论

![歌曲评论](https://cdn.jsdelivr.net/gh/maomao1996/Vue-mmPlayer/screenshots/6.jpg)

### 移动端

![移动端一](https://cdn.jsdelivr.net/gh/maomao1996/Vue-mmPlayer/screenshots/7.jpg)
![移动端二](https://cdn.jsdelivr.net/gh/maomao1996/Vue-mmPlayer/screenshots/8.jpg)


## 其他说明
## 重点重点
- 个人练手项目！！！！！！！！！
- 如果您喜欢该作品，请到[maomao1996](https://github.com/maomao1996) 进行支持或关注，本人只负责练手。
- 如有问题请直接在 [Issues](https://github.com/maomao1996/Vue-mmPlayer/issues/new) 中提，或者您发现问题并有非常好的解决方案，欢迎 PR

## 鸣谢

特别感谢 [JetBrains](https://www.jetbrains.com/) 为开源项目提供免费的 [WebStorm](https://www.jetbrains.com/webstorm/) 授权

## License

[MIT](https://github.com/maomao1996/Vue-mmPlayer/blob/LICENSE)
