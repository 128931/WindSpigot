# WindSpigot [![GitHub Workflow Status](https://github.com/Wind-Development/WindSpigot/actions/workflows/windspigot-build-and-upload.yml/badge.svg)](https://nightly.link/Wind-Development/WindSpigot/workflows/windspigot-build-and-upload/master/WindSpigot-server.zip) [![Codacy Badge](https://app.codacy.com/project/badge/Grade/3c5ee8d2ef324d23ab085d89139ea0e7)](https://www.codacy.com/gh/Wind-Development/WindSpigot/dashboard?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=Wind-Development/WindSpigot&amp;utm_campaign=Badge_Grade) [![Discord](https://img.shields.io/discord/949530782261714974?label=discord)](https://discord.gg/hqbJvQZpV2)

##### WindSpigot is a 1.8.8 Minecraft server software focused on improving overall server performance and pvp mechanics. WindSpigot is based on a **[fork of NachoSpigot](https://github.com/Argarian-Network/NachoSpigot/tree/async-entity-tracker)**.

**WindSpigot supports Java 8 to Java 17!**

## Downloads
See the **[releases](https://github.com/Wind-Development/WindSpigot/releases)** tab for the latest release. Alternatively, you can download the latest build **[here](https://nightly.link/Wind-Development/WindSpigot/workflows/windspigot-build-and-upload/master/WindSpigot-server.zip)**. The latest build may be unstable, but contains more features.

## FAQ

#### What combat mechanics are improved on?
WindSpigot makes potion speed and hit delay configurable. We also have NachoSpigot's configurable knockback.

#### What does WindSpigot do to improve overall performance?
WindSpigot moves heavy work off of the main server thread and splits up the server load.

#### What is done asynchronously to achieve this?
- Worlds (ticked parallel to each other)
- Entity path searching (entity AI calculations are done async)
- The entity tracker (updated with multiple threads, based on **[this](https://github.com/Argarian-Network/NachoSpigot/tree/async-entity-tracker)**)
- Knockback (packets are sent with high priority, based on **[this](https://github.com/Argarian-Network/NachoSpigot/tree/async-kb-hit)**)

#### What other modifications does WindSpigot have?
See the patches list below.

## Patches
**All credit goes to the people that made these patches.**<br>
*Give credit where credit is due!*
```
[WindSpigot-0001] Thread affinity
[WindSpigot-0002] WindSpigot config
[WindSpigot-0003] Mob AI toggle command
[WindSpigot-0004] Parallel world ticking
[WindSpigot-0005] Disable mob spawning if tps is not stable
[WindSpigot-0006] Remove fastmath usage from explosions
[WindSpigot-0007] Player ping command
[WindSpigot-0008] Make NachoSpigot's async TNT configurable
[WindSpigot-0009] Configurable entity hit delay
[WindSpigot-0010] Configurable potion speeds
[WindSpigot-0011] Make console display of player ips toggleable
[WindSpigot-0012] Re-implement Spigot's max tick time for certain configurable entities
[WindSpigot-0013] More configuration for knockback
[WindSpigot-0014] Async entity path searching
[WindSpigot-0015] Configurable explosion animations and sound
[WindSpigot-0016] Configurable weather changes

[Spigot-0097] Remove DataWatcher Locking by spottedleaf
[Spigot-0138] Branchless NibbleArray by md5
[Spigot-2380] Hitting in the air will always load the chunk at 0,0 by md_5

[Paper-0021] Implement Paper VersionChecker
[Paper-0033] Optimize explosions
[Paper-0044] Use UserCache for player heads
[Paper-0072] Fix Furnace cook time bug when lagging by Aikar
[Paper-0076] Optimized Light Level Comparisons by Aikar
[Paper-0083] Waving banner workaround by Gabscap
[Paper-0068] Use a Shared Random for Entities by Aikar
[Paper-0085] Add handshake event to allow plugins to handle client handshaking logic themselves
[Paper-0093] Don't save empty scoreboard teams to scoreboard.dat by Aikar
[Paper-0097] Faster redstone torch rapid clock removal by Martin Panzer
[Paper-0100] Avoid blocking on Network Manager creation by Aikar
[Paper-0102] Update log4j
[Paper-0103] Add setting for proxy online mode status
[Paper-0112] Reduce IO ops opening a new region file by Antony Riley
[Paper-0122] Don't let fishinghooks use portals by Zach Brown
[Paper-0125] Optimize World.isLoaded(BlockPosition)Z by Aikar
[Paper-0125] Improve Maps (in item frames) performance and bug fixes by Aikar
[Paper-0141] Do not let armorstands drown
[Paper-0144] Improve Minecraft Hopper Performance by Aikar
[Paper-0152] Disable ticking of snow blocks by killme
[Paper-0164] [MC-117075] TE Unload Lag Spike by mezz
[Paper-0168] Cache user authenticator threads by vemacs
[Paper-0207] Shame on you Mojang moves chunk loading off https thread by Aikar
[Paper-0249] Improve BlockPosition inlining by Techcable
[Paper-0254] Don't blindly send unlit chunks when lighting updates are allowed by Shane Freeder
[Paper-0266] [MC-99321] Dont check for blocked double chest for hoppers
[Paper-0302] Don't load chunks for villager door checks by Aikar
[Paper-0313] Optimize World Time Updates by Aikar
[Paper-0321] Server Tick Events
[Paper-0342] Always process chunk removal in removeEntity by Aikar 2018
[Paper-0344] [MC-111480] Start Entity ID's at 1
[Paper-0346] [MC-135506] Experience should save as Integers
[Paper-0347] don't go below 0 for pickupDelay, breaks picking up items by Aikar
[Paper-0350] use a Queue for Queueing Commands by Aikar
[Paper-0352] Optimize BlockPosition helper methods by Spottedleaf
[Paper-0353] Send nearby packets from world player list not server list by Mystiflow
[Paper-0389] performance improvement for Chunk.getEntities by wea_ondara
[Paper-0539] Optimize NetworkManager Exception Handling by Andrew Steinborn
[Paper-0451] Reduce memory footprint of NBTTagCompound by spottedleaf
[Paper-0797] Use Velocity compression and cipher natives
[Paper-????] Cleanup allocated favicon ByteBuf by Shane Freeder

<--> by Heath
[Nacho-0001] Remove stream usage when counting entities
[Nacho-0002] Check if the fuel is coal first before checking others
[Nacho-0003] Disable Snooper
[Nacho-0004] Do not repeatily allocate EnumDirection
[Nacho-0005] Do not reallocate enums via values
[Nacho-0006] Use Caffeine instead of Guava for player heads
[Nacho-0007] Add timings for packets
[Nacho-0008] Upgrade Netty version to 4.1.50 and support java 14
[Nacho-0009] Remove an extra file io call within world credit bob7l
[Nacho-0010] Use jchambers' FAST UUID methods
[Nacho-0011] Optimize weather update loops
[Nacho-0012] Don't load chunks for physics
[Nacho-0013] Use less resources for collisions
[Nacho-0014] stop timings crashing the server but still print the error
[Nacho-0015] Remove the usage of BlockPosition from getCubes
[Nacho-0016] faster getHighestBlockYAt function
[Nacho-0017] tiny winy optimization for async lighting
[Nacho-0018] more tiny winy optimization to lighting
[Nacho-0019] Avoid lock every packet send
[Nacho-0020] Packet Listener Api
[Nacho-0021] Add setMaxPlayers within Bukkit.getServer() and SetMaxSlot Command
[Nacho-0022] Stop raytracing loading chunks
[Nacho-0023] Optimize EntityTracker for the chunk updater
[Nacho-0024] Do not create new BlockPosition when loading chunk
[Nacho-0025] Disable random tickSpeed being modified (Every call it had to convert String into int via a string key which is costly)
[Nacho-0026] Optimize packet Split by Velocity
[Nacho-0027] Netty IP_TOS 0x18
[Nacho-0028] only fire InventoryCloseEvent if inventory is open
[Nacho-0029] add leash api
[Nacho-0030] add a ChunkPreLoadEvent
[Nacho-0031] remove unused vars
[Nacho-0033] Faster Operator search method
[Nacho-0048] Don't allocate empty int arrays for particles
[Nacho-0049] Option to disable Enchantment table ticking

<--> by Rastrian
[Nacho-????] Async entity tracker
[Nacho-????] Async knockback and hit detection packets
[Nacho-????] Ticking fixes, tile optimization, and optional fast math
[Nacho-????] Many more config options

<--> by Sculas
[Nacho-0034] Remove Java 8 message from TacoSpigot which made it so you couldn't run Java 8 or higher
[Nacho-0035] Made it so you can switch the brand name in nacho.yml
[Nacho-0036] Add toggles for commands "reload", "version" and "plugins"
[Nacho-0037] Add toggle for "Faster Operator"
[Nacho-0039] Fixed a bug in Netty's epoll when using Windows
[Nacho-0040] Change deprecated Netty parameter in ResourceLeakDetector
[Nacho-0041] Fix block placement
[Nacho-0042] Remove Spigot Watchdog
[Nacho-0043] Fix Citizens
[Nacho-0044] Async obfuscation
[Nacho-0045] Add Player#jump and Player#sendActionBar
[Nacho-0046] Little anti-malware
[Nacho-0047] Little anti-crash
[Nacho-0050] Custom knockback
[Nacho-0051] Rework ServerConnection and MinecraftPipeline (credits to Minestom)

[Yatopia-0030] Don't save Fireworks and Arrows by tr7zw (Arrows and firework Entities, eg stuck arrows in the ground)
[Yatopia-0047] Smarter statistics ticking
[Yatopia-0050] Smol entity optimisation

[IonSpigot-0003] Explosion Improvements
[IonSpigot-0006] Fix Chunk Loading
[IonSpigot-0012] Movement Cache
[IonSpigot-0013] Implement PandaWire
[IonSpigot-0014] Faster Chunk Entity List
[IonSpigot-0020] Faster EntityTracker Collections
[IonSpigot-0026] Lag Compensated Potions
[IonSpigot-0035] Optimise Entity Collisions
[IonSpigot-0037] Fast Cannon Entity Tracker

[InsanePaper-269] Cache Chunk Coordinations
[InsanePaper-390] Heavily optimize Tuinity controlled flush patch

[Akarin-0001] Avoid double I/O operation on load player file by tsao chi
[Akarin-0010] Save Json list asynchronously

[Tuinity-????] Skip updating entity tracker without players
[Tuinity-0017] Allow controlled flushing for network manager by Spottedleaf
[Tuinity-0018] Consolidate flush calls for entity tracker packets
[Tuinity-0052] Optimise non-flush packet sending

[SportPaper-0027] Fix head rotation packet spam
[SportPaper-0043] Get blocks in Chunk API
[SportPaper-0162] Fix PlayerInteractEvent not cancelling properly
[SportPaper-0197] Optimize head rotation patch
[SportPaper-0201] Cache block break animation packet
[SportPaper-0203] Fix Teleport Invisibility
[SportPaper-0204] Optimize toLegacyData removing unneeded sanity checks

[PaperBin-????] WorldServer#everyoneDeeplySleeping optimization

[KigPaper-0039] Fix Entity and Command Block memory leaks
[KigPaper-0128] Fix Entity and Command Block memory leaks
[KigPaper-0129] Fix more EnchantmentManager leaks
[KigPaper-0138] Fix some more memory leaks
[KigPaper-0161] Fix CraftingManager memory leak
[KigPaper-0167] Add setType without lighting update API
[KigPaper-0172] NBT no-op for block place packet
[KigPaper-0191] Don't calculate initial light if not requested

[FlamePaper-0032] Dont load chunks for chests
[FlamePaper-0033] Dont check occluding hoppers
[FlamePaper-0034] Hopper item lookup optimizations
[FlamePaper-0102] Fixed chunk memory leak
[FlamePaper-0103] Limit CraftChatMessage iterations
[FlamePaper-0104] Return last slot by default
[FlamePaper-0105] Fix memory leaks by Minetick
[FlamePaper-0106] Fix sending irrelevant block updates to the client
[FlamePaper-0110] Fix NullPointerException exploits for invalid logins
[FlamePaper-0113] Remove unused code from beacons
[FlamePaper-0115] Patch Book Exploits
[FlamePaper-0117] Pearl through blocks

[MineTick-0006] Fix Occasional Client Side Unloading of Chunk 0 0
[MineTick-0011] Optimize Idle Furnaces
[MineTick-0017] Fix Insane Nether Portal Lag

[Migot-0009] Prevent Creature Spawning in Unloaded Chunks

[Sugarcane-0022] Add YAML comments

[AW-Spigot-????] Fast random
```
