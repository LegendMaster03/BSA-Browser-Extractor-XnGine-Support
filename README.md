## BSA Browser

### XnGine support in this fork

This repository is a fork of [AlexxEG/BSA_Browser](https://github.com/AlexxEG/BSA_Browser). The upstream application, general archive browser, and original credits remain those of the upstream project. The fork adds an XnGine archive reader to the existing archive listing and extraction infrastructure; it is not a separate BSA Browser implementation.

The additions include:

- Recognition of XnGine-style `.bsa`, `.snd`, and `.sav` record archives in the existing GUI and CLI archive-opening paths.
- Parsing of footer-based name and numeric record indices, with a fallback for legacy headerless `.bsa` name indices.
- A dedicated `XNGBSAFileEntry` that exposes archive record offsets, sizes, compression status, and record IDs.
- Battlespire-style LZSS decompression for records marked compressed.

The parser checks record sizes and that the indexed data exactly occupies the region before the footer. This is format parsing, not proof of compatibility with every XnGine title or archive variant. Compressed records are currently decompressed in memory, and the decoder's treatment of truncated input warrants additional validation before relying on it for untrusted archives.

The implementation is primarily in `Sharp.BSA.BA2/BSAUtil/BSA.cs`, `Sharp.BSA.BA2/BSAUtil/XNGBSAFileEntry.cs`, and `Sharp.BSA.BA2/Utils/CompressionUtils.cs`. The original upstream build requirements and credits follow.

### Introduction
BSA Browser is a Bethesda Archive browser & extractor application for Windows. Games that are supported includes the Fallout series and Elder Scrolls series (except Elder Scrolls Online).

BSA Browser started as a fork of [Fallout Mod Manager](https://sourceforge.net/projects/fomm/)'s BSA Browser as a standalone application & has been steadily improved with more features.

Read more at [BSA Browser](https://www.nexusmods.com/skyrimspecialedition/mods/1756) on Nexus Mods.

Requires .NET Framework 4.8

### Features
 - Browse & extract files from .BSA/.BA2/.DAT archives
 - Browse multiple archive files simultaneously
 - Drag & drop for opening archives and extracting
 - File search, with wildcard and regex support
 - Preview supported files with built-in tools. And for all other files open with the default system application
 - Recent Files list
 - Setup quick exporting for frequently used paths (See Tools -> Options)
 - Copy full path, folder path or file name
 - Compare archives, see new, changed or removed files
 - Supports PS4 modding (Though untested by me)
 
### Forked Version
Fork is based on Fallout Mod Manager [v0.13.21](https://sourceforge.net/p/fomm/code/685/tree/branches/qfomm/)

### License and Copyright
[Fallout Mod Manager](https://sourceforge.net/projects/fomm/) is licensed under GPLv3.

All rights on source code and libraries belong to their respective owners.

### Credits
- Thanks to Timeslip, Q & kaburke for [Fallout Mod Manager](https://sourceforge.net/projects/fomm/)
- Thanks to [SockNastre](https://github.com/SockNastre) for the help with GNF support
- [bsaopt](https://github.com/Ethatron/bsaopt)
- [BA2Lib](https://github.com/digitalutopia1/BA2Lib)
- [F4SE's ba2extract tool](http://f4se.silverlock.org/)
- [B.A.E. - Bethesda Archive Extractor](http://www.nexusmods.com/fallout4/mods/78)
