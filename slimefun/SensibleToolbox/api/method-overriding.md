## Overriding Methods

The STB item inheritance hierarchy looks like this:
<pre>
  BaseSTBItem
        ↓
  BaseSTBBlock
        ↓
  BaseSTBMachine
        ↓
  AbstractProcessingMachine
        ↓
  AbstractIOMachine</pre>

  Each subclass adds a few methods, most of which provide default behaviour, but a few of which are abstract and must be implemented by you. All of these methods are detailed in the following section.

  # BaseSTBItem

  ## Abstract Methods
  You must always provide an implementation for the following methods:
  
<table><tbody><tr><th>public String getItemName()</th><td>The custom item's display name (as returned by item.getItemMeta().getDisplayName())</td></tr>
<tr><th>public String[] getLore()</th><td>The custom item's lore (as returned by item.getItemMeta().getLore()) - this is where you can put some descriptive text about what the item does, for example</td></tr>
<tr><th>public MaterialData getMaterialData()</th><td>The vanilla material and data used to represent the item in an inventory.  Note this returns a MaterialData, not just a plain Material; this allows for coloured glass/clay etc. to be used.  The <strong>STBUtil.makeColouredMaterial()</strong> utilty method may be handy here.</td></tr>
<tr><th>public Recipe getRecipe()</th><td>Returns a recipe to make the item.  You can return null here if you don't want the item to be crafted with a vanilla recipe.</td></tr>
</tbody></table>

## Optional Methods
You <i>may</i> also implement/override the following methods:

<table><tbody><tr><th>public String getDisplaySuffix()</th><td>Any string returned here is appended to the item's display name.  You can override this to encode some of the item's state (e.g. paint level in a Paint Brush) in the item's display name</td></tr>
<tr><th>public String[] getExtraLore()</th><td>Any string array returned here is appened to the item's lore.  This can be used to encode more of the item's state (e.g. items filtered by an Item Router module)</td></tr>
<tr><th>public Recipe[] getExtraRecipes()</th><td>If there's more than one way to make your item, you can override this method to return one or more extra vanilla recipes.</td></tr>
<tr><th>public boolean hasGlow()</th><td>If you want the vanilla item that represents your STB item to have a glow effect (as if enchanted), override this method to return true.  Note that items will only glow if ProtocolLib is installed.</td></tr>
<tr><th>public boolean isWearable()</th><td>If your item uses a vanilla material but should not be worn, override this method to return false.</td></tr>
<tr><th>public ItemStack getSmeltingResult()</th><td>If your item can be smelted (in a vanilla furnace, or STB Smelter), override this method to return the item that should be produced as a result.  This method returns null by default.</td></tr>
<tr><th>public boolean isEnchantable()</th><td>Define whether this item may be enchanted in a vanilla enchanting table.  By default, this method returns true.  If your item uses an enchantable material, but enchanting it doesn't make sense, return false here.</td></tr>
</tbody></table>

## Event Handler Methods
The following methods define how items respond to certain events. The default behaviour is generally to ignore the event, but you may override any or all of these:

<table><tbody><tr><th>public void onInteractItem(PlayerInteractEvent event)</th><td>Called when a player interacts with your item while holding it.</td></tr>
<tr><th>public void onItemConsume(PlayerItemConsumeEvent event)</th><td>Called when a player attempts to consume your item (which will only happen if your item uses a vanilla material which is consumable, e.g. food, water bottle...)</td></tr>
<tr><th>public void onInteractEntity(PlayerInteractEntityEvent event)</th><td>Called when a player right-clicks some entity while holding your item.</td></tr>
<tr><th>public void onItemHeld(PlayerItemHeldEvent event)</th><td>Called when a player holds shift and rolls the mouse wheel while holding your item.  Note that the held item will never be changed in this case; STB overrides the shift-mouse-wheel to call this event.  It may be useful to configure some numeric or cyclable property of your item.</td></tr>
<tr><th>public void onBreakBlockWithItem(BlockBreakEvent event)</th><td>Called when a block is broken while holding your item.  Note that is only called when the block will definitely be broken; you must <em>never</em> cancel or otherwise change the outcome of the BlockBreakEvent.</td></tr>
</tbody></table>

# BaseSTBBlock

## Optional Methods
<table><tbody><tr><th>public int getTickRate()</th><td>Defines how often the <strong>onServerTick()</strong> method (see below) should be called for this object.  Default is 0, which means never call onServerTick().  If your block should have some periodic behaviour, override this method and onServerTick() to define how frequently it should act.</td></tr>
</tbody></table>

## Event Handler Methods

<table><tbody><tr><th>public void onBlockDamage(BlockDamageEvent event)</th><td>Called when this block is damaged.  This event may be cancelled to prevent damage.</td></tr>
<tr><th>public void onBlockPhysics(BlockPhysicsEvent event)</th><td>Called when this block receives a physics event; a change in state of a neighbouring block.</td></tr>
<tr><th>public void onInteractBlock(PlayerInteractEvent event)</th><td>Called when a player interacts with this block in some way.  The default behaviour is to attach a label sign if left-clicked with a sign; if you want to preserve this behaviour in your block, then be sure to call <strong>super.onInteractBlock(event)</strong> in your overriden method.</td></tr>
<tr><th>public boolean onSignChange(SignChangeEvent event)</th><td>Called when a sign attached to your block is updated.  You could override this to allow some kind of configuration of the block based on the sign's text.</td></tr>
<tr><th>public boolean onEntityExplode(EntityExplodeEvent event)</th><td>Called when this block is affected by an explosion.  Default behaviour is to return true, meaning the block will break, and drop its item form.  If you override this to return false, your block will be immune to explosions.</td></tr>
<tr><th>public void onServerTick()</th><td>Called periodically for this block.  The frequency of this call depends on what you have define for <strong>getTickRate()</strong> (see above)</td></tr>
<tr><th>public void onBlockPlace(BlockPlaceEvent event)</th><td>Called when this block is placed in the world.  If you override this, you must <em>always</em> call <strong>super.onBlockPlace(event)</strong>.</td></tr>
<tr><th>public void onBlockBreak(BlockBreakEvent event)</th><td>Called when this block broken.  If you override this, you must <em>always</em> call <strong>super.onBlockBreak(event)</strong> and you must <em>never</em> cancel the event or otherwise alter the event's outcome.</td></tr>
</tbody></table>