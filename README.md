# **Quantum Silicon Core Loader**

Primary Core: **qslcl.elf**

Assistant Module: **qslcl.bin (v0.6.3)**

Universal Controller: **qslcl.py (v1.2.5)**

---

# Overview

**Quantum Silicon Core Loader (QSLCL)** is a post-bootloader, post-vendor, post-exploit execution layer operating directly at the silicon boundary.

It executes beyond traditional security models and is capable of surviving firmware transitions, negotiating trust, and interpreting device state without CVEs or patches.

QSLCL runs in:

* **Qualcomm EDL / Firehose**
* **MediaTek BROM / Preloader**
* **Apple DFU**
* **Engineering / META / Diagnostic Modes**
* **Any USB/Serial exposed interface**

> **"You don't run QSLCL — silicon interprets it."**

---

# What's New in **v0.6.3**

- minor improvements has been made
  

---

# qslcl.py — Universal Controller **v1.2.5**

# What's New in **v1.2.5**

- major improvements to improve stability in some commands and parsers
  
## Complete Command List

**Core Memory Operations:**
- `READ` - Advanced memory reading with verification
- `WRITE` - Professional memory writing with safety checks
- `ERASE` - Secure data erasure with multiple patterns
- `PEEK` - Memory inspection with type detection
- `POKE` - Precision memory writing with bit operations
- `PATCH` - Advanced binary patching with verification

**System Commands:**
- `HELLO` - Device handshake and identification
- `PING` - Latency testing and connectivity verification
- `GETINFO` - Comprehensive device information
- `GETVAR` - System variable access
- `GETSECTOR` - Storage sector size detection

**Advanced Operations:**
- `RAWMODE` - Privilege escalation and hardware access
- `GETCONFIG` - System configuration management
- `RESET` - System reset and restart control
- `BRUTEFORCE` - Advanced system exploration
- `AUTHENTICATE` - Security authentication

**Specialized Commands:**
- `OEM` - Original Equipment Manufacturer functions
- `ODM` - Original Design Manufacturer controls
- `MODE` - System mode management
- `POWER` - Power domain control
- `VOLTAGE` - Voltage regulation
- `BYPASS` - Security bypass operations
- `GLITCH` - Fault injection framework
- `VERIFY` - System integrity verification
- `SETCONFIG` - Set configuration

---

# Installation & Quick Start

## Requirements

```bash
pip install pyserial pyusb
pip install requests tqdm   # optional
```

## Basic Usage

```bash
# Test basic functionality
python qslcl.py hello --loader=qslcl.bin
python qslcl.py getinfo --loader=qslcl.bin
python qslcl.py ping --loader=qslcl.bin
```

## Professional Usage

```bash
# Complete memory operations
python qslcl.py read boot boot.img --loader=qslcl.bin
python qslcl.py write boot modified_boot.img --loader=qslcl.bin --verify
python qslcl.py erase cache --pattern random --loader=qslcl.bin
python qslcl.py patch 0x880000 file patch.bin --loader=qslcl.bin

# Bootstrap operations
python qslcl.py bootstrap --architecture arm64 --loader=qslcl.bin
python qslcl.py bootstrap --verify --loader=qslcl.bin

# Advanced debugging
python qslcl.py peek 0x100000 --hexdump --loader=qslcl.bin
python qslcl.py poke 0x200000 0xDEADBEEF --bit-op OR --loader=qslcl.bin

# System control
python qslcl.py rawmode unlock --loader=qslcl.bin
python qslcl.py rawmode set JTAG_ENABLE 1 --loader=qslcl.bin
```

## Advanced Usage

```bash
# With authentication
python qslcl.py hello --loader=qslcl.bin --auth

# Wait for device detection
python qslcl.py getinfo --loader=qslcl.bin --wait 10

# Multiple commands with same loader
python qslcl.py hello --loader=qslcl.bin && python qslcl.py getinfo --loader=qslcl.bin

# Professional patching workflow
python qslcl.py read boot boot.img --loader=qslcl.bin
# Modify boot.img externally
python qslcl.py patch boot file boot_patched.img --loader=qslcl.bin --verify
```

---

# Device Compatibility

| Vendor   | Mode             | Detection Method            | Status |
|----------|------------------|-----------------------------|-------------|
| Qualcomm | EDL              | Sahara + Firehose handshake | ✅ Enhanced |
| MediaTek | BROM / Preloader | 0xA0 preloader ping         | ✅ Enhanced |
| Apple    | DFU              | DFU signature               | ✅ Enhanced |
| Generic  | USB CDC/Bulk     | Endpoint auto-discovery     | ✅ Universal |
| Any      | Serial COM       | UART auto sync              | ✅ Universal |

---

## Key Philosophy

* **Universal Execution** - One binary, all architectures, 30+ complete commands + dynamic bootstrap
* **Silicon Intimacy** - Direct hardware conversation with bit-level precision
* **Adaptive Intelligence** - Environment-aware behavior with safety enforcement
* **Professional Grade** - Enterprise-level memory operations with verification
* **Advanced Patching** - Professional binary modification with read-back verification
* **Dynamic Bootstrapping** - Universal cross-architecture initialization
* **Ethical Empowerment** - Capability with responsibility and safety controls
