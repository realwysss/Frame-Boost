<p align="center"><img src="icon.png" width="128"></p>

# Frame Boost

less stutter and higher 1% lows on cpus with few cores. made for crystal and anchor pvp with motion blur, where every hitch is felt.

client side fabric mod for 1.21.11, 26.1 and 26.2. it only needs fabric api. there is nothing to set up, it works as soon as it is installed.

- **no yield (1.21.11)**: every frame the game hands its cpu core to other threads for a moment. on a 4 core cpu the core often does not come back for 10 to 15 ms, so you get a stutter. the mod skips that hand-off. newer versions do not have it anymore
- **priority**: the game runs at above normal priority, so discord, spotify, browsers and other background apps stop stealing its cpu time
- **render thread first**: the thread that draws the frames gets the highest priority inside the game, chunk building and the rest work around it

the config is in `config/frameboost.json`: `noyld` (skip the hand-off), `prio` (0 normal, 1 above normal, 2 high) and `rthr` (render thread first). high is not faster than above normal and can starve chunk loading, so above normal is the default.

## download

| jar | minecraft |
|---|---|
| `frame-boost-mc1.21.11-1.0.0.jar` | 1.21.11 |
| `frame-boost-mc26.1-1.0.0.jar` | 26.1 |
| `frame-boost-mc26.2-1.0.0.jar` | 26.2 |

on the releases page. fabric loader 0.16 or newer, fabric api.

## how much does it give

measured on an i5-6500 (4 cores) with a gtx 1650, 1.21.11, sodium and about 60 mods, motion blur on, while strafing and blowing up end crystals and respawn anchors:

| | without | with |
|---|---|---|
| 1% low fps, crystal spam | 52 | 244 |
| 1% low fps, anchors | 92 | 185 |
| 1% low fps, crystals + anchors + strafing | 90 | 201 |
| frames over 16 ms in 20 s of crystal spam | 27 | 0 |
| average fps, flying over new chunks | 341 | 518 |

the average fps goes up a bit, the big change is in the stutters. on a cpu with many cores there is less to gain.

all rights reserved. made by wysss.
