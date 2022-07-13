# Developer API

STB offers an API to make it easy for other plugins to define their own custom items and blocks, and benefit from STB's framework of automated event routing, energy system, GUI methods and block persistence.
* [API Javadocs](http://desht.github.io/sensibletoolbox/)

As of v0.0.4 the API has settled down somewhat and later versions of STB should (hopefully!) not introduce any API breakage without good warning via deprecation.
<br><br>

<b>The basic steps to creating an STB-based plugin are:</b>

<ol><li>Add SensibleToolbox as a build dependency to your plugin
</li><li>Add a dependency on SensibleToolbox  (soft or hard, depends on how you're using STB) in your plugin's <code>plugin.yml</code> file
</li><li>Define your custom item/block class(es) in your plugin
</li><li>Attempt to hook SensibleToolbox in your plugin's <strong>onEnable()</strong> method
</li><li>If you successfully hook SensibleToolbox, register your custom item/block class(es) with a simple API call
</li></ol>

The above steps will now be explained in more detail...
<br><br>

## Add STB as a Build Dependency

If you build your plugin with Maven (recommended!), just add these lines to your `pom.xml`:

<pre><span>&lt;!--add this to your repositories section --&gt;</span>
<span>&lt;repository&gt;</span>
  <span>&lt;id&gt;</span>hawkfalcon-repo<span>&lt;/id&gt;</span>
  <span>&lt;name&gt;</span>Hawkfalcon Repository<span>&lt;/name&gt;</span>
  <span>&lt;url&gt;</span><a href="/linkout?remoteUrl=http%253a%252f%252fci.hawkfalcon.com%252fplugin%252frepository%252feverything" rel="nofollow">http://ci.hawkfalcon.com/plugin/repository/everything</a><span>&lt;/url&gt;</span>
<span>&lt;/repository&gt;</span>

<span>&lt;!--add this to your dependencies section --&gt;</span>
<span>&lt;dependency&gt;</span>
  <span>&lt;groupId&gt;</span>me.desht<span>&lt;/groupId&gt;</span>
  <span>&lt;artifactId&gt;</span>sensibletoolbox<span>&lt;/artifactId&gt;</span>
  <span>&lt;version&gt;</span>0.0.4<span>&lt;/version&gt;</span>
  <span>&lt;scope&gt;</span>provided<span>&lt;/scope&gt;</span>
<span>&lt;/dependency&gt;</span>
</pre>

I recommend using an explicit `<version>` number there. The current release version at time of writing is 0.0.4.

If you don't use Maven, you'll need to [download the desired version of SensibleToolbox.jar](https://thebusybiscuit.github.io/builds/Slimefun/SensibleToolbox/master/) and manually add it as a build dependency in your IDE.
<br><br>

## Add a plugin.yml dependency

Easy enough; just add this line to your <code>plugin.yml</code>:
<pre><span>depend</span><span>:</span> <span>[</span> <span>ProtocolLib</span><span>,</span> <span>SensibleToolbox</span> <span>]</span>
</pre>
or if your plugin already depends on other plugins, add it to the list:
<pre><span>depend</span><span>:</span> <span>[</span> <span>ProtocolLib</span><span>,</span> <span>SensibleToolbox</span> <span>]</span>
</pre>

## Defining a Custom Item/Block Class

This is most complex part. Defining a new STB item or block basically consists of creating a class which extends one of the existing base classes provided by SensibleToolbox, overriding several mandatory methods, and optionally overriding many more methods. The useful base classes to extend are:

<ul><li><strong>BaseSTBItem</strong> - extend this class if your new item is just an item, and not placeable in the world as a block.  Example: <a href="https://github.com/desht/sensibletoolbox/blob/master/src/main/java/me/desht/sensibletoolbox/items/TapeMeasure.java" rel="nofollow">https://github.com/desht/sensibletoolbox/blob/master/src/main/java/me/desht/sensibletoolbox/items/TapeMeasure.java</a>
</li><li><strong>BaseSTBBlock</strong> - extend this class if your new item is a generic block (but read on for more specific types of block).  Example: <a href="https://github.com/desht/sensibletoolbox/blob/master/src/main/java/me/desht/sensibletoolbox/blocks/RedstoneClock.java" rel="nofollow">https://github.com/desht/sensibletoolbox/blob/master/src/main/java/me/desht/sensibletoolbox/blocks/RedstoneClock.java</a>
</li><li><strong>BaseSTBMachine</strong> - extend this class if your new item is a generic machine, with input/output slots, an energy cell slot and can be charged with SCU.  Example: <a href="https://github.com/desht/sensibletoolbox/blob/master/src/main/java/me/desht/sensibletoolbox/blocks/machines/FiftyKBatteryBox.java" rel="nofollow">https://github.com/desht/sensibletoolbox/blob/master/src/main/java/me/desht/sensibletoolbox/blocks/machines/FiftyKBatteryBox.java</a>
</li><li><strong>AbstractProcessingMachine</strong> - extend this class if your machine will have a progress bar to indicate its progress.  Note that this can also be used to indicate any kind of numeric quantity, e.g. see <a href="https://github.com/desht/sensibletoolbox/blob/master/src/main/java/me/desht/sensibletoolbox/blocks/machines/BigStorageUnit.java" rel="nofollow">https://github.com/desht/sensibletoolbox/blob/master/src/main/java/me/desht/sensibletoolbox/blocks/machines/BigStorageUnit.java</a> (the processing indicator here shows the number of items in the BSU)
</li><li><strong>AbstractIOMachine</strong> - extend this class if your machine does simple input-&gt;output item processing, with possible custom recipes.  Example: <a href="https://github.com/desht/sensibletoolbox/blob/master/src/main/java/me/desht/sensibletoolbox/blocks/machines/Masher.java" rel="nofollow">https://github.com/desht/sensibletoolbox/blob/master/src/main/java/me/desht/sensibletoolbox/blocks/machines/Masher.java</a>
</li></ul>

The Javadocs contain a full reference of the methods which must be or may be overridden in your new subclass.
<br><br>

## Hooking SensibleToolbox and Registering your Item(s)

You'll want to use code similar to the following in your `onEnable()`:

<pre><span>public</span> <span>void</span> <span>onEnable</span><span>()</span> <span>{</span>
  <span>// ... do other stuff</span>

  <span>Plugin</span> <span>stb</span> <span>=</span> <span>pm</span><span>.</span><span>getPlugin</span><span>(</span><span>"SensibleToolbox"</span><span>);</span>
  <span>if</span> <span>(</span><span>stb</span> <span>!=</span> <span>null</span> <span>&amp;&amp;</span> <span>stb</span><span>.</span><span>isEnabled</span><span>())</span> <span>{</span>
    <span>SensibleToolbox</span><span>.</span><span>getItemRegistry</span><span>().</span><span>registerItem</span><span>(</span><span>this</span><span>,</span> <span>new</span> <span>YourCustomItemClass</span><span>());</span>
  <span>}</span>

  <span>// ...</span>
<span>}</span>
</pre>

## An Example Plugin

The STBTest plugin has been created to use as a testbed for hooking into Sensible Toolbox, but also to serve as example code on how the Sensible Toolbox API can be used:
* https://github.com/desht/stbtest/

So far, only one new item has been added, the Lightning Gun: https://github.com/desht/stbtest/blob/master/src/main/java/me/desht/stbtest/LightningGun.java - the code is heavily commented and worth browsing to get an idea of how a simple STB item would be created. It includes concepts such as freezing/thawing item data, storing and using SCU, and using custom STB ingredients in its crafting recipe.