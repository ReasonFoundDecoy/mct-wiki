{% hint style="warning" %}
This page is a work in progress. Information may not be accurate.
{% endhint %}

# Basic Utilities

## Block Update Detector
#### ![BUD](../../../.gitbook/assets/WIP.png)
This block emits a brief redstone pulse when it detects that a neighbouring block has updated (this could be any kind of update: block placed/broken, crops growing, door opening, lever flipping, redstone activating...).  This block is configurable - right-click it once placed to 

This block emits a brief redstone pulse when it detects that a neighbouring block has updated (this could be any kind of update: block placed/broken, crops growing, door opening, lever flipping, redstone activating...).  This block is configurable - right-click it once placed to open the GUI.  The pulse duration and sleep time can be both be adjusted by GUI buttons (left click to decrease by 10 ticks, right click to increase by ticks, and hold shift to adjust by 1 tick).

The sleep time is used to "dampen" the updates - after a pulse, the block will ignore any changes during its sleep time.  This can be useful if you want to avoid extra pulses for blocks that change rapidly.

## Elevator
#### ![Elevator](../../../.gitbook/assets/WIP2.png)
This useful item allows quick and easy vertical travel in both directions.  Place elevator blocks directly above other elevator blocks with clear space in between (it is OK to put "passable" blocks like carpets on top of an elevator).  Then, while standing on an elevator, press Space to warp up to the next elevator above, and Shift to warp down to the next elevator below.
Elevators can be coloured by right-clicking them with a dye or an STB [Paint Brush](../Items/painting.md); only elevators of the same colour can be warped between.

## Ender Leash
#### ![Ender Leash](../../../.gitbook/assets/WIP.png)
This magically-infused leash allows capture and release of passive animals.  Right-click any animal to capture it within the leash indefinitely; right-click again to release the animal wherever you want.
Special data on the animal (e.g. sheep colour, horse colour/style, animal names) will be preserved.

## Recipe Book
#### ![Recipe Book](../../../.gitbook/assets/WIP2.png)
See the [Quick Start Guide](../quick-start-guide.md) for a detailed description of the recipe book.

## Redstone Clock
#### ![Redstone Clock](../../../.gitbook/assets/WIP.png)
This block emits a redstone pulse at a regular interval.  The duration and interval of the pulse are both configurable; right-click the block once placed to open the configuration GUI.  There are two buttons on the left-hand side to adjust pulse & duration (left click to decrease by 10 ticks, right click to increase by ticks, and hold shift to adjust by 1 tick).

## Sound Muffler
#### ![Sound Muffler](../../../.gitbook/assets/WIP2.png)
Getting a little tired of that incessant bleating and mooing from your cow/sheep farm?  This block is what you need.  Place it down and all sounds within an 8-block radius will be muffled; by default, reduced to 10% of their normal volume.  The block is configurable; right-click it to open a GUI, where the volume can be adjusted, from 0% to 100% of normal.
Notes:
* The <a href="http://dev.bukkit.org/bukkit-plugins/protocollib/" rel="nofollow">ProtocolLib</a> plugin is required for this block to function.
* Some sounds, e.g. rainfall, are client-side and cannot be muffled by this block.  Only sound packets sent from server to client can be intercepted and modified.

## Tape Measure
#### ![Tape Measure](../../../.gitbook/assets/WIP.png)
This item allows for easy measurement of the distance between two blocks.  Shift-right click a block to set the initial measurement point.  Now right-click any nearby block and you will be told the X, Y & Z offsets from the initial block, as well as the overall distance.

## Trash Can
#### ![Trash Can](../../../.gitbook/assets/WIP2.png)
This item is a convenient way to destroy items without the need for a dangerous lava pool or cactus plant.  It's also possible to pipe items into it with a hopper or STB [Item Router](../Items/routing.md).  Any items which enter it will be lost forever!