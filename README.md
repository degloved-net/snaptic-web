## snaptic web port

![snaptic](screenshot.png)

you need [gdre tools](https://github.com/GDRETools/gdsdecomp/releases/tag/v2.7.3) and [godot 4.7.1](https://github.com/godotengine/godot/releases/tag/4.7.1-stable) with the web export templates installed.

`recover.sh` asks for your recovered snaptic folder or `snaptic.pck`, gdre tools if needed, and any dlc packs. it puts the recovered project in `work/project` and applies the patches. encrypted packs also ask for a key file and decryptor script. these patches are for demo 0.82.

```bash
sh scripts/recover.sh
```

if you already have the patched source, put it in `work/project`. keep `.godot/imported` with it. building from this source doesnt need gdre tools or recovery keys

`build.sh` asks for godot. it makes `build/web` and `build/web-threads`.

```bash
sh scripts/build.sh
```

`build/web` is singlethreaded so it doesnt need headers

`build/web-threads` uses threads for better performance. it must be served with these headers on every response

```
cross-origin-opener-policy: same-origin
cross-origin-embedder-policy: require-corp
```

paths are saved in `work/paths`, which is gitignored. press enter to keep a saved path, or type `-` to clear it.

## changes

run `sh scripts/recover.sh`, make changes in `work/project`, then run

```bash
sh scripts/add-patch.sh
```

to name and add the patch
