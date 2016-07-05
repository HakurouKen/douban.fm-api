# My FM

<a name="play_record"></a>
## Play Record (播放记录)
Get the play record.
### Request
` GET: /j/play_record `
### Parameters
* *ck*: the key `ck` in your cookie
* *spbid*: value `::` plus the key `bid` in your cookie
* *type*
	- *liked*: hearted song
	- *banned*: trashed song
	- *played*: played song

### Response
The songlist and detail infos.
### Example
**Request**
```
	GET: /j/play_record?ck=your_ck_key&spbid=your_spbid_key&type=liked
```
**Response**
```javascript
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
```


<a name="fav_channels"></a>
## Fav Channels (收藏兆赫)
Get all favorite channels.
### Request
` GET /j/fav_channels `
### Parameters
None.
### Response
The channel list.
### Example
**Request**
```
	GET: /j/fav_channels
```
**Response**
```javascript
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
```


<a name="artist_suggest"></a>
Guess the aritst by the word you typed.
## Artist Suggest (歌手猜测)
### Request
` GET: /j/artist_suggest `
### Parameters
* *q*: word

### Response
The artists name
#### Example
**Request**
```
	GET: /j/artist_suggest?q=nick
```
**Response**
```
	nick glennie-smith, hans zimmer, harry gregso
	nick cave and warren ellis
	nick barker and alana
	nick barker
	Nicky Hopkins
```


<a name="add_artist"></a>
## Add Artist (添加喜爱歌手)
Add favorite artist.
### Request
` POST: /j/add_artist `
### Parameters
* *ck*: the key `ck` in your cookie
* *name*: the artist's name

### Response
A artist html string.
### Example
**Request**
```
	POST: /j/add_artist
	Data:
		ck: your_ck_key
		name: Jay-Z And Linkin Park
```
**Response**
```
	"{\"html\":\"<li class=\\\"j a_add_artist\\\">Coldplay<\/li><li class=\\\"j a_add_artist\\\">Eminem<\/li><li class=\\\"j a_add_artist\\\">Maroon 5<\/li><li class=\\\"j a_add_artist\\\">Evanescence<\/li>\"}"
```


<a name="remove_artist"></a>
## Remove Artist (删除喜爱歌手)
Delete an artist you liked.
### Request
` POST: /j/remove_artist `
#### Parameters
* *ck*: the key `ck` in your cookie
* *name*: the artist's name

### Response
The operation status.
### Example
**Request**
```
	POST: /j/add_artist
	Data:
		ck: your_ck_key
		name: Jay-Z And Linkin Park
```
**Response**
```javascript
	{"r":0}
```


<a name="interest"></a>
## Interest (歌曲加心)
Change the heart status of a song.
### Request
` POST: /j/song/<song_id>/interest `
### Parameters
* *song_id (in Request url)*: the song's id
* *ck*: the key `ck` in your cookie
* *action*
	- *y* : like
	- *n* : dislike

### Response
`y`
### Example
**Request**
```
	POST: /j/song/747585/interest
	Data:
		action: n
		ck: your_ck_key
```
**Response**
```
	y
```


<a name="undo_ban"></a>
## Undo Ban (歌曲移出垃圾桶)
Remove a song out of ban list.
### Request
` POST: /j/song/<song_id>/undo_ban `
### Parameters
* *song_id (in Request url)*: the song's id
* *ck*: the key `ck` in your cookie

### Response
`y`
### Example
**Request**
```
	POST: /j/song/33149/undo_ban
	Data:
		ck: your_ck_key
```
**Response**
```
	y
```
