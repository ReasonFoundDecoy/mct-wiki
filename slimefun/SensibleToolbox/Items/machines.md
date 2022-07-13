{% hint style="warning" %}
This page is a work in progress. Information may not be accurate.
{% endhint %}

# Machines and Upgrades
## Overview

Most machines require [energy](slimefun/SensibleToolbox/Items/energy.md), in the form of SCU</a> to run.
Machines tend to have a fairly standard look and feel to the GUI.  This is an example of a Smelter GUI, currently processing some iron dust into iron ingots.  (Iron dust is an STB item made by processing iron ore in the Masher).
#### ![machine-gui](../../../.gitbook/assets/WIP.png)

1. Input slot: you can place items here manually, or move them in with an [Item Router](slimefun/SensibleToolbox/Items/routing.md).
2. Processing indicator: this shows the item being processed and a progress indicator above it (the icon used for the progress indicator depends on the machine)
3. Output slot: finished items go here and can be extracted manually, with an Ejector Upgrade (see below), or with an Item Router.
4. These are the usual Redstone, Public/Private and Charge Meter slots found in most blocks and machines.
5. Upgrades go here: this machine has two Speed Upgrades and an Ejector Upgrade installed.
6. An energy cell can be installed here, and the button controls whether power will be transferred to or from the cell.

## Machines
### Masher
#### ![recipe-masher](../../../.gitbook/assets/WIP2.png)
The masher's primary purpose is the grinding of ores into dusts: one iron ore produces two Iron Dust, and one gold ore produces two Gold Dust.  Dusts can be smelted into ingots, effectively doubling your ingot yield per ore.
The masher is also capable of grinding and processing other ingredients, with usually better results than manually processing them, or making conversions possible that previously weren't:
<table><tbody><tr><td>Cobblestone</td><td>1 sand</td></tr>
<tr><td>Gravel</td><td>1 sand</td></tr>
<tr><td>Bone</td><td>5 bone meal</td></tr>
<tr><td>Blaze rod</td><td>4 blaze powder</td></tr>
<tr><td>Redstone ore</td><td>6 redstone</td></tr>
<tr><td>Diamond ore</td><td>2 diamonds</td></tr>
<tr><td>Lapis ore</td><td>8 lapis</td></tr>
<tr><td>Glowstone</td><td>4 glowstone dust</td></tr>
<tr><td>Tree leaves</td><td>1 green dye</td></tr>
<tr><td>Wool</td><td>4 string</td></tr>
</tbody></table>

The power required by a Masher depends on the material being processed.  Processing one iron ore requires 120 SCU; some materials cost more, most cost less.

## Sawmill
#### ![recipe-sawmill](../../../.gitbook/assets/WIP.png)
Processing a log in a sawmill yields 6 planks instead of 4, so it's a more efficient way to get wood.  This operation costs 60 SCU per log.
The sawmill can also break down several wooden item, returning the planks used to make them.  This generally costs 40 SCU per item.

## Smelter
#### ![recipe-smelter](../../../.gitbook/assets/WIP2.png)
The smelter is basically a furnace, processing the same items that a vanilla furnace processes, but using SCU instead of directly burning items.  It is significantly faster and nearly twice as efficient than a vanilla furnace; most items take 6 seconds to process instead of the vanilla furnace's 10 seconds, and food items take only 2 seconds per item to cook.  

## Pump
#### ![recipe-pump](../../../.gitbook/assets/WIP.png)

The Pump allows you to pump Liquids and fill them into Buckets. Currently it has three purposes/functions:<br>
1. Pumping Water - If you place the Pump above a Water Block it will fill a Bucket/Glass Bottle in its Input Slot with Water and move it to the Output Slot ready for extraction. The Water Block will be removed.
2. Infinite Water Pump - If you place the Pump above an Infinite Water Source. It is going to constantly fill Buckets/Glass Bottles without removing any Source Blocks
3. Pumping Lava - If you place the Pump above one or more Lava Blocks, it will fill Buckets in its Input Slot with Lava and move it to the Output Slot ready for extraction. The Pump will automatically seek for the furthest Lava Block and will then slowly make its way towards the Block below the Pump. This is very useful for pumping huge Lava seas and can be used in combination with the Magmatic Engine very nicely. Pumped Lava Blocks will then be replaced with Stone.

## Electrical Energizer
#### ![recipe-electrical-energizer](../../../.gitbook/assets/WIP2.png)
This machine allows you to easily convert Iron/Gold/Quartz into their energized Form without the need of any infernal Dust.
<table><tbody><tr><td>Iron Dust</td><td>1 Energized Iron Dust</td></tr>
<tr><td>Gold Dust</td><td>1 Energized Gold Dust</td></tr>
<tr><td>Iron Ingot</td><td>1 Energized Iron Ingot</td></tr>
<tr><td>Gold Ingot</td><td>1 Energized Gold Ingot</td></tr>
<tr><td>Nether Quartz</td><td>1 Energized Quartz</td></tr>
</tbody></table>

## Fermenter
#### ![fermenter](../../../.gitbook/assets/WIP.png)
The Fermenter is a machine that currently allows you to convert Rotten Flesh to Fish Bait which you can later use in the Fishing Net, and convert Spider Eye to Fermented Spider Eye.

