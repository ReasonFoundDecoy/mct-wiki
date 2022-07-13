{% hint style="warning" %}
This page is a work in progress. Information may not be accurate.
{% endhint %}

# Ender Storage
## Overview
#### ![enderstorage](../../../.gitbook/assets/WIP.png)
Sensible Toolbox features a sophisticated Ender Storage system that is a huge improvement over the basic vanilla Ender Chest:
* Storage frequencies: up to 1000 separate personal (per-player) inventories, plus a further 1000 global (common to all players) inventories.
* Ender Box: looks like a vanilla Ender Chest, but can have its frequency tuned with the Ender Tuner.  The Ender Box can also be interacted with via an [item router](slimefun/SensibleToolbox/Items/routing.md).
* Ender Bag: basically a portable Ender Box, allowing access to inventories on the go.  Ender Bags can also be tuned with the Ender Tuner, or linked to an Ender Box by shift-right-clicking one with the Ender Bag in hand.  (The Ender Bag replaces the Bag of Holding from v0.0.1 alpha; if you have one of these in your inventory, you can place it in a crafting grid to get an Ender Bag).
* Ender Tuner: this tool is used to tune the frequency and scope (global or personal) of Ender Boxes and Ender Bags.

## Comparison with Forge mod
If you have ever used Chickenbones' excellent <a href="http://www.minecraftforum.net/topic/909223-164-smp-chickenbones-mods/" rel="nofollow">Ender Storage</a> Forge mod, the concept will be familiar; here are the similarities and differences ("ES" refers to the Ender Storage mod): 
* The Ender Pouch and Ender Chest from ES are the Ender Bag and Ender Box, respectively.
* Unlike ES, Sensible Toolbox does not remove the vanilla Ender Chest from the game (and the Ender Chest is used as a crafting ingredient in the Ender Bag and Ender Box recipes).
* ES uses (and consumes) up to 3 dyes to set the "frequency" of a chest or pouch; STB has the re-usable Ender Tuner tool to configure boxes and bags.
* ES gives 16^3 = 4096 channels.  STB gives 1000 channels (per player, plus 1000 global).
* ES Ender Chests are global by default, and require a diamond to convert to personal.  STB Ender Boxes/Bags have personal scope by default, and use the Ender Tuner tool to convert to global scope (although a diamond is needed to craft a bag or box).
* Both ES and STB allow linking a bag (pouch) to a box (chest) by right-clicking the block object with the held item (although STB requires a shift-right-click).
* STB crafting recipes may be considered slightly more expensive than the ES equivalents, although only 1 blaze powder is required, and no blaze rods.

## Items
## Ender Bag
#### ![enderbag-recipe](../../../.gitbook/assets/WIP2.png)
A newly crafted Ender Bag is a personal 54-slot inventory store on ender frequency ƒ1.  Since the storage is extra-dimensional, the items in the bag are safe from destruction, if the bag is destroyed, e.g. by a fall into lava.  Just craft a new bag, and the items will be available again.  All other Ender Bags and Ender Boxes on the same personal frequency will show the same inventory when opened.
To change the ender frequency or scope of a bag, use the Ender Tuner tool, described below.  You can also link a held Ender Bag to a placed Ender Box by shift-right-clicking the box with the bag.  If successful, you will hear a beep, and the bag's title will reflect the new frequency for the bag.

## Ender Box
#### ![enderbox-recipe](../../../.gitbook/assets/WIP.png)
The Ender Box behaves (and looks) rather like a vanilla Ender Chest, but provides a 54-slot inventory and uses the same frequencies/inventories as the Ender Bag.

It is also possible to interact with an Ender Box via the [item router](slimefun/SensibleToolbox/Items/routing.md) (but not with a vanilla hopper); this allows for some powerful functionality if you carry an Ender Bag on the same frequency with you - if you have an item router configured to pull items out of the box and into storage in your base, you can place items in the bag at any distance from your base and instantaneously "send them home".  When an item router tries to interact with an Ender Box on a personal frequency, the owner of the item router is used to determine whose ender inventory will be accessed.

To change the ender frequency or scope of a box, use the Ender Tuner tool described below.

It is useful to place a [label sign](slimefun/SensibleToolbox/Items) on Ender Boxes; this will distinguish them from vanilla ender chests, as well as displaying the box's current ender frequency and scope.

## Ender Tuner
#### ![endertuner-recipe](../../../.gitbook/assets/WIP2.png)
This tool allows the configuration of the ender frequency and scope of Ender Bags and Ender Boxes.
To configure a bag, or box item in inventory, right-click the Ender Tuner to get the resulting GUI:
#### ![endertuner1](../../../.gitbook/assets/WIP.png)
1. Place an Ender Bag or Ender Box in this slot.
2. Click this button to alter the frequency of any bag or box in the above slot.  Left-click to decrease by 1, right-click to increase by 1.  Hold Shift to decrease/increase by 10, respectively.
3. Click this button to toggle the bag or box between Personal and Global scope.
Any changes are immediately applied to the bag/box in the item slot.  Closing the tuner GUI will return the bag to your inventory, or you can manually remove the item from the GUI.

You can also use the tuner to configure placed Ender Boxes.  Simply right-click a box with a tuner in hand to get the resulting GUI:
#### ![endertuner2](../../../.gitbook/assets/WIP2.png)
This behaves very much like the item configuration GUI above, except:
1. The Ender Box displayed in the item slot is fixed and cannot be removed from the GUI.
2. An extra public/private GUI button is available.  Note that "public/private" is distinct from "global/personal" scope.  Private ender boxes can be accessed only by the box's owner, i.e. the player who placed the box originally.  Public boxes can be accessed by anyone (but a box with personal scope will of course display the accessing player's ender inventory, not the box owner's ender inventory!)