# Bomberman Fantasy Race  Recompiled

Static recompilation of **Bomberman Fantasy Race** built on
[psxrecomp](https://github.com/mstan/psxrecomp) and
[recomp-ui](https://github.com/mstan/recomp-ui).

If you're looking for fun racing action, look no further than Bomberman Fantasy Race! Lightning fast competition, zany obstacle infested tracks and of course bombs! It's a battle-racing game like you've seen. Features: * Wacky animal racing! Race atop 10 different animals through 7 unique fantasy courses. Use special techniques , such as the triangle jump, bomb dash and catapult to get ahead of the competition! * Intense 2 player action! Compete against your friends in the split screen mode to prove who's #1! Best of all, clean out their piggy bank with the unique wagering system! * Over 15 crazy power-ups! Wield over 15 wacky weapons, including rocket bombs, power bombs, shields and power suits. Unleash long range attacks utilizing the unique throw meter!

| | |
|---|---|
| Players | 2 |
| Region | USA |
| Publisher | Atlus USA |
| Year | 1998 |

Scaffolded with the New Project Layout. See
`psxrecomp/docs/GAME_PROJECT_SETUP.md` for the full flow.

## Legal

You must own the original game. Disc images under `disc/` are gitignored and
must never be committed. Retail BIOS dumps are not redistributed; OpenBIOS is
used for Generate unless you supply your own SCPH locally.

Optional box art under `launcher_assets/img/` may come from
[libretro-thumbnails](https://github.com/libretro-thumbnails/libretro-thumbnails)
(`Named_Boxarts`); see `BOXART_SOURCE.txt` when present.

## Quick start (dev)

```bash
git submodule update --init --recursive
./psxrecomp/tools/ci/build_emitters.sh
python3 psxrecomp/psxrecomp_cli.py generate \
  --config game.toml --project-root . --disc disc/<your>.cue
cmake -S . -B build-release -G Ninja -DCMAKE_BUILD_TYPE=Release
cmake --build build-release --target psx-runtime
```

Zip prefix for CI artifacts: `bfr`.

## Symbols

Progressive map: `symbols.toml` → `python3 tools/sync_symbols.py` →
`psx_symbols.h` (`PSX_FN_*`). See `psxrecomp/docs/SYMBOLS.md`.

## Framework pins

Submodule gitlinks (`psxrecomp`, optional `recomp-ui`, nested `recomp-net`)
are authoritative. `framework_pins.txt` is an optional scaffold snapshot;
release CI logs SHAs with `record_pins.sh` but builds whatever the gitlinks
resolve to. Bump submodules deliberately — do not float on `main`/`master`
in release CI.
