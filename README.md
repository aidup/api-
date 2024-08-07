![](https://github.com/aidup/api-/blob/main/20248710233.jpg?raw=true)
# api-maccms影视api解析,资源采集api聚合搜索
# 视频搜索应用

用户可以通过选择 API 和输入关键词来搜索相关视频，并查看视频详情及播放链接

## 功能

- 选择不同的视频 API 进行搜索
- 输入关键词进行视频搜索
- 显示视频列表及其详细信息
- 根据视频链接播放视频，包括 m3u8 格式的视频

## 目录结构


├── index.html # 主页面

├── api-config.json # API 配置文件

└── README.md # 项目说明文件


## 使用方法

### 环境准备

纯html+css+js,没什么好说的

### 配置 API

在项目根目录下创建一个 `api-config.json` 文件，并按照以下格式配置：

```json
{
    "apis": [
        {
            "name": "飞速资源api",
            "list": "采集maccms域名/api.php/provide/vod/?ac=list",
            "detail": "采集maccms域名://www.feisuzyapi.com/api.php/provide/vod/?ac=detail"
        }
    ],
    "m3u8ParserUrl": "你的m3u8解析器地址"
}
```

server.js用来解决跨域,不需要可以无视


