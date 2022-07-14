{% hint style="warning" %}
This page is a work in progress. Information may not be accurate.
{% endhint %}

# Item Router

STB adds an Item Router device, whose purpose is to move items into, out of, or between inventories.  A little like a vanilla hopper, but far, far more powerful.  The Item Router is crafted as follows:
#### ![recipe-item-router](../../../.gitbook/assets/WIP.png)
To configure an Item Router, place it as a block, and right-click it for the following GUI:

#### ![item-router-gui](../../../.gitbook/assets/WIP2.png)
1. Any item(s) currently in the router's buffer are shown here.  As of v0.99.0, you can extract items from the GUI here (but not insert them).  Shift-left-clicking the item router block will also cause it to eject any items in the buffer onto the ground.
2. These are the redstone behaviour and access controls common to most blocks.
3. Here you can install up to 9 <em>router modules</em> - these are what defines what this router does, and which items it should operate upon.

## A Note on Inventories
An <em>inventory</em> for the purposes of an Item Router can be any vanilla inventory (chest, furnace, hopper, dropper, brew stand, enchanting table...) or any STB block which has an inventory (machines, BSU/HSU devices, other Item Routers...).

## Item Router Modules
Item Router Modules define what an Item Router actually does.  You can insert up to 9 modules in the bottom row of the router's GUI.  They are executed in left to right order each time a router ticks (which is every 20 ticks by default, but see the Speed Module below).  By default each module will attempt to process a single item, but see the Stack Module below.

Most router modules operate on an inventory adjacent to the item router block, in a configured direction; to configure the direction that a router module works in, you have two options:

1. Left-click the module item on the corresponding face of any block before inserting it.  Note that the configured direction is the same as the direction you're <em>facing</em> when you click, e.g. if you click the bottom face of a ceiling block <em>above</em> you, the module will be set to operate on the inventory <em>above</em> the item router it's installed in.
2. Right-click the module item to open its GUI; on the right hand side you can choose the direction it should operate in. <em>(v0.0.4+)</em>

Either way works; use whichever way you feel most comfortable with.

## Item Filtering
By default, item router modules work on any item.  However, you can configure a module to either white-list or black-list certain items by right-clicking it (in your hand, before it's installed in the router) to open the module GUI:
#### ![module-gui](../../../.gitbook/assets/WIP.png)

1. You can configure up to 9 items here.  Left- or right-click any of these slots with an item on your cursor, and that item will be copied into the filter list.  You can clear a slot simply by clicking it with nothing on the cursor.
2. This button controls whether the listed items are white-listed or black-listed.
3. This button defines how the item is matched: 1) by material only, 2) by material and data byte (aka block metadata) or 3) by material, data byte, and item meta (aka NBT data)
4. This button controls the <em>termination</em> mode of this module: if this module succeeds in processing an item and termination is ON, then no more modules will execute on this tick, even if there are still items in the buffer.  If termination is OFF (the default) then any modules after this one will execute as normal.
5. These controls allow configuration of the module's direction (as mentioned above).

## A Note on Matching
* Match by MATERIAL: only the material type is check, not the block metadata.  For example, coal and charcoal use the same material ID, but different block metadata.  If you place a lump of coal in the filter, and leave the filter type as MATERIAL, the module will process both coal and charcoal.
* Match by BLOCK_DATA: this will match on both material <em>and</em> block metadata.  Following on from above, if you set the filter type to BLOCK_DATA with a lump of coal in the filter, the module will process coal, but not charcoal.
* Match by ITEM_META: this match on material, block metadata, and item metadata (sometimes known as NBT data).  For example, if you place a diamond sword with Looting II in the filter, <em>only</em> diamond swords with that precise enchantment (and durability) will be matched, no others.

## A Note on Termination
Termination may sound a little confusing, and in most cases it isn't necessary.  However consider a scenario like this:

* You have an item router which is being fed with items by one or more other item routers.  It could be receiving multiple items per tick.
* In your router is a sender module which sends all coal in one direction.
* After that module is a sender module which sends all items in a different direction.

Since this router doesn't have stack upgrades, each module will work on <em>one</em> item at a time.  Say 8 coal arrive in the router:
1. The first sender will match coal, and send it on to the right place, leaving 7 coal in the router's buffer.
2. The second sender will match anything, and send the coal on... to the wrong place.

Here's a case where it could be useful to switch termination on for the first module - if it finds coal and processes it, stop there; don't let the second module send coal on to the wrong place.

## Module List
### <u>Blank Item Router Module</u>
#### ![recipe-blank-module](../../../.gitbook/assets/WIP2.png)
This is the basis for crafting all other modules, and doesn't do anything itself.

### <u>Puller Module</u>
#### ![recipe-puller-module](../../../.gitbook/assets/WIP.png)
This module will attempt to pull items from an inventory in its configured direction and place them in the router's buffer.  If the buffer is full, or there's already an item of a different type in the buffer, nothing will be pulled.

