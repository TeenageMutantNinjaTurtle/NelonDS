# NelonDS

melonDS with background music at normal speed during fast-forward (and pitch-preserving fast-forward sound effects), for desktop and the melonDS Android app.

- `melonDS/`: the emulator core and Qt frontend (upstream melonDS-emu/melonDS). The `nelonds` branch of this repo carries the change set that is also proposed upstream as `TeenageMutantNinjaTurtle/melonDS:realtime-bgm-fastforward`.
- `android/melonDS-android/`: the Android app (rafaelvcaetano/melonDS-android) with its core `melonDS-android-lib/` vendored in-tree instead of as a submodule, plus the NelonDS hooks and the Thor-tuned `nelon` build type.
- `docs/`: design notes and research.
- `tools/`: SDAT scanner used to validate the sequence classifier.

`main` is the untouched upstream code; `nelonds` is the feature. Review `nelonds` against `main`.

Build (NixOS): `nix develop --command bash -c 'cd melonDS && cmake -B build -G Ninja -DCMAKE_BUILD_TYPE=Release && ninja -C build'`; Android: `cd android && nix develop --command bash -c 'cd melonDS-android && bash ./gradlew --no-daemon :app:assembleGitHubProdNelon -Pandroid.injected.build.abi=arm64-v8a'`. That APK is tuned for the AYN Thor (ARMv8.6); add `-Pnelon.generic` for one that runs on any arm64 device. Prebuilt APKs are on the releases page.
