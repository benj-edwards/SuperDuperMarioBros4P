# Four-Player Super Mario Bros. - Super Duper Mario Bros. 4P

An experimental, unofficial fan mod of Super Mario Bros. for the NES: up to **four players
at once**, on one screen, as **Mario, Luigi, Toad or Princess Peach**. Not made or endorsed by
Nintendo.

> **Unofficial fan mod patch. No ROMs included.** This is a patch, not a game: you need your
> own copy of Super Mario Bros. for the NES, and the patch turns it into Super Duper Mario
> Bros. 4P.

Version v45, experimental: see [Status](#status) for what's rough and what has been tested.

## What it does

- **1 to 4 players at once** with an NES Four Score (or NES Satellite). Players 1 and 2
  work without one.
- **Pick a character** on the title screen with left/right on your own controller: Mario,
  Luigi, Toad or Princess Peach (no two players the same; Peach floats as in Super Mario
  Bros. 2). Each has a fire form.
- **Join at any time:** a controller without a player presses **Start** to come in; a player
  out of lives presses **Start** to continue.
- **One shared screen:** a stuck player is brought along, a player who loses a life comes
  back next to a partner (with a life from the partner who has the most, if their own are
  gone), and the level starts over only when everyone is down.
- **An item for every player** in every power-up block.
- **Bounce** off each other's heads.
- **Bubbles:** press **Select** to float safely in a bubble behind a teammate; **Select**
  again pops you out next to them.
- **Infinite lives mode** selectable on the title screen (keep pushing **Select**).
- The status bar shows every player's score and coins; the castle says THANK YOU EVERYONE!
- In the 8-4 ending, with a Peach playing, the princess in the castle is **Rosalina**.
- **1 PLAYER GAME** with Mario is the original game.

## Making the ROM

You need **Super Mario Bros. (World)** for the NES, the common dump:

| your ROM file | size | CRC32 | SHA-1 | patch |
|---|---|---|---|---|
| iNES header (most copies) | 40,976 bytes | `3337EC46` | `ea343f4e445a9050d4b4fbac2c77d0693b1d0922` | `SuperDuperMarioBros4P-v45.bps` |
| NES 2.0 header | 40,976 bytes | `393A432F` | `33d23c2f2cfa4c9efec87f7bc1321ce3ce6c89bd` | `SuperDuperMarioBros4P-v45-nes2header.bps` |

Without its 16-byte header the game data is CRC32 `D445F698`,
SHA-1 `facee9c577a5262dbe33ac4930bb0b58c8c037f7`. If your file has another header, put this one in its first 16 bytes
(with a hex editor; RomPatcher.js's Remove header option keeps your old header and won't work):
`4E 45 53 1A 02 01 01 00 00 00 00 00 00 00 00 00`.

Apply the patch with any BPS patcher:

- **RomPatcher.js** (in a web browser): <https://www.marcrobledo.com/RomPatcher.js/>. Pick
  your ROM and the `.bps` file, then *Apply patch*.
- **Floating IPS** (Windows, Linux): *Apply Patch*, the `.bps`, then your ROM.
- On the command line (Floating IPS):

  ```
  flips --apply SuperDuperMarioBros4P-v45.bps "Super Mario Bros. (World).nes" "Super Duper Mario Bros 4P.nes"
  ```

The result: 262,160 bytes, CRC32 `878E5C3D`, SHA-1 `187c0c195aff620016f76dd6f8183ae5e82cc872`.

## Playing it

- **On an NES:** an MMC3 game (mapper 4) with 256 KB of program ROM, 8 KB of CHR-RAM and
  8 KB of work RAM; it runs from flash carts such as the EverDrive N8 and the PowerPak.
  Players 3 and 4 need an **NES Four Score** or **NES Satellite** with its switch on 4
  players; on a Famicom, controllers in the expansion port are players 3 and 4.
- **In an emulator,** switch the Four Score (or multitap) on in the input settings: Mesen,
  FCEUX, Nestopia UE and RetroArch's NES cores have it. OpenEmu gives players 1 and 2
  only. MAME:

  ```
  mame nes -cart "Super Duper Mario Bros 4P.nes" -ctrl1 4score_p1p3 -ctrl2 4score_p2p4
  ```
- **Title screen:** Select steps through 1, 2, 3 and 4 PLAYER GAME, then the same with
  INFINITE LIVES; left/right on each controller picks that player's character; Start begins.
- **In play:** Select goes into a bubble or out of it; Start on a controller without a
  player joins or continues; Start on any controller pauses.

## Status

This is an experiment, and parts of it are rough:

- **Flicker:** the NES draws at most 8 sprites on a line, and a big character is 8 sprites, so
  with four players and enemies on the same lines, sprites flicker.
- **Slowdown:** four players means running the player code four times a frame. In busy scenes
  the game slows down; in testing, four players running through 11 busy levels ran at 92-100%
  of full speed.
- **Colors:** Peach has red hair and a white dress (the sprite palettes have no pink or
  yellow), and with Luigi in a water, underground or castle level, some enemies show their
  above-ground colors.
- **Testing:** in MAME, with scripted scenarios, comparisons against the original game and
  long random-play runs; two players also in OpenEmu; and four players on a real NES with an
  NES Four Score.

Please report problems on the [Issues](https://github.com/benj-edwards/SuperDuperMarioBros4P/issues)
page, with the version, the emulator or flash cart, and where in the game it happened.

## Credits

- NINTENDO, of course! Thank you for this gift to the world.
- Coding by Anthropic Claude Opus 5.5 with Claude Code
- Benj Edwards (4P Mod Design Guidance)
- Built on [doppelganger's Super Mario Bros. disassembly](https://gist.github.com/1wErt3r/4048722).
- Toad and Peach sprites adapted from Super Mario Maker 2 (Toad), Super Mario Maker (small
  Peach) and Super Mario Bros. 2 (big Peach).

Super Mario Bros. is © Nintendo. This is an unofficial fan modification, not made or
endorsed by Nintendo, and contains no ROM.
