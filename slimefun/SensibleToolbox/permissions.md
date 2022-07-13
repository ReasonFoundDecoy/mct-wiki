# Permissions
STB will work with any superperms-supporting permissions plugin.  The following permission nodes are understood:

## General Nodes
<table><tbody><tr><th>Node</th><th>Description</th><th>Default</th></tr>
<tr><td>stb.admin</td><td>Gives full permission to do anything with STB</td><td>op</td></tr>
<tr><td>stb.access.any</td><td>Allows access to private block GUI's</td><td>op</td></tr>
</tbody></table>

## Command Nodes
<table><tbody><tr><th>Node</th><th>Description</th><th>Default</th></tr>
<tr><td>stb.commands.charge</td><td>Allows the <code>/stb charge</code> command to be used</td><td>op</td></tr>
<tr><td>stb.commands.debug</td><td>Allows the <code>/stb debug</code> command to be used</td><td>op</td></tr>
<tr><td>stb.commands.getcfg</td><td>Allows the <code>/stb getcfg</code> command to be used</td><td>op</td></tr>
<tr><td>stb.commands.give</td><td>Allows the <code>/stb give</code> command to be used</td><td>op</td></tr>
<tr><td>stb.commands.recipe</td><td>Allows the <code>/stb recipe</code> command to be used</td><td>player</td></tr>
<tr><td>stb.commands.rename</td><td>Allows the <code>/stb rename</code> command to be used</td><td>player</td></tr>
<tr><td>stb.commands.rename.free</td><td>Allows the <code>/stb rename</code> command to be used for no experience cost</td><td>op</td></tr>
<tr><td>stb.commands.save</td><td>Allows the <code>/stb save</code> command to be used</td><td>op</td></tr>
<tr><td>stb.commands.setcfg</td><td>Allows the <code>/stb setcfg</code> command to be used</td><td>op</td></tr>
<tr><td>stb.commands.show</td><td>Allows the <code>/stb show</code> command to be used</td><td>op</td></tr>
<tr><td>stb.recipebook.freefab</td><td>Allows free fabrication of items via the recipe book</td><td>op</td></tr>
</tbody></table>

For full documentation of what each command does, see [Commands](slimefun/SensibleToolbox/commands.md).

## Item-Specific Nodes
These nodes exists for every known item ID - see [Item Reference](slimefun/SensibleToolbox/item-reference.md) for a full list of item IDs.

<table><tbody><tr><th>Node</th><th>Description</th><th>Default</th></tr>
<tr><td>stb.interact.{item-id}</td><td>Allows an item to be used (left- or right-clicking with the item in hand)</td><td>true</td></tr>
<tr><td>stb.interact_block.{item-id}</td><td>Allows a placed block to be used by right-clicking it</td><td>true</td></tr>
<tr><td>stb.place.{item-id}</td><td>Allows the item to be placed as a block</td><td>true</td></tr>
<tr><td>stb.break.{item-id}</td><td>Allows a placed block to be broken</td><td>true</td></tr>
<tr><td>stb.craft.{item-id}</td><td>Allows the item to be crafted (<em>v0.0.4+</em>)</td><td>true</td></tr>
<tr><td>stb.allow.{item-id}</td><td>Parent node giving all of the above nodes (<em>v0.0.4+</em>)</td><td>true</td></tr>
</tbody></table>

For example, to prevent a player (or permission group) breaking Redstone Clocks, add the permission node <strong>stb.break.redstoneclock = false</strong> to the player or group.  The syntax here obviously depends on the permission plugin you're using.

The default permissions allow all actions to be taken on/with every STB item block.

For block protection, larger servers will probably be best served by using a dedicated protection plugin such as WorldGuard but these permissions exist as another protection option for specific STB block and item types.