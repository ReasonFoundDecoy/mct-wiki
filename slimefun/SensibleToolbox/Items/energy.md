{% hint style="warning" %}
This page is a work in progress. Information may not be accurate.
{% endhint %}

# Energy System
## Overview
#### ![energy-net-example](../../../.gitbook/assets/WIP.png)
Some STB items and blocks require energy to operate; units of this energy are called <em>SCU</em> - Sensible Charge Units.  There are a couple of ways of charging an item or block:
* Chargeable blocks usually have a slot for an [energy cell](https://reasonfounddecoy.gitbook.io/mctantrum-wiki/slimefun/addons/sensibletoolbox/items/energy#energy-cells) in their GUI; you can install a cell into the block to charge it.  Note that blocks usually also have a Charge Direction button next to the cell slot; make sure this is configured to send charge in the right direction.
* Chargeable blocks can also be connected via <em>cables</em> to other blocks; some blocks supply charge (e.g. Heat Generator, Basic Solar Cell), some blocks demand charge (Smelter, Masher...), and some blocks can both supply <em>and</em> demand charge (Battery Box).
* An energy cell can be used to charge certain items: with the item you want to charge in your hotbar, and the energy cell in your hand, press and hold the right mouse button, and charge will transfer from the cell to the item.

As an idea of how much 1 SCU is worth, 1 lump of coal will produce 1800 SCU when burnt in a Heat Generator (see below).  It takes 120 SCU for a Smelter to smelt a block of iron ore into an ingot; so one lump of coal will smelt 15 ingots; nearly twice as efficient as a vanilla furnace.  However, you also want to run ores through a Masher to double the ingot output, which also requires 120 SCU per ore.  So to turn one iron ore into two iron ingots via the Masher -> Smelter ore doubling process requires 240 SCU; slightly more energy per ore than vanilla smelting, but double the output.  (Gold, being softer than iron, requires a little less energy in the Masher).

## Energy Nets
An <em>energy net</em> is basically any collection of charge suppliers and charge consumers linked together by cabling.
* Use the vanilla Iron Fence block for cabling.
* Charge is not transferred through machines, only through cabling.
* All chargeable blocks can be on zero or more energy nets.  It is possible for a block to receive or supply charge to multiple nets (and this is a common case for battery boxes).
* Linking two separate energy nets with cabling will create a single new unified energy net.
* Breaking an energy net by cutting cabling will create two (or maybe more) new separate energy nets.

Energy nets "tick" periodically, and attempt to balance out the charge demanded against the available charge supply.  During the tick, charge is moved from blocks which can supply it to blocks which need it; the available charge is distributed as equally as possible.  The default tick period is every 10 server ticks, or twice per second.

## Energy Cells
### 10K Energy Cell
#### ![recipe-10k-cell](../../../.gitbook/assets/WIP2.png)
This basic energy cell can store up to 10,000 SCU, and can transfer its charge at a maximum of 100 SCU/tick.

### 50K Energy Cell
#### ![recipe-50k-cell](../../../.gitbook/assets/WIP.png)
This second-tier energy cell can store up to 50,000 SCU, and can transfer its charge at a maximum of 500 SCU/tick.  Note that (as of v0.0.4) it requires [Energized Iron Ingots](../Items/components.md) to craft.

## Battery Boxes
### 10K Battery Box
#### ![recipe-10k-batbox](../../../.gitbook/assets/WIP2.png)
This basic battery box can store up to 10,000 SCU and transfer energy at maximum of 100 SCU/tick.  <em>Added in v0.0.4</em>

### 50K Battery Box
#### ![recipe-50k-batbox](../../../.gitbook/assets/WIP.png)
This second-tier battery box can store up to 50,000 SCU and transfer energy at maximum of 500 SCU/tick.
To configure a battery box's operation, right-click to open its GUI:

#### ![batbox-gui](../../../.gitbook/assets/WIP2.png)

1. You can place an energy cell here to charge or discharge
2. These six buttons (around the central batbox icon) allow configuration of charge direction: each face of the block can supply charge, receive charge, or do neither.
3. These are the Redstone, Public/Private, and Charge Indicator buttons common to many STB blocks.

## Generators
### Heat Engine
#### ![recipe-heat-engine](../../../.gitbook/assets/WIP.png)
This generator can turn a variety of burnable items into energy.  Different items provide varying quantities of energy, and have varying burn times:
<table><tbody><tr><th>Item</th><th>SCU</th><th>Burn Time (server ticks)</th></tr>
<tr><td>Coal</td><td>1800</td><td>120</td></tr>
<tr><td>Charcoal</td><td>1200</td><td>80</td></tr>
<tr><td>Coal Block</td><td>16800</td><td>960</td></tr>
<tr><td>Blaze Rod</td><td>2700</td><td>180</td></tr>
<tr><td>Blaze Powder</td><td>675</td><td>30</td></tr>
<tr><td>Logs</td><td>400</td><td>40</td></tr>
<tr><td>Planks</td><td>100</td><td>20</td></tr>
<tr><td>Sticks</td><td>50</td><td>20</td></tr>
<tr><td>Fire Charges</td><td>1000</td><td>20</td></tr>
</tbody></table>

Notes:
* Fire charges produce a lot of SCU very quickly (1000 SCU per second)
* Coal blocks are slightly (3.7%) more efficient than the 9 lumps of coal used to create them (the SCU/tick is the same, but they burn a little longer).
* The Heat Engine has an internal storage cell of 5000 SCU, and can transfer its charge at a maximum of 50 SCU/tick.
* If the Heat Engine's internal cell is more than 75% full, the engine's burn rate is progressively reduced to conserve fuel.
* If you install a [Regulator Upgrade](../Items/machines.md) in a Heat Engine, it will only start burning a fuel item if there is definitely enough room in its internal SCU buffer to store the SCU that would be generated; this can save a lot of fuel in the long run.

### Bio Engine
#### ![recipe-bio-engine](../../../.gitbook/assets/WIP2.png)
This engine can convert various organic Materials into energy.
<table><tbody><tr><th>Item</th><th>SCU</th><th>Burn Time (server ticks)</th></tr>
<tr><td>Rotten Flesh</td><td>180</td><td>60</td></tr>
<tr><td>Spider Eye</td><td>210</td><td>60</td></tr>
<tr><td>Bone</td><td>180</td><td>60</td></tr>
<tr><td>Ink Sack</td><td>240</td><td>60</td></tr>
<tr><td>Slime Ball</td><td>480</td><td>80</td></tr>
<tr><td>Sapling</td><td>360</td><td>60</td></tr>
<tr><td>Leaves</td><td>240</td><td>40</td></tr>
<tr><td>Tall Grass</td><td>320</td><td>80</td></tr>
<tr><td>Apple</td><td>1000</td><td>100</td></tr>
<tr><td>Melon Slice</td><td>1000</td><td>100</td></tr>
<tr><td>Melon Seeds</td><td>1000</td><td>100</td></tr>
<tr><td>Melon</td><td>9000</td><td>900</td></tr>
<tr><td>Pumpkin</td><td>1000</td><td>100</td></tr>
<tr><td>Pumpkin Seeds</td><td>1000</td><td>100</td></tr>
<tr><td>Wheat</td><td>1000</td><td>100</td></tr>
<tr><td>Seeds</td><td>1000</td><td>100</td></tr>
<tr><td>Carrot</td><td>1000</td><td>100</td></tr>
<tr><td>Potato</td><td>1000</td><td>100</td></tr>
<tr><td>Sugar Cane</td><td>800</td><td>100</td></tr>
<tr><td>Nether Wart</td><td>1680</td><td>140</td></tr>
<tr><td>Dirt</td><td>10</td><td>20</td></tr>
<tr><td>Grass</td><td>10</td><td>20</td></tr>
<tr><td>Flower</td><td>880</td><td>80</td></tr>
<tr><td>Mushroom</td><td>880</td><td>80</td></tr>
<tr><td>Vine</td><td>640</td><td>80</td></tr>
<tr><td>Cactus</td><td>800</td><td>100</td></tr>
<tr><td>Lilypad</td><td>640</td><td>80</td></tr>
</tbody></table>

### Magmatic Engine
#### ![recipe-magmatic-engine](../../../.gitbook/assets/WIP.png)
This Engine produces 16000 SCU in total (16 SCU/t for 1000 Ticks) and runs on Lava Buckets

### Basic Solar
#### ![recipe-basic-solar](../../../.gitbook/assets/WIP2.png)
This generator produces a steady trickle of up to only 0.5 SCU/tick.  It has an internal storage cell of a measly 100 SCU, and can only transfer energy at a maximum of 5 SCU/tick.

### Dense Solar
#### ![recipe-dense-solar](../../../.gitbook/assets/WIP.png)
Eight Basic Solars and an [Integrated Circuit](../Items/components.md) are required to craft.

This tier 2 generator produces a steady trickle of up to 4.0 SCU/tick.  It has an internal storage cell of 240 SCU, and can transfer energy at a maximum of 12 SCU/tick.  <em>Added in v0.0.4</em>

Solars require sunlight to run on.  There needs to be clear view of the sky (glass above is OK), and it must be day time.  It will produce energy as long as the light level is 12 or greater, but requires light level of 15 for optimum efficiency:

<table><tbody><tr><th>Light Level</th><th>SCU/tick (Basic)</th><th>SCU/tick (Dense)</th></tr>
<tr><td>15</td><td>0.5</td><td>4.0</td></tr>
<tr><td>14</td><td>0.375</td><td>3.0</td></tr>
<tr><td>13</td><td>0.25</td><td>2.0</td></tr>
<tr><td>12</td><td>0.125</td><td>1.0</td></tr>
<tr><td>11 or under</td><td>0</td><td>0</td></tr>
</tbody></table>

#### <u>PV Cells</u>
As of v0.0.4, Solars require a PV cell to be installed, which must be crafted separately:

#### ![recipe-pv-cell](../../../.gitbook/assets/WIP2.png)
Note that a [Silicon Wafer](../Items/components.md) is required to craft.

A PV cell is fairly long-lived: it provides 180 (real) minutes of power generation (note that PV cell lifetime is only consumed when power is actively being generated).  Once its lifetime is over, a new PV cell must be crafted.

It should be noted that [Item Routers](../Items/routing.md) can be used to insert and extract PV cells to/from the Solar, adding automation possibilities...

## Consumers
There are several different types of charge consumer, and they are documented on their own pages:
* See [Machines](../Items/machines.md) for a list of the different processing machines
* See [Items/Storage](../Items/storage.md) for a description of the HSU (HyperStorage Unit), which needs a small amount of energy to operate

## Utilities
### Power Monitor
#### ![recipe-power-monitor](../../../.gitbook/assets/WIP.png)
The Power Monitor will show you
the Net Gain/Loss of your Energy Net on an attached Sign.
It needs to be directly adjacent to a part of your Energy Net (preferably a Cable).
Above or Below a Cable will not work. It has to be on a Side.
Examples: -263 SCU/t + 32.1K SCU/t

### Holographic Monitor
#### ![holographicmonitor](../../../.gitbook/assets/WIP2.png)
Since version 1.1 a new type of power monitor has been added.

The Holograpic Monitor utilizes <a href="http://dev.bukkit.org/bukkit-plugins/holographic-displays/" rel="nofollow">HolographicDisplays</a> to display the Net Gain/Loss, otherwise it will not display anything.
An example of it can be found here:
#### ![holograpicmonitor-example](../../../.gitbook/assets/WIP.png)

### Multimeter
#### ![recipe-multimeter](../../../.gitbook/assets/WIP2.png)
This little device is useful for basic energy net analysis:
* Right-clicking any cable will display:
    * The number of cables in this energy net
    * The number of charge suppliers (sources) and charge consumers (sinks) on this energy net
    * The charge available (instantaneous measurement at the last energy net tick)
    * The charge demanded (instantaneous measurement at the last energy net tick)

* Right-clicking any chargeable block will display:
    * The number of energy nets to which the block is connected
    * The block's current charge level and max charge transfer rate

#### ![multimeter-display](../../../.gitbook/assets/WIP.png)
As a bonus, the multimeter comes with a free clock!