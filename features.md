---
layout: default
keywords:
comments: false

title: DQS Documentation
description: Full documentation for all DQS features.

page_nav:
    prev:
        content: Home
        url: 'https://dqs.dewy.dev'
---

# DQS Documentation

**This page contains full documentation and overviews for all DQS commands and features.**

The DQS command prefix is `&`.

All in game commands use `/`.

## Command List & Summaries

All valid DQS commands and their summaries are listed below;

#### Information

- `&help` - Displays a link to this page and the support center.
- `&info` - Displays your account's biometrics and statistics.
- `&modules` - Displays currently active modules and their configurations.
- `&pos` - Get your queue position and the queue lengths from 2b2t.io

#### Modules

- `&autodisconnect` - Toggle and configure the Auto Disconnect module.
- `&autoreconnect` - Configure the Auto Reconnect module.
- `&autorespawn` - Toggle and configure the Auto Respawn module.
- `&focus` - Switch the account you'd like to be 'focused' on. **For those with additional accounts only.**
- `&notifications` - Toggle and configure the Notifications module.
- `&spammer` - Toggle and configure the Chat Spammer module.
- `&whitelist` - Toggle and configure the Whitelist module.

#### Chat

- `&relay` - Toggle the DQS chat relay.
- `&say` - Say something into public chat.
- `&whisper` - Whisper a message to a given username.

#### Taribone

- `&antiafk` - Activate Taribone's AntiAFK (6 hours)
- `&begin` - Start a Taribone session.
- `&end` - End a Taribone session.
- `&farm` - Automatically farms crops for you.
- `&follow` - Follow a given entity.
- `&goal` - Set a Taribone goal to be acted on with `&path`.
- `&goto` - Go to a set of given coordinates.
- `&invert` - Inverts your goal.
- `&path` - Path to a goal set earlier by `&goal`.
- `&pause` - Pause a currently running Taribone process.
- `&resume` - Resume a paused Taribone process.
- `&stop` - Kills a Taribone process.

#### Utilities

- `&recover` - In the event of a critical error, in which Auto Reconnect cannot function, use this to get back up and running.
- `&relog` - Relog / re-queue your account.
- `&signin` - Sign in using your IGN and Mojang email/pass.

#### Gateway

- `&auth and /auth` - Authenticate with the DQS Gateway.
- `/forget` - Log out of the DQS Gateway and re-authenticate. In-game command only.

## Key Concepts

### Taribone

Taribone is a headless pathfinding an automation implementation built to replicate Baritone functionality for DQS. It offers the same high quality pathfinding Baritone offers, with mob avoidance and the like included, controlled over Discord via the DQS bot.

Most useful Baritone commands have been implemented, though more are currently in development, including `&mine` and `&build`.

This is the first time a queueskip service has implemented pathfinding and automation on this scale, with DQS leading the charge into true cloud-based Minecraft automation.

### Gateway

The DQS gateway is the authentication system for gaining access to your DQS instance and, therefore, your account. Account sharing can be organised, and 2 or more players may take control of a single account at any time, with no extra charge.

### Modules

A module is a configurable and toggleable aspect of DQS that can be customised to meet your needs. An example would be the Notifications module, with its settings including but not limited to:

- Player In Range Notifs (true/false)
- Crystal Warnings (true/false)
- Almost Finished Queueing Notifs (true/false)
- Almost Finished Queueing Threshold (int)

## Gateway & Authentication

To authenticate using the gateway and gain access to your instance and account, you must connect to `dqs.dewy.dev` and use the `/auth` command in-game.

<img src="/core/assets/img/authcode.png" alt="Here's your six-digit code: 112743. Use the auth command in your channel to authenticate.">

Once you've typed `/auth`, a message like this will appear. As it says, you must use your **DQS channel provided in the Discord Server** to authenticate with the code given.

### Auth Command

You can use the `&auth` command in your channel to authenticate with the gateway.

##### Arguments

1. `<CODE>` - Authentication code given to you in game.
2. `<ACCOUNT ID>` - The account you wish to connect to. 

In order to authenticate with the Gateway with the code in the image above, I'd use this:

`&auth 122743 1`

Once you've authenticated once, you don't have to do it ever again.

### Forget Command

