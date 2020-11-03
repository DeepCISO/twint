# twint

This is a fork of [twintproject/twint](https://github.com/twintproject/twint) which is focused on Elasticsearch compatibility, performance, and DeepCISO's specific needs. When in doubt, we tend to rip things out (ex. geolocation in tweets, geopy dependency), so this is not 100% compatible with twint upstream.

We will not be supporting this in its current form. Issues requesting support will be closed without response.

## Installing

```bash
git clone --depth=1 https://github.com/DeepCISO/elastwint.git
cd elastwint
pip3 install . -r requirements.txt
```

## CLI
A few simple examples:

- `twint -u username` - Scrape all the Tweets of a *user* (doesn't include **retweets** but includes **replies**).
- `twint -u username -s pineapple` - Scrape all Tweets from the *user*'s timeline containing _pineapple_.
- `twint -s pineapple` - Collect every Tweet containing *pineapple* from everyone's Tweets.
- `twint -u username --year 2014` - Collect Tweets that were tweeted **before** 2014.
- `twint -u username --since "2015-12-20 20:30:15"` - Collect Tweets that were tweeted since 2015-12-20 20:30:15.
- `twint -u username --since 2015-12-20` - Collect Tweets that were tweeted since 2015-12-20 00:00:00.
- `twint -u username -o file.txt` - Scrape Tweets and save to file.txt.
- `twint -u username -o file.csv --csv` - Scrape Tweets and save as a csv file.
- `twint -u username --email --phone` - Show Tweets that might have phone numbers or email addresses.
- `twint -s "Donald Trump" --verified` - Display Tweets by verified users that Tweeted about Donald Trump.
- `twint -g="48.880048,2.385939,1km" -o file.csv --csv` - Scrape Tweets from a radius of 1km around a place in Paris and export them to a csv file.
- `twint -u username -es localhost:9200` - Output Tweets to Elasticsearch
- `twint -u username -o file.json --json` - Scrape Tweets and save as a json file.
- `twint -u username --database tweets.db` - Save Tweets to a SQLite database.
- `twint -u username --followers` - Scrape a Twitter user's followers.
- `twint -u username --following` - Scrape who a Twitter user follows.
- `twint -u username --favorites` - Collect all the Tweets a user has favorited (gathers ~3200 tweet).
- `twint -u username --following --user-full` - Collect full user information a person follows
- `twint -u username --timeline` - Use an effective method to gather Tweets from a user's profile (Gathers ~3200 Tweets, including **retweets** & **replies**).
- `twint -u username --retweets` - Use a quick method to gather the last 900 Tweets (that includes retweets) from a user's profile.
- `twint -u username --resume resume_file.txt` - Resume a search starting from the last saved scroll-id.

More detail about the commands and options are located in the [twint wiki](https://github.com/twintproject/twint/wiki/Commands)