# Usage

Without version specified, the version of the server will be guessed automatically, you can set a specific one using the version option.
For example `version:"1.8"`.

For full method / api details see the official Mineflayer documentation at [API - mineflayer](http://mineflayer.prismarine.js.org/#/api).

## Echo Example

```js
var mineflayer = require("mineflayer");
var bot = mineflayer.createBot({
  host: "localhost", // the server address (default is localhost)
  port: 25565, // optional
  username: "email@example.com", // email and password are required only for
  password: "12345678", // online-mode=true servers
  version: "1.8.8", // "1.8.8" corresponds to the version for the server, put false for auto detect version
});
bot.on("chat", function (username, message) {
  // a function called for each chat received by the bot from the server
  if (username === bot.username) return; // if the sender is current bot, would not execute next code (spam prevention)
  bot.chat(message); // this will send `message` to the chat
});
bot.on("error", (err) => console.log(err)); // print any error to the console
```

## Debug

You can enable some protocol debugging output using `DEBUG` environment variable:

```bash
DEBUG="minecraft-protocol" node [...]
```

On windows :

```bat
set DEBUG=minecraft-protocol
node your_script.js
```

## More Examples

- In the [examples](https://github.com/PrismarineJS/mineflayer/tree/master/examples) folder.
- [vogonistic's REPL bot](https://gist.github.com/vogonistic/4631678)
