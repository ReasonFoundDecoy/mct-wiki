# Configuration
## Overview

Sensible Toolbox stores its configuration in <code>plugins/SensibleToolbox/config.yml</code>.
Use the <code>/stb getcfg</code> and <code>/stb setcfg</code> [commands](slimefun/SensibleToolbox/commands.md) to show or modify configuration settings.  Editing the <code>config.yml</code> file while the server is running is not recommended at this time - there is no command to reload it other than a full server restart (a <code>/stb reload</code> command is planned, though).

## Settings
The settings are:
<table><tbody><tr><th>Setting</th><th>Type</th><th>Default</th><th>Description</th></tr>
<tr><th>block_protection</th><td><em>special</em></td><td>best</td><td>The block protection system to use.  See <a href="https://dev.bukkit.org/projects/sensible-toolbox/pages/protection" rel="nofollow">Protection</a> for more information.</td></tr>
<tr><th>coloured_console</th><td>boolean</td><td>true</td><td>If true, messages to the console will be coloured.  Set to false if your console doesn't have working colour support, or you just prefer uncoloured messages</td></tr>
<tr><th>debug_level</th><td>integer</td><td>0</td><td>The current debug level.  Leave this at 0 under normal circumstances.</td></tr>
<tr><th>default_access</th><td><em>special</em></td><td>public</td><td>This is the default <a href="https://reasonfounddecoy.gitbook.io/mctantrum-wiki/slimefun/addons/sensibletoolbox/access-control" rel="nofollow">access control</a> that newly-placed STB blocks have.  One of "public", "private" or "restricted".</td></tr>
<tr><th>default_redstone</th><td><em>special</em></td><td>ignore</td><td>This is the default <a href="https://dev.bukkit.org/projects/sensible-toolbox/pages/items" rel="nofollow">Redstone Response</a> for newly-placed STB blocks.  One of "ignore", "high", "low", or "pulsed".</td></tr>
<tr><th>energy.tick_rate</th><td>integer</td><td>10</td><td>The interval in server ticks between <a href="https://dev.bukkit.org/projects/sensible-toolbox/pages/items/energy" rel="nofollow">energy net</a> ticks; energy supply and demand will be calculated and resolved this often.</td></tr>
<tr><th>explode_item_drop_chance</th><td>integer</td><td>50</td><td>If a STB item is broken by an explosion, this is the percentage chance that it will drop as an item, rather than being destroyed completely</td></tr>
<tr><th>gui.texture.bg</th><td>Material spec.</td><td>stained_glass_pane:blue</td><td>The background material to use in inventory GUI's.</td></tr>
<tr><th>gui.texture.button</th><td>Material spec.</td><td>wood_button</td><td>The material to use for button gadgets in inventory GUI's.</td></tr>
<tr><th>gui.texture.input</th><td>Material spec.</td><td>stained_glass_pane:cyan</td><td>The material to use around input slots in machine inventory GUI's.</td></tr>
<tr><th>gui.texture.label</th><td>Material spec.</td><td>book</td><td>The material to use for labels in inventory GUI's.</td></tr>
<tr><th>gui.texture.output</th><td>Material spec.</td><td>stained_glass_pane:orange</td><td>The material to use around output slots in machine inventory GUI's.</td></tr>
<tr><th>holo_messages.enabled</th><td>boolean</td><td>true</td><td>If true and the HoloAPI plugin is installed, some messages will be displayed via temporary "holograms", to reduce chat clutter.</td></tr>
<tr><th>holo_messages.duration</th><td>float</td><td>2.0</td><td>The duration in seconds per message line for which popup messages will be displayed. E.g. with the default of 2.0, a 4-line message will be displayed for 8 seconds.</td></tr>
<tr><th>inventory_protection</th><td><em>special</em></td><td>best</td><td>The inventory protection system to use.  See <a href="https://dev.bukkit.org/projects/sensible-toolbox/pages/protection" rel="nofollow">Protection</a> for more information.</td></tr>
<tr><th>items_enabled.&lt;item-id&gt;</th><td>boolean</td><td>true</td><td>There is actually one setting for every known item ID - for a full list of known ID's, see <a href="https://dev.bukkit.org/projects/sensible-toolbox/pages/item-reference" rel="nofollow">Item Reference</a>.  If the setting for an item is set to false, then that item is made unavailable - it cannot be crafted or obtained with the <code>/stb give</code> command.</td></tr>
<tr><th>item_settings.<br> autobuilder.scu_per_op</th><td>integer</td><td>30</td><td>The base amount of SCU required by the <a href="https://dev.bukkit.org/projects/sensible-toolbox/pages/items/building" rel="nofollow">Auto Builder</a> to place or break a block.  Note that breaking a block may cost more or less SCU than the base, depending on the block material.</td></tr>
<tr><th>item_settings.<br> multibuilder.scu_per_op</th><td>integer</td><td>30</td><td>The base amount of SCU required by the <a href="https://dev.bukkit.org/projects/sensible-toolbox/pages/items/building" rel="nofollow">Multibuilder</a> to place or swap a block.  Note that this amount can be reduced by an Efficiency enchantment on the tool.</td></tr>
<tr><th>item_settings.<br> paintbrush.wood_staining</th><td>boolean</td><td>true</td><td>If true, the paintbrush can be made to stain wood planks and slabs, effectively turning them into other wood types.  See <a href="https://dev.bukkit.org/projects/sensible-toolbox/pages/items/painting" rel="nofollow">Paintbrush</a> for more information.</td></tr>
<tr><th>item_settings.<br> paintcan.paint_per_dye</th><td>integer</td><td>25</td><td>The amount of paint made by mixing a dye in the <a href="https://dev.bukkit.org/projects/sensible-toolbox/pages/items/painting" rel="nofollow">Paint Can</a></td></tr>
<tr><th>item_settings.<br> paintroller.wood_staining</th><td>boolean</td><td>true</td><td>See <em>item_settings.paintbrush.wood_staining</em></td></tr>
<tr><th>noisy_machines</th><td>boolean</td><td>true</td><td>If true, machines will make a variety of noises when working</td></tr>
<tr><th>particle_effects</th><td>integer</td><td>2</td><td>The amount and frequency of particle effects.  Valid values are 0-2.  Reduce this to save a little CPU/bandwidth.</td></tr>
<tr><th>rename_level_cost</th><td>integer</td><td>5</td><td>The cost, in experience levels, to rename an animal which is captured in an <a href="https://dev.bukkit.org/projects/sensible-toolbox/pages/items/basic" rel="nofollow">Ender Leash</a>.</td></tr>
</tbody></table>