# Cybersecurity Tools

Common tools used for CTFs, competitions, labs, forensics, networking, and reverse engineering.

Only use security tools on systems you own or are authorized to test.

## `nmap`

Network scanner for finding ports, services, and versions.

```bash
sudo apt install -y nmap
```

## `tshark`

Command-line Wireshark for analyzing packet captures.

```bash
sudo apt install -y tshark
```

## `wireshark`

GUI packet analyzer for inspecting network traffic.

```bash
sudo apt install -y wireshark
```

## `john`

Password and hash cracking tool.

```bash
sudo apt install -y john
```

## `hashcat`

Fast password and hash cracking tool.

```bash
sudo apt install -y hashcat
```

## `bitlocker2john`

Extracts BitLocker hashes for John or Hashcat. Usually installed with John.

```bash
sudo apt install -y john
```

## `ffuf`

Fast web directory and content discovery.

```bash
sudo apt install -y ffuf
```

## `gobuster`

Directory, DNS, and virtual-host enumeration.

```bash
sudo apt install -y gobuster
```

## `feroxbuster`

Recursive web directory discovery.

```bash
sudo apt install -y feroxbuster
```

## `sqlmap`

Automates SQL injection testing.

```bash
sudo apt install -y sqlmap
```

## `CyberChef`

Useful for encoding, decoding, hashes, XOR, compression, cryptography, and data conversion.

Usually used through the CyberChef website.

## `exiftool`

Extracts metadata from images, documents, audio, and video.

```bash
sudo apt install -y libimage-exiftool-perl
```

## `binwalk`

Finds embedded files and data inside binaries and firmware.

```bash
sudo apt install -y binwalk
```

## `foremost`

Recovers files from disk images and raw data.

```bash
sudo apt install -y foremost
```

## `dislocker`

Accesses BitLocker-encrypted volumes when you have valid credentials or recovery information.

```bash
sudo apt install -y dislocker
```

## `volatility3`

Memory forensics framework for analyzing RAM dumps.

```bash
python3 -m venv ~/.venvs/volatility3
source ~/.venvs/volatility3/bin/activate
pip install volatility3
```

## `steghide`

Hides and extracts data from supported image and audio files.

```bash
sudo apt install -y steghide
```

## `stegseek`

Fast password recovery tool for steghide files.

```bash
sudo apt install -y stegseek
```

## `zsteg`

Finds hidden data in PNG and BMP images.

```bash
sudo apt install -y ruby ruby-dev
sudo gem install zsteg
```

## `ffmpeg` / `ffprobe`

Analyzes, converts, and extracts audio and video data.

```bash
sudo apt install -y ffmpeg
```

## `mkvextract`

Extracts tracks, subtitles, and attachments from MKV files.

```bash
sudo apt install -y mkvtoolnix
```

## `Ghidra`

GUI reverse-engineering and decompilation tool.

Install Java first:

```bash
sudo apt install -y openjdk-21-jdk
```

Then download Ghidra from the official release.

## `gdb`

Debugger for Linux binaries.

```bash
sudo apt install -y gdb
```

## `GEF`

Adds reverse-engineering and exploitation features to GDB.

```bash
bash -c "$(curl -fsSL https://gef.blah.cat/sh)"
```

## `checksec`

Checks binary protections such as NX, PIE, RELRO, and stack canaries.

```bash
sudo apt install -y checksec
```

## `pwntools`

Python framework for CTF and binary exploitation scripting.

```bash
python3 -m venv ~/.venvs/pwntools
source ~/.venvs/pwntools/bin/activate
pip install pwntools
```

## `ROPgadget`

Finds ROP gadgets inside binaries.

```bash
pip install ROPgadget
```

## `ropper`

Searches binaries for ROP gadgets.

```bash
pip install ropper
```

## `dig`

DNS lookup and troubleshooting tool.

```bash
sudo apt install -y dnsutils
```

## `whois`

Looks up public domain and IP registration information.

```bash
sudo apt install -y whois
```

## Wordlists

SecLists contains useful wordlists for web discovery, usernames, passwords, fuzzing, and CTF challenges.

```bash
sudo apt install -y seclists
```

Common location:

```text
/usr/share/seclists/
```

## Quick Install

Install most of the tools at once:

```bash
sudo apt update

sudo apt install -y \
nmap tshark wireshark john hashcat ffuf gobuster feroxbuster sqlmap \
libimage-exiftool-perl binwalk foremost dislocker steghide stegseek \
ruby ruby-dev ffmpeg mkvtoolnix gdb checksec dnsutils whois seclists \
python3 python3-pip python3-venv git curl wget unzip
```
