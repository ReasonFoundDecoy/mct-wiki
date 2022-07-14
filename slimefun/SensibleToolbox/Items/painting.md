{% hint style="warning" %}
This page is a work in progress. Information may not be accurate.
{% endhint %}

# Painting
## Paint Can
#### ![recipe-paint-can](../../../.gitbook/assets/WIP.png)
Paint cans let you mix a bucket of milk with any dye to make <em>paint</em>.  Paint can be used to re-colour any colourable block or entity in the world:

* Wool
* Carpets
* Stained clay
* Stained glass/panes
* Glass/panes (will be converted to stained glass)
* Sheep
* Wolf Collars
* Paintings
* Wood planks & slabs (depending on plugin configuration; see below)

To mix some paint, place a paint can down, and right-click it:
#### ![paint-can-gui](../../../.gitbook/assets/WIP2.png)
1. Place a milk bucket and one more dyes in these two slots
2. Press this button to mix the milk and dye, making 25 paint per dye.  The milk will be consumed, returning an empty bucket. 
3. Or press this button to empty all paint from the can.  Useful if you want to re-use the can for a different colour of paint.
4. This indicator shows the level of paint in the can.
5. This button can be used to set the paint can into public or private (only usable by its creator) mode.

Other notes:
* The paint can can hold up to 200 paint.
* If there is already paint in the can, and you mix new paint which can combine with the existing paint, it will be mixed.  E.g. blue paint and red paint will make purple paint.  If the colours don't combine, the old paint will be discarded.
* 25 paint is made per dye used, which makes this a very efficient way of colouring things.  That value is configurable via the <strong>paint_per_dye</strong> [Configuration](../configuration.md) setting.
* Paint cans will keep their paint if broken and placed elsewhere.
* [Label signs](../Items/README.md) are really useful to keep track of how much paint is in a can.

## Paint Brush
#### ![recipe-paint-brush](../../../.gitbook/assets/WIP.png)
To apply the paint you've mixed, you'll need a brush.  To load the brush with paint, right click a Paint Can.  The brush will hold up to 25 paint at a time.  If the brush already holds paint of a different colour, that paint will be discarded.

Painting things is easy: just right-click any colourable block or entity (sheep) and it will be painted.  The brush will paint up to 9 adjacent blocks of the same type as the clicked block at a time, making painting large areas very quick.  One unit of paint per coloured block will be consumed.  If you hold shift while right-clicking, only the clicked block will be painted.

You can also right-click paintings; doing so will pop up a GUI allowing direct selection of paintings by name.  This will consume paint proportional to the size of the painting, e.g. a 2x2 painting requires 4 paint.

Finally, you can empty the paint from the brush by shift-right-clicking with no block targeted.

### Wood Staining
If wood staining is enabled (see the <strong>item_settings.paintbrush.wood_staining</strong> and <strong>item_settings.paintroller.wood_staining</strong> config settings), then it is possible to paint wood planks and slabs, effectively changing their wood type.  The following paint colours are used:

<table><tbody><tr><th>Paint Colour</th><th>New Wood Type</th></tr>
<tr><td>grey</td><td>Oak</td></tr>
<tr><td>brown</td><td>Spruce</td></tr>
<tr><td>white</td><td>Birch</td></tr>
<tr><td>pink</td><td>Jungle</td></tr>
<tr><td>orange</td><td>Acacia</td></tr>
<tr><td>black</td><td>Dark Oak</td></tr>
</tbody></table>

## Paint Roller
#### ![recipe-paint-roller](../../../.gitbook/assets/WIP2.png)

The paint roller behaves exactly like the brush, with two major differences:

* It can hold up to 100 paint, instead of 25
* It can paint up to 25 blocks at a time, instead of 9

The roller is most useful when you have very large areas to cover.