If you wish to re-authenticate with the Gateway, you can use the `/forget` command to sign out of the Gateway. Note that this command does NOT log your account out of the target server. It only logs you out of the Gateway.

This is an in-game exclusive command, and can only be run when connected to a DQS instance.

You can use `/forget` to stop automatically connecting to one account and authenticate to take control of another, if you've attached multiple accounts.

##### Syntax

- `/forget`

## Information Commands

**These commands are used for retrieving data.**

### Help Command

This command will display a message detailing where to find support and documentation. Here!

##### Syntax

- `&help`

##### Aliases

- `&?`
- `&h`
- `&halp`

### Info Command

This command will display the focused account's biometrics and statistics.

##### Syntax

- `&info`

##### Aliases

- `&i`
- `&stats`
- `&statistics`
- `&information`
- `&figures`
- `&biometrics`

### Modules Command

This command will display information about the status and configuration of all DQS modules.

##### Syntax

- `&modules`

##### Aliases

- `&m`
- `&mods`
- `&features`

### Pos Command

This command will display information about your current queue position and the live queue lengths, courtesy of the [2b2t.dev](https://2b2t.dev/) API.

##### Syntax

- `&pos`

##### Aliases

- `&qpos`
- `&position`

## Module Commands

**These commands are used to configure and toggle DQS modules.**

### Auto Disconnect Command

Toggle and configure the DQS Auto Disconnect module. This module is only active when not in control.

##### Syntax

- `&autodisconnect` - Toggles the module in its entirety.
- `&autodisconnect player` - Toggles automatically relogging if a player comes into range.
- `&autodisconnect crystal` - Toggles automatically relogging if a crystal comes into range.
- `&autodisconnect queue` - Toggles automatically relogging if you get close to the end of the queue, leaving you in an endless queue loop that can only end if you take control.
- `&autodisconnect queue [POSITION]` - Modify the threshold that used to tell if you are 'close to the end of the queue'. Must be greater than 5.

##### Aliases

- `&autodc`
- `&adc`

### Auto Reconnect Command

Configure the DQS Auto Reconnect module.

##### Syntax

- `&autoreconnect <DELAY>` - Modify the auto reconnect delay (seconds). Must be greater or equal to 90 to get around Hause's new measures. ._.

##### Aliases

- `&autorc`
- `&arc`

### Auto Respawn Command

Toggle and configure the DQS Auto Respawn module.

##### Syntax

- `&autorespawn` - Toggles the module in its entirety.
- `&autorespawn [DELAY]` - Modify the auto respawn delay (seconds).

##### Aliases

- `&autors`
- `&respawn`
- `&spawn`
- `&ars`

### Notifications Command

Toggle and configure the DQS Notifications module. Being as Taribone AntiAFK is not activated upon joining, it is crucial that you take control a bit before you finish queueing. This module can help with that.

##### Syntax

- `&notifications` - Toggles the module in its entirety.
- `&notifications player` - Toggles player in range notifications.
- `&notifications crystal` - Toggles crystal in range notifications.
- `&notifications queue` - Toggles 'close to the end of queue' notifications. 
- `&notifications queue [POSITION]` - Modify the threshold that used to tell if you are 'close to the end of the queue'. Must be greater than 5.

##### Aliases

- `&n`
- `&notifs`
- `&notify`
- `&dqswarn`

### Spammer Command

Toggle and configure the DQS Chat Spammer module. With this, you can advertise a shop, a client, or anything else. Just be considerate please.

##### Syntax

- `&spammer` - Toggles the module in its entirety.
- `&spammer display` - Display all messages in the DQS Chat Spammer registry.
- `&spammer add [MESSAGE]` - Add a message to the DQS Chat Spammer registry.
- `&spammer remove [MESSAGE ID]` - Removes a message from the DQS Chat Spammer registry.
- `&spammer delay [DELAY]` - Modify the Chat Spammer's delay in seconds. If this is too low, you may be kicked on certain servers, eg `oldfag.org`.

##### Aliases

- `&spam`
- `&chatspam`
- `&chatspammer`
- `&dqsspam`

### Whitelist Command

Toggle and configure the DQS Whitelist module.

##### Syntax

- `&whitelist` - Toggles the module in its entirety.
- `&whitelist display` - Display all players on the DQS Whitelist.
- `&whitelist add [IGN]` - Add a player to the DQS Whitelist.
- `&whitelist remove [IGN]` - Removes a player from the DQS Whitelist.

##### Aliases

- `&wl`
- `&wlist`

## Chat Commands

**These commands are used as utilities for working with chat in DQS.**

### Relay Command

Toggle the DQS Chat Relay. This will relay everything to your **DMs**, including 'position in queue' messages and whispers.

This can essentially act as mail forwarding.

##### Syntax

- `&relay`

##### Aliases

- `&cr`
- `&chatrelay`
- `&lolritter`

### Say Command

Send a message into public chat.

##### Syntax

- `&say <MESSAGE>` - Sends a given message into public chat. The message must be less than **255** characters in length.

##### Aliases

- `&chat`
- `&shout`
- `&pubchat`

### Whisper Command

Send a whisper to somebody. Keep in mind that currently there is no way to see if the recipient is actually online, so be careful with typos!

##### Syntax

- `&whisper <IGN> <MESSAGE>` - Sends a whisper to a given player. The message itself must be less than **250** characters in length.

##### Aliases

- `&w`
- `&pm`
- `&msg`

## Taribone Commands

**These commands are used for automation and pathfinding with DQS.**

### AntiAFK Command

Start up Taribone's AntiAFK, which will keep you connected to the main server for up to **6 hours.**

##### Syntax

- `&antiafk` - Starts an AntiAFK Taribone process.

### Begin Command

Begins a Taribone session. You can not run any other Taribone commands without running this one first.

##### Syntax

- `&begin` - Begins a Taribone session.

### End Command

Ends the currently active Taribone session, allowing you to take control again.

##### Syntax

- `&end` - Ends the currently active Taribone session.

### Farm Command

Automatically farms crops close by you, just like a Baritone `#farm` process.

##### Syntax

- `&farm` - Starts a farming Taribone process.

### Follow Command

Follow a given entity, just like a Baritone `#follow` process.

##### Syntax

- `&follow entities` - Follow all entities seen.
- `&follow player <IGN>` - Follow a player of a given name.
- `&follow entity <TYPE>` - Follow all entities of a given type.



### Goal Command

Set Taribone's goal to a set of coordinates, to later be acted on with `&path`.

##### Syntax

- `&goto <Y>` - Set Taribone's goal to a given Y level.
- `&goto <X> <Z>` - Set Taribone's goal to a given XZ coordinate.
- `&goto <X> <Y> <Z>` - Set Taribone's goal to an exact set of coordinates.

### Goto Command

Have your account path towards a given set of coordinates, just like a Baritone `#goto`.

##### Syntax

- `&goto <Y>` - Path towards a given Y level.
- `&goto <X> <Z>` - Path towards a given XZ coordinate.
- `&goto <X> <Y> <Z>` - Path towards an exact set of coordinates.

### Invert Command

Inverts your goal, ie you'll begin to head away from the goal, just like a `#invert` in normal Baritone.

##### Syntax

- `&invert` - Inverts your Taribone goal.

### Path Command

Have your account path towards the set of coordinates defined earlier with `&goal`.

##### Syntax

- `&path` - Path towards the goal set with `&goal`.

### Pause Command

Pause the currently active Taribone process.

##### Syntax

- `&pause` - Pauses the currently active Taribone process.

### Resume Command

Continue with a previously paused Taribone process.

##### Syntax

- `&resume` - Continue with a previously paused Taribone process.

### Stop Command

Cancels the running Taribone process.

##### Syntax

- `&stop` - Cancels the running Taribone process.
- `&stop force` - Forcefully kills the running Taribone process.

## Utility Commands

**These commands are general utilities to be used in specific circumstances.**

### Sign In Command

This command will log your Mojang account into DQS. Please see [here](#privacy) if you (understandably) have security concerns.

##### Syntax

- `&signin <IGN> <EMAIL> <PASSWORD>`

##### Aliases

- `&login`

### Relog Command

This command will relog and requeue you manually.

##### Syntax

- `&relog`

##### Aliases

- `&restart`

### Recover Command

If you get ratelimitied by Mojang's auth API or another catastrophic error occurs, you can use this command to get yourself back up and running.

##### Syntax

- `&recover`