## Fishing Net
#### ![fishingnet](../../../.gitbook/assets/WIP2.png)
The Fishing Net uses Fishing Bait which was previously made in the Fermenter, to catch fish. For the Fishing Net to work, you will need to place a water bucket under the machine, and provide power to it. It can catch all known fish:

* Raw Fish
* Raw Salmon
* Clownfish
* Pufferfish

An example of how to set it up can be seen here:
#### ![fishing_net-example](../../../.gitbook/assets/WIP.png)

## Upgrades

Machines can take upgrades to modify their characteristics; there are currently four available upgrades:

## Speed Upgrade
#### ![recipe-speed-upgrade](../../../.gitbook/assets/WIP2.png)
You can install multiple speed upgrades in a machine; each upgrade increases the machines speed by 40% and its power requirement by 60%:

<table><tbody><tr><th>Upgrades</th><th>Processing Speed</th><th>Processing Time</th><th>Power Requirement</th></tr>
<tr><td>0</td><td>100%</td><td>100%</td><td>100%</td></tr>
<tr><td>1</td><td>140%</td><td>71%</td><td>160%</td></tr>
<tr><td>2</td><td>196%</td><td>51%</td><td>256%</td></tr>
<tr><td>3</td><td>274%</td><td>36%</td><td>410%</td></tr>
<tr><td>4</td><td>383%</td><td>26%</td><td>655%</td></tr>
</tbody></table>

...and so on.  So installing 4 speed upgrades in a smelter will allow it to cook iron dust into iron ingots in about 1.5 seconds instead of 6, but will require about 204 SCU instead of 120  (120 * 6.55 * 0.26).

## Ejector Upgrade
#### ![recipe-ejector-upgrade](../../../.gitbook/assets/WIP.png)
If you install an ejector upgrade, the machine will automatically eject finished items.  You must configure an ejector upgrade's direction first; to do this, left-click any block face with the ejector in hand.  E.g. clicking the bottom face of a ceiling block <em>above</em> you will configure the ejector to eject items to the inventory <em>above</em>.  If there isn't an inventory in the configured direction, items will be ejected onto the floor.  You can also right-click the Ejector Upgrade while holding it to open a GUI where the direction can be configured.  Use whichever method is most convenient.

Note: an [Item Router](slimefun/SensibleToolbox/Items/routing.md) is another way of pulling finished items from a machine; use whichever method is most suitable for the task in hand.

## Regulator Upgrade
#### ![regulator-recipe](../../../.gitbook/assets/WIP2.png)
Regulator upgrades are somewhat expensive to craft, but provide efficiency improvements that are very worthwhile in the long run.  Regulators behave differently depending on what they're inserted into:

* A Regulator Upgrade in a [Heat Engine](slimefun/SensibleToolbox/Items/energy.md) will ensure that fuel is only pulled into the burner if there is definitely enough space to store the resulting SCU.  E.g. if there is coal (1800 SCU) in the input slot, it will not be pulled into the burner if the Heat Engine's internal charge is over 3200 SCU (since its maximum storage is 5000 SCU).  This can greatly improve fuel efficiency.
* A Regulator Upgrade in any machine (smelter, masher, sawmill...) will slightly mitigate the inefficiency introduced by adding Speed Upgrades; each upgrade will reduce the power multiplier by 0.1.  For example, two Speed Upgrades cause a power multiplier of 2.56, but adding three Regulator Upgrades reduces this to 2.26.  Regulator Upgrades will not reduce the power multiplier below 1.0, so are only useful in conjunction with Speed Upgrades.

## Thoroughness Upgrade
#### ![recipe-thoroughness](../../../.gitbook/assets/WIP.png)

Thoroughness Upgrades require a tier 2 [Integrated Circuit](slimefun/SensibleToolbox/Items/components.md) to craft.
A Thoroughness Upgrade slows a machine down (speed x 0.7) and increases its power consumption (SCU x 1.6).  So what's the point?  Each upgrade adds a small chance (+8%) for output boosting!

<table><tbody><tr><th>Upgrades</th><th>Processing Speed</th><th>Processing Time</th><th>Power Requirement</th></tr>
<tr><td>0</td><td>100%</td><td>100%</td><td>100%</td></tr>
<tr><td>1</td><td>70%</td><td>142%</td><td>160%</td></tr>
<tr><td>2</td><td>49%</td><td>204%</td><td>256%</td></tr>
<tr><td>3</td><td>34%</td><td>291%</td><td>410%</td></tr>
</tbody></table>

The speed penalty is roughly equally offset by a Speed Upgrade, but the power requirements of course stack.  One Masher with 4 Speed Upgrades and 4 Thoroughness Upgrades will need 1.6^6 = 42.94 SCU/tick, instead of the base 1 SCU/tick!  Since the max SCU transfer rate of a Masher is 20 SCU/tick, such a configuration will rapidly drain the Masher's internal battery and it will stall.  So there is a practical limit to the number of power-hungry upgrades which can be installed.

As an example, a Masher normally converts 1 diamond ore into 2 diamonds.  With 4 Thoroughness Upgrades, there is a 32% chance per operation that 3 or 4 diamonds will be produced instead of 2.