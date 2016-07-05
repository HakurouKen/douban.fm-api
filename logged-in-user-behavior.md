# Logged in User Behavior

<a name="get_login_channels"></a>
## Get Login Channels(登录后获取频道列表)
Use for init the channel after login.
### Request
` GET: /j/explore/get_login_chls `
### Parameters
* *uk* : the user's number id

### Response
Favorite channels and recently listend channels.
### Example
**Request**
```
	GET: /j/explore/get_login_chls?uk=64965813
```
**Response**
```javascript
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
```


<a name="clear_anonymous_data"></a>
## Clear Anonymous Data (清除匿名数据)
Delete the data when not logged in.
### Request
` POST: /j/clear_anonymous_data `
### Parameters
None.
#### Response
The operation status.


<a name="record_explanation"></a>
## Record Explanation (记录)
Record the user behavior.
### Request
` GET: /j/mine/rec_explanation `
### Parameters
None
#### Response
The operation status.


<a name="fav_channel"></a>
## Fav Channel (收藏兆赫)
Add the channel to the favorites.
### Request
` GET: /j/explore/fav_channel `
### Parameters
*cid*: the id of the channel

### Response
The status of the operation.
### Examples
**Request**
```
	GET: /j/explore/fav_channel?cid=1
```
**Response**
```javascript
	{
		status: true,
		data: {
			res: 1
		}
	}
```


<a name="unfav_channel"></a>
## Unfav Channel (取消收藏兆赫)
Remove the channel from the favorites.
### Request
` GET: /j/explore/unfav_channel `
## Parameters
* *cid*: the id of the channel

### Response
The status of the operation.
### Example
**Request**
```
	GET: /j/explore/unfav_channel?cid=2
```
**Response**
```javascript
	{
		status: true,
			data: {
				res: 1
		}
	}
```


<a name="get_favorite_channel"></a>
## Get Favorite Channel (我的收藏)
Get a channel from favorites.
### Request
` GET: /j/explore/get_fav_chl `
### Parameters
* *ofavs*: a string join with `|` and the channel's id. The channels includes your recently listened channels(最近收听) and your favorite channels that had already added (我的收藏).

### Response
The channel result.
### Examples
**Request**
```
	GET: /j/explore/get_fav_chl?ofavs=1004355|1000740|1001609|1003949
```
**Response**
```javascript
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
```


<a name="get_recommend_channel"></a>
## Get Recommend Channel (推荐频道，试试这些)
Get a recommend channel.
### Request
` GET: /j/explore/get_recommend_chl `
### Parameters
* *orecs*: a string join with `|` and the channel's id. The channels includes your recently listened channels(最近收听) and your favorite channels(我的收藏).

### Response
A channel result.
### Examples
**Request**
```
	GET: /j/explore/get_recommend_chl?orecs=1002754|49088|1004880|2|1004355|1000740|1001609|1003949
```
**Response**
```javascript
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
```


<a name="is_favorite_channel"></a>
## Is Favorite Channel (判断是否收藏)
Judge if a song is in the favorites.
### Request
` GET: /j/explore/is_fav_channel `
### Parameters
* *uk*: user id
* *cid*: the channel id

### Response
Whether the song is favorited.
### Examples
**Request**
```
	GET: /j/explore/is_fav_channel?uk=64965813&cid=1003949
```
**Response**
```javascript
	{
	    status: true,
	    data: {
	        res: {
	            is_fav: true
	        }
	    }
	}
```


<a name="add_channel_tag"></a>
## Add Channel Tag (添加标签)
Add tags to the channel.
### Request
` POST: /j/explore/add_channel_tags `
### Parameters
* *tags*: the tags you want to add (encoded)
* *cid*: the channel id
* *ck*: the key `ck` in your cookie

### Response
The operation status.
### Examples
**Request**
```
	POST: /j/explore/add_channel_tags
	Data:
		tags : +%E5%85%89%E8%89%AF+%E6%A2%81%E9%9D%99%E8%8C%B9
		cid : 1
		ck : your_ck_key
```
**Response**
```javascript
	{
		"status":true,
		"data":{
			"result":1
		}
	}
```


<a name="add_board_post"></a>
## Add Board Post (添加评论)
Add a comment to the channel.
### Request
` POST: /j/explore/add_board_post `
### Parameters
* *text*: the comment you want to add
* *channel_id*: the channel's id
* *ck*: the key `ck` in your cookie

