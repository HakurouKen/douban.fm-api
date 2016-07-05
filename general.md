# General API

<a name="get_captcha_id"></a>
## Get Captcha id
### Request
` GET: /j/new_captcha `
### Parameters
None.
### Response
The captcha id.
### Example
**Request**
```
	GET: /j/new_captcha
```
**Response**
```
	"f002Un7LjuEW29TOGGRR4han:en"
```


<a name="get_captcha"></a>
## Get Captcha (获取验证码)
### Request
` GET: /misc/captcha `
### Parameters
* *size*
	- *s*: small (250x40)
	- *m*: medium (220x40) // shouldn't it larger than s ???
	- *l*: large (400x60)
* *id*: the id get from new_captcha

### Response
A captcha image


<a name="get_form"></a>
## Get Form (请求表单html)
Get the html code of login form.
### Request
` GET: /j/misc/login_form `
### Parameters
None.
### Response
The html code of login form.


<a name="login"></a>
## Login (登录)
### Request
` POST: /j/login `
### Parameters
* *source*: value `radio`
* *alias*: the e-mail of your douban account
* *form\_password*: the password of your douban account
* *captcha\_solution*: the captcha you input
* *captcha\_id*: the captcha id get from `/j/new_captcha`
* *task*: value `sync_channel_list` ,use to sync the playlist
* *remember*
	- *on*： remember
	- *undefined*: do not remember

### Response
* Success:
	* *r*: value `0` , represent for succeed
	* *user\_info*: the user info details
* Fail:
	* *err\_msg*: the error message
	* *err\_no*: the error number
	* *r*: value `1` , represent for failed


<a name="hot_channels"></a>
## Hot Channels (热门兆赫)
Get the hot channels.
### Request
` GET: /j/explore/hot_channels `
### Parameters
None.
#### Response
The hot channel's list.


<a name="up_trending_channels"></a>
## Up Trending Channels (上升最快兆赫)
### Request
` GET: /j/explore/up_trending_channels `
### Parameters
None.
### Response
The up trending channel's list.


<a name="search_channel"></a>
## Search Channel (搜索兆赫)
Search the channel by keywords.
### Request
` GET: /j/explore/search `
### Parameters
* *query*: The key word you want to search by.
* *start(optional)*: the start of the channel result, default value is `0`
* *limit(optional)*: limit the number of the channels, default value is `20`

### Response
The channels array.
### Example
**Request**
```
	GET: /j/explore/search?query=linkin%20park
```
**Response**
```javascript
	{
	    status: true,
	    data: {
	        channels: [{
	            intro: "为你推荐 Linkin Park 以及相似的艺术家",
	            name: "Linkin Park 系",
	            song_num: 0,
	            creator: {
	                url: "http://site.douban.com/douban.fm/",
	                name: "豆瓣FM",
	                id: 1
	            },
	            banner: "http://img3.douban.com/img/fmadmin/chlBanner/19135.jpg",
	            cover: "http://img3.douban.com/img/fmadmin/icon/19135.jpg",
	            id: 28202,
	            hot_songs: [
	                "New Divide (8-Bit)",
	                "Where'd You Go (feat. Holly Brook And Jonah Matranga)",
	                "Iridescent"
	            ]
	        }, {
	            intro: "Linkin Park是一组来自加利福尼亚州洛杉矶的歌唱组合兼流行摇滚乐团，也被认为是新金属中最成功的乐团。",
	            name: "林肯公园LP",
	            song_num: 84,
	            creator: {
	                url: "http://www.douban.com/people/ckMac/",
	                name: "ckMac陈萌调",
	                id: 55700577
	            },
	            banner: "http://img5.douban.com/img/fmadmin/chlBanner/26019.jpg",
	            cover: "http://img5.douban.com/img/fmadmin/icon/26019.jpg",
	            id: 1005150,
	            hot_songs: [
	                "New Divide",
	                "What I've Done",
	                "Burn It Down"
	            ]
	        }],
	        total: 1
	    }
	}
```	 


