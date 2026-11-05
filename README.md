# VoidFrequency (mod id: mcradio) - Forge 1.21.1, Java 21

Industrial radio mod: streams, repeaters, cables, jammers, number stations.

## Physics
- Signal quality at a receiver = distance falloff (fades near the edge of a radius) x depth x shielding x (1 - jam).
- Depth: full above Y=60, smooth fade below, total radio silence (white noise) at Y<=0.
- Obsidian, crying obsidian, iron blocks and raw iron blocks block signals on the line to the receiver
  (and above a receiver for the sky signal of number stations).
- Antenna Cable networks link repeaters: a repeater whose input frequency equals the output frequency of an
  active repeater on the same cable network re-emits it with no depth loss, at any depth.
- Quality < 100 %: the client attenuates audio and mixes static/crackle; 0 %: pure white noise.

## Blocks
Distributor (emitter, MP3 playlist / live mic), Computer (remote terminal for a distributor), Transmitter (+32
blocks radius per connected antenna), Repeater, Radio Receiver (32 blocks), Industrial Horn (64 blocks,
distorted), Wall Speaker (16 blocks), Antenna Cable, Signal Jammer (radius 8-96, GUI switch or redstone).

## Items
Walkie-Talkie (300 blocks, hold V), Field Radio (800 blocks, heavy), Pocket Player (needle shows quality),
Radio Scanner (overhears relayed talk), Radio Decoder (number station ciphers), Radio Tablet (map with coverage,
pulsing jammer fields), Circuit Board, Ferrite Coil, Antenna Rod, Satellite Core.

## Number stations
Frequencies 313, 666, 1947, 2077 (any receiver or pocket player). They send a Morse cipher (10 digits). Type it
into the Decoder, or let it capture from a receiver within 8 blocks; the Decoder reveals the site coordinates
(bunker or crashed satellite, generated once, with loot).

## Build
JDK 21, Gradle 8.8+ (`gradle wrapper`, then `./gradlew build`) or the GitHub Actions workflow in `.github`.
Put `.mp3` files into `config/mc_radio/tracks/` on the machine hosting the world.
`tools/generate_assets.py` regenerates textures, models, lang, recipes; `tools/merge_single_file.py` merges all
classes into `single_file/McRadio.java`.
