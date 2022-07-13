# Commands.

## Overview

* The top-level command is `/stb`\

* All commands are subcommands of `/stb`, e.g. `/stb getcfg`\

* Tab-completion is comprehensively supported - press Tab at any time during typing a command, and STB will attempt to complete the command or argument for you.

## Admin Commands

### Setting an Item or Block's SCU (energy) Level
<dl><dt>/stb charge &lt;new-charge-amount&gt;</dt>

If you're holding a chargeable item or targeting a chargeable block, this command will let you set its SCU level directly to the given amount, without the need to connect it to an energy net or install an energy cell.  Free energy!  You can't set the charge to less than 0 or greater than the item's max charge (see the item tooltip or charge meter in the block's GUI to get the maximum charge level for the item/block).

See [Energy](../SensibleToolbox/Items/energy.md) for more information on how charge, or SCU, works.

### Toggling Debugging

/stb debug\
This command is equivalent to doing `/stb set debug_level 1` if the current debug level is 0, and `/stb set debug_level 0` if the current debug level is not 0. I.e. it toggles between no debugging and basic level 1 debugging. Debug messages are sent to the console and server.log.

### Obtaining Items
<dl><dt>/stb give &lt;item-id&gt; [&lt;amount&gt;] [&lt;player-name&gt;]</dt>

This command gives STB items directly to you or another player without the need to craft them.  For a list of valid item ID's, see [Item Reference](../SensibleToolbox/item-reference.md).  Note that Tab completion can be very helpful here.
If an amount is specified, multiple items can be given.
If a player name is specified and that player is online, items will be given to that player instead.
</dl>

### Getting a Config Setting
<dt>/stb getcfg [&lt;item&gt;]</dt>

This command lets you view the setting of the given [Configuration](../SensibleToolbox/configuration.md) item, or all items if no argument is given.


### Changing a Config Setting
<dl><dt>/stb setcfg &lt;item&gt; &lt;new-value&gt;</dt>

This command lets you update the setting of a given [Configuration](../SensibleToolbox/configuration.md) item.
</dl>

### Forcing a Save
<dl><dt>/stb save</dt>

This command forces an immediate save to database of all persisted data.  Data is normally saved every 30 seconds (but see the <strong>save_interval</strong> [Configuration](../SensibleToolbox/configuration.md) item), and when the server is stopped or reloaded, but you can use this command to force a save if necessary.
</dl>

### Displaying Known Blocks
<dl><dt>/stb show [-w &lt;world-name&gt;] [-type &lt;item-id&gt;] [&lt;location&gt;]</dt>

This command allows listing of all known STB blocks in the world, and/or inspection of the data stored on that block.  The default action if no options are given is to list all known blocks in all worlds with their locations (location in the form X,Y,Z,WORLD)

With the -w option, only blocks in the given world will be shown.

With the -type option, only blocks of the given type will be shown.  See [Item Reference](../SensibleToolbox/item-reference.md) for a list of all item and block types.

If a location is given (in the form X,Y,Z,WORLD), detailed information for the block at that location will be displayed.  If you are player (rather than on the console), you can also give "." as a location which is taken to mean "the block you are targeting".
</dl>

## Player Commands
### Searching for Recipes

/stb recipe \<string>\
If you're holding a Recipe Book, this will open the Recipe Book GUI, filtered to show only those items which match the given `<string>`. E.g. `/stb recipe diamond` will show the recipes for all items with "diamond" in the item name. If you are near a crafting bench and have it targeted, the recipe view will also include a "Fabricate" button.

### Renaming Captured Animals
<dl><dt>/stb rename &lt;new-name&gt;</dt>

If you're holding an Ender Leash with a captured animal, this command allows you to rename the captured animal.  This comes with a level cost (unless you have the <strong>stb.commands.rename.free</strong> permission) - the default is 5 levels, but this is configurable via the <strong>rename_level cost</strong> [Configuration](../SensibleToolbox/configuration.md) item.
</dl>

### Adding a Friend

/stb friend \<player-name-or-id>\
Use this command to add a player as a friend. Players who you trust as friends can access any STb block you place in Restricted mode (via the block's GUI). You can use a player name if the player is online at the time, or if you know the player's UUID, you can also add offline players as friends.

### Removing a Friend

/stb unfriend \<player-name-or-id>\
Use this command to remove a player as a friend. That player will no longer be able to access any of your Restricted mode STB blocks. The same syntax applies as for the `/stb friend` command.\
