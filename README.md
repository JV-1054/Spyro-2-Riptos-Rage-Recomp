# Spyro 2: Ripto's Rage! Recompiled

Static recompilation of the US PlayStation release (**SCUS-94425**) using
[PSXRecomp](https://github.com/mstan/psxrecomp).

## Prebuilt Windows executable

`artifacts/Spyro_2_Riptos_Rage_Recompiled.exe` is ready to run. Its matching
OpenBIOS and license are in `artifacts/bios/`. Place your own game image in the
repository root `isos/` folder, next to `artifacts/`.

## Build from source

```powershell
cmake -S . -B build-spyro-2 -G Ninja -DCMAKE_BUILD_TYPE=Release -DPSX_REWIND=OFF
cmake --build build-spyro-2 --target psx-runtime --parallel 12
```

The project config points to `isos/Spyro 2 - Ripto's Rage! (USA).cue`, which
references its BIN in the same directory. Disc files are local inputs and are
not included in this repository.

## Symbols

Edit `symbols.toml` and regenerate `psx_symbols.h` with:

```powershell
python tools/sync_symbols.py
```

Run `python tools/sync_symbols.py --check` to verify the generated header.

## Legal

You must own the original game. Disc images and retail BIOS dumps are local
inputs and are not redistributed. The bundled OpenBIOS is redistributable; its
license is included beside it.
