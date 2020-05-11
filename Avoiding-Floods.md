# Avoiding Flods

Most of floods from `bot.chat` method, so we need becareful when using it. Or we can build better `bot.chat` method.

## Example

```js
var mineflayer = require("mineflayer");
var bot = mineflayer.createBot({
  host: "localhost",
  port: 25565,
  username: "email@example.com",
  password: "12345678",
  version: "1.8.8",
});

function sayPlugin(bot, options) {
  function getTime() {
    // get current time
    return Math.floor(Date.now());
  }
  function say(message) {
    if (
      getTime() - bot.say_prev > bot.say_interval ||
      bot.say_prev_msg != message
    ) {
      // if time pass after previous message or current message difer from previous message, then the message sent to chat
      bot.say_prev_msg = message;
      bot.chat(message);
      return true;
    }
    return false;
  }
  function say_after(message, time) {
    setTimeout(() => {
      say(message);
    }, time);
  }
  bot.say_prev_msg = null;
  bot.say_interval = 2 * 1000;
  bot.say_prev = 0;
  bot.say = say;
  bot.say_after = say_after;
}

bot.loadPlugin(sayPlugin);

bot.on("chat", function (username, message) {
  // a function called for each chat received by the bot from the server
  if (username === bot.username) return; // if the sender is current bot, would not execute next code (spam prevention)
  bot.say(message); // this will send `message` to the chat using method from sayPlugin
});
bot.on("error", (err) => console.log(err)); // print any error to the console
```
