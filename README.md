# JenkinsSlack

Start a build in Jenkins using a Slack Command

## Features
- Start a build
  - `/jenkins MyAwesomeApp`
- Start a parameterized build
  - `/jenkins MyAwesomeApp param1=value1 param2=value2`
  
## In Progress
- Error handling when staring the build fails

## Installation

### 1. Setup Slack integrations

- Create a new "Slash Command"
  - Name command `/jenkins`
  - Set the URL to the url of your Heroku instance (created in [step 3](#3-spin-up-heroku-instance))
  - Method should be POST
- Create a new "Inbound Webhook"
  - Set the channel you would like to post to
  - Set the bot name `Anything That You Like`

### 2. Setup environment variables on your Heroku instance

- Required environment variables
 - `SLACK_TOKEN` - token from your "Slash Command"
 - `JENKINS_URL` - URL to your jenkins host
   - NOTE: if your jenkins requires authentication url will look like `http://user:auth-token@your-jenkins-host:port`. To obtain user authentication token click your name on the top right corner on every page, then click "Configure" to see your API token. (The URL `$host/me/configure` is a good shortcut.), 
 - `JENKINS_TOKEN` - API token for jenkins job. 
   - NOTE: you will need to enable remote builds for every job you would like to invoke remotely. Turn on "Trigger builds remotely (e.g., from scripts)" checkbox under `Bild Triggers` section in job configuration. Then input any random token and save. You will need to use the same token for all jobs you are planning to build from slack remotely, otherwise jenkins will fail with authentication error.
- `SLACK_WEBHOOK_URL` - your incoming webhook URL
  
### 3. Spin up Heroku instance

[![Deploy](https://www.herokucdn.com/deploy/button.png)](https://heroku.com/deploy?template=https://github.com/tonythomas28/JenkinsSlack)
  
- Or You can even deploy it in you local, but Make sure the Above said environment variables is set

### 4. Execute command in Slack

```
/jenkins <buildName>
```

