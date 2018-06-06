# music-api
- 对网易云、虾米音乐、QQ音乐统一封装
- 绝大部分来源于[Binaryify/NeteaseCloudMusicApi](https://github.com/Binaryify/NeteaseCloudMusicApi)和[LIU9293/musicAPI](https://github.com/LIU9293/musicAPI)等
- Node >= 6
- 支持[安卓/ios](https://github.com/sunzongzheng/musicApi/blob/master/dist/app.native.js)通过Fly调用，详见[Fly文档](https://wendux.github.io/dist/#/doc/flyio/native)

# Api列表
- 歌曲搜索
````js
function searchSong( keyword='关键字',offset='偏移页数' ) {
    return {
        status:Boolean, // 请求是否成功
        data:{
            netease: Object,
            qq: Object,
            xiami: Object
        }
    }
}
````
- 歌曲url
````js
function getSongUrl( vendor='歌曲来源',id='歌曲id' ) {
    return {
        status: Boolean, // 请求是否成功
        data: {
            url:'歌曲地址'
        }
    }
}
````
- 歌曲歌词
````js
function getLyric( vendor='歌曲来源',id='歌曲id' ) {
    return {
        status: Boolean, // 请求是否成功
        data: Array, // 歌词数组
    }
}
````
- 歌曲评论

**由于网易云、QQ音乐的`评论逻辑不一样`，`hotComments`及`comments`没有进行强封装**
````js
function getComment( vendor='歌曲来源',id='歌曲id',offset='偏移页数',limit='页大小' ) {
    return {
        status: Boolean, // 请求是否成功
        data: {
            hotComments: Array, // 热评
            comments: Array, // 所有评论
            total: Number, //评论总数
        }
    }
}
````
- 歌曲详情

````js
function getSongDetail( vendor='歌曲来源',id='歌曲id' ) {
    return {
        status: Boolean, // 请求是否成功
        data: {
            album: {
                id: Number | String,
                name: String,
                cover: String
            },
            artists: Array,
            name: String,
            id: Number | String,
            commentId: Number | String,
            cp: Boolean
        }
    }
}
````
- 批量获取歌曲详情

````js
function getBatchSongDetail( vendor='歌曲来源',ids='歌曲id数组' ) {
    return {
        status: Boolean, // 请求是否成功
        data: [{
            album: {
                id: Number | String,
                name: String,
                cover: String
            },
            artists: Array,
            name: String,
            id: Number | String,
            commentId: Number | String,
            cp: Boolean
        }]
    }
}
````