# Test or Abandon

<a name="person_channel_tags"></a>
## Person Channel Tags (个人频道标签)
Get the personal channel tags.
### Request
` GET: /j/explore/person_channnel_tags ` // channnel seems to be a typo
### Parameters
None.
#### Response
The tag list.


<a name="person_tag_test"></a>
## Person Tag Test (个人标签测试)
Get whether the user are participate the person tag's test.
### Request
` GET: /j/explore/person_tag_test?accept=1 `
### Parameters
* *accept* : `1` or `0`

### Response
The result.


<a name="is_tags_song_exists"></a>
Check whether the song meet the conditions exists.
## Is Tags Song Exists (指定标签歌曲是否存在)
### Request
` GET: /j/explore/is_tags_song_exists `
### Parameters
* *tags* : tags join with `_`

### Response
Whether the song exists.


<a name="channel_personal_tag"></a>
## Channel Personal Tag (个人频道标签)
Get the tags that fit the user.
### Request
` GET: /j/explore/channel_personnel_tag `   // personnel seems to be a typo
### Parameters
None.
### Response
The tags' name and id.
### Example
**Request**
```
	GET: /j/explore/channel_personnel_tag
```
**Response**
```javascript
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
```
