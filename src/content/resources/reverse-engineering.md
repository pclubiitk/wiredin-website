---
title: 'Reverse Engineering Guide'
description: 'How to analyze compiled binaries and understand program behavior.'
category: 'reversing'
order: 1
---

## What is Reverse Engineering?

Reverse engineering is the process of analyzing compiled programs to understand their behavior without access to source code. In CTFs, you're typically given a binary and need to find a flag hidden within its logic.

## Static Analysis

### Disassemblers & Decompilers

Use tools to convert machine code back to assembly or pseudo-C:

- **Ghidra** — free, powerful, extensible (NSA tool)
- **IDA Pro** — industry standard (expensive, but IDA Free exists)
- **Binary Ninja** — modern alternative with good APIs
- **Cutter** — open-source GUI for radare2

### Key Skills

- Reading x86/x64 assembly
- Understanding calling conventions
- Identifying common patterns (loops, conditionals, function calls)
- Recognizing standard library functions

## Dynamic Analysis

### Debuggers

- **GDB** with pwndbg or GEF extensions
- **x64dbg** (Windows)
- **lldb** (macOS)

### Techniques

- Set breakpoints at key locations
- Inspect register and memory state
- Trace execution flow
- Patch instructions at runtime

## Anti-Reversing Techniques

Be prepared to encounter:

- Obfuscation (control flow flattening, opaque predicates)
- Packing (UPX, custom packers)
- Anti-debugging checks
- VM-based protection

## Practice

- **crackmes.one** — community crackme challenges
- **Flare-On** — annual RE challenge by Mandiant
- **Microcorruption** — embedded security CTF

## Tips

1. Always run `file` and `strings` first
2. Check for known packers with `Detect It Easy`
3. Start with the entry point and work outward
4. Rename functions and variables as you understand them
5. Take notes — RE is a puzzle, and notes are your map
