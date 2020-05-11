# Running bot on android

Here quick setup for running bot on android device using [Termux](https://termux.com/).

## Steps

### Install Termux

Install [Termux](https://termux.com/) and start it.

### Setup

First, update the Termux packages

```bash
pkg update -y
```

Now install `nodejs`, `npm` should be automaticaly installed as well:

```bash
pkg install nodejs -y
```

Finally, install `mineflayer` library:

```bash
npm install mineflayer@latest
```

Repeat process if error happened.

### Editing script

Install nano for editing script, you can use your favourite editor:

```bash
pkg install nano -y
```

Now you can use nano to creare / edit your script. Example:

```bash
nano myscript.js
```

### Start your bot

Start the bot:

```bash
node myscript.js
```

### Updating library

First, update `nodejs` and `npm`:

```bash
pkg install nodejs -y
```

Then update `mineflayer`:

```bash
npm install mineflayer@latest
```
