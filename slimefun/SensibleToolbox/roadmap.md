# Roadmap
{% hint style="warning" %}
As of now (July 13, 2022), none of this info is current. This is all assumed to be from `desht`. I'm including it here to get a peak into the dev's ideas, so that maybe they can be designed in the future, continuing the legacy, and keeping STB in the eye's of server owners!
{% endhint %}

The current STB release creates a useful framework for custom item definition and persistence, adds an energy system, and adds a number of handy items and blocks, but it is very much a beta at this point.  Here's an idea of what needs to be done:

<a href="http://dev.bukkit.org/bukkit-plugins/sensible-toolbox/files/7-sensible-toolbox-v0-99-2-rc3/" rel="nofollow">v0.99.2 is now approved!</a>

### Next Release (v1.0?)
* Blast Furnace: supercharged furnace, will need to be adjacent to lava & also require SCU.  Tier 2 machine.  Multi-block (2 high) structure. Will be needed for certain higher-tier (tier 3?) recipes.  Undecided if it will be able to process standard furnace recipes...
* XP Bank - bank XP, possibly absorb raw XP items, for a SCU cost.  Will probably allow dispensing XP in the form of Bottles O' Enchanting, or raw XP.  (Later on, this will be able to supply machines which use XP: auto-enchanting, mob-spawning..)
* Repair Station: repair tools using SCU and repair resources (e.g. iron for iron tools, etc.).  No XP cost, but non-trivial SCU cost.
* Geothermal Generator: tier 2 generator, requires water (a use for the Pump!) and to be placed above lava.  Will slowly turn lava below it to stone (cobble?) and will send the resulting steam to a Steam Turbine to generate SCU.  Will be rather efficient.
* Wind Generator: convert wind energy to SCU.  Will need plenty of space and work better at higher Y levels.  Will require a crafted rotor, which will wear out over time (possibly multiple tiers of rotor with differing lifespans & SCU generation).  More SCU but more rotor wear during storms.  Will also require a Rotary Generator to actually generate SCU.
* Hydro Generator: convert flowing water to SCU.  Like the wind generator, will need crafted turbine blades and a separate Rotary Generator.  Best power generation will be from water falling directly onto the top of the generator from a great height.
* Item Router Storage module: place in an Item Router which is adjacent to a bank of BSU/HSU blocks, and it will intelligently store or pull the item in the right storage unit.  This will only work with BSU/HSU's, not vanilla chests.
* Auto-crafting machine; place an item into it, choose one of the (vanilla crafting) recipes which make that item, and it will automatically make copies of the item from ingredients in its inventory.
* Wireless redstone: behaving somewhat like ender storage with frequencies and global/personal visibility.

### More on Energy Generation
The current two tier 1 & 2 generators (Heat Engine and Basic/Dense Solars) are single-block generators, but future energy generation is likely to require multiple blocks to actually output SCU.  For example:

* Geothermal Generator will produce steam, by piping water into lava and getting steam back (slowly solidifying the lava in the process).
* A Boiler will produce steam from water and burnable fuel (will be more efficient than a Heat Engine)
* Wind Turbine will produce rotary energy, as will a Hydro Generator.
* A Steam Turbine will turn steam energy (from Geothermal & Boiler) into rotary energy.
* A Rotary Generator will turn rotary energy (from Steam Turbine, Wind Generator & Hydro Generator) into SCU.
* Some kind of biofuel engine (producing rotary energy) fuelled by fermented farm products is likely in the future.  Fermentation process will require machinery & SCU too...

The idea will be to place these blocks adjacent to each other, possibly on a specific side.  E.g. Wind Generator will output rotational energy at the back, so put the Generator behind it.  A Boiler will output steam upward, so put a Steam Turbine on top of the boiler and Generator behind the turbine.  And so on...

It all gets a bit more complex than single generators in a block, but hopefully also a bit more interesting.  There will be some maintenance costs to all this - I don't want free energy especially from solar/wind (solar already requires consumable PV cells) - but at the same time I want to keep the tediousness low.  Turbine blades for wind/hydro/steam generators may need replacement (or repair, for less material cost) periodically for example; better materials and perhaps a craftable lubricant could mitigate that.  Geothermal not much of an issue; lava is a consumable resource.

#### Tier 3 Stuff?
* *Need to decide on tier 3 components and requirements to make them...
* Tier 3 energy storage: 1M energy cell and 1M battery box.  Going to need diamonds.
* Ender cage: upgraded version of the ender leash which can also store a hostile mob.  Won't be cheap.
* Mob spawner: will need SCU, XP, and an ender cage with a stored mob - will spawn copies of that mob.  Won't work on bosses (wither/ender dragon).  Will need limiting mechanic to avoid excessive spawning of mobs like wither skeletons (probably high SCU or XP requirement)
* Auto-enchanter: will need SCU and XP.  May allow specific enchantment to be selected.  Possibly require the enchantment to be learned first via insertion of enchanted book.
* Auto-disenchanter: will need SCU.  Strip random enchantments off items, probably damaging the item, producing enchanted books.
* Auto-miner: scan downwards, pulling ores out of the ground, replacing with stone (cobble/dirt?).  High SCU requirement.  Configurable via upgrades?

### Testing
This really needs a ton of testing by people other than myself.  I'd welcome any and all attempts to break it, asking only that well-written bug reports (or even better, github pull requests!) are sent.

In particular, I'd like to know:

* *How well this performs with many players using many blocks and items.  Some functionality is likely to be somewhat CPU intensive (item routers in particular need to do a lot of inventory scanning and the vacuum module needs to regularly search for items on the ground).
* How well it interacts with other plugins, in particular protection plugins.  I know that plugins such as Movecraft which shift blocks around <em>will</em> break this, but I'm not sure there's an easy workaround.
* Any potential exploits which allow item/block duping etc.

### Tech Tree
The initial release adds a few items and machine, but I plan to design a bigger tech tree with multiple tiers of advancement.  Everything in the current release can be considered tier 1 (although I'm debating whether solar cells should be as easy to obtain - free power and all that...)
Newer categories of items will include:
* Machines that require a water supply or lava supply - a use for the Pump
* Automated farming - I like the way Minefactory Reloaded does things and I may emulate some of that, but I have other ideas too
* Automated crafting
* Better enchantment handling
* Mob spawning control
* Larger scale machines: terrain modification, automated mining... this will be higher tier stuff for sure
* More varied and interesting mechanisms for power generation and storage
* Powered item repair system (alternative to the anvil)
* New weapons and armour perhaps?
* Higher tech item storage and retrieval system (think Applied Energistics, only probably more limited :) )

Some of this may be released as separate plugins; STB is intended to make it very easy for other plugins to create new items & blocks.