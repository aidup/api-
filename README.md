
# api-![Uploading 20248710233.jpg…]()

maccms影视api解析,资源采集api聚合搜索
# 视频搜索应用

这是一个基于 Vue.js 的视频搜索应用。用户可以通过选择 API 和输入关键词来搜索相关视频，并查看视频详情及播放链接。

## 功能

- 选择不同的视频 API 进行搜索
- 输入关键词进行视频搜索
- 显示视频列表及其详细信息
- 根据视频链接播放视频，包括 m3u8 格式的视频

## 目录结构

.
├── index.html # 主页面
├── api-config.json # API 配置文件
└── README.md # 项目说明文件

less
复制代码

## 使用方法

### 环境准备

1. 确保你已安装最新版本的 [Node.js](https://nodejs.org/) 和 [npm](https://www.npmjs.com/)。
2. 安装一个本地服务器，如 [http-server](https://www.npmjs.com/package/http-server)。

### 配置 API

在项目根目录下创建一个 `api-config.json` 文件，并按照以下格式配置：

```json
{
    "apis": [
        {
            "name": "飞速资源api",
            "list": "https://www.feisuzyapi.com/api.php/provide/vod/?ac=list",
            "detail": "https://www.feisuzyapi.com/api.php/provide/vod/?ac=detail"
        }
    ],
    "m3u8ParserUrl": "你的m3u8解析器地址"
}

运行项目
在项目根目录下运行本地服务器：
bash
复制代码
http-server .
打开浏览器并访问 http://localhost:8080（端口号可能会根据你的本地服务器配置有所不同）。
使用步骤
选择一个 API。
输入关键词进行搜索。
查看搜索结果，点击播放按钮播放视频。
代码说明
HTML 和 CSS
index.html 包含了基本的页面布局和样式。样式采用了简单的设计，以确保清晰和易用性。

JavaScript 和 Vue.js
页面使用 Vue.js 进行开发，主要功能包括：

组件化开发：使用 Vue 组件来实现视频详情和播放按钮的独立化。
API 请求：通过 fetch 方法请求 API，获取视频列表和详情数据。
错误处理：在 API 请求失败时进行错误处理并提示用户。
播放视频：处理不同格式的视频播放链接，特别是 m3u8 格式。
主要 Vue 组件
VideoDetails 组件
用于显示视频详情和播放按钮。

vue
复制代码
Vue.component('VideoDetails', {
    props: ['video', 'm3u8ParserUrl'],
    template: `
        <div class="video-details" v-if="video.details">
            <img :src="video.details.vod_pic" alt="视频图片">
            <div class="video-info">
                <p><strong>简介:</strong> {{ video.details.vod_content }}</p>
                <p><strong>类型:</strong> {{ video.details.type_name }}</p>
                <p><strong>年份:</strong> {{ video.details.vod_year }}</p>
                <p><strong>更新时间:</strong> {{ video.details.vod_time }}</p>
                <div class="play-button">
                    <button v-if="!video.playUrls || video.playUrls.length === 0">播放</button>
                    <button v-for="(url, index) in video.playUrls" :key="index" @click="$emit('playVideo', url)">
                        {{ video.playUrls.length === 1 ? '播放' : `第${index + 1}集` }}
                    </button>
                </div>
            </div>
        </div>
    `
});
app 实例
包含了搜索视频、获取视频详情和播放视频的主要逻辑。

vue
复制代码
new Vue({
    el: '#app',
    data: {
        keyword: '',
        videos: [],
        loading: false,
        selectedApi: '',
        apiList: [],
        apis: {},
        m3u8ParserUrl: ''
    },
    async created() {
        // 加载 JSON 配置文件
    },
    methods: {
        async searchVideos() {
            // 搜索视频
        },
        async fetchAllVideoDetails() {
            // 获取视频详情
        },
        parsePlayUrls(playUrl) {
            // 解析播放链接
        },
        playVideo(url) {
            // 播放视频
        },
        isM3u8Url(url) {
            // 判断是否为 m3u8 链接
        }
    }
});
注意事项
确保 api-config.json 文件配置正确，特别是 API 地址和 m3u8 解析器地址。
本地运行时，请确保浏览器允许跨域请求，或使用类似 cors-anywhere 的工具。
贡献
欢迎提出建议和反馈！如有任何问题，请提交 issue 或 pull request。

许可证
本项目基于 MIT 许可证开源。
