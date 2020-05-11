# Plugins

Mineflayer is pluggable; anyone can create a plugin that adds an even
higher level API on top of Mineflayer.

## Third Party Plugins

- [navigate](https://github.com/andrewrk/mineflayer-navigate/) - get around
  easily using A\* pathfinding. [YouTube Demo](https://www.youtube.com/watch?v=O6lQdmRz8eE)
- [radar](https://github.com/andrewrk/mineflayer-radar/) - web based radar
  interface using canvas and socket.io. [YouTube Demo](https://www.youtube.com/watch?v=FjDmAfcVulQ)
- [blockfinder](https://github.com/Darthfett/mineflayer-blockFinder) - find blocks in the 3D world
- [scaffold](https://github.com/andrewrk/mineflayer-scaffold) - get to
  a target destination even if you have to build or break blocks to do so.
  [YouTube Demo](http://youtu.be/jkg6psMUSE0)
- [auto-auth](https://github.com/G07cha/MineflayerAutoAuth) - chat-based bot authentication
- [Armor Manager](https://github.com/G07cha/MineflayerArmorManager) - automatic armor managment
- [Bloodhound](https://github.com/Nixes/mineflayer-bloodhound) - determine who and what is responsible for damage to another entity
- [tps](https://github.com/SiebeDW/mineflayer-tps) - get the current tps (processed tps)

## Build your own plugins

Here basic example on creating plugins

```js
function somePlugin(bot, options) {
  function someFunction() {
    bot.chat('Yay!');
  }
  bot.someFunction = someFunction;
  // adding method into bot
}

var bot = mineflayer.createBot(...);
bot.loadPlugin(somePlugin);
bot.once('login', function() {
  bot.someFunction(); // Yay!
});
```
