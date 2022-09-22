# deci3dbg
Deci3dbg - Ida Pro Debugger Module for Playstation 3. Updated to support IDA 7.5 SDK.

Whoever used to debug on Playstation 3 knows that there is only one debugger available - SN Systems ProDG. It has some nice features (that I even miss in others debuggers) but overall… its not that good. There also was a gdb client but it was pulled around 1.xx sdk (specification changed, there is no more step cmd, etc). So after some time that I spent with ProDG I realized that it just dont works for me and decided to get host debugger to communicate with Ida. It would have allowed me to use all those nice features like scripts, plugins, tracing, leaving comments in place, interface and hotkeys to which I am used to over the years.

Okay, I hear that someone of you is asking why I did Ida module and not some kind of gdb proxy instead, and reasons are simple:

- I already have experience of making gdb proxys and hosts, but not had experience of making Ida debugger modules (actually not much who did this)
- Ida’s gdb client is not open source

[IMAGE HERE]

So I did it and it works pretty well. Was testing it for months, catching bugs. At the last time fixed some remaining bugs around half year ago, so it should be much better, but not used it much since then.


## Features
- PPU debugging
- General and Float registers
- Exceptions, Breakpoints, Step thru code
- Hardware breakpoints (DABR)
- Threads and Modules
- Read/Write memory
- Works with official Sony’s Reference Tools and Debug Stations (DECR/DECH)
- Also works with custom firmwares

## Notes
It uses ProDG’s TMAPI for communication over deci3 protocol with ps3. Its pretty good and even if deci3 specification docs are leaked its saved alot of time. Therefor, its supports only Windows platform.

## Building Requirements
- Visual Studio 2022+
- Sony PS3 4.75+ SDK w/ Visual Studio Integration
- IDA 7.5 SDK

## Build
1. Edit the system environment variables and make a 'New..' 
	- Variable Name: IDADIR
	- Variable Value: C:\Program Files\IDA 7.5
2. Edit the system environment variables and make a 'New..' 
	- Variable Name: IDASDK
	- Variable Value: C:\Program Files\IDA 7.5\idasdk75
3. Build using Visual Studio 2022

## Installation
- Copy deci3dbg-x64-Release-ida32.dll and deci3dbg-x64-Release-ida64.dll to plugins folder inside your Ida Pro installation.

## How to use
1. Load PPC binary in Ida Pro
2. Debugger -> Select debugger… -> DECI3 debugger plugin
3. Debugger -> Attach to process…
4. Select target and press OK (target may be showed as ‘disconnected’, bug of TMAPI)
5. Select process

Licensed under the GPLv2 license.