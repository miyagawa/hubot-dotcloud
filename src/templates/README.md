Hubot
=====

This is a version of GitHub's Campfire bot, hubot.  He's pretty cool.

This version is designed to be deployed on DotCloud.

Playing with Hubot
==================

You'll need to install the necessary dependencies for hubot.  All of
those dependencies are provided by [npm](http://npmjs.org).

    % bin/hubot

You'll see some startup output about where your scripts come from.

    Loading deploy-local scripts at /Users/me/nubot/scripts
    Loading hubot core scripts for relative scripts at /Users/me/nubot/src/hubot/scripts
    Hubot: the Shell.
    { id: '1', name: 'Shell' }
    Loading hubot-scripts from /Users/me/nubot/hubot-scripts.json
    Successfully connected to Redis

Then you can interact with Hubot by typing `hubot help`.

    hubot help

    animate me <query>  - The same thing as `image me`, except adds a few
    convert me <expression> to <units> - Convert expression to given units.
    help - Displays all of the help commands that Hubot knows about.
    ...

Take a look at the scripts in the `./scripts` folder for examples.
Delete any scripts you think are silly.  Add whatever functionality you
want hubot to have.


hubot-scripts
=============

There will inevitably be functionality that everyone will want.  Instead
of adding it to hubot itself, you can submit pull requests to
[hubot-scripts](https://github.com/github/hubot-scripts).  To enable
scripts from the hubot-scripts package, add the script name to the
hubot-scripts.json file in this repo.

Deployment
==========

Clone [hubot-dotcloud](https://github.com/miyagawa/hubot-dotcloud) and
the repository has all the modifications you need for a deployment on
DotCloud.

    % git clone git://github.com/miyagawa/hubot-dotcloud.git
    % cd hubot-dotcloud
    % dotcloud create hubot
    % dotcloud push hubot

Hubot also needs four environmental variables set to run and to keep him
running on DotCloud.

Campfire Variables
------------------

Create a separate user for your bot and get their token from the web UI.

    % dotcloud var hubot set HUBOT_CAMPFIRE_TOKEN="..."

Get the numeric ids of the rooms you want the bot to join, comma
delimited.

    % dotcloud var hubot set HUBOT_CAMPFIRE_ROOMS="42,1024"

Add the subdomain hubot should connect to. If you web URL looks like
`http://mysubdomain.campfirenow.com` then you'd add it like this.

    % dotcloud var hubot set HUBOT_CAMPFIRE_ACCOUNT="mysubdomain"

Restart the bot
---------------
You may want to get comfortable with `dotcloud restart hubot.robot`
if you're having issues.