### <u>Sender Module</u>
#### ![recipe-sender-module](../../../.gitbook/assets/WIP2.png)
This module will attempt to send items from the router's buffer in its configured direction:
* If there is an inventory block directly adjacent to the router, it will attempt to deposit the item in that inventory.
* If there is another item router in direct line of sight (along the X, Y or Z axis) within 10 blocks, and with an installed receiver module, the sender can wirelessly send items to that router.  The line of sight must be clear ("passable" items like carpets are OK, as is glass).

### <u>Advanced Sender Module</u>
#### ![recipe-advanced-sender](../../../.gitbook/assets/WIP.png)
This more powerful (and expensive!) version of the Sender Module can send items wirelessly to any other Item Router with an installed Receiver module within 25 blocks; no line of sight is needed.  To configure where the Advanced Sender will send items to, left-click it on a router with an installed Receiver module; you will receive a confirmation message and the target router's location will be recorded in the module.

### <u>Hypersender Module</u>
#### ![recipe-hypersender](../../../.gitbook/assets/WIP2.png)
 <em>Added in v0.0.4</em>

This even more powerful (and yes, expensive) version of the Sender Module can send items wirelessly to any other Item Router with an installed Receiver module with no line of sight or distance limitation at all.  It can even send items across worlds!  The Hypersender is configured in the same way as the Advanced Sender; left-click on an Item Router with an installed Receiver module. 

Crafting the Hypersender Module requires an Advanced Sender Module, plus two [Energized Gold Ingots](../Items/components.md) and an [Integrated Circuit](../Items/components.md).

### <u>Distributor Module</u>
#### ![recipe-distributor-module](../../../.gitbook/assets/WIP.png)
This module functions somewhat like a combined Puller and Sender module: it pulls items from an adjacent inventory in the configured direction, and round-robin distributes them to all other adjacent inventories.  Unlike the Sender module, however, it does not do any wireless item sending.

### <u>Receiver Module</u>
#### ![recipe-receiver-module](../../../.gitbook/assets/WIP2.png)
This module does nothing itself, but you must install one if the router is to accept items from a sender/distributor/advanced sender module in a different router.

### <u>Dropper Module</u>
#### ![recipe-dropper-module](../../../.gitbook/assets/WIP.png)
This module drops an item from the router's buffer on the ground in the configured direction.  This may be useful if you want to move items around using vanilla mechanics (water, ice, etc.)

### <u>Vacuum Module</u>
#### ![recipe-vacuum-module](../../../.gitbook/assets/WIP2.png)
This module will attempt to suck any items on the ground within a 6-block radius into the router's buffer.  If a direction is configured, the module will only pull items that lie in that direction from the centre of the router; if no direction is configured, then the module will suck items from all directions.
The module will attempt to suck items that lie behind walls, even if the item can't reach the router.

### <u>Sorter Module</u>
#### ![recipe-sorter-module](../../../.gitbook/assets/WIP.png)
This module will attempt to move an item from the router's buffer into the adjacent inventory in the configured direction, but only if:

* The inventory is empty, OR
* There is already an item of that type in the inventory

You can create simple sorting systems with this module; use the Sorter to send to an adjacent chest, followed by a Sender to send items on to the next router, which can sort/send any items this Sorter didn't pick up.  

## <u>Breaker Module</u>
#### ![breaker-recipe](../../../.gitbook/assets/WIP2.png)
If there is room in the item router's buffer, this module will break any solid block (except bedrock) in its configured direction, and pull the resulting item drop into the buffer.  This could be useful for cobblestone/stone/obsidian generators and melon/pumpkin farms, and potentially many other applications in future.

If breaking a block causes multiple item types to drop, only the primary drop will be pulled into the item router.  E.g. breaking mature wheat is likely to drop both a wheat item and one or more seeds; only the wheat item will be pulled in.  You could use the Vacuum Module to pull in supplementary drops if desired.

## <u>Speed Module</u>
#### ![recipe-speed-module](../../../.gitbook/assets/WIP.png)
This module is a passive module; it doesn't move items, but rather increases the speed at which the router operates by reducing the tick interval:

* 0 speed modules: 20 ticks
* 1 speed modules: 15 ticks
* 2 speed modules: 10 ticks
* 3 speed modules: 5 ticks

Note that this will incur a CPU penalty; using the <strong>Stack Module</strong> is usually a better way to move items more quickly.  You may even wish to disable this module entirely with <code>/stb set items_enabled.speedmodule false</code> if you're concerned about players abusing them.

## <u>Stack Module</u>
#### ![recipe-stack-module](../../../.gitbook/assets/WIP2.png)
This module is a passive module; it doesn't move items, but rather increases the number of items that are moved in each operation.  With no stack modules, a router will move one item per operation.  You can add up to six Stack modules; each one doubles the number of items moved at a time, up to a maximum of 64 items (or the item's native stack size; e.g. not more than 16 signs can be moved at a time).