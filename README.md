<h1 align="center">shiedless</h1>

<p align="center">ios reverse engineering — game engines, obfuscation, anti-cheat internals</p>

<p align="center">
  <img src="https://img.shields.io/badge/focus-iOS%20reverse%20engineering-C7192E?style=for-the-badge" alt="focus">
  <img src="https://img.shields.io/badge/arch-arm64%20%2F%20arm64e-000000?style=for-the-badge" alt="arch">
  <img src="https://img.shields.io/badge/scope-read--only%20%2F%20analysis-1f6feb?style=for-the-badge" alt="scope">
</p>

--- 

i reverse iOS game binaries and write down how the internals actually work —
the engines, the string obfuscation, the hooking, and the anti-cheat that sits on
top of all of it. everything is read-only, analysis-oriented, and stops at
understanding on purpose.

- **engines** — unreal engine 4 (`GWorld`/`GNames`/`ProcessEvent`/`FName`), unity
  il2cpp, roblox's luau vm
- **the low level** — arm64/arm64e by hand: inline hooks, W^X, instruction
  relocation, PAC, XOR string deobfuscation
- **anti-cheat** — how tencent's ACE (`anogs`) is built, and why the naive attacks
  on it crash or ban instead of working

--- 

### the notes

a connected series — each one leans on the last. start at the hub:

- [**ios-ue4-re**](https://github.com/shiedless/ios-ue4-re) — the index for the whole
  series, plus how the pieces fit together
- [**ios-binary-re-notes**](https://github.com/shiedless/ios-binary-re-notes) — the
  groundwork: decrypt, slice, load, read an iOS app at all
- [**xor-string-deobf-notes**](https://github.com/shiedless/xor-string-deobf-notes) —
  breaking XOR string obfuscation and pulling every hidden string statically
- [**arm64-ios-inline-hook-notes**](https://github.com/shiedless/arm64-ios-inline-hook-notes) —
  inline hooks by hand, and the four things that crash you
- [**ue4-ios-gworld-gnames-notes**](https://github.com/shiedless/ue4-ios-gworld-gnames-notes) —
  the two globals everything hangs off, and the anti-tamper traps around them
- [**ue4-ios-fname-notes**](https://github.com/shiedless/ue4-ios-fname-notes) — turning
  an FName index into a string by walking `FNamePool`
- [**ue4-ios-processevent-notes**](https://github.com/shiedless/ue4-ios-processevent-notes) —
  finding `ProcessEvent`, the funnel every UFunction call goes through
- [**tencent-ace-anogs-notes**](https://github.com/shiedless/tencent-ace-anogs-notes) —
  how ACE is built and why the easy attacks fail — analysis, not a bypass
- [**roblox-ios-luau-vm-notes**](https://github.com/shiedless/roblox-ios-luau-vm-notes) —
  reversing roblox's luau runtime on iOS: functions, anchors, `lua_State` layout
- [**ida-pro-guide**](https://github.com/shiedless/ida-pro-guide) — a practical guide to
  getting around a binary in IDA

### the example

- [**Reveal**](https://github.com/shiedless/Reveal) — a ~500-line skeleton ESP for UE4
  on iOS. the concrete version of every note above: read `GWorld`, walk the actors,
  project the bones, draw. read-only.

---

### what i work with

<p align="left">
  <img src="https://img.shields.io/badge/IDA%20Pro-C7192E?style=flat-square" alt="ida">
  <img src="https://img.shields.io/badge/ARM64%20asm-000000?style=flat-square" alt="arm64">
  <img src="https://img.shields.io/badge/C%2B%2B-000000?style=flat-square" alt="c++">
  <img src="https://img.shields.io/badge/Objective--C-000000?style=flat-square" alt="objc">
  <img src="https://img.shields.io/badge/Theos-000000?style=flat-square" alt="theos">
  <img src="https://img.shields.io/badge/Metal%20%2F%20ImGui-1f6feb?style=flat-square" alt="metal">
  <img src="https://img.shields.io/badge/IDAPython-1f6feb?style=flat-square" alt="idapython">
</p>

---

<p align="center"><sub>for research and defensive purposes. the repos don't ship attacks — they stop at how things work.</sub></p>