<a name="genre"></a>
## Genre (歌曲类型筛选)
Get channels by the genre.
### Request
` GET /j/explore/genre `
### Parameters
* *gid*: the id of the channel genre
* *start(optional)*: the start of the channel result, default value is `0`
* *limit(optional)*: limit the number of the channels, default value is `20`

### Response
The channel list.
#### Example
**Request**
```
	GET: /j/explore/genre?gid=335&start=1&limit=1
```
**Response**
```javascript
	{
	    status: true,
	    data: {
	        channels: [{
	            intro: "关于欧美流行音乐的一切，就在这里了",
	            name: "欧美",
	            song_num: 8873,
	            creator: {
	                url: "http://site.douban.com/douban.fm/",
	                name: "豆瓣FM",
	                id: 1
	            },
	            banner: "http://img3.douban.com/img/fmadmin/chlBanner/26384.jpg",
	            cover: "http://img3.douban.com/img/fmadmin/icon/26384.jpg",
	            id: 2,
	            hot_songs: [
	                "Whistle",
	                "The Show",
	                "If I Were A Boy"
	            ]
	        }],
	        total: 97
	    }
	}
```


<a name="get_channel_info"></a>
## Get Channel Info (获取兆赫信息)
Get the channel info by channel id.
### Request
` GET /j/explore/get_channel_info `
### Parameters
* *cid*: the channel id

### Response
The brief intro of channel.
### Example
**Request**
```
	GET: /j/explore/get_channel_info?cid=32
```
**Response**
```javascript
	{
	    status: true,
	    data: {
	        res: {
	            intro: "我不在喝咖啡，就在听咖啡兆赫。",
	            cover: "http://img3.douban.com/img/fmadmin/raw/26379",
	            id: 32,
	            name: "咖啡"
	        }
	    }
	}
```


<a name="channel_detail"></a>
## Channel Detail (兆赫详情)
Get the channel detail by the channel id , including creator info , channel board , channel intro , song's number , etc.
### Request:
` GET: /j/explore/channel_detail `
### Parameters:
* *channel_id*: the id of channel

### Response:
* Success:
	* *status*: `true`
	* *data*: the details of the channel
* Fail:
	* *status*: `false`
	* *msg*: the error message

