# Line bot

## Bot logic
* if the request is location info
	+ if next question is location info
		- store user id and location info(lat, lng)
		- switch next question as bar type
		- reply the next question
  + else
		- ignore
* if the request is text
	+ if next question is bar type
		- store bar type
		- switch next question as bar name
		- reply the next question
	+ if next question is bar name
		- if the text is "ない"|"no?"
			- store bar name as all
		- else
			- store bar type
		- switch next question as bar name
		- confirm to user whether can search, or not
* if the request is postback
	+ reset next question as "location info"
	+ if user's answer is okaytosearch=true
		- get stored query
		- search by BAR-NAVI API
		- reply result
  + else
		- reply as 'もう一度位置情報から教えて下さい'
* else
	+ ignore

## Use case
### User
* send location info

### Bot
* store location, and reply the next question(bar type)

### User
* send bar type

### Bot
* store bar type, and reply the next question(bar name)

### User
* send bar name

### Bot
* store bar name, and confirm to user whether can search, or not

### User
* click yes or no

### Bot
* if yes, then search and reply the result(10 [bar], and type is location)
