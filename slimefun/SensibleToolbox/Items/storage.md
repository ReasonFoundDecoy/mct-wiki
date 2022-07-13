{% hint style="warning" %}
This page is a work in progress. Information may not be accurate.
{% endhint %}

# Storage
STB provides a couple of blocks for efficient mass storage of items.

## BSU (Big Storage Unit)
#### ![recipe-bsu](../../../.gitbook/assets/WIP.png)
The BSU can store up to 128 stacks of a single item (so up to 8192 items if the item's stack size is 64).

Right-clicking the BSU will open a GUI:

#### ![bsu-gui](../../../.gitbook/assets/WIP2.png)

1. Place items to be stored in this slot.  They will be automatically pulled into storage, if there's room.  If there are items in storage, then only items of <em>exactly</em> the same type (material, block data and metadata) will be accepted.
2. Items stored are shown here; the tooltip shows the number of items stored and the maximum number storable.
3. This is the output slot; this is automatically filled from the internal storage up to the stored item's maximum stack size.
4. The bottom button here toggles the BSU's "locked" mode; when locked, the BSU will remember its stored item even when emptied, and only accept that item, either via the GUI or from an Item Router.  When unlocked, the BSU will forget its stored item if it's emptied, and accept any item.

[Labelling a BSU with a sign](slimefun/SensibleToolbox/Items/README.md) is a useful thing to do; you will see at a glance what is stored and how much.  A locked BSU shows the item quantity in red (unlocked shows the quantity in black).

There are other ways to quickly store and extract items:

* Right-clicking a BSU with the same item in hand as the item that is stored will automatically store that item in the BSU. Right-clicking an empty BSU will always open the GUI.  Note that right-clicking with block items (e.g. stone) may require you to stand a little back from the BSU - this is a CraftBukkit limitation on how events are fired when right-clicking with a block item, and not something that STB can control.
* Double-right-clicking will store <em>all</em> items in the player's inventory that match the stored item.
* Left-clicking a BSU will pop out one stack of the stored item on the floor.
* Shift-left-clicking a BSU will pop out a single item.
* You can also move items in and out with an [Item Router](slimefun/SensibleToolbox/Items/routing.md).

If you break a BSU, its contents will be scattered on the floor.  Breaking a full BSU is not a great idea!  In addition, a maximum of 4096 items will be dropped; any stored items over that will be lost forever.

## HSU (Hyper Storage Unit)
#### ![hsu](../../../.gitbook/assets/WIP.png)
The HSU functions in a similar manner to the BSU, but with these important differences:

* The HSU can store up to <em>2 billion</em> items in a nearby dimensional pocket
* Due to its extra-dimensional nature, the HSU does <em>not</em> lose its contents when broken.  This makes it an excellent solution for moving very large quantities of items around.
* The HSU requires a small amount of <a href="https://www.curseforge.com/wiki/invalid-link/" rel="nofollow">energy</a> to run:
    * Inserting items (manually or via an Item Router) uses 0.05 SCU per item inserted.  So a stack of 64 items requires 3.2 SCU.
    * Extracting items via an Item Router uses 0.05 SCU per item extracted.
    * Extracting items manually does not require power, so if you run out of energy, your items are still available to you.
* The HSU has an internal charge buffer of 1000 SCU, and can receive energy at a maximum rate of 10 SCU/tick.  It can also take an energy cell.

Note that as of STB v0.0.3, the HSU requires an [Integrated Circuit](slimefun/SensibleToolbox/Items/components.md) to craft.