### Example
**Request**
```
	GET: /j/explore/channel_detail?channel_id=177
```
**Response**
```javascript
	{
	    "status": true,
	    "data": {
	        "is_fav": false,
	        "is_com": true,
	        "channel": {
	            "creator": {
	                "url": "http:\/\/site.douban.com\/douban.fm\/",
	                "chls": [{l
	                    "tags": ["周杰伦", "陈奕迅", "很经典的"],
	                    "cover": "http:\/\/img3.douban.com\/img\/fmadmin\/icon\/26383.jpg",
	                    "id": 1,
	                    "name": "华语"
	                }, {
	                    "tags": ["欧美", "抒情", "慢歌"],
	                    "cover": "http:\/\/img3.douban.com\/img\/fmadmin\/icon\/26384.jpg",
	                    "id": 2,
	                    "name": "欧美"
	                }, {
	                    "tags": ["70", "9"],
	                    "cover": "http:\/\/img3.douban.com\/img\/fmadmin\/icon\/26385.jpg",
	                    "id": 3,
	                    "name": "七零"
	                }, {
	                    "tags": ["怀旧", "熟悉的旋律", "喜欢"],
	                    "cover": "http:\/\/img5.douban.com\/img\/fmadmin\/icon\/26386.jpg",
	                    "id": 4,
	                    "name": "八零"
	                }, {
	                    "tags": ["1993", "呵呵", "1994"],
	                    "cover": "http:\/\/img5.douban.com\/img\/fmadmin\/icon\/26387.jpg",
	                    "id": 5,
	                    "name": "九零"
	                }, {
	                    "tags": ["陈奕迅", "喜欢粤语", "卫兰"],
	                    "cover": "http:\/\/img5.douban.com\/img\/fmadmin\/icon\/26388.jpg",
	                    "id": 6,
	                    "name": "粤语"
	                }, {
	                    "tags": ["rock", "中文摇滚", "喜欢"],
	                    "cover": "http:\/\/img5.douban.com\/img\/fmadmin\/icon\/26389.jpg",
	                    "id": 7,
	                    "name": "摇滚"
	                }, {
	                    "tags": ["民谣", "治愈系", "喜欢"],
	                    "cover": "http:\/\/img3.douban.com\/img\/fmadmin\/icon\/26390.jpg",
	                    "id": 8,
	                    "name": "民谣"
	                }, {
	                    "tags": ["心灵音乐", "想聆听，便至我灵魂的另一个世界！！！", "peaceful."],
	                    "cover": "http:\/\/img3.douban.com\/img\/fmadmin\/icon\/26391.jpg",
	                    "id": 9,
	                    "name": "轻音乐"
	                }, {
	                    "tags": ["电影原声", "悲惨世界", "有故事的音乐"],
	                    "cover": "http:\/\/img3.douban.com\/img\/fmadmin\/icon\/26395.jpg",
	                    "id": 10,
	                    "name": "电影原声"
	                }],
	                "pic": "http:\/\/img3.douban.com\/view\/site\/small\/public\/54be8a91ccef8bb.jpg",
	                "name": "豆瓣FM",
	                "id": 1
	            },
	            "channel_board": [{
	                "text": "m~",
	                "owner_id": 1192478,
	                "pid": "24538",
	                "time": "2014-02-20 15:06:06",
	                "author": {
	                    "url": "http:\/\/www.douban.com\/people\/35974126\/",
	                    "id": "35974126",
	                    "pic": "http:\/\/img3.douban.com\/icon\/u35974126-36.jpg",
	                    "name": "森冉和",
	                    "uid": "35974126"
	                }
	            }, {
	                "text": "碼一个",
	                "owner_id": 1192478,
	                "pid": "24416",
	                "time": "2014-02-14 09:25:16",
	                "author": {
	                    "url": "http:\/\/www.douban.com\/people\/ld6688hk\/",
	                    "id": "74570552",
	                    "pic": "http:\/\/img3.douban.com\/icon\/u74570552-8.jpg",
	                    "name": "逆光の星",
	                    "uid": "ld6688hk"
	                }
	            }, {
	                "text": "shafa",
	                "owner_id": 1192478,
	                "pid": "24397",
	                "time": "2014-02-13 15:32:54",
	                "author": {
	                    "url": "http:\/\/www.douban.com\/people\/Vincentcaiwm\/",
	                    "id": "72817015",
	                    "pic": "http:\/\/img3.douban.com\/icon\/user_normal.jpg",
	                    "name": "Vincentcaiwm",
	                    "uid": "Vincentcaiwm"
	                }
	            }, {
	                "text": "sofa",
	                "owner_id": 1192478,
	                "pid": "24289",
	                "time": "2014-02-08 19:47:31",
	                "author": {
	                    "url": "http:\/\/www.douban.com\/people\/67782916\/",
	                    "id": "67782916",
	                    "pic": "http:\/\/img3.douban.com\/icon\/u67782916-2.jpg",
	                    "name": "清 味道",
	                    "uid": "67782916"
	                }
	            }],
	            "intro": "",
	            "banner": "http:\/\/img5.douban.com\/img\/fmadmin\/chlBanner\/29398.jpg",
	            "id": 177,
	            "cate": "detail-page",
	            "name": "捷达 情人节",
	            "tags": ["love"],
	            "cover": "http:\/\/img5.douban.com\/img\/fmadmin\/icon\/29398.jpg",
	            "rec_stats": 0,
	            "song_num": 100,
	            "listened_count": 33201
	        },
	        "auto_create": 0
	    }
	}
```


<a name="except_report"></a>
## Except Report (问题报告)
Report the exception.
### Request
` GET: /j/except_report `
### Parameters
* *kind*: value `ra006`
* *env*: the user agent string
* *reason*: the report content

### Response
The operation status.
### Example
**Request**
```
	GET: /j/except_report?kind=ra006&env=Mozilla/5.0%20(Windows%20NT%206.1;%20WOW64)%20AppleWebKit/537.36%20(KHTML,%20like%20Gecko)%20Chrome/33.0.1750.117%20Safari/537.36+&reason=test
```
**Response**
```javascript
	{r:0}
```
