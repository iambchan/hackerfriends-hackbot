
# How I added hubot to our slack channel
Mostly copied from slackhq/hubot-slack github

### FOLLOW THE INSTRUCTIONS IN THIS PAGE:
https://github.com/slackhq/hubot-slack
```
	npm install -g hubot coffee-script yo generator-hubot
	mkdir -p /path/to/hubot
	cd /path/to/hubot
	yo hubot
	npm install hubot-slack --save
```

### Get hubot slack token
a. Go into slack integrations for your team
b. API token will be available after adding it.

### Edit procfile
Edit your Procfile and change it to use the slack adapter: (located in root of folder after installing in step 1)
```
 	web: bin/hubot --adapter slack
```


### Run and test locally
```
HUBOT_SLACK_TOKEN=<insert valid token here> ./bin/hubot --adapter slack
```
	
Go into slack and hubot's status should be green -- online


### Create heroku app and configure add on
```
 > heroku create hackerfriends-hackbot

 > heroku addons:create redistogo:nano
```

I couldn't do this without specifying the app, so I went to the dashboard and added 'Redis to go' manually.
	https://elements.heroku.com/addons/redistogo#addon-plans
	https://dashboard.heroku.com/apps/hackerfriends-hackbot

### Add config variables

You can do this in your dashboard settings https://dashboard.heroku.com/apps/hackerfriends-hackbot/settings 
	or terminal:
```
heroku config:add HEROKU_URL=https://hackerfriends-hackbot.herokuapp.com

heroku config:add HUBOT_SLACK_TOKEN= <token from generated from slack integrations>
```

### Push to deploy to heroku
Remember to add remote 
```
git remote add heroku https://git.heroku.com/hackerfriends-hackbot.
```

Deploy: 
```
git push heroku master
```
