# OM-Feedstock

(WIP) Feedstock rattler build manifest for OpenModelica

# Goal

- [ ] linux-64
- [ ] osx_arm64

## Patch OpenModelica for OSX ARM64

Zlib 1.2 caused some compilation issues. Those were fixed in 1.3.1. Also OMEdit may be compiled by fetching the relevant packages on conda-forge. The following sections summarizes the changes done in the patch.

### https://github.com/Vincenz0Git/OpenModelica.git

- Branch patch/osx_arm64
- Based on tag v1.25.1
- Force Lightmode via OpenModelica/OMEdit/OMEditGUI/Info.plist

### https://github.com/Vincenz0Git/OMCompiler-3rdParty.git

- Branch patch/osx_arm64
- Based on sha256:05b2332389883ff2a6021ecdf2e13d5a00ebf286
- Update zlib to 1.3.1 from https://github.com/madler/zlib/tree/v1.3.1 (src files only, kept CMakeLists.txt)

### https://github.com/Vincenz0Git/OMSimulator.git

- Branch patch/osx_arm64
- Based on sha256:86e9635bda23ffc87a33c90bfbbc6ee7192cbb7a
- Points to forked 3rdParty

### https://github.com/Vincenz0Git/OMSimulator-3rdParty.git

- Branch patch/osx_arm64
- Based on sha256:4ee9733a8fa6de86ce6fc18d775de4efbd7aae9f
- Update zlib to 1.3.1 from https://github.com/madler/zlib/tree/v1.3.1

## TODO

Lots of branching and updating submodule commits. A more convenient way is needed

## Use

```bash
pixi add --git https://github.com/Vincenz0Git/OM-Feedstock.git --branch osx_arm64 OpenModelica
```

OMEdit GUI is installed in the Application folder, which is not in PATH. I'm not sure how to do that. Use with

```bash
.pixi/envs/default/Applications/OMEdit.app/Contents/MacOS/OMEdit 
```
