# Quick Start Guide
## Installation
To install Sensible Toolbox:
1. Download the latest release from <a href="https://thebusybiscuit.github.io/builds/Slimefun/SensibleToolbox/master/" rel="nofollow">TheBusyBiscuit's builds page</a>
2. Optional dependency: install <a href="http://dev.bukkit.org/bukkit-plugins/protocollib/" rel="nofollow">ProtocolLib</a> for glowing items, working Sound Muffler and a few more features (recommended)
3. Optional dependency: install <a href="http://dev.bukkit.org/bukkit-plugins/holoapi/" rel="nofollow">HoloAPI</a> for popup info holograms on certain blocks (reduces chat clutter!)
4. Copy SensibleToolbox.jar into your <code>bukkit/plugins</code> folder
5. Restart or reload your server
6. Enjoy!

## Getting Started
This guide is best used if you have op status, although most of Sensible Toolbox's features are accessible to players by default.

Sensible Toolbox (hereafter referred to as STB) adds a ton of new functionality and this guide should give you a good overview of what to expect.  More detailed information about each item, block and system is included in the [Items](../SensibleToolbox/Items/README.md) section of this site.

## The Recipe Book
To get started, get yourself a Recipe Book.  Since STB adds many recipes, this item will make your life very much easier when trying to craft or obtain stuff.  Just get a book and a crafting table, and combine them (shapeless), to get the Recipe Book.  Hold it in your hand, and right-click.

#### ![Recipe Book](../../.gitbook/assets/WIP.png)
The resulting popup window shows every single craftable item in the game, including furnace recipes.  The bottom row of the GUI window includes several buttons: in the bottom right are buttons to skip to the next and previous pages of recipes.  Bottom left is an indicator showing the recipe page you're on (a typical server will have around 9 pages, but it could be more if you've added other plugins which add recipes), as well as a toggle button to display all recipes, vanilla recipes only, or STB recipes only.

Clicking on a craftable item will switch the book to displaying the recipe window for that item.  There could be multiple recipes for creating an item; in that case you'll see two buttons on the left and right-hand edges for cycling through the recipes.  Bottom right is a button to take you back to the item list.

#### ![Recipe Book 2](../../.gitbook/assets/WIP.png)
You can also click on items in the recipe window to drill further down (e.g. when viewing the recipe for a piston, you can click on one of the wood blocks to see how they're made).  In that case, a second button will appear in the bottom right to go back to the previous recipe.  You can drill as far down as you like, which could be many levels for some complex recipes.

### Recipe Searching
You can search for a particular recipe too; with a Recipe Book anywhere in your inventory, type <code>/stb recipe `search-term`</code> where <code>search-term</code> is any string you want to search for.  E.g. <code>stb recipe wood</code> will show recipes for all items with "wood" in the item name.  When you're in search mode, you'll see another button bottom left indicating the active search filter; you can click it to clear the filter and display all items again.

### Fabrication
Another useful feature of the Recipe Book is automatic item fabrication.  If you right click the book on a crafting table (or have a crafting table targeted and close enough when using <code>stb recipe ...</code>), another button will be available on the bottom row of the recipe view: <strong>Fabricate</strong>. Clicking this will automatically make the item for you, if you have the materials.  If you don't, you'll be told what's missing.  If you have the <strong>stb.fabricate.free</strong> permission node (true for ops by default), then you don't need to have the materials.

### Advanced Recipe Book
If you take your recipe book and craft it together with a diamond, you'll get the Advanced Recipe Book.  This acts very much like the basic recipe book, with one important advantage: in fabrication mode, crafting ingredients can also be pulled from any inventory (vanilla or STB) that is adjacent to the crafting table.

So, for example, you can fill a chest with cobblestone, wood, iron ingots and redstone, then put a workbench beside it, target that workbench and type <code>/stb recipe piston</code>, and fabricate pistons from the ingredients in the chest!

## Next Steps
The <a href="https://www.youtube.com/watch?v=2bMbXNfBJwQ" rel="nofollow">video review of v0.0.1 by MusicTechnician</a> is well worth watching.
After that, have a read of the reference sections for each part of STB: [Items](../SensibleToolbox/Items/README.md)