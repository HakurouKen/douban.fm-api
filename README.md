#Douban FM API Pirvate Documentation

## Explanation
This is **not** a Douban FM offical API doucmentation. **Please only use it for learning purposes.** All the request is based on the root `http://douban.fm` .


## Index

### General (通用)
* [Get Captcha id (获取验证码ID)](#get_captcha_id)
* [Get Captcha (获取验证码)](#get_captcha)
* [Get Form (请求表单html)](#get_form)
* [Login (登录)](#login)
* [Hot Channels (热门兆赫)](#hot_channels)
* [Up Trending Channels (上升最快兆赫)](#up_trending_channels)
* [Search Channel (搜索兆赫)](#search_channel)
* [Genre (歌曲类型筛选)](#genre)
* [Get Channel Info (获取兆赫信息)](#get_channel_info)
* [Channel Detail (兆赫详情)](#channel_detail)
* [Except Report (问题报告)](#except_report)

### Logged in User Behavior (已登录用户操作)
* [Get Login Channels(登录后获取频道列表)](#get_login_channel)
* [Transfer Data (数据提交)](#transfer_data)
* [Clear Anonymous Data (清除匿名数据)](#clear_anonymous_data)
* [Record Explanation (记录)](#record_explanation)
* [Fav Channel (收藏兆赫)](#fav_channel)
* [Unfav Channel (取消收藏兆赫)](#unfav_channel)
* [Get Favorite Channel (我的收藏)](#get_favorite_channel)
* [Get Recommend Channel (推荐频道，试试这些)](get_recommend_channel)
* [Is Favorite Channel (判断是否收藏)](#is_favorite_channel)
* [Add Channel Tag (添加标签)](#add_channel_tag)
* [Add Board Post (添加评论)](#add_board_post)
* [Delete Board Post (删除评论)](#delete_board_post)
* [Get My Tags (我加过的标签)](#get_my_tags)
* [Select Channel (选择频道)](#select_channel)
* [Change Channel (改变频道)](#change_channel)
* [Remove Recent Channel (删除最近收听频道)](#remove_recent_channel)
* [Player Behavior (播放器操作：红心，垃圾桶，跳过)](#player_behavior)
* [Logout (注销)](#logout)

### My FM (我的FM)
* [Play Record (播放记录)](#play_record)
* [Fav Channels (收藏兆赫)](#fav_channels)
* [Artist Suggest (歌手猜测)](#artist_suggest)
* [Add Artist (添加喜爱歌手)](#add_artist)
* [Remove Artist (删除喜爱歌手)](#remove_artist)
* [Interest(歌曲加心)](#interest)
* [Undo Ban (歌曲移出垃圾桶)](#undo_ban)


### Test && Abandon (测试 && 废弃)
* [Person Channel Tags (个人频道标签)](#person_channel_tags)
* [Person Tag Test (个人标签测试)](#person_tag_test)
* [Is Tags Song Exists (指定标签歌曲是否存在)](#is_tags_song_exists)
* [Channel Personal Tag (个人频道标签)](#channel_personal_tag)

### Time Machine (豆瓣留声机)
* [Show Time Machine (是否显示Time Machine)](#show_time_machine)
* [Discard Time Machine Tips (不显示Time Machine)](#discard_time_machine_tips)


## API Description

<a name="get_captcha_id"></a>
### Get Captcha id (获取验证码ID)
#### Request 
``` GET: /j/new_captcha ```
#### Usage
Get the captcha id.
#### Parameters
none
#### Response
The captcha id.
#### Example:
**Request**

	GET: /j/new_captcha

**Response**

	f002Un7LjuEW29TOGGRR4han:en



<a name="get_captcha"></a>
### Get Captcha (获取验证码)
#### Request
``` GET: /misc/captcha ```
#### Usage
Get the captcha.
#### Parameters
* *size*
	- *s* : small (250x40)
	- *m* : medium (220x40) // shouldn't it larger than s ???
	- *l* : large (400x60)
* *id*<br/>
	the id get from new_captcha
#### Response
a captcha image
#### Example
none



<a name="get_form"></a>
### Get Form (请求表单html)
#### Request
``` GET /j/misc/login_form ```
#### Usage
Get the html code of login form.
#### Parameters
none
#### Response
the html code of login form
#### Example
none



<a name="login"></a>
### Login (登录)
#### Request
``` POST: /j/login ```
#### Parameters
* *source*<br/>
value `radio`
* *alias*<br/>
the e-mail of your douban account
* *form\_password*<br/>
the password of your douban account
* *captcha_solution*<br/>
the captcha you input
* *captcha_id*<br/>
the captcha id get from `/j/new_captcha`
* *task*<br/>
value `sync_channel_list` ,use to sync the playlist
* *remember*<br/> 
	- *on* ： remember
	- *undefined* : do not remember
#### Response
* Success:
	* *r*<br/>
	value `0` , represent for succeed
	* *user\_info*<br/>
	the user info details
* Fail
	* *err\_msg*<br/>
	the error message
	* *err\_no*<br/>
	the error number
	* *r*<br/>
	value `1` , represent for failed
#### Examples
**Request**
	
	/* POST: /j/login */
	source:radio
	alias: my_email_here@xmail.com
	form_password: my_password_here
	captcha_solution: profit
	captcha_id: Rc6zxTUxDa7crcSXjdpi3tyz:en
	task: sync_channel_list

**Response**

	{
	    "user_info": {
	        "ck": "o7hG",
	        "play_record": {
	            "fav_chls_count": 19,
	            "liked": 2453,
	            "banned": 246,
	            "played": 20568
	        },
	        "is_new_user": 0,
	        "uid": "64965813",
	        "third_party_info": null,
	        "url": "http:\/\/www.douban.com\/people\/64965813\/",
	        "is_dj": false,
	        "id": "64965813",
	        "is_pro": false,
	        "name": "白楼剑bravo47"
	    },
	    "r": 0
	}



<a name="hot_channels"></a>
### Hot Channels (热门兆赫)
#### Request
``` GET: /j/explore/hot_channels ```
#### Usage
Get the hot channels.
#### Parameters
none
#### Response
the hot channel's list
#### Examples
none


<a name="#up_trending_channels"></a>
### Up Trending Channels (上升最快兆赫)
#### Request
``` GET: /j/explore/up_trending_channels ```
#### Usage
Get the up trending channels.
#### Parameters
none
#### Response
the up trending channel's list
#### Examples
none



<a name="#search_channel"></a>
### Search Channel (搜索兆赫)
#### Request
``` GET: /j/explore/search ```
#### Usage
Search the channel by keywords.
#### Parameters
* *query*<br/>
the key word you want to search by
* *start(optional)*<br/>
the start of the channel result, default value is `0`
* *limit(optional)*<br/>
limit the number of the channels, default value is `20`
#### Response
the channels array
#### Example
**Request**

	GET: /j/explore/search?query=linkin%20park

**Response**

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
	 


<a name="genre"></a>
### Genre (歌曲类型筛选)
#### Request
``` GET /j/explore/genre ```
#### Usage
Get channels by the genre.
#### Parameters
* *gid*<br/>
the id of the channel genre
* *start(optional)*<br/>
the start of the channel result, default value is `0`
* *limit(optional)*<br/>
limit the number of the channels, default value is `20`
#### Response
the channel list
#### Example
**Request**

	GET: /j/explore/genre?gid=335&start=1&limit=1

**Response**
	
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



<a name="#get_channel_info"></a>
### Get Channel Info (获取兆赫信息)
#### Request
``` GET /j/explore/get_channel_info ```
#### Usage
Get the channel info by channel id.
#### Parameters
* *cid*<br/>
the channel id
#### Response
the brief intro of channel
#### Example
**Request**

	GET: /j/explore/get_channel_info?cid=32

**Response**
	
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



<a name="channel_detail"></a>
### Channel Detail (兆赫详情)
#### Request:
``` GET: /j/explore/channel_detail ```
#### Usage:
Get the channel detail by the channel id , including creator info , channel board , channel intro , song's number , etc.
#### Parameters:
* *channel_id*<br/>
the id of channel
#### Response:
* Success:
	* *status*<br/>
	true
	* *data*<br/>
	the details of the channel
* Fail:
	* *status*<br/>
	false
	* *msg*<br/>
	the error message
#### Example
**Request**

	GET: /j/explore/channel_detail?channel_id=177

**Response**
	
	{
	    "status": true,
	    "data": {
	        "is_fav": false,
	        "is_com": true,
	        "channel": {
	            "creator": {
	                "url": "http:\/\/site.douban.com\/douban.fm\/",
	                "chls": [{
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



<a name="except_report"></a>
### Except Report (问题报告)
#### Request
``` GET: /j/except_report ```
#### Usage
Report the exception.
#### Parameters
* *kind*
value `ra006`
* *env*
the user agent string
* *reason*
the report content
#### Response
the operation status
#### Example
**Request**

	GET: /j/except_report?kind=ra006&env=Mozilla/5.0%20(Windows%20NT%206.1;%20WOW64)%20AppleWebKit/537.36%20(KHTML,%20like%20Gecko)%20Chrome/33.0.1750.117%20Safari/537.36+&reason=test

**Response**

	{r:0}



<a name="get_login_channels"></a>
### Get Login Channels(登录后获取频道列表)
#### Request
``` GET: /j/explore/get_login_chls ```
#### Usage
Use for init the channel after login.
#### Parameters
* *uk*<br/>
the user's number id.
#### Response
favorite channels and recently listend channels
#### Example
**Request**

	GET: /j/explore/get_login_chls?uk=64965813

**Response**

	// omit some data...
	{
	    status: true,
	    data: {
	        res: {
	            fav_chls: [{
	                intro: "关于欧美流行音乐的一切，就在这里了",
	                name: "欧美",
	                song_num: 8873,
	                creator: {
	                    url: "http://site.douban.com/douban.fm/",
	                    name: "豆瓣FM",
	                    id: 1
	                },
	                banner: "http://img3.douban.com/img/fmadmin/chlBanner/26384.jpg",
	                cover: "http://img3.douban.com/img/fmadmin/small/26384.jpg",
	                id: 2,
	                hot_songs: [
	                    "Whistle",
	                    "The Show",
	                    "If I Were A Boy"
	                ]
	            }, {...}, {...}, {....}, {...}],
	            rec_chls: [{
	                intro: "乡村音乐给缓慢的老调添加了欢快清新。",
	                name: "我爱乡村音乐",
	                song_num: 161,
	                creator: {
	                    url: "http://www.douban.com/people/penwai/",
	                    name: "过江人",
	                    id: 1316167
	                },
	                banner: "http://img3.douban.com/img/fmadmin/chlBanner/16300.jpg",
	                cover: "http://img3.douban.com/img/fmadmin/small/16300.jpg",
	                id: 1001433,
	                hot_songs: [
	                    "Take Me Home, Country Roads",
	                    "When You Say Nothing At All",
	                    "Rocky Mountain High"
	                ]
	            }, {...}, {...}, {...}, {...}]
	        }
	    }
	}



<a name="transfer_data"></a>
### Transfer Data (数据提交)
#### Request
```GET /j/transfer_data```
#### Usage
Transfer the listened data when not login.
#### Parameters
* *ck*
the key `ck` in your cookie
#### Response
the number of data that transfered
#### Example
**Request**

	GET /j/transfer_data

**Response**

	{
	    "r": 0,
	    "transfer_info": {
	        "liked": 0,
	        "days": 0,
	        "played": 0
	    }
	}



<a name="clear_anonymous_data"></a>
### Clear Anonymous Data (清除匿名数据)
#### Request
``` POST: /j/clear_anonymous_data ```
#### Usage
Delete the data when not logged in.
#### Parameters
none
#### Response
the operation status
#### Example
none



<a name="record"></a>
### Record Explanation (记录)
#### Request
``` GET: /j/mine/rec_explanation ```
#### Usage
Record the user behavior.
#### Parameters
none
#### Response
the operation status
#### Example
none
	


<a name="fav_channel"></a>
### Fav Channel (收藏兆赫)
#### Request
``` GET: /j/explore/fav_channel ```
#### Usage
Add the channel to the favorites.
#### Parameters
* *cid*<br/>
the id of the song
#### Response
the status of the operation
#### Examples
**Request**

	GET: /j/explore/fav_channel?cid=1

**Response**

	{
		status: true,
		data: {
			res: 1
		}
	}	



<a name="unfav_channel"></a>
### Unfav Channel (取消收藏兆赫)
#### Request
``` GET: /j/explore/unfav_channel ```
#### Usage
Remove the channel from the favorites.
#### Parameters
* *cid*<br/>
the id of the channel
### Response
the status of the operation
#### Example
**Request**

	GET: /j/explore/unfav_channel?cid=2

**Response**
	
	{
		status: true,
			data: {
				res: 1
		}
	}



<a name="get_favorite_channel"></a>
### Get Favorite Channel (我的收藏)
#### Request
``` GET: /j/explore/get_fav_chl ```
#### Usage
Get a channel from favorites.
#### Parameters
* *ofavs*<br/>
a string join with `|` and the channel's id. The channels includes your recently listened channels(最近收听) and your favorite channels that had already added (我的收藏).
#### Response
a channel result
#### Examples
**Request**

	GET: /j/explore/get_fav_chl?ofavs=1004355|1000740|1001609|1003949

**Response**
	
	{
	    status: true,
	    data: {
	        res: {
	            intro: "关于欧美流行音乐的一切，就在这里了",
	            cover: "http://img3.douban.com/img/fmadmin/raw/26384",
	            id: 2,
	            name: "欧美"
	        }
	    }
	}




<a name="#get_recommend_channel"></a>
### Get Recommend Channel (推荐频道，试试这些)
#### Request
``` GET: /j/explore/get_recommend_chl ```
#### Usage
Get a recommend channel.
#### Parameters
* *orecs*<br/>
a string join with `|` and the channel's id. The channels includes your recently listened channels(最近收听) and your favorite channels(我的收藏).
#### Response
a channel result
#### Examples
**Request**

	GET: /j/explore/get_recommend_chl?orecs=1002754|49088|1004880|2|1004355|1000740|1001609|1003949

**Response**
	
	{
	    status: true,
	    data: {
	        res: {
	            intro: "抽出一点时间，闭上眼睛，选个舒服的姿势，戴上耳机，伴着温柔的音乐，好好享受一下这小憩的时光吧！",
	            cover: "http://img3.douban.com/img/fmadmin/raw/17198",
	            id: 1001889,
	            name: "小憩时光"
	        }
	    }
	}



<a name="is_favorite_channel"></a>
### Is Favorite Channel (判断是否收藏)
#### Request
``` GET: /j/explore/is_fav_channel ```
#### Usage
Judge if a song is in the favorites.
#### Parameters
* *uk*<br/>
user id
* *cid*<br/>
the channel id
#### Response
whether the song is favorited
#### Examples
**Request**

	GET: /j/explore/is_fav_channel?uk=64965813&cid=1003949

**Response**
	
	{
	    status: true,
	    data: {
	        res: {
	            is_fav: true
	        }
	    }
	}



<a name="add_channel_tag"></a>
### Add Channel Tag (添加标签)
#### Request
``` POST: /j/explore/add_channel_tags ```
#### Usage
Add tags to the channel.
#### Parameters
* *tags*<br/>
the tags you want to add (encoded)
* *cid*<br/>
the channel id
* *ck*<br/>
the key `ck` in your cookie
#### Response
the operation status
#### Examples
**Request**

	/* POST: /j/explore/add_channel_tags */
	tags: +%E5%85%89%E8%89%AF+%E6%A2%81%E9%9D%99%E8%8C%B9
	cid: 1
	ck: your_ck_key

**Response**
	
	{
		"status":true,
		"data":{
			"result":1
		}
	}



<a name="add_board_post"></a>
### Add Board Post (添加评论)
#### Request
``` POST: /j/explore/add_board_post ```
#### Usage
Add a comment to the channel
#### Parameters
* *text*<br/>
the comment you want to add
* *channel_id*<br/>
the channel's id
* *ck*<br/>
the key `ck` in your cookie
#### Response
the commiter and the channel ownner's info
#### Example
**Request**

	/* POST: /j/explore/add_board_post */
	text: test...
	channel_id: 1
	ck: your_ck_key

**Response**

	{
	    "status": true,
	    "data": {
	        "post": {
	            "text": "test...",
	            "owner_id": "1192478",
	            "pid": "24720",
	            "time": "2014-02-28 00:38:08",
	            "author": {
	                "url": "http:\/\/www.douban.com\/people\/64965813\/",
	                "id": "64965813",
	                "pic": "http:\/\/img3.douban.com\/icon\/user_normal.jpg",
	                "name": "白楼剑bravo47",
	                "uid": "64965813"
	            }
	        }
	    }
	}




<a name="delete_board_post"></a>
### Delete Board Post (删除评论)
#### Request
``` POST: /j/explore/delete_board_post ```
#### Usage
Delete the comment you have posted.
#### Parameters
* *pid*<br/>
the id of the comment
* *author_id*<br/>
the author's (your) number id
* *ck*<br/>
the key `ck` in your cookie
#### Response
the operation status
#### Examples
**Request**

	pid: 24720
	author_id: 64965813
	ck: your_ck_key

**Response**
	
	{"status":true}



<a name="get_my_tags"></a>
### Get My Tags (我加过的标签)
#### Request
``` GET: /j/explore/get_my_tags ```
#### Usage
Get the tag you have added.
#### Parameters
* *channel_id*<br/>
the channel id
#### Response
*Success:
the tags you added most and added in this channel
*Fail:
error message
#### Example
**Request**
	
	GET: /j/explore/get_my_tags?channel_id=2

**Response**

	{
	    status: true,
	    data: {
	        user_hot_channel_tags: [],
	        my_channel_tags: []
	    }
	}



<a name="select_channel"></a>
### Select Channel (选择频道)
#### Request
``` POST: /j/explore/channel_select ```
#### Usage
Tell the server you select a channel.
#### Parameters
* *cid*<br/>
channel id
* *ctype*
	- *r* :  the channel belongs to system channels shown in the pages
	- *c* : the channel belongs to your favorites shown in the pages
* *ck*
the key `ck` in your cookie
#### Response
""
#### Example
none



<a name="change_channel"></a>
### Change Channel (改变频道)
#### Request
``` GET: /j/explore/change_channel ```
#### Usage
Change a channel and switch to a new playlist
#### Parameters
* *fcid*<br/>
current channel's id
* *tcid*<br/>
goal channel's id
* *area*<br/>
	which part of the page the channel belongs to
	- *songchannel* : the fm player init
	- *system_chls* : private (私人兆赫) / hearted (红心兆赫)
	- *history_chls* : lastest heard (最近收听)
	- *promotion_chls* : recommend channels (试试这些)
	- *fav_chls* : favorites (我的收藏)
	- *com_chls* : brand FM (品牌兆赫)
	- *recent_chls* : recently listened (最近收听) &&  hot channel (热门周爱河) && up trending channel (上升最快)
	- *search* : search (搜索)
#### Response
an operation flag
#### Example
none



<a name="remove_recent_channel"></a>
### Remove Recent Channel (删除最近收听频道)
#### Request
``` POST: /j/explore/rm_recent_chl ```
#### Usage
Remove recent listened channel . 
#### Parameters
* *cid*<br/>
the channel id
* *ck*<br/>
the key `ck` in your cookie
#### Response
operation status
#### Example
**Request**

	/* POST: /j/explore/rm_recent_chl */
	cid: 2
	ck: your_ck_key

**Response**

	{"status":true}



<a name="player_behavior"></a>
### Player Behavior (播放器操作：红心，垃圾桶，跳过)
#### Request
``` GET: /j/mine/playlist ```
#### Usage
Get new playlist when player status change.
#### Parameters
* *type*<br/>
	- *n* : None. Used for get a song list only.
	- *e* : Ended a song normally.
	- *u* : Unlike a hearted song.
	- *r* : Like a song.
	- *s* : Skip a song.
	- *b* : Trash a song.
* *sid*<br/>
the song's id
* *pt*<br/>
how long the song has passed when operated
* *channel*<br/>
channel id
* *pb*<br/>
for the normal user(not pro) , value `64`
* *from*<br/>
value `mainsite`
* *r*<br/>
a 10 digits 16 hex random number
#### Resopnse
*e* : the operate status
*others* : a playlist
#### Example
**Request**

	GET: /j/mine/playlist?type=s&sid=1395079&pt=3.3&channel=0&pb=64&from=mainsite&r=41c64da174

**Response**
	
	// omit some data...
	{
	    "r": 0,
	    "song": [{
	        "album": "\/subject\/4202241\/",
	        "picture": "http:\/\/img3.douban.com\/mpic\/s4105320.jpg",
	        "ssid": "3380",
	        "artist": "天門",
	        "url": "http:\/\/mr3.douban.com\/201402282319\/87a382bff43bf5019aca82e4978b46ca\/view\/song\/small\/p1635559.mp3",
	        "company": "コミックス・ウェーブ",
	        "title": "きみのこえ(Instrumental)",
	        "rating_avg": 4.68519,
	        "length": 298,
	        "subtype": "",
	        "public_time": "2009",
	        "sid": "1635559",
	        "aid": "4202241",
	        "sha256": "edaa737b9fc761d47e4ba8d3e2ce877c89e7ee085ed58433d516c45e6d1201c7",
	        "kbps": "64",
	        "albumtitle": "新海誠作品イメー...",
	        "like": 1
	    }, {
	        "album": "\/subject\/3141335\/",
	        "picture": "http:\/\/img3.douban.com\/mpic\/s3555220.jpg",
	        "ssid": "821f",
	        "artist": "萧人凤",
	        "url": "http:\/\/mr3.douban.com\/201402282319\/df428f46f7106b7e57d28192666e2793\/view\/song\/small\/p1829165.mp3",
	        "company": "",
	        "title": "仙剑问情",
	        "rating_avg": 4.58454,
	        "length": 257,
	        "subtype": "U",
	        "public_time": "2003",
	        "sid": "1829165",
	        "aid": "3141335",
	        "sha256": "32d617e11a92820fb3e44057ac0d11268ae6136deb96131d61c3840d8d26b82e",
	        "kbps": "64",
	        "albumtitle": "仙剑奇侠传三外传...",
	        "like": 1
	    }, {...
	    }, {...
	    }, {...
	    }]
	}



<a name="logout"></a>
### Logout (注销)
#### Request
``` GET: /partner/logout```
#### Usage
Logout.
#### Parameters
* *source*<br/>
value `radio`
* *ck*<br/>
the key `ck` in your cookie
* *no_login*<br/>
value `y`
#### Response
none
#### Example
none



<a name="play_record"></a>
### Play Record (播放记录)
#### Request
``` GET: /j/play_record ```
#### Usage
Get the play record.
#### Parameters
* *ck*<br/>
the key `ck` in your cookie
* *spbid*<br/>
value `::` plus the key `bid` in your cookie
* *type*<br/>
	- *liked*: hearted song
	- *banned*: trashed song
	- *played*: played song
#### Response
the songlist and detail infos
#### Example
**Request**
	
	http://douban.fm/j/play_record?ck=your_ck_key&spbid=your_spbid_key&type=liked

**Response**
	
	//omit some data...
	{
		"total": 2465,
		"start": 0,
		"per_page": 15,
		"songs": [{
			"picture": "http:\/\/img5.douban.com\/spic\/s26811799.jpg",
			"liked": true,
			"artist": "Ramin Djawadi",
			"title": "Pacific Rim",
			"subject_title": "Pacific Rim",
			"path": "http:\/\/music.douban.com\/subject\/24840163\/",
			"id": "1936121"
		},{...},{...},
			...
		],
		"song_type": "liked"
	}



<a name="fav_channels"></a>
### Fav Channels (收藏兆赫)
#### Request
``` GET /j/fav_channels ```
#### Usage
Get all favorite channels.
#### Parameters
* *ck*<br/>
the key `ck` in your cookie
#### Response
the channel list
#### Example
**Request**

	GET: /j/fav_channels?ck=your_ck_key

**Response**

	// omit some data...
	{
		"channels": [{
			"intro": "纪念那些曾经让我们感动的声音,我们只爱旧流行",
			"name": "ACG音乐茶座",
			"song_num": 462,
			"creator": {
				"url": "http:\/\/www.douban.com\/people\/yiphu\/",
				"name": "找回自己",
				"id": 4899571
			},
			"banner": "http:\/\/img5.douban.com\/img\/fmadmin\/chlBanner\/19008.jpg",
			"cover": "http:\/\/img5.douban.com\/img\/fmadmin\/icon\/19008.jpg",
			"id": 1002754,
			"hot_songs": ["あなただけ見つめてる", "ありがとう…", "私へ"]
		},
		{
			"intro": "Linkin Park是一组来自加利福尼亚州洛杉矶的歌唱组合兼流行摇滚乐团，也被认为是新金属中最成功的乐团。",
			"name": "林肯公园LP",
			"song_num": 84,
			"creator": {
				"url": "http:\/\/www.douban.com\/people\/ckMac\/",
				"name": "ckMac陈萌调",
				"id": 55700577
			},
			"banner": "http:\/\/img5.douban.com\/img\/fmadmin\/chlBanner\/26019.jpg",
			"cover": "http:\/\/img5.douban.com\/img\/fmadmin\/icon\/26019.jpg",
			"id": 1005150,
			"hot_songs": ["Burning In The Skies", "Roads Untraveled", "Hands Held High"]
		},
		...
		]
	}



<a name="artist_suggest"></a>
### Artist Suggest (歌手猜测)
#### Request
``` GET: /j/artist_suggest ```
#### Usage
Guess the aritst by the word you typed.
#### Parameters
* *q*<br/>
word
#### Response
the artists name
#### Example
**Request**

	GET: /j/artist_suggest?q=nick

**Response**

	nick glennie-smith, hans zimmer, harry gregso
	nick cave and warren ellis
	nick barker and alana
	nick barker
	Nicky Hopkins



<a name="add_artist"></a>
### Add Artist (添加喜爱歌手)
#### Request
``` POST: /j/add_artist ```
#### Usage
Add favorite artist.
#### Parameters
* *ck*<br/>
the key `ck` in your cookie
* *name*<br/>
the artist's name
#### Response
a artist html string
#### Example
** Request**

	/* POST: /j/add_artist */
	ck: your_ck_key
	name: Jay-Z And Linkin Park

**Response**
	
	"{\"html\":\"<li class=\\\"j a_add_artist\\\">Coldplay<\/li><li class=\\\"j a_add_artist\\\">Eminem<\/li><li class=\\\"j a_add_artist\\\">Maroon 5<\/li><li class=\\\"j a_add_artist\\\">Evanescence<\/li>\"}"



<a name="remove_artist"></a>
### Remove Artist (删除喜爱歌手)
#### Request
``` POST: /j/remove_artist ```
#### Usage
Delete an artist you liked.
#### Parameters
* *ck*<br/>
the key `ck` in your cookie
* *name*<br/>
the artist's name
#### Response
the operation status
#### Example
** Request**

	POST: /j/add_artist
	ck: your_ck_key
	name: Jay-Z And Linkin Park

**Response**
	
	{"r":0}



<a name="interest"></a>
### Interest (歌曲加心)
#### Request
``` POST: /j/song/<song_id>/interest ```
#### Usage
Change the heart status of a song.
#### Parameters
* *song_id (in Request url)*<br/>
the song's id
* *ck*<br/>
the key `ck` in your cookie
* *action*<br/>
	- *y* : like
	- *n* : dislike
#### Response
`y`
#### Example
**Request**
	
	/* POST: /j/song/747585/interest */
	action: n
	ck: your_ck_key

**Response**

	y



<a name="undo_ban"></a>
### Undo Ban (歌曲移出垃圾桶)
#### Request
``` POST: /j/song/<song_id>/undo_ban ```
#### Usage
Remove a song out of ban list.
#### Parameters
* *song_id (in Request url)*<br/>
the song's id
* *ck*<br/>
the key `ck` in your cookie
#### Response
`y`
#### Example
**Request**
	
	/* POST: /j/song/33149/undo_ban */
	ck: your_ck_key

**Response**

	y



<a name="person_channel_tags"></a>
### Person Channel Tags (个人频道标签)
#### Request
``` GET: /j/explore/person_channnel_tags ``` // channnel seems to be a typo
#### Usage
Get the personal channel tags.
#### Parameters
none
#### Response
the tag list
#### Example
none



<a name="person_tag_test"></a>
### Person Tag Test (个人标签测试)
#### Request
``` GET: /j/explore/person_tag_test?accept=1 ```
#### Usage
Get whether the user are participate the person tag's test.
#### Parameters
* *accept*<br/>
	`1` or `0`
#### Response
the result
#### Example
none



<a name="is_tags_song_exists"></a>
### Is Tags Song Exists (指定标签歌曲是否存在)
#### Request
``` GET: /j/explore/is_tags_song_exists ```
#### Usage
Check whether the song meet the conditions exists.
#### Parameters
* *tags*<br/>
tags join with `_`
#### Response
whether the song exists
#### Example
none



<a name="channel_personal_tag"></a>
### Channel Personal Tag (个人频道标签)
#### Request
``` GET: /j/explore/channel_personnel_tag   // personnel seems to be a typo```
#### Usage
Get the tags that fit the user.
#### Parameters
none
#### Response
the tags' name and id
#### Example
**Request**
	
	GET: /j/explore/channel_personnel_tag

**Response**

	// omit some data...
	{
	    "status": true,
	    "data": {
	        "tags": [{
	            "tag_name": "流行",
	            "tag_id": "27945"
	        }, {
	            "tag_name": "女声",
	            "tag_id": "14046"
	        }, {
	            "tag_name": "日本",
	            "tag_id": "17596"
	        }, {
	            "tag_name": "原声",
	            "tag_id": "15551"
	        },{
	        	...
	        }]
	    }
	}



<a name="show_time_machine"></a>
### Show Time Machine (是否显示Time Machine)
#### Request
``` GET: /j/timemachine/show_time_machine ```
#### Usage
Get whether show time machine or not
#### Parameters
none
#### Response
`0` or `1`
#### Example
none



<a name="discard_time_machine_tips"></a>
### Discard Time Machine Tips (不显示Time Machine)
#### Request
``` GET: /j/timemachine/disgard_tm_tip ``` // disgard seems to be a typo...
#### Usage
Do not show the Time Machine tips again.
#### Parameters
none
#### Response
`0`
#### Example
none
