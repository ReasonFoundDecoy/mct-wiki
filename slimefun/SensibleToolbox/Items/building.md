{% hint style="warning" %}
This page is a work in progress. Information may not be accurate.
{% endhint %}

# Building
## Multibuilder
The Multibuilder is a powerful dual-purpose tool which takes a lot of the tedium out of large-scale construction (at least when you don't have access to creative mode or plugins like WorldEdit!)

#### ![recipe-multibuilder](../../../.gitbook/assets/WIP.png)
<i>Note that as of v0.0.3, the Multibuilder requires an [Integrated Circuit](slimefun/SensibleToolbox/Items/components.md) to craft.</i>

The Multibuilder has two modes <strong>Build</strong> and <strong>Swap</strong>; to switch between them, hold Shift and roll the mouse wheel.
The Multibuilder requires [power](slimefun/SensibleToolbox/Items/energy.md) to operate.  A newly-crafted Multibuilder has no charge - to charge it, get a charged Energy Cell, and with the Multibuilder on your hotbar, hold the Energy Cell in your hand and press & hold the right mouse button.  The Multibuilder will slowly charge up (you don't need to charge it to full to use it).

<i>A future release of STB will add a Charging Station where chargeable items can be inserted and left to charge unattended</i>

### <u>Build Mode</u>
In Build mode, the Multibuilder can be used to extend existing walls, floors etc.  To do this, right click on the edge of the structure you want to extend.  If the tool has enough power and you have enough materials, the tool will auto-place enough blocks to extend the structure.

You can also preview what would be placed by left-clicking with the tool:

#### ![Multibuilder build mode preview](../../../.gitbook/assets/WIP2.png)

The white stained glass blocks appear for one second, and show where building (in this case, Smooth Stone Bricks) will occur if you right-click with the tool.
As of v0.99.0, if you hold shift while left- or right-clicking, the tool works in <i>line</i> mode.  Here the tool will always try to place a straight line of blocks, even you click in the middle of a large area.  The direction of the line is decided as follows:
* For building on a horizontal surface (click the top or bottom of a block), the line will be drawn perpendicular to the direction you face.  E.g. if you're facing north, the line will go east/west.
* For building on a vertical surface (click the side of a block):
    * If you click near the top or bottom edge of the block's face, the line will be vertical
    * Otherwise, the line will be horizontal

### <u>Swap Mode</u>
In Swap mode, the Multibuilder swaps blocks in the world with blocks in your inventory:
* Shift-right-click a block with the tool - this becomes the tool's <i>target block</i> and the display name will update to reflect that.  Then:
* Right-click a block to replace it and multiple adjacent blocks with material from your inventory matching the target block
* Left-click a block to replace only that block with material from your inventory matching the target block

#### ![Multibuilder swap mode](../../../.gitbook/assets/WIP.png)

Here, this stone brick wall is being swapped for a wood plank wall.

You must have sufficient power in the tool and sufficient materials in your inventory.

### <u>Power Consumption</u>
The Multibuilder requires a base 30 SCU per block placed or swapped, but this can be modified with the <strong>multibuilder.charge_per_op</strong> [Configuration](slimefun/SensibleToolbox/configuration.md) setting.

### <u>Enchantments</u>
The Multibuilder can be enchanted, and the following enchantments have useful effects:
* The Efficiency enchantment reduces the charge needed per operation.  Charge needed is (BASE_CHARGE LEVEL * 0.8 ^ EFFICIENCY), e.g. Efficiency III will reduce the charge needed to 51.2% of the base charge level.
* The Sharpness enchantment will increase the maximum number of blocks affected in an operation.
    * The maximum blocks affected in Swap mode is variable, and depends on how many blocks are available.  The level of SHARPNESS basically affects how far the tool will search for candidate blocks. <i>(21 * 1.2 ^ SHARPNESS before v0.99.0)</i>
    * The maximum blocks affected in Build mode 9 + 3 * SHARPNESS <i>(9 + 2 * SHARPNESS before v0.99.0)</i>
* The Silk Touch enchantment will allow the swapping of blocks directly into your inventory in Swap mode.  Without this, blocks are broken as normal (e.g. grass becomes dirt, diamond ore becomes a diamond...)

## Auto Builder
<i>Added in v0.0.4</i>

#### ![recipe-multibuilder](../../../.gitbook/assets/WIP2.png)
The Auto Builder is a machine which can clear or build on large areas of land.  It requires SCU to operate, and an inventory of building materials if it's in construction mode.

The Auto Builder GUI:


#### ![autobuilder-gui](../../../.gitbook/assets/WIP.png)
1. This is where the area to be worked on is defined.  Get two Land Markers (see below) and place them in the two slots here.  Note that only a copy of the Land Markers is inserted into the GUI; you get to keep the actual Land Marker items.
2. This button controls the current build mode:
    1. Clear: set the terrain to AIR
    2. Fill: fill every (currently empty) block with blocks from the build inventory
    3. Walls: flll the walls of the build area (good for house building)
    4. Frame: fill the outer edges only of the build area
3. This is a status indicator; mouse over it to get some useful information about the builder's current status.
4. These are the redstone response, access control and charge indicators common to most machines.
5. This important little button starts the machine running (or pauses it if pressed while already running).
6. These 10 slots hold the build inventory; blocks are taken from here in Fill/Walls/Frame mode.
7. An energy cell can be inserted here if desired.

Some other important things to note:
* The Auto Builder has a max charge of 20,000 SCU and a max transfer rate of 50 SCU/t.
* It will place or break up to one block per tick.
* Placing a block costs 30 SCU (configurable: see the <strong>item_settings.autobuild.scu_per_op</strong> [Configuration](slimefun/SensibleToolbox/configuration.md) setting).
* Breaking a block has a variable cost: 30 SCU multiplied by the block's hardness.  The hardness for blocks [can found here](https://minecraft.fandom.com/wiki/Breaking#Blocks_by_hardness).  As an example, breaking a dirt block costs only 15 SCU, but breaking an obsidian block costs a whopping 1500 SCU!  Blocks such as bedrock and ender portal blocks cannot be broken by the Auto Builder.
* If the Auto Builder runs out of inventory in a placing mode, you can add new blocks and press the Start button to resume from the same place.
* The Auto Builder will respect any block protection: see [Protection](slimefun/SensibleToolbox/protection.md) for more information.
* The Auto Builder must be placed outside the build area, but not more than 5 blocks from the closest edge of the build area.

### Land Markers
These items are used to mark a specific location in the world.  At this time, their only use is to define a work area for the Auto Builder.
#### ![recipe-landmarker](../../../.gitbook/assets/WIP2.png)