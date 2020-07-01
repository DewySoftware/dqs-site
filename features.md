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

This command will display information about your current queue position and the live queue lengths, courtesy of the [2b2t.dev](https://2b2t.dev/) and [2b2t.io](https://2b2t.io/api) APIs.

##### Syntax

- `&pos`

##### Aliases

- `&qpos`
- `&queuepos`
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
- `&autodisconnect queue [POSITION]` - Modify the threshold that is used to tell if you are 'close to the end of the queue'. Must be greater than 5.
- `&autodisconnect hp` - Toggles automatically relogging if your health gets below the low HP threshold.
- `&autodisconnect hp [THRESHOLD]` - Modify the low HP threshold that is used to tell if you are close to death. Must be less than 9.5

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
- `&notifications hp` - Toggles low HP notifications. 
- `&notifications hp [THRESHOLD]` - Modify the threshold that used to tell if you are close to death. Must be less than 9.5

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

- `&goal <Y>` - Set Taribone's goal to a given Y level.
- `&goal <X> <Z>` - Set Taribone's goal to a given XZ coordinate.
- `&goal <X> <Y> <Z>` - Set Taribone's goal to an exact set of coordinates.

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

### Focus Command

This command can be used to focus on another account if you have additional accounts attached to your plan.

##### Syntax

- `&focus <IGN>` - Focus on a given account.

## Modules

### Auto Disconnect

**Command:** `&autodisconnect`

This module will automatically disconnect you depending on whether certain events occur.

##### Full Explanation

This module is fully configurable and toggleable, and does NOT run when a player is in control. It runs when a Taribone session is active and will end the Taribone session on disconnect.

These events include:

- A player coming into range
- A crystal appearing in range
- Nearly reaching the end of queue

For those migrating from **DQS 2**, this can be used as a ForeverQ alternative.

### Auto Reconnect

**Command:** `&autoreconnect`

This module is responsible for automatically reconnecting you when you get kicked / disconnected.

##### Full Explanation

This module is configurable, but NOT toggleable. This module is on at all times, no matter what.

The seconds delay must be above 90 due to Hause's new anti-DQS measures and Mojang's authentication API rate limit. A fix is currently being investigated.

### Auto Respawn

**Command:** `&autorespawn`

This module will automatically respawn you if you die.

##### Full Explanation

This module is NOT active while you are in control. When you die, you will automatically respawn with this module after a configurable delay of 1 or more seconds.

### Notifications

**Command:** `&notifications`

This module is responsible for rolling out notifications for different events to do with your account(s).

##### Full Explanation

Notifications are ALWAYS sent in DMs, not the channel, no matter what. You will receive notifications regardless of whether you are focused on the account the notification is referring to.

The events that can trigger notifications include:

- A player coming into range
- A crystal appearing in range
- Nearly reaching the end of queue
- Relogging of any kind

This is the new, modernised version of **DQSWarn**.

### Spammer

**Command:** `&spam`

This module acts as a fully configurable chat spammer.

##### Full Explanation

The DQS Chat Spammer registry is a list of all spam messages added by the user. Each message on that list has an ID, which can change based on the list's length and the removal of other spam messages on the registry.

Spam message IDs can be viewed when a new spam message is added, or with the `&spam display` command.

### Whitelist

**Command:** `&whitelist`

This module acts as a fully configurable and toggleable whitelist, useful for account sharing, which can be done without restriction, free of charge.

##### Full Explanation

This module is enabled by default for security, though it can be disabled. You can add and remove players from the whitelist for account sharing, which can be done for free. DM Dewy to organise account sharing for your instance.

## Focusing & Additional Accounts

Using DQS with more than one account can be done for an extra £5/mo per account. Focusing allows you to change 'focus' on which account you'd like to command.

For example, if I had 2 accounts, `Johanne` and `No0dle`, and I was currently focused on `Johanne`, I'd be able to modify the DQS instance for `Johanne` and their settings.

If I were to `&focus` on `No0dle`, I'd be modifying the DQS instance for `No0dle` instead.

Keep in mind you may have to `/forget` in the Gateway in order to take control of different accounts, to get around the authentication caching system.

Dewy will DM you a list of accounts registered to your name and their IDs, that you will use with Gateway authentication. Here's an example:

- Johanne (1): `&auth <CODE> 1`
- No0dle (2): `&auth <CODE> 2`

## Event Scheduling

**The DQS service undergoes a restart every 6 days.**

During that time, your account will NOT be connected to any server, and your instance will not be active.

Your settings are saved however, don't worry.

**DQS will receive updates once every 18 days.**

These updates will include new features, bug fixes and improvements on existing features.

## Privacy

The nature of these services makes them big targets. This is why DQS has the best security of all queueskip services currently existing, to keep your account and its secrets safe.

Dewy is well known to be unbiased and not leaning towards any particular ingame group or faction.

Much like the coming VoQ service from the Vortex Coalition, all account details are encrypted and locked in a box, to prevent any attacker from snatching them if they were to get into the database. They'd need the jars, which are heavily obfuscated and protected with HWID auth and the like, to stop any potential attackers.

Not to mention that the DQS server provider, Hetzner, provides excellent security, along with top-end DDOS protection and firewalling, to keep DQS up and running no matter its opposition.

Feel free to ask current subscribers about their experiences with DQS's security. We don't lie around here, we ain't cheese.

## Other Servers

While DQS is intended for 2B2T, it isn't bound to it. When signing up, you gain the option to choose which 'target server' you'd like your instance to always be connected to. This server can be anything that supports 1.12.2 Minecraft clients, including **Constantiam**, **Oldfag** and many more.
