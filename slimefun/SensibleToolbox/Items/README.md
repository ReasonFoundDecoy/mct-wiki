# Items and Blocks
This is divided into several sections:
* [Components](slimefun/SensibleToolbox/Items/components.md)
* [Basic Utilities](slimefun/SensibleToolbox/Items/ender-storage.md)
* [Farming](slimefun/SensibleToolbox/Items/farming.md)
* [Painting](slimefun/SensibleToolbox/Items/painting.md)
* [Building](slimefun/SensibleToolbox/Items/building.md)
* [Item Routing](slimefun/SensibleToolbox/Items/routing.md)
* [Item Storage](slimefun/SensibleToolbox/Items/storage.md)
* [Ender Storage](slimefun/SensibleToolbox/Items/ender-storage.md)
* [Energy System](slimefun/SensibleToolbox/Items/energy.md)
* [Machines (ore processing etc.)](slimefun/SensibleToolbox/Items/machines.md)

See also the full item reference:
* [Full Item Reference](slimefun/SensibleToolbox/item-reference.md)
</li></ul>

## General Information
### Label Signs
If you left-click the side of any STB block with a sign, that sign will be automatically attached to the block and set to display information about the block.  In most cases, that is just the block's name, but some blocks display more information (e.g. a BSU will display the item it's holding and the quantity, Ender Boxes display the configured ender frequency, Paint Cans display their paint colour and paint level, and as of v0.0.4, any chargeable machine will show is charge level as a pretty SCU meter).

### ![](.gitbook/assets/common\WIP.png) Label Signs Image here

Item signs are smart, in that if you break an STB block with one or more attached item signs, the signs will also automatically disappear and not drop as items.  The block remembers which signs are attached to which face, and when you place the block again, the signs will automatically reappear (assuming there is room to place them)!  To remove a sign, just break the sign itself.

Item signs also have a little glyph in line 1, in front of the item name indicating which direction the block faces:
<table><tbody><tr><th>Symbol</th><th>Meaning</th></tr>
<tr><td>▣</td><td>Sign is on the front of the block</td></tr>
<tr><td>▶</td><td>Sign is on the left of the block (arrow points to front)</td></tr>
<tr><td>◀</td><td>Sign is on the right of the block (arrow points to front)</td></tr>
<tr><td>▼</td><td>Sign is on the back of the block</td></tr>
</tbody></table>

Since most vanilla block materials have the same texture on all sides, this can be a useful indicator as to which direction the block faces. While most blocks don't currently care which way they face, this could be much more important in future.

### Item GUIs
Many items and blocks can be configured by right-clicking them to pop up an inventory-based GUI.  There are some common controls found on most GUI's:

### ![](.gitbook/assets/common\WIP.png) Smelter GUI Image here


1. Redstone response button, represented by gunpowder/redstone dust/glowstone dust. Default is for the block to IGNORE any redstone signal affecting it.  You can also set the block to either require a signal (HIGH) or require no signal (LOW) to operate.  This can be useful if you want a machine to only process things when a lever is pulled, for example.  In <em>v0.0.4+</em>, there is also a PULSED mode, which not all blocks support; in this mode, the machine will carry out one operation per redstone pulse detected: an item router will process one item(stack) when a pulse is received, and a processing machine will pull one item into processing.  This could be useful to control item flow via an externally clocked signal, for example.

2. PUBLIC/PRIVATE/RESTRICTED access button, represented by green/red/yellow wool.  Click to cycle between access modes.  When the block is set to PRIVATE access, only the block's owner (the person who placed the block) or someone with the <strong>stb.access.any</strong> permission can access the block's GUI, or insert/extract items. Note that private access does not prevent the block being <em>broken</em> by others - STB doesn't provide any block protection at this time (although it may in future); use a separate plugin such as WorldGuard for that.  In RESTRICTED access mode, only the block's owner and friends of the block's owner can access the block's GUI.  Friends are added/remove with the <code>/stb friend</code> and <code>/stb unfriend</code> [commands](slimefun/SensibleToolbox/commands.md)

3. Machines which can be charged [Energy System](slimefun/SensibleToolbox/Items/energy.md) also have a charge indicator, represented by a yellow-coloured leather helmet.

4. Machines which can take an energy cell (portable charging) will have a slot for that cell, and usually a button to control whether charge should be transferred from the cell to the machine, or vice versa.

5. Machines which take upgrades (to modify/improve their behaviour) have a set of slots to place those upgrade items in.

6. Machines may have one or more input slots where items to be processed are inserted.

7. Machines may have one or more output slots where finished items are placed, ready for extraction.