## SkybotV2 :: A Lua powered Discord Bot

### This is still an early prototype, so everything is subject to change

SkybotV2 is a Discord bot written in Lua and utilizes Luvit and the Discordia library.

The main functionality of the bot will come from an assortment of plugins included with the bot.

Currently all commands are processed within commands.lua within the netlib. The only functionality right now is to output Factoids.

## Setup

### Windows

To run the bot under Windows, execute the InstallLuvit.ps1 script. After running the script, go to [SQLite.org Downloads](https://sqlite.org/download.html) and get the corresponding pre-compiled Windows Binaries for your system. From the archive copy the sqlite3.ddl into the project directory. That's it.

### Linux

The Setup script should get everything running. If you want to do it manually, you need to grab [Luvit](https://luvit.io/) and install it yourself as well as copy the correct files around. What should be copied can be found within the Setup script (location of libsqlite3.so can change based on the distro you use):

```
#!/bin/bash
#Installer for SkybotV2

# Install Luvit
curl -L https://github.com/luvit/lit/raw/master/get-lit.sh | sh
cp lit /usr/local/bin/lit
cp luvi /usr/local/bin/luvi
cp luvit /usr/local/bin/luvit

# Copy libsqlite3.so to the project directory
cp /usr/lib/x86_64-linux-gnu/libsqlite3.so.0 libsqlite3.so

# Generate the default config
cp blacklist.lua.default blacklist.lua
cp config.lua.default config.lua
```

## Configuration

Configuring the bot is simple, it currently features two files that are supposed to be edited:

### blacklist.lua
```
-- This file lets you block certain users based on their ID
-- Example: BlockedUsers = {"123456","234567",...}
BlockedUsers = {}
return BlockedUsers
```

### config.lua
```
-- This file stores the config for the bot, mainly the token and the trigger (more to come)
-- Just copy and paste your token into the field and you are good to go
-- Example: Settings = {token = "ThisIsWhereYourTokenGoes", trigger = "~"}
local Settings = {token = "", trigger = "!"}

function GetConfig(name)
  return Settings[name]
end
```


## Dependencies

This bot is built using following projects:
* [Luvit](https://github.com/luvit/luvit)
* [Lit-Sqlite3](https://github.com/SinisterRectus/lit-sqlite3)*

\*This plugin has been patched to include a following fix: [stepelu/lua-ljsqlite3/FIX: rowexec()](https://github.com/stepelu/lua-ljsqlite3/commit/b954905003880105926ed51a01df2b5ac32701f1)

##

**Thanks to Neffi from the Skyrimmods Discord for helping out with this project and providing valuable feedback.**
##

**Due to a mistake, I commited as Netrve instead of Dakraid. Both are the same person.**