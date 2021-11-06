# Twitter bot



Firstly you need to figure out what profile the Twitter bot will be connected to. Log in with the twitter account you want to use. If you don't want it connected to your personal then simply create a new account



## Creating the bot

To create a Twitter bot go to https://developer.twitter.com/

Now click `Create new app`. Follow the instructions.

Remember to give the correct permission for what you want to do and also give the account a profile image and description.

Now go to `Keys and tokens` and get the API Key and Secret and the Access Token and Secret

This you will be using to connect nodejs to your account through a npm library called Twitter. 



## Programming the bot

To program the bot you can use this code

```javascript
var Twitter = require("twitter");
require("dotenv").config();

var client = new Twitter({
  consumer_key: process.env.consumer_key,
  consumer_secret: process.env.consumer_secret,
  access_token_key: process.env.access_token_key,
  access_token_secret: process.env.access_token_secret,
});

client.get("search/tweets", { q: "sunshine" }).then((tweets) => {
  tweets.statuses.forEach((tweet) => {
    console.log(tweet.text);
  });
});
```

This just show how to search for tweets but you can do lots more. Checkout the documentation here: https://www.npmjs.com/package/twitter



Here is a link for the Twitter api: https://developer.twitter.com/en/docs/twitter-api/v1



### Create a new Tweet

```javascript
const statusText = client
	.post("statuses/update", {
		status: "this is a reply to a tweet @account_name",
		in_reply_to_status_id: tweetToReplyToId,
	})
	.then((result) => {
		console.log(result);
	})
	.catch((error) => {
		console.log(error);
	});
```

`in_reply_to_status_id` is because i am replying to a tweet. Remember to add the persons account name in the update



### Follow an account

```javascript
client
    .post("friendships/create", { screen_name: account })
    .then((result) => {
        console.log(result);
    })
    .catch((error) => {
        console.log(error);
    });
```



## Like a tweet

```javascript
 client
     .post("favorites/create", { id: tweetId })
     .then((result) => {
         console.log(result);
     })
     .catch((error) => {
         console.log(error);
     });
```



### Retweet a tweet

```javascript
client
	.post("statuses/retweet", { id: tweetId })
	.then((result) => {
        console.log(result);
    })
	.catch((error) => {
        console.log(error);
    });
```

