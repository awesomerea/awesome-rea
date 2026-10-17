# Awesome REA [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated list of resources for REA (Reverse Engineer Anything), the open-source MCP server and CLI that lets AI coding agents reverse engineer native binaries, Electron and JavaScript apps, .NET assemblies, Android APKs, firmware, network captures, and live app behavior.

REA connects agents such as Claude Code, Codex, Cursor, and Gemini CLI to reverse-engineering tools like Ghidra, Hopper, IDA, JADX, and Frida through the Model Context Protocol (MCP). Analysis runs on your own machine, and every finding comes with the evidence and limitations behind it.

```bash
npx rea-agents@latest setup
```

This list is community-maintained and not affiliated with the REA project. Contributions welcome, see [CONTRIBUTING.md](CONTRIBUTING.md).

> **Install only from the official sources.** Trojanized copies of REA have circulated under similar names. The real project is `morluto/rea` on GitHub and `rea-agents` on npm.

> **Legal note.** REA is for lawful research and analysis of software you own or are authorized to examine. Commercial engines (IDA Pro, Hopper, JEB) require your own license.

## Contents

- [Official](#official)
- [Getting Started](#getting-started)
- [Guides](#guides)
- [Showcases and Case Studies](#showcases-and-case-studies)
- [Built with REA](#built-with-rea)
  - [Games and Reconstructions](#games-and-reconstructions)
  - [Desktop Apps and Tools](#desktop-apps-and-tools)
  - [Creative and Office Suites](#creative-and-office-suites)
  - [Hardware, Drivers, and Protocols](#hardware-drivers-and-protocols)
  - [Analyses, Audits, and Evaluations](#analyses-audits-and-evaluations)
- [Documentation by Target](#documentation-by-target)
  - [Native Binaries](#native-binaries)
  - [JavaScript, Electron, and Web](#javascript-electron-and-web)
  - [Mobile and Managed Code](#mobile-and-managed-code)
  - [Firmware, Hardware, and Runtime](#firmware-hardware-and-runtime)
- [Integrations and Agent Setup](#integrations-and-agent-setup)
  - [Tools Built on REA](#tools-built-on-rea)
  - [Packaging](#packaging)
  - [Agent Adapters](#agent-adapters)
- [Architecture and Internals](#architecture-and-internals)
- [Articles and Tutorials](#articles-and-tutorials)
- [Reviews and Critical Takes](#reviews-and-critical-takes)
- [Community](#community)
- [Translations](#translations)
- [Case Trackers and Other Lists](#case-trackers-and-other-lists)
- [Related Tools](#related-tools)
- [Related Awesome Lists](#related-awesome-lists)

## Official

- [morluto/rea](https://github.com/morluto/rea) - Source repository. MIT licensed, written in TypeScript.
- [rea.tools](https://rea.tools/) - Official website with guides, showcases, blog, and FAQ in 20 languages.
- [rea-agents on npm](https://www.npmjs.com/package/rea-agents) - The published package behind `npx rea-agents` and the `rea` CLI.
- [Releases](https://github.com/morluto/rea/releases) - Versioned release notes.
- [Changelog](https://github.com/morluto/rea/blob/main/CHANGELOG.md) - Full change history.
- [Roadmap](https://github.com/morluto/rea/blob/main/docs/roadmap.md) - Planned work and direction.
- [FAQ](https://rea.tools/faq/) - Common questions, including what data reaches your model provider.

## Getting Started

- [Get started](https://rea.tools/get-started/) - Step-by-step setup for Windows, macOS, and Linux, including the curl installer.
- [Installation docs](https://github.com/morluto/rea/blob/main/docs/installation.md) - Node.js requirements, engine detection, and per-target prerequisites.
- [Your first investigation](https://rea.tools/first-investigation/) - A guided walk through a small Notes app, end to end.
- [Dinosaur speed lab](https://rea.tools/examples/dino-lab/) - Interactive example: find what controls the speed of the Chrome dinosaur game.
- [CLI reference](https://github.com/morluto/rea/blob/main/docs/cli.md) - Every `rea` command, including `rea doctor`, `rea update`, and the analysis subcommands.
- [New to RE with AI? What to reverse engineer first, and how to ask](https://github.com/morluto/rea/discussions/2412) - Community beginner ladder from a program you wrote yourself up to malware in a VM.

## Guides

- [Recover a sound-pan calculation](https://rea.tools/guides/native/) - Native binaries. Inspect instructions, follow a caller, read constants, and check the recovered C.
- [Follow a CSV export](https://rea.tools/guides/javascript/) - JavaScript and Electron. Trace one feature across renderer, preload, IPC, and main process.
- [Observe a click](https://rea.tools/guides/browser/) - Browser behavior. Capture a request and find the code that turns the response into a download.
- [Native investigation](https://github.com/morluto/rea/blob/main/docs/native-investigation.md) - The full native workflow the agent follows.
- [JavaScript application workflows](https://github.com/morluto/rea/blob/main/docs/javascript-application-workflows.md) - Module graphs, artifact reconstruction, and runtime reconciliation.

## Showcases and Case Studies

- [How an authenticator generates a login code](https://rea.tools/showcase/aegis/) - Android APK. Finds the six-digit TOTP calculation in Aegis and explains the 30-second rotation.
- [Solve a CTF flag checker](https://rea.tools/showcase/ctf/) - Native binary. Turns a DownUnderCTF checker into equations and verifies the flag.
- [DX-Ball's sound-pan calculation](https://rea.tools/showcase/dx-ball/) - 1996 Windows game. Recovers a C function that passes 3,205 original x86 test cases.
- [How Notion copies text and HTML](https://rea.tools/showcase/notion/) - Electron. Traces the clipboard bridge from renderer through preload and IPC to the main process.
- [How TH04 aims a ring of bullets](https://rea.tools/showcase/th04/) - PC-98 DOS executable. Matches a 16-bit angle helper to readable C++ and compares against historical compiler output.
- [All showcases](https://rea.tools/showcase/) - Index with evidence pages for each case.

## Built with REA

Projects whose README or author write-up credits REA for the investigation. Listing is not an endorsement, and most are early previews. Check each project's own notes on what was verified.

### Games and Reconstructions

- [dx-ball](https://github.com/N0zoM1z0/dx-ball) - The 1996 Windows game, version 1.07, reconstructed in C/C++ with REA and Codex, backed by original-x86 differential tests and byte-exact MSVC oracles.
- [th04](https://github.com/N0zoM1z0/th04) - Source reconstruction of Touhou 4 (PC-98). The bullet-ring maths is the subject of the official TH04 showcase.
- [desktop-games-nostalgia](https://github.com/ucodia/desktop-games-nostalgia) - The 2000 Gemtree desktop-smashing toy ported to macOS and the browser with REA and Ghidra.
- [rea-ski-or-die-reconstruction](https://github.com/tuunanet/rea-ski-or-die-reconstruction) - The Snowball War minigame from Ski or Die (1990, MS-DOS) rebuilt in Rust and SDL2.
- [OpenBattlefield2](https://github.com/Moxnatiy/OpenBattlefield2) - Clean-room C++20 reimplementation of the Refractor 2 engine. Uses REA for function-level evidence, credited in its agent instructions rather than the README.
- [lezac-decompilation](https://github.com/Hubert-Rybak/lezac-decompilation) - Evidence-backed decompilation of the DOS game Larax and Zaco with REA and Ghidra.
- [fnv-rea](https://github.com/Matheus2250/fnv-rea) - How Fallout: New Vegas persists object positions across cells, traced with REA and Ghidra, then reimplemented clean-room.
- [neon-rooftops](https://github.com/kingabzpro/neon-rooftops) - Original pixel-art endless runner built after mapping the Chrome dinosaur engine statically with REA.
- [rea-dino-reverse-engineering](https://github.com/zhxunzh84/rea-dino-reverse-engineering) - Chrome T-Rex Runner analysed with REA and Codex, reimplemented with regression tests.
- [samp-client-re](https://github.com/NathanKanaeru/samp-client-re) - Buildable clean-room reimplementation of the SA-MP 0.3.DL client, with the architecture map from REA and Ghidra.
- [ultima6](https://github.com/2lab-ai/ultima6) - Ultima VI for the Amiga reverse-engineered with REA and Ghidra and ported to Rust and WebAssembly. Engine only, bring your own game files.
- [rustfighter](https://github.com/Mynd-labs/rustfighter) - Street Fighter 2 in Rust, with the analysis done in REA.
- [naruto-uzumaki-chronicles-2](https://github.com/byescaleira/naruto-uzumaki-chronicles-2) - Portuguese. The PS2 game reimplemented in Swift and Metal for Apple platforms, with REA run on the Emotion Engine executable.
- [UltraSunnyMoon](https://github.com/tylergraydev/UltraSunnyMoon) - Pokémon Ultra Sun decompilation with REA-led analysis, reproducible builds, and public verification tracking.
- [LStarwars-Decompile](https://github.com/nmdurkee/LStarwars-Decompile) - Lego Star Wars: The Complete Saga decompilation, with REA as the initial analysis toolkit.
- [card-games-to-go-revived](https://github.com/Ozdotdotdot/card-games-to-go-revived) - The 2002 Pocket PC card games revived in the browser after decompiling the Windows CE ARM executables with REA.
- [minesweeper-linux-recomp](https://github.com/NexonSU/minesweeper-linux-recomp) - Windows XP Minesweeper decompiled and ported to Linux by a locally running model through the REA MCP server.
- [mystery-sdl](https://github.com/viny182/mystery-sdl) - SDL2 Linux port of the Microsoft Plus! Mystery screen saver, binaries analysed with REA. Needs your own copy.
- [re-twist-tt2](https://github.com/jcchikikomori/re-twist-tt2) - Reconstruction of Text Twist 2 (2008) with REA and Ghidra, to play it with an updated dictionary.
- [mikropuhe](https://github.com/WokenBits/mikropuhe) - A 1990 Finnish MS-DOS speech synthesiser running again on modern systems, with REA as the way into the binary.
- [ai-rebuilds](https://github.com/a-barzanti/ai-rebuilds) - Abandoned games rebuilt for the open web from REA-derived behavior specs.
- [creative-destruction-reborn](https://github.com/crasyimperior/creative-destruction-reborn) - French and English. Local server and client mod to play Creative Destruction offline, a fan preservation project with no game files.
- [cuphead-apple-port-tools](https://github.com/IgnacioPardo/cuphead-apple-port-tools) - Experimental recovery tooling and native Apple helpers for Cuphead, with REA used in the analysis.
### Desktop Apps and Tools

- [ledger-reborn](https://github.com/lxistired/ledger-reborn) - Desktop accounting app for Mac and Windows, independently implemented after a REA and Ghidra study of QuickBooks Desktop. Posted as [Project #000001](https://github.com/morluto/rea/discussions/2198).
- [tax-reborn](https://github.com/lxistired/tax-reborn) - Offline US personal tax preparation for desktop and Android, with REA tracing the original calculation resources. Posted as [Project #000002](https://github.com/morluto/rea/discussions/3110).
- [rea-capcut](https://github.com/Xiangyu-CAS/rea-capcut) - ReaCut, an open-source video editor built in Electron after REA-assisted research into CapCut's local behavior and project format.
- [paper-rs](https://github.com/michaelshimeles/paper-rs) - Native Rust infinite-canvas design app, clean-room reimplementation studied with REA and Claude Code.
- [rec-rs](https://github.com/michaelshimeles/rec-rs) - macOS screen and camera recorder in Rust, an OBS alternative studied with REA.
- [terminal-rs](https://github.com/michaelshimeles/terminal-rs) - Bloomberg-style trading terminal in Rust, with chart behavior studied through REA's website mode.
- [hexgrab](https://github.com/iammukeshm/hexgrab) - Tiny .NET 10 color picker for Windows, built from a REA study of the PowerToys Color Picker.
- [AdamTerm](https://github.com/AdamLinCodes/AdamTerm) - Minimal macOS terminal built by pointing REA at Ghostty.
- [vitals-clone](https://github.com/Samin12/vitals-clone) - SwiftUI menu-bar activity monitor rebuilt from a static REA analysis of the shipped Vitals app.
- [rea-codex](https://github.com/victcn/rea-codex) - Static and binary source reconstruction of the OpenAI Codex CLI via REA.
- [wispr-flow-rea-teardown](https://github.com/az9713/wispr-flow-rea-teardown) - Static teardown of Wispr Flow's voice pipeline plus a 64-line local rebuild with test receipts.
- [ananasar](https://github.com/andy778/ananasar) - Rust port of the public-domain Ananas Modbus/TCP tool, built with REA.
- [open-obsidian](https://github.com/JingHao-Leon/open-obsidian) - Clean-room local-first Markdown vault with wikilinks, backlinks, graph view, and a plugin API, reverse-engineered with REA.
- [rea-claude-code](https://github.com/victcn/rea-claude-code) - Static and runtime source reconstruction of Claude Code via REA.
- [open-claude-ui](https://github.com/Caho1/open-claude-ui) - Chinese. High-fidelity recreation of the Claude design system and interaction behavior from a REA teardown.
- [glide](https://github.com/michaelshimeles/glide) - Open-source Screen Studio in Rust, behavior reverse-engineered with REA and Claude.
- [RENotepad](https://github.com/nikkoxgonzales/RENotepad) - Windows 10 Notepad rebuilt in Rust with the Windows 11 look, analysed with Ghidra through REA.
- [DiskLens](https://github.com/KarlssonChristoffer/DiskLens) - WinDirStat-style disk usage analyzer for Windows 11 in Rust, Tauri, and Svelte, started as a test of REA.
- [DiskDude](https://github.com/heictojpgpics/DiskDude) - macOS disk space analyzer with Swift source recovered via REA's composed Ghidra workflow.
- [review](https://github.com/KingDomino/review) - Preview-style PDF and image viewer and editor for Linux in Rust, with the Preview analysis done in REA.
- [lino](https://github.com/yruichen/lino) - File-first Markdown editor with a native macOS shell and Rust core, credits REA's application analysis tools.
- [diodon-clone](https://github.com/h-gj/diodon-clone) - Chinese. The Diodon GTK clipboard manager replicated in Python from REA and Ghidra evidence.
- [mucrab](https://github.com/soyrochus/mucrab) - Rust port of the Java file manager muCommander, recovered with REA and a JVM decompiler.
- [dji-reframe-linux](https://github.com/dhomoney/dji-reframe-linux) - Linux port of DJI's Reframe OFX plugin for DaVinci Resolve, reconstructed from the Windows binary with REA and Ghidra.
- [60FPSVideo](https://github.com/wasim-osman/60FPSVideo) - Native macOS frame-interpolation app for Apple Silicon, with REA as the reverse-engineering toolchain.
- [WH3SaveEditor](https://github.com/davehornik/WH3SaveEditor) - Total War: Warhammer 3 save editor, formats recovered with REA on top of Ghidra.
### Creative and Office Suites

The ArtCraft "Crafting Apps" by storytold: Adobe, Microsoft Office, and other professional tools reimplemented in pure Rust with Claude, launched in the same week REA went viral. Note that the author describes them as clean-room work without reverse engineering and the repositories do not credit REA. All are early alpha, dual-licensed MIT or Apache-2.0, and available from [getartcraft.com](https://getartcraft.com).

Adobe alternatives:

- [PhotoCraft](https://github.com/storytold/photocraft) - Photo editor in the style of Photoshop. The flagship, and the most-starred of the suite.
- [VectorCraft](https://github.com/storytold/vectorcraft) - Vector art tool in the style of Illustrator.
- [FilmCraft](https://github.com/storytold/filmcraft) - Nonlinear video editor in the style of Premiere Pro.
- [LightCraft](https://github.com/storytold/lightcraft) - Non-destructive photo editor in the style of Lightroom.
- [EffectCraft](https://github.com/storytold/effectcraft) - Motion graphics and compositing in the style of After Effects.
- [DesignCraft](https://github.com/storytold/designcraft) - Page and layout design in the style of InDesign.
- [PdfCraft](https://github.com/storytold/pdfcraft) - PDF reader and editor in the style of Acrobat.
- [AniCraft](https://github.com/storytold/AniCraft) - 2D animation editor in the style of Animate.

Microsoft Office alternatives:

- [WordCraft](https://github.com/storytold/wordcraft) - Clean-room reimplementation of Word.
- [GridCraft](https://github.com/storytold/gridcraft) - Clean-room spreadsheet in the style of Excel.
- [DeckCraft](https://github.com/storytold/deckcraft) - Presentations and slide shows in the style of PowerPoint.

Other professional tools:

- [FigCraft](https://github.com/storytold/figcraft) - Interface design and prototyping in the style of Figma.
- [CADCraft](https://github.com/storytold/cadcraft) - Computer-aided design and drafting in the style of AutoCAD.
- [SoundCraft](https://github.com/storytold/soundcraft) - Digital audio workstation in the style of Avid Pro Tools.
- [ArtCraft](https://github.com/storytold/artcraft) - The crafting engine the suite is built around, and the project's main repository.
- [Craft Launcher](https://github.com/storytold/craft-launcher) - Installs and updates all of the apps above.

### Hardware, Drivers, and Protocols

- [picoprint](https://github.com/bigtower17/picoprint) - Makes the LX-D02 Bluetooth thermal printer a regular Windows printer after recovering the app's CRC16 handshake from a Hermes bundle. Write-up in [discussion #4152](https://github.com/morluto/rea/discussions/4152).
- [VSL-DSP](https://github.com/grisuno/VSL-DSP) - Linux kernel module for the PreSonus AudioBox VSL family, with some vendor-library findings from REA.
- [vd-streamer-linux](https://github.com/cudanexus/vd-streamer-linux) - Unofficial Linux port of the Virtual Desktop Streamer for Quest, Pico, and Vive headsets, built with Claude Code and REA.
- [remote-me](https://github.com/jxgedouard/remote-me) - Web remote for Apple TV and LG TVs, built by reverse-engineering Apple's own remote with REA and Ghidra.
- [samsung-tv-remote](https://github.com/Duyfrom/samsung-tv-remote) - macOS menu bar remote for a 2016 Samsung Tizen TV, protocol recovered from Samsung's .NET assemblies with REA.
- [MiTV-Remote](https://github.com/EndLess728/MiTV-Remote) - Xiaomi TV remote for macOS, Android, and iOS, with the undocumented MiLink protocol reverse-engineered with REA.
- [soundconnect-desktop](https://github.com/B-Howell/soundconnect-desktop) - Unofficial Windows controller for Sony Bluetooth headphones, built as a test drive of REA.
- [yamaha-rs-232c](https://github.com/zqushair/yamaha-rs-232c) - Serial control of a Yamaha RX-V2500 receiver with MQTT and Home Assistant discovery, frames recovered from the dealer application with REA.
- [ha-govee-ring](https://github.com/raulpetruta/ha-govee-ring) - Home Assistant control of a Govee ceiling light's ring separately from its panel, fully local, protocol found with REA.
- [iledcolor-backpack](https://github.com/PeterkoCZ91/iledcolor-backpack) - Open-source Android app and BLE protocol documentation for iledcolor LED backpacks.
- [Gamemax-linux-apps](https://github.com/oxpoe/Gamemax-linux-apps) - Linux bridge and tray app for the LCD panel of GAMEMAX AIO coolers, from REA managed-code analysis and Ghidra.
- [TVSRideCompanion](https://github.com/athulkrishna2015/TVSRideCompanion) - Companion app for TVS SmartXonnect motorcycle clusters that mirrors navigation over Bluetooth LE with no account or server.
### Analyses, Audits, and Evaluations

- [OpenBSD_netcat_REA](https://github.com/NullLabTests/OpenBSD_netcat_REA) - Static analysis of the netcat-openbsd binary with REA and Ghidra, documented end to end.
- [REA-demo](https://github.com/az9713/REA-demo) - REA reverse-engineering its own installed package, with the receipt.
- [Outside-in leak check of a Next.js and Stripe app](https://github.com/morluto/rea/discussions/1406) - Black-box audit of a production portal with REA's browser tools. Found one real HTTPS issue.
- [A stripped bzip2 build on Linux](https://github.com/morluto/rea/discussions/2254) - What REA returned on a stripped binary, checked against the build and the docs.
- [rea-groundtruth](https://github.com/UnknownHacker1/rea-groundtruth) - Compares what REA reports against the actual code, with one-command repros for its blind spots.
- [Benchmarks: REA on Linux](https://github.com/morluto/rea/discussions/1998) - Startup times on Node 22, 24, and 26 plus five local models.
- [First speed results: kuna, rsleigh, and Ghidra](https://github.com/morluto/rea/discussions/3858) - Engine comparison on the same three files.
- [anti-rea](https://github.com/848gaming/anti-rea) - Defensive toolkit that hardens Flutter, .NET, and Electron builds against REA-style analysis.
- [x6831-analysis](https://github.com/jhonneiber/x6831-analysis) - Spanish. Static analysis of the Infinix X6831 prebuilt arm64 kernel with REA and headless Ghidra in GitHub Actions.
- [papertrade-contract-research](https://github.com/aa-matthew/papertrade-contract-research) - REA reconstructions of deployed EVM contracts, with recovered Solidity and local verification.
- [rea-research-lab](https://github.com/Ginderlax/rea-research-lab) - Ten reproducible reverse-engineering studies with REA: evidence, independent reconstructions, and differential tests.
- [rea-platform-validation-lab](https://github.com/danielobede20-pixel/rea-platform-validation-lab) - Isolated Linux validation lab for REA and Ghidra on synthetic open-source targets.
- [die-a-rea](https://github.com/danihelenterprises/die-a-rea) - Decompiler interference engine that tests defenses against REA and GhidraMCP.
- [herculesdefierro](https://github.com/Javilonte/herculesdefierro) - Reverse-engineering notes and Ghidra-decompiled analysis of the Hercules mainframe emulator, produced with REA 6.5.0.
- [rea-video-codec-study](https://github.com/qinyishcn/rea-video-codec-study) - Chinese. Which encoding parameters can be recovered from a commercial video client, checked against native transcoding experiments.
- [rea-benchmarks](https://github.com/Adkid-Zephyr/rea-benchmarks) - Independent, reproducible visual reconstruction benchmarks with REA across coding models, with audits and interactive comparisons.
- [leanrea](https://github.com/aicodeking/leanrea) - One 8 KB skill file that replaces REA with plain CLI tools and no MCP, benchmarked as faster and cheaper. A critical alternative worth reading.
- [reaproof](https://github.com/Junhan2/reaproof) - Rates how exposed a shipped app is to REA-style agents and closes what can be closed.
## Documentation by Target

### Native Binaries

- [Ghidra provider](https://github.com/morluto/rea/blob/main/docs/ghidra-provider.md) - Free engine path. Needs a JDK 21 or newer.
- [IDA provider](https://github.com/morluto/rea/blob/main/docs/ida-provider.md) - Using an existing IDA Pro install.
- [Go binaries](https://github.com/morluto/rea/blob/main/docs/go-binaries.md) - Symbol recovery and runtime structures in Go executables.
- [Rust binaries](https://github.com/morluto/rea/blob/main/docs/rust-binaries.md) - Working with Rust mangling and panics.
- [Raw binary](https://github.com/morluto/rea/blob/main/docs/raw-binary.md) - Headerless images and unknown formats.
- [WebAssembly artifacts](https://github.com/morluto/rea/blob/main/docs/wasm-artifacts.md) - Inspecting WebAssembly modules.
- [EVM bytecode](https://github.com/morluto/rea/blob/main/docs/evm-bytecode.md) - Smart contract bytecode analysis.
- [Recorded crashes](https://github.com/morluto/rea/blob/main/docs/recorded-crashes.md) - Reading Linux crash recordings.
- [Binary diagnostics](https://github.com/morluto/rea/blob/main/docs/binary-diagnostics.md) - Offline ELF layout and format checks.
- Ghidra platform notes: [DOS](https://github.com/morluto/rea/blob/main/docs/ghidra-dos.md), [MIPS](https://github.com/morluto/rea/blob/main/docs/ghidra-mips.md), [PowerPC](https://github.com/morluto/rea/blob/main/docs/ghidra-ppc.md), [PSP](https://github.com/morluto/rea/blob/main/docs/ghidra-psp.md), [RISC-V](https://github.com/morluto/rea/blob/main/docs/ghidra-riscv.md), [.NET NativeAOT](https://github.com/morluto/rea/blob/main/docs/ghidra-nativeaot.md), [Windows](https://github.com/morluto/rea/blob/main/docs/windows-ghidra-p0.md).

### JavaScript, Electron, and Web

- [JavaScript application graph](https://github.com/morluto/rea/blob/main/docs/javascript-application-graph.md) - Modules, imports, and Electron boundaries as JSON.
- [JavaScript recovery](https://github.com/morluto/rea/blob/main/docs/javascript-recovery.md) - Deminifying and recovering readable source.
- [JavaScript artifact reconstruction](https://github.com/morluto/rea/blob/main/docs/javascript-artifact-reconstruction.md) - Rebuilding bundles into modules.
- [JavaScript runtime observation](https://github.com/morluto/rea/blob/main/docs/javascript-runtime-observation.md) - Watching code execute in a Chrome-family browser.
- [Electron observation](https://github.com/morluto/rea/blob/main/docs/electron-observation.md) - Attaching to packaged Electron apps.
- [Electron fuses](https://github.com/morluto/rea/blob/main/docs/electron-fuses.md) - What Electron fuses allow and block.
- [Browser observation](https://github.com/morluto/rea/blob/main/docs/browser-observation.md) - Capturing live website behavior.
- [Website module trace](https://github.com/morluto/rea/blob/main/docs/website-module-trace.md) - Following a feature through a site's scripts.
- [Website script export](https://github.com/morluto/rea/blob/main/docs/website-script-export.md) - Pulling scripts out of a live page.
- [Web network captures](https://github.com/morluto/rea/blob/main/docs/web-network-captures.md) - HAR and SAZ files.
- [Packet captures](https://github.com/morluto/rea/blob/main/docs/packet-captures.md) and [PCAP analysis](https://github.com/morluto/rea/blob/main/docs/pcap-analysis.md) - Network-level evidence.

### Mobile and Managed Code

- [Android analysis](https://github.com/morluto/rea/blob/main/docs/android-analysis.md) - APKs via JADX. Needs a JDK.
- [ADB device analysis](https://github.com/morluto/rea/blob/main/docs/adb-device-analysis.md) - Working against a connected Android device.
- [Apktool resource analysis](https://github.com/morluto/rea/blob/main/docs/apktool-resource-analysis.md) - Resources, manifests, and layouts.
- [Apple application analysis](https://github.com/morluto/rea/blob/main/docs/apple-application-analysis.md) - macOS and iOS app bundles.
- [Flutter analysis](https://github.com/morluto/rea/blob/main/docs/flutter-analysis.md) - Dart snapshots in Flutter apps.
- [HarmonyOS analysis](https://github.com/morluto/rea/blob/main/docs/harmony-analysis.md) - HarmonyOS packages.
- [Managed code analysis](https://github.com/morluto/rea/blob/main/docs/managed-code-analysis.md) - .NET assemblies without a native engine.
- [JEB analysis](https://github.com/morluto/rea/blob/main/docs/jeb-analysis.md) - Using existing JEB projects.

### Firmware, Hardware, and Runtime

- [Firmware analysis](https://github.com/morluto/rea/blob/main/docs/firmware-analysis.md) - Embedded images.
- [Signal recordings](https://github.com/morluto/rea/blob/main/docs/signal-recordings.md) - Logic-analyzer captures.
- [Process capture](https://github.com/morluto/rea/blob/main/docs/process-capture.md) - Observing a running process.
- [Frida instrumentation](https://github.com/morluto/rea/blob/main/docs/frida-instrumentation.md) - Dynamic hooks with Frida.
- [SQLite databases](https://github.com/morluto/rea/blob/main/docs/sqlite-databases.md) - Inspecting app data stores.

## Integrations and Agent Setup

- [Client configuration](https://github.com/morluto/rea/blob/main/docs/client-configuration.md) - Manual MCP registration for any agent with local MCP support.
- [Client verification](https://github.com/morluto/rea/blob/main/docs/client-verification.md) - Confirm your agent sees the REA tools.
- [MCP contracts](https://github.com/morluto/rea/blob/main/docs/mcp-contracts.md) - Tool inputs, outputs, and guarantees.
- [MCP prompts](https://github.com/morluto/rea/blob/main/docs/mcp-prompts.md) - Prompt templates REA exposes to agents.
- [morluto/rea on skills.sh](https://www.skills.sh/morluto/rea) - Install the bundled skills with `npx skills add morluto/rea`.
- [REA as a DSH plugin](https://www.dshplugin.store/plugin/morluto/rea) - Plugin store listing.
- [Reverse Engineer Anything skill on TypingMind](https://www.typingmind.com/skills/morluto-reverse-engineer-anything) - Skill packaging for other LLM frontends.
- [A 32K local model drove REA over MCP](https://github.com/morluto/rea/discussions/3098) - Running REA with a small local model, 3 of 3 tasks with 10 tools.

### Tools Built on REA

- [eleven](https://github.com/Zfinix/eleven) - Agent-first reverse engineering for macOS, Windows, and Linux. Any ACP agent reads, renames, and patches binaries, with native code read by Ghidra through REA.
- [reverseport](https://github.com/laaielichter/reverseport) - CLI and MCP server that takes apart apps and games and ports them to Godot, Unity, Unreal, or three.js.
- [era-agent](https://github.com/dav1dngy/era-agent) - Evidence-driven reverse-engineering agent built on REA with a controlled Improvement Lab.
- [ReaFuse](https://github.com/sickpyramid/ReaFuse) - Dissects two JS/TS projects with REA and fuses their capabilities into a new verified one.
- [REA-Reconstruction-Companion](https://github.com/ShadowSwaps/REA-Reconstruction-Companion) - Model-independent agent skill for evidence-based software reconstruction with REA.
- [rea-casebook](https://github.com/pablodiazjorge/rea-casebook) - Claude Code mod that keeps a live casebook of the evidence REA gives the agent, with Markdown export.
- [CleanRoom](https://github.com/Sage-is/CleanRoom) - Python reimplementation of REA as a local MCP server and CLI with pageable evidence. AGPL-3.0.
- [appbeam](https://github.com/alanhu0513-oss/appbeam) - Reverse-engineers an app with REA, rewrites it as Expo components with Gemini, and deploys it live to Vercel.
- [Unvibe](https://github.com/TamTunnel/Unvibe) - Move, rebuild, or reverse engineer vibe-coded apps from a URL, with REA as the bounded investigation step.
- [tracebrief](https://github.com/dany331x/tracebrief) - Turns a REA evidence bundle into an evidence-first reverse-engineering report.
- [rea-ui](https://github.com/wyfirstname/rea-ui) - Graphical front-end for the REA CLI. Windows portable build with 153 schema-generated commands, no Node install needed.
- [rea-jev](https://github.com/juan-viox/rea-jev) - Claude Code plugin that pairs REA with a verification workflow.
- [rea-workbench](https://github.com/ycgiio/rea-workbench) - Local reverse-engineering workspace with REA, OmniRoute, and OpenCode for managing investigations, evidence, and reports.
- [reverse-engineer-everything](https://github.com/gryszzz/reverse-engineer-everything) - Local workbench for evidence-backed investigation and bounded verification, built on the REA engine.
- [reverso](https://github.com/ReversoAgent/reverso) - Agent that investigates a target with REA or through screenshots and interactions, then rebuilds it.
- [rea-comfyui-bridge](https://github.com/chengyansen-ai/rea-comfyui-bridge) - REA investigations of creative apps paired with read-only ComfyUI workflow audits.
- [rea-rs](https://github.com/jlien/rea-rs) - Clean-room Rust MCP toolkit for inspecting Mach-O, ELF, PE, and LE binaries.
- [REA-Argonaut](https://github.com/PNWcoastie/REA-Argonaut) - Superset of REA with verified Rust reconstruction kits for Gemini and Google Antigravity.
- [proofwork](https://github.com/Devaretanmay/proofwork) - Evidence-ledger approach to software synthesis that connects to REA for binary targets. Formerly rea-investigate.
- [ai-reverse-engineering-agent-skill](https://github.com/dairymatrix-collab/ai-reverse-engineering-agent-skill) - Portable, evidence-first agent skill for lawful reverse engineering with REA CLI and MCP workflows.
- [binsight](https://github.com/Alessiolucini/binsight) - Offline, cross-platform static reverse-engineering intelligence for agents and the CLI, built on REA.
- [traceforge](https://github.com/Alps-is-Core/traceforge) - Local workbench with an evidence ledger, version diffs, dependency maps, and offline reports over REA's pinned engine.
- [fea](https://github.com/surajse/fea) - Forward Engineer Anything. Consumes REA's analysis as the reader and runs the verified reimplementation loop.
- [tracea](https://github.com/Hisernberg/tracea) - Dynamic reverse engineering for agents: hooks, syscalls, memory, and network as evidence records. The dynamic half to REA's static half.
- [REA-For-Web](https://github.com/sulaimwn/REA-For-Web) - Web service that explores uploaded apps, visualises their architecture, and answers questions about how they work.
- [rea-workbench (NIU-123370)](https://github.com/NIU-123370/rea-workbench) - Local single-user software-archaeology workbench on REA 6.4.0.
- [reverse-engineering-workbench](https://github.com/bingxijun/reverse-engineering-workbench) - Windows and .NET workbench plus Codex skill with traceable evidence and verified resume.
- [rea-light-mcp](https://github.com/funkeyyou/rea-light-mcp) - Chinese. Lightweight stateful REA MCP for Codex that loads four tools at startup and fetches schemas on demand.
- [rea-python](https://github.com/kandada/rea-python) - Unofficial Python port of REA for Python-based agent stacks.
- [rea-addons](https://github.com/majbal87/rea-addons) - PlayStation 1 reverse-engineering skill and Apple Silicon notes for REA.
- [coop-anything](https://github.com/cranebeaker/coop-anything) - MCP server and playbook for adding online or split-screen co-op to single-player games, paired with REA for the analysis.
- [CalcoWeb](https://github.com/Edwin1719/CalcoWeb) - Spanish. Captures a web page with REA and rebuilds it over the original with editable palette and text layers.
- [crashlens](https://github.com/mingleiw/crashlens) - Finds why a program crashed when the logs say nothing, walking an REA-connected agent from a core dump to a cause.
- [stack-xray](https://github.com/jatingargiitk/stack-xray) - Diagram of how a startup's product is built, including which AI providers it really uses, with traffic captured through REA.
- [rev-agent](https://github.com/sami-mag07/rev-agent) - German. Autonomous reverse-engineering agent for Claude Code using radare2 natively and REA for everything else.
### Packaging

- [rea-agent-docker](https://github.com/alexmi256/rea-agent-docker) - One Docker image per analysis engine (Ghidra, Hopper, IDA) with a full toolchain, MCP-ready.
- [rea-flake](https://github.com/Fractal-Tess/rea-flake) - REA packaged for Nix.
- [Homebrew formula](https://github.com/moonfruit/homebrew-tap/blob/main/Formula/rea-agents.rb) - Community tap for rea-agents.
- [rea-installer](https://github.com/scottkw/rea-installer) - One-command install and clean uninstall of REA and its dependencies on macOS, Windows, and Linux.
- [rea-ghidra-setup](https://github.com/yyds8170-ctrl/rea-ghidra-setup) - Chinese. One-click REA and Ghidra deployment on cloud desktops and Linux servers, with Homebrew and Scoop packages.
- [rea-pixi-env](https://github.com/SilenWang/rea-pixi-env) - Pinned pixi environment with REA MCP and Ghidra for Mach-O static analysis.
- [rea-windows-setup](https://github.com/wilcox101-maker/rea-windows-setup) - Windows script that installs Temurin JDK 21 and Ghidra for REA.
- [rea-run-lab](https://github.com/ylwl1997/rea-run-lab) - GitHub Codespaces lab for REA against a bundled self-owned Electron demo.
### Agent Adapters

- [rea-mcp for LM Studio](https://github.com/Nowng/rea-mcp) - Wraps the REA MCP server as an LM Studio plugin.
- [picode-rea](https://github.com/cognixws/picode-rea) - PiCode extension exposing REA's static tools.
- [dsh-rea (Fanqi89)](https://github.com/Fanqi89/dsh-rea) - DeepSeek Harness bridge exposing all REA tools.
- [dsh-plugin-rea](https://github.com/czcdr/dsh-plugin-rea) - DeepSeek Harness plugin that also prepares Node, the REA CLI, a JDK, and Ghidra.
- [dsh-rea (zhaofeng130)](https://github.com/zhaofeng130/dsh-rea) - DeepSeek Harness adapter registering the REA skill and doctor tools.
- [rea-dsh-plugin](https://github.com/ya123-4/rea-dsh-plugin) - DeepSeek Harness plugin bundling the MCP server and the agent skill in one install.
- [dsh-rea-mcp](https://github.com/sheilacraig/dsh-rea-mcp) - Config-only DeepSeek Harness bundle, no plugin code.
- [dsh-reverse-mode](https://github.com/xingxue-ux/dsh-reverse-mode) - DeepSeek Harness preset that mounts REA only in a dedicated reverse-engineering mode.
- [dsh-rea (caixuf)](https://github.com/caixuf/dsh-rea) - DeepSeek Harness plugin covering native, APK, and web or Electron static tools.
- [rea-reverse-engineering](https://github.com/Ydjin1984/rea-reverse-engineering) - Russian. ZCode plugin exposing a curated set of REA tools.
- [dsh-mcp-rea](https://github.com/Ersith/dsh-mcp-rea) - Chinese. Thin MCP bridge exposing 21 curated REA tools with a 6.7 KB schema instead of the full 1.8 MB one.
- [rea-mcp-bridge](https://github.com/tororex250-ship-it/rea-mcp-bridge) - Spanish. Runs the REA MCP server in GitHub Codespaces for Gemini.
- [rea-cloud](https://github.com/andresanino/rea-cloud) - REA workbench for Claude Code cloud sessions.
- [nodecode-rea](https://github.com/ThomShark/nodecode-rea) - REA as a Nodecode cell with its MCP server registered.
- [muse-rea](https://github.com/solivansprvill-droid/muse-rea) - Unofficial Muse skill wrapping a pinned rea-agents with a safety-gated CLI.
- [dsh-rea (BJ1919810)](https://github.com/BJ1919810/dsh-rea) - One DeepSeek Harness switch for the REA MCP server and its three workflow skills together.
- [dsh-rea-android](https://github.com/adeahejshshsh/dsh-rea-android) - REA MCP bridge for DeepSeek Harness on Android via Termux.
## Architecture and Internals

- [Docs index](https://github.com/morluto/rea/blob/main/docs/index.md) - Entry point to all reference docs.
- [Tool design](https://github.com/morluto/rea/blob/main/docs/tool-design.md) - Principles behind REA's MCP tool surface.
- [Reverse engineering tools](https://github.com/morluto/rea/blob/main/docs/reverse-engineering-tools.md) - Engines REA can drive and how they are detected.
- [Reconstruction readiness](https://github.com/morluto/rea/blob/main/docs/reconstruction-readiness.md), [coverage](https://github.com/morluto/rea/blob/main/docs/reconstruction-coverage.md), and [obligation ledgers](https://github.com/morluto/rea/blob/main/docs/reconstruction-obligation-ledgers.md) - How REA tracks what a reconstruction still owes.
- [Testing](https://github.com/morluto/rea/blob/main/docs/testing.md) - Test layout and how to run the suite.
- [Migration to 6.2](https://github.com/morluto/rea/blob/main/docs/migration-6.2.md) - Breaking changes in the 6.x line.
- [Contributing](https://github.com/morluto/rea/blob/main/CONTRIBUTING.md) - How to contribute to REA itself.
- [Security policy](https://github.com/morluto/rea/blob/main/SECURITY.md) - Reporting vulnerabilities in REA.
- [Does reverse engineering need a bigger model?](https://rea.tools/blog/reverse-engineering-models/) - Official blog, October 2026. Specialized versus general models, with compiler-feedback learning.
- [The industrial revolution in reverse engineering](https://rea.tools/blog/touhou-reconstruction/) - Official blog, October 2026. Reconstructing TH04, TH08, and TH095 with agents and verification.

## Articles and Tutorials

- [rea-cn](https://github.com/bbylw/rea-cn) - Chinese translation of the REA documentation and README.
- [rea-research](https://github.com/ringozzt/rea-research) - Chinese. Deep technical survey of REA with sources graded as primary or secondary.
- [Reverse-Engineer-Anything](https://github.com/valorisa/Reverse-Engineer-Anything) - French. Unofficial teaching guide to analyzing apps and binaries with REA.
- [rea-engenharia-reversa](https://github.com/inematds/rea-engenharia-reversa) - Portuguese, English, and Spanish. REA explained with links, cases, and cautions.
- [rea.run](https://rea.run/) - Unofficial bilingual community docs, source in [ylwl1997/rea-run](https://github.com/ylwl1997/rea-run).
- [reatool](https://github.com/ZooHero500/reatool) - Unofficial tutorials and comparisons for installing REA with different coding agents.
- [rea-lab](https://github.com/pablodiazjorge/rea-lab) - Verifying, measuring, and visualising the tools agents use with REA and Ghidra on Windows.
- [rea-deep-dive](https://github.com/neuralsun/rea-deep-dive) - Chinese. Source mechanisms, original papers, reproducible experiments, and evidence-driven behavior reconstruction.
- [rea-practice](https://github.com/jkf87/rea-practice) - Korean. Hands-on practice analysing your own Electron app and C program with REA, Ghidra, and Claude Code.
- [rea-playbook](https://github.com/jinshi666888/rea-playbook) - Hands-on playbook with a minimal Electron target, an evidence extractor, and an MCP probe.
- [REA explained](https://hoangyell.com/rea-explained/) - HoangYell. Plain-language introduction.
- [REA: reverse engineering for coding agents](https://elsolitario.org/en/2026/10/10/rea-reverse-engineering-for-coding-agents/) - El Solitario. Getting-started guide.
- [How To Use REA To Clone Any Software In Minutes](https://www.youtube.com/watch?v=FnB9tHKBJXQ) - Eric Tech. Video tutorial.
- [Hacker News discussion](https://news.ycombinator.com/item?id=50028275) - Long thread on AI decompilation, preservation, and clean-room claims.
- [Reverse Engineering with AI: Trace Electron and Native Apps](https://www.sitepoint.com/reverse-engineering-with-ai-rea-electron-tracing/) - SitePoint. Install, run `rea doctor`, and trace a feature from UI into native code.
- [REA explained for AI coding agents](https://dev.to/daviddeng/rea-explained-for-ai-coding-agents-5g6j) - DEV Community. Walkthrough with advice to pin versions.
- [REA: Let Your AI Agent Reverse Engineer the App Features You Wish You Had](https://dev.to/arshtechpro/rea-let-your-ai-agent-reverse-engineer-the-app-features-you-wish-you-had-3en7) - DEV Community.
- [REA: Teaching AI Agents to Reverse Engineer Binaries Through MCP](https://starlog.is/articles/ai-agents/morluto-rea) - Starlog. Architecture-focused overview.
- [REA: Reverse Engineer Anything With AI Agents](https://www.kunalganglani.com/blog/rea-reverse-engineer-anything-agents) - Kunal Ganglani. Overview and setup.
- [What is REA (Reverse Engineer Anything)?](https://apidog.com/blog/what-is-rea-reverse-engineer-anything/) - Apidog. Covers the star surge and the FAQ note on what reaches your model provider.
- [REA Reverse Engineer Anything GitHub: Free Quick Start](https://agentos.guide/rea-reverse-engineer-anything-github) - AgentOS guide.
- [How to Reverse Engineer Anything](https://howtorea.com/) - Independent companion handbook, not affiliated with the project.
- [REA v6.4.0 verified on Windows 11 with Claude Code and Codex CLI](https://wikidocs.net/451131) - Korean. Hands-on verification notes.
- [REA 讓 AI Agent 協助拆解軟體運作](https://www.inside.com.tw/article/42615-rea-reverse-engineer-anything-open-source-mcp-ai-agent-github) - Traditional Chinese. INSIDE coverage.
- [REA GitHub Erfolg](https://www.all-ai.de/news/news26top/rea-github-erfolg) - German. all-ai.de coverage.

## Reviews and Critical Takes

- [rea: reverse engineering tools for agents](https://gittested.com/reviews/morluto-rea/) - GitTested. Tested 6.2.0 and found plain shell tools matched it on small programs. Verdict: adopt with care.
- [Reverse Engineer Anything MCP: hands-on](https://www.mindstudio.ai/blog/reverse-engineer-anything-mcp/) - MindStudio. Rebuilt parts of macOS Preview with and without REA and compared.
- [REA: Reverse Engineer Anything](https://www.eigent.ai/blog/rea-reverse-engineer-anything) - Eigent. Argues the tool mostly wires existing RE tools together.
- [Reverse Engineer Anything GitHub repo](https://www.geeky-gadgets.com/reverse-engineer-anything-github-repo/) - Geeky Gadgets. Raises IP and DRM concerns.

## Community

- [Discord](https://discord.gg/GkcryMnJDM) - Official server.
- [@reatools on X](https://x.com/reatools) - Official account.
- [GitHub Discussions](https://github.com/morluto/rea/discussions) - Q&A, show and tell, ideas.
- [Reverse Engineering 101 with REA + Ghidra](https://github.com/morluto/rea/discussions/3791) - Community learning resource.
- [Reverse Engineering toolkit](https://github.com/morluto/rea/discussions/3845) - Community-shared toolkit.
- [Contributors](https://rea.tools/contributors/) - People behind the project.

## Translations

Official README translations in the repo: [简体中文](https://github.com/morluto/rea/blob/main/docs/readme/README_zh.md), [繁體中文](https://github.com/morluto/rea/blob/main/docs/readme/README_zh-TW.md), [日本語](https://github.com/morluto/rea/blob/main/docs/readme/README_ja.md), [한국어](https://github.com/morluto/rea/blob/main/docs/readme/README_ko.md), [Deutsch](https://github.com/morluto/rea/blob/main/docs/readme/README_de.md), [Español](https://github.com/morluto/rea/blob/main/docs/readme/README_es.md), [Français](https://github.com/morluto/rea/blob/main/docs/readme/README_fr.md), [Português (Brasil)](https://github.com/morluto/rea/blob/main/docs/readme/README_pt-BR.md), [Русский](https://github.com/morluto/rea/blob/main/docs/readme/README_ru.md), [Italiano](https://github.com/morluto/rea/blob/main/docs/readme/README_it.md), [Polski](https://github.com/morluto/rea/blob/main/docs/readme/README_pl.md), [Türkçe](https://github.com/morluto/rea/blob/main/docs/readme/README_tr.md), [Українська](https://github.com/morluto/rea/blob/main/docs/readme/README_uk.md), [Tiếng Việt](https://github.com/morluto/rea/blob/main/docs/readme/README_vi.md), [ไทย](https://github.com/morluto/rea/blob/main/docs/readme/README_th.md), [Bahasa Indonesia](https://github.com/morluto/rea/blob/main/docs/readme/README_id.md), [العربية](https://github.com/morluto/rea/blob/main/docs/readme/README_ar.md), [فارسی](https://github.com/morluto/rea/blob/main/docs/readme/README_fa.md), [Ελληνικά](https://github.com/morluto/rea/blob/main/docs/readme/README_el.md).

## Case Trackers and Other Lists

- [awesome-REA-cases](https://github.com/songshikang0111/awesome-REA-cases) - Chinese. Tracks public REA and AI reverse-engineering cases six times a day, deduplicated and categorised.
- [rea-gems](https://github.com/sqwu/rea-gems) - Auto-updated gallery of REA cases, refreshed daily by GitHub Actions.
- [rea-case-rankings](https://github.com/miles990/rea-case-rankings) - Daily scored ranking of REA cases, apps, and write-ups.
- [awsome-REA](https://github.com/Asymmetrical-1024/awsome-REA) - Chinese. REA case collection with original posts, official evidence, and verification limits.
- [awsome-rea (jiaqiwang969)](https://github.com/jiaqiwang969/awsome-rea) - Evidence-backed REA projects, research, and compatibility tools. English and Chinese.
- [rea-casebook (aliaihub)](https://github.com/aliaihub/rea-casebook) - REA case studies, reconstructions, demos, and the evidence behind each result.
- [awesome-ai-rewrite](https://github.com/qqxhb/awesome-ai-rewrite) - Chinese. The AI clean-room rewrite wave, from the Adobe suite to Claude Code and REA.
- [awesome-reverse-engineer-anything](https://github.com/AIshihzong/awesome-reverse-engineer-anything) - AI reverse engineering and rebuilds, noting which ones really used REA.
- [Awesome-REA (reacher-z)](https://github.com/reacher-z/Awesome-REA) - Tools, projects, case studies, and research papers across websites, games, apps, binaries, firmware, and protocols.
- [awesome-rea (git-sanbu)](https://github.com/git-sanbu/awesome-rea) - English and Chinese. REA use cases and case studies with primary sources.
- [awesome-rea (StandonJoyner)](https://github.com/StandonJoyner/awesome-rea) - Finished results only: reimplemented engines, byte-matching decompilations, formats, protocols, and ports.
- [awesome-rea-games](https://github.com/HaozheH3/awesome-rea-games) - Game decompilations, recompilations, demos, and ports gathered in one place.
- [All-REA](https://github.com/ismagoat/All-REA) - Utility-first directory of open-source apps and reconstructions sourced from REA and similar workflows.
- [awesome-rea (kaixinbaba)](https://github.com/kaixinbaba/awesome-rea) - Open-source reimplementations and compatible alternatives with licenses and honest limits.
- [awesome-rea (yibie)](https://github.com/yibie/awesome-rea) - AI-assisted decompilation, recompilation, and native ports, each with its acceptance test. Not REA-specific.
- [awesome-ai-reverse-engineering](https://github.com/zhuyansen/awesome-ai-reverse-engineering) - AI reverse-engineering tools for coding agents, each read and security-graded.
- [awesome-ai-reverse](https://github.com/DiscoverBox/awesome-ai-reverse) - Chinese. MCP servers, skills, plugins, and agents for AI-assisted reverse engineering.
- [awesome-reverse-engineered-games](https://github.com/heaven-hm/awesome-reverse-engineered-games) - Games decompiled and rebuilt with AI models and agents.
- [awesome-reverse-engineering](https://github.com/morluto/awesome-reverse-engineering) - By REA's author. General reverse-engineering tools and learning resources.

## Related Tools

Engines and runtimes REA drives or complements.

- [Ghidra](https://github.com/NationalSecurityAgency/ghidra) - Free software reverse engineering suite from the NSA. REA's default native engine.
- [Hopper](https://www.hopperapp.com/) - macOS and Linux disassembler. REA setup can install it with approval.
- [IDA Pro](https://hex-rays.com/ida-pro) - Commercial disassembler and decompiler.
- [JADX](https://github.com/skylot/jadx) - Dex to Java decompiler used for Android targets.
- [Frida](https://github.com/frida/frida) - Dynamic instrumentation toolkit used for runtime hooks.
- [Model Context Protocol](https://modelcontextprotocol.io/) - The protocol REA speaks to agents.
- [ida-mcp](https://github.com/HexRaysSA/ida-mcp) - Hex-Rays' official MCP server for IDA.
- [ida-pro-mcp](https://github.com/mrexodia/ida-pro-mcp) - MCP server for IDA Pro, used by REA's IDA profile.
- [ida-free-mcp](https://github.com/0xshlomil/ida-free-mcp) - Native MCP bridge for IDA Free.
- [GhidraMCP](https://github.com/LaurieWired/GhidraMCP) - Peer MCP server for Ghidra. REA drives Ghidra directly instead.

## Related Awesome Lists

- [awesome](https://github.com/sindresorhus/awesome) - The root list.
- [awesome-reversing](https://github.com/tylerha97/awesome-reversing) - General reverse engineering resources.
- [awesome-mcp-servers](https://github.com/punkpeye/awesome-mcp-servers) - Other MCP servers.

