The Myplanet README
===================

This document aims to be the bare minimum needed to help folks
Myplaneteers contribute to the Pantzbot IRC bot.

Contributing
------------

Pantzbot is open for anyone at Myplanet to hack on. It's pretty hard to
break, and as of right now, we're not using it for anything mission
critical, so definitely do worry too much about jumping in and adding
some plugins.

Here are some quick pointers to help orientate you before your first
contribution:

- There are tons of community scripts available:
  https://github.com/github/hubot-scripts/blob/master/src/scripts/

- Community scripts are already pulled in as a package via `package.json`,
  so we just need to enable them in in `hubot-scripts.json`.

- Custom scripts can be placed as `scripts/*.coffee`. These do not need
  to be loaded in in `hubot-scripts.json`.

- A few scripts come with the actual hubot package (rather than the
  community scripts package) and are also pulled in via `package.json`.
We treat them a little like custom scripts, and load them by symlinking
them into our `scripts/` directory.

- You can test pantzbot locally by running it like this:

        brew install redis
        redis-server 2>&1 > /dev/null &
        npm install
        bash bin/hubot
        Hubot> hubot help

  If the functionality you wish to test requires configuration via
environment variables, you can start the bot like this:

        HUBOT_VAR1=value1 HUBOT_VAR2=value2 bash bin/hubot

- `npm-shrinkwrap.json` is the lockfile of specific npm packages that
  should be installed, and is derived from the `package.json` file. The
easiest way to upgrade packages is to erase the lockfile and run `npm
install` to regenerate it fresh.

- Some scripts will have node package dependencies that will need to be
  added to `package.json`. (Make sure to regenerate
`npm-shrinkwrap.json` afterward.)

- We host pantzbot on Heroku, a service like Acquia, but for
  node.js apps rather than Drupal. Once you've tested your changes to
pantzbot, you'll need to get Heroku access in order to push it live.
  - Create a Heroku account:
  - Ask anyone with prior access (most obviously patcon or mparker17),
    and they should be able to grant you access via this page:
https://dashboard.heroku.com/apps/pantzbot/collaborators
  - You'll probably want to install the heroku gem for convenience:
            gem install heroku

  - If you need to set any configurations via environment variables, so
    it like so:
            heroku config:set ENVVAR1=value1 ENVVAR2=value2

  - Lastly, add the git remote and push:
            git remote add heroku git@heroku.com:pantzbot.git
            git push heroku