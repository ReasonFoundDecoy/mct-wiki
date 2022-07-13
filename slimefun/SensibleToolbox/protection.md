# Protection
Sensible Toolbox has some support for protecting blocks and inventories from griefing on multiplayer servers.

## Block Protection
There are several possible methods of block protection, protecting blocks in the world from modification by various STB devices.  STB will make every attempt to honour any protection mechanism in place on the server.

There is a [config](slimefun/SensibleToolbox/configuration.md) setting - <strong>block_protection</strong> - to choose the active protection method.  Most methods require an additional plugin to be installed.

<table><tbody><tr><th>Config setting</th><th>Required Plugin</th><th>Notes</th></tr>
<tr><th>best</th><td><em>varies</em></td><td>Automatically choose the optimal method, depending on what plugin(s) are installed</td></tr>
<tr><th>worldguard</th><td>WorldGuard</td><td>Use the WorldGuard plugin for block protection</td></tr>
<tr><th>precious_stones</th><td>PreciousStones</td><td>Use the Precious Stones plugin for block protection</td></tr>
<tr><th>bukkit</th><td>-</td><td>Fire Bukkit BlockPlaceEvent/BlockBreakEvent to check if blocks may be placed or broken, and see if the event gets cancelled <em>NOTE: this protection type has been removed in dev build #108 due to some potentially server-crashing bugs</em></td></tr>
<tr><th>none</th><td>-</td><td>Do no protection at all.  Only recommended for single player or whitelisted servers with a highly trusted player-</td></tr>
</tbody></table>

The default setting is <strong>best</strong>: this will use WorldGuard or PreciousStones if either of those plugins are installed, and will fall back to Bukkit event firing otherwise.

## Inventory Protection
There are also several methods of inventory protection.  Inventory protection protects vanilla inventory blocks from access by STB blocks such as the [Item Router](slimefun/SensibleToolbox/Items/routing.md) and Advanced Recipe Book.  (STB blocks which hold inventories have their own access protection, which can be adjust in the GUI of most STB blocks).

Again, there is a [config](slimefun/SensibleToolbox/configuration.md) setting - <strong>inventory_protection</strong> - to choose the active method:

<table><tbody><tr><th>Config setting</th><th>Required Plugin</th><th>Notes</th></tr>
<tr><th>best</th><td><em>varies</em></td><td>Automatically choose the best protection method</td></tr>
<tr><th>lwc</th><td>LWC</td><td>Use the LWC plugin for inventory protection.  You will need to <a href="http://dev.bukkit.org/bukkit-plugins/lwc/" rel="nofollow">up-to-date development build of LWC with UUID support from here</a></td></tr>
<tr><th>worldguard</th><td>WorldGuard</td><td>Use the WorldGuard plugin for inventory protection.  UUID support is not yet available in WorldGuard; see below more information on the implications of this.</td></tr>
<tr><th>none</th><td>-</td><td>No inventory protection at all.  Only recommended for single player or whitelisted servers with a highly trusted player-base</td></tr>
</tbody></table>

## UUID Support
All STB blocks store owner information in the form of a player UUID (this is the primary reason why STB is only supported on CraftBukkit 1.7.9 and later).  It is this UUID which is used to check the access an STB block such as the Item Router or Auto Builder has when it wants to modify a block in the world, or the contents of a vanilla inventory.

Unfortunately, UUID support is still somewhat patchy in protection plugins at this time (July 2014); most plugin expect a Bukkit Player object.  As a workaround STB can get this object, but the impact is that block protection will only work when the player who owns the STB block is actually online (otherwise STB can't get the Player object for the owner UUID).  As an example, if you place an Auto Builder, start it digging a big hole and log out while it's running, it will stop.

An exception is LWC, where recent builds do have UUID support.  This means that Item Routers can pull from LWC-protected vanilla chests etc. when the Item Router owner is offline.  Hopefully other plugins (WorldGuard etc.) will also add UUID support soon.