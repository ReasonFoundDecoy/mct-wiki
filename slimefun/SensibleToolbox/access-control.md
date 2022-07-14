# Access Control
* Permission-based: each type of item has one permission node, and each type of block has four permission nodes which define the actions that players may take with them.

* Block-based: STB defines access levels for individual STB blocks - Public & Private. This controls who may open the block's GUI (if it has one), and who may interact with the block's inventory (via item routers).

* Inventory-based: STB will use other plugins (currently only LWC, but maybe others in future) to protect vanilla inventories from access by STB items and blocks such as the Advanced Recipe Book and the [Item Routers](../Items/routing.md).


# Permission-Based Access
This is described in more detail [here](../permissions.md).


# Block-Based Access
Most STB blocks have a GUI button (usually in the top-right corner) allowing the block's owner (and only the block's owner) to toggle the block's current access level. There are currently two access levels:

* Public - anyone can interact with the block
* Private - only the block's owner can interact with the block

"Interact" means to open a block's GUI by right-clicking it, and to insert/extract items from that GUI.

This also applies to [Item Routers](../Items/routing.md): if a block is marked as private, then an Item Router will only be able to insert/extract items if it is owned by the same player.

One exception: players with the <b>stb.access.any</b> permission node are not subject to access checks. It is recommended that only server admins are given this node (it is only available to server ops by default). This node does not apply to Item Router access, only to players who directly interact with STB blocks.



# LWC Support
[LWC](https://dev.bukkit.org/projects/lwc) is a powerful block protection plugin, which Sensible Toolbox (v0.0.2+) will integrate with, if installed:

[Item Routers](../Items/routing.md) will only interact with vanilla inventories for which the Item Router's owner actually has LWC access rights
The Advanced Recipe Book will only pull ingredients from vanilla inventories for which the player actually has LWC access rights
You will require a version of LWC with UUID support; at the time of writing (Jul 2014), this means a development build from here.

{% hint style="info" %}
MCTantrum does not use LWC, however the same rule applies for access rights inside a claim.
{% endhint %}