# anonymous-slack
A service you can upload to Heroku to be able to send anonymous messages to colleagues.

How to set up? As a slack administrator,

0. Create a new heroku app with the Go buildpack: https://github.com/kr/heroku-buildpack-go

1. Add a Slash command, for example, `/anon` . Set the URL in Slack to your Heroku URL. The resulting slack "token" should be set as a Heroku environment variable:

   heroku config:set INCOMING_SLACK_TOKEN=XXX

2. Add a Slash Incoming webhook. The resulting "webhook url" should be set as the Heroku
   environment variable:

   heroku config:set INCOMING_SLACK_WEBHOOK=https://hooks.slack.com/services/BLAH/BLAH/BLAH

3. Deploy to heroku.

   git push heroku master

Success! Now if you direct-message @slackbot with a message like the following:

    /anon @somebodyelse hey this is anonymous

A random animal will in turn direct message `@username` with your message. Be
nice!
