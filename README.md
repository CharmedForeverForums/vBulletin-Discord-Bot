# vBulletin-Discord-Bot

Gets updates from a vBulletin RSS feed and posts them in a discord channel. 

## Setup

Get a bot token and a channel ID by following the instructions found at: https://github.com/Chikachi/DiscordIntegration/wiki/How-to-get-a-token-and-channel-ID-for-Discord

Also enable the RSS feed for your vBulletin board, and get the URL. See: http://bfy.tw/GpLA

Alter the [config.ini](config.ini) file to include this bot token, channel id, and RSS feed URL.

eg.

```buildoutcfg
[Options]
update_frequency = 60
multi_line = true
bot_token = my.bot.token
channel_id = 0123456789012345
rss_feed_url = http://my-forum.com/external?type=rss2
message_format = `New Post on MyForum!`
    **{post_title}** _by {post_author}_
    **Link:** {post_link}
    **Preview:**
    {post_preview}
```

You can change `update_frequency` to change how often the forum is polled, this value is in seconds.

The message format defines what the bot will post in discord. The options in curly brackets, {}, will be replaced as follows:

| Option | Replacement |
| --- | --- |
| {post_title} | The title of the post |
| {post_author} | The author of the post |
| {post_link} | A link to the post |
| {post_preview} | A small preview of the post |

You can format the messages as you like, for example if you just want the post title and a preview:

```buildoutcfg
message_format = {post_title} - {post_preview}
```

If you have newlines in your message format you will need to add a tab at the beginning of the line for the config file to correctly parse:

Good:
```
message_format = First line!
    Second Line...
    ...Third line
```

Bad:
```
message_format = First line!
Second line...
...Third line
```

## Running the Script

### Windows

If you're using Windows you can use the latest release here: https://github.com/LucyGoosey/vBulletin-Discord-Bot/releases/

First edit the `config.ini` as described above, and then just run the `.exe` and off you go!

If, when you run the `.exe`, the window immediately closes please try running the program from within a command prompt. The program is likely showing an error but the window is closing too quickly for it to be seen.

### Everything Else

This project uses Python 3.8 and pipenv.

Python 3: https://www.python.org

Pipenv: `pip install --user pipenv`

You can download python from the link above, and once python is installed you can run the command `pip install --user pipenv` from within a command-line/terminal to install pipenv.

After Python and Pipenv are installed, open a command-line/terminal in the directory the code is based and run the following commands:

```
pipenv install --ignore-pipfile
pipenv run python vbulletin-discord-bot.py
```

Off you go!

## Example

The bot will make a discord post similar to the below when a new forum post is made:

![Example image](ExamplePost.png)

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
