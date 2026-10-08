# NelonDS

A fork of melonDS that includes some of the PRs not merged into it yet and a novel feature that **PRESERVES ORIGINAL MUSIC SPEED DURING FAST FORWARD** while keeping sound effects sped up to not have them overlay each other.

https://github.com/user-attachments/assets/1848c92d-d9a3-48ca-9098-0e0a95b94754

This sounds quite decent in a few pokemon games which is what I am mainly interested in.

If the sped-up sound effects and cries get on your nerves there is a "Mute sound effects during fast-forward" option that keeps only the music, the way [PokeDaisy](https://github.com/lidor30/pokedaisy) does it for GBA.

How does it work? I don't know and I don't care I'm busy vibin to the music while EV training my pokemon.
ALL MY commits were generated with AI. I am AI you are AI everything is AI - AIAIAI.

Also didn't like the settings menu so did some rounds of AI for it too.

**Confirmed working:**
- Pokemon Volt White 2 Redux (vanilla BW2 and everything else based off of that should too)
- Pokemon Platinum (overworld is fine but some battles might be messed up)

---

AI SLOP

- `melonDS/`: the emulator core and Qt frontend (upstream melonDS-emu/melonDS). The `nelonds` branch of this repo carries the change set that is also proposed upstream as `TeenageMutantNinjaTurtle/melonDS:realtime-bgm-fastforward`.
- `android/melonDS-android/`: the Android app (rafaelvcaetano/melonDS-android) with its core `melonDS-android-lib/` vendored in-tree instead of as a submodule, plus the NelonDS hooks and the Thor-tuned `nelon` build type.
- `docs/`: design notes and research.
- `tools/`: SDAT scanner used to validate the sequence classifier.

`main` is the untouched upstream code; `nelonds` is the feature. Review `nelonds` against `main`.

Build (NixOS): `nix develop --command bash -c 'cd melonDS && cmake -B build -G Ninja -DCMAKE_BUILD_TYPE=Release && ninja -C build'`; Android: `cd android && nix develop --command bash -c 'cd melonDS-android && bash ./gradlew --no-daemon :app:assembleGitHubProdNelon -Pandroid.injected.build.abi=arm64-v8a'`. That APK is tuned for the AYN Thor (ARMv8.6); add `-Pnelon.generic` for one that runs on any arm64 device. Prebuilt APKs are on the releases page.