### Response
The commiter and the channel ownner's info.
### Example
**Request**
```
	POST: /j/explore/add_board_post
	Data:
		text: test...
		channel_id: 1
		ck: your_ck_key
```
**Response**
```javascript
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
```


<a name="delete_board_post"></a>
## Delete Board Post (删除评论)
Delete the comment you have posted.
### Request
` POST: /j/explore/delete_board_post `
### Parameters
* *pid*: the id of the comment
* *author_id*: the author's (your) number id
* *ck*: the key `ck` in your cookie

### Response
The operation status.
### Examples
**Request**
```
	POST: /j/explore/delete_board_post
	Data:
		pid: 24720
		author_id: 64965813
		ck: your_ck_key
```
**Response**
```javascript
	{"status":true}
```


<a name="get_my_tags"></a>
## Get My Tags (我加过的标签)
Get the tag you have added.
### Request
` GET: /j/explore/get_my_tags `
### Parameters
* *channel_id*: the channel id

### Response
* Success:
	The tags you added most and added in this channel.
* Fail:
	Error message.
### Example
**Request**
```
	GET: /j/explore/get_my_tags?channel_id=2
```
**Response**
```javascript
	{
	    status: true,
	    data: {
	        user_hot_channel_tags: [],
	        my_channel_tags: []
	    }
	}
```


<a name="select_channel"></a>
## Select Channel (选择频道)
Tell the server you select a channel.
### Request
` POST: /j/channel_select `
### Parameters
* *cid*: channel id
* *ctype*
	- *r*:  the recent channel ( which belongs to system channels ) shown in the pages ( but not the private channel or heart channel )
	- *c*: the channel belongs to your favorites shown in the pages
* *ck*: the key `ck` in your cookie

### Response
""


<a name="change_channel"></a>
## Change Channel (改变频道)
Change a channel and switch to a new playlist
### Request
` GET: /j/explore/change_channel `
### Parameters
* *fcid*: current channel's id
* *tcid*: goal channel's id
* *area*<br/>
	which part of the page the channel you wanna change belongs to
	- *songchannel*: the fm player init
	- *system_chls*: private (私人兆赫) / hearted (红心兆赫)
	- *history_chls*: lastest heard (最近收听)
	- *promotion_chls*: recommend channels (试试这些)
	- *fav_chls*: favorites (我的收藏)
	- *com_chls*: brand FM (品牌兆赫)
	- *recent_chls*: the recently listened channel( the channel under the private/hearted , recently listened which do not belongs to any channel lists such as similar song(听相似的歌) &&  hot channel (热门兆赫) && up trending channel (上升最快) will added to this part ).
	- *search*: search (搜索)

### Response
An operation flag.


<a name="remove_recent_channel"></a>
## Remove Recent Channel (删除最近收听频道)
Remove recent listened channel .
### Request
` POST: /j/explore/rm_recent_chl `
### Parameters
* *cid*: the channel id
* *ck*: the key `ck` in your cookie

### Response
Operation status.
### Example
**Request**
```
	POST: /j/explore/rm_recent_chl
	Data:
		cid: 2
		ck: your_ck_key
```
**Response**
```javascript
	{"status":true}
```


<a name="player_behavior"></a>
## Player Behavior (播放器操作：红心，垃圾桶，跳过)
Get new playlist when player status change.
### Request
` GET: /j/mine/playlist `
### Parameters
* *type*
	- *n*: None. Used for get a song list only.
	- *e*: Ended a song normally.
	- *u*: Unlike a hearted song.
	- *r*: Like a song.
	- *s*: Skip a song.
	- *b*: Trash a song.
	- *p*: Use to get a song list when the song in playlist was all played.
* *sid*: the song's id
* *pt*: how long the song has passed when operated
* *channel*: channel id
* *pb*: for the normal user(not pro) , value `64`
* *from*: value `mainsite`
* *r*: a 10 digits 16 hex random number

### Resopnse
* *e*: the operate status
* *others*: a playlist

### Example
**Request**
```
	GET: /j/mine/playlist?type=s&sid=1395079&pt=3.3&channel=0&pb=64&from=mainsite&r=41c64da174
```
**Response**
```javascript
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
```


<a name="logout-fm"></a>
## Logout (注销)
### Request
` GET: /partner/logout`
### Parameters
* *source*: value `radio`
* *ck*: the key `ck` in your cookie
* *no_login*: value `y`

#### Response
None.
