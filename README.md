# HSHX

> Hash Helper Toolkit — hash identification, verification, and controlled cracking workflow support.

![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=flat-square&logo=python&logoColor=white)
![Category](https://img.shields.io/badge/Category-Hash%20Analysis-9333ea?style=flat-square)
![Status](https://img.shields.io/badge/Interface-Direct%20CLI-brightgreen?style=flat-square)
![License](https://img.shields.io/badge/License-MIT-blue?style=flat-square)

---

## Overview

HSHX helps identify hash formats, verify candidate passwords, and organize controlled cracking workflows.

This project is intended for labs, CTFs, internal audits, and authorized password security validation.

---

## Features

- Hash type identification.
- Single hash verification.
- File-based hash loading.
- Wordlist-based verification.
- Hashcat/John command template generation.
- Masked output.
- JSON/TXT reports.
- Safety gate for cracking workflows.

---

## Installation

```bash
git clone https://github.com/NeiveZ/Hash-Helper-Toolkit.git
cd Hash-Helper-Toolkit
chmod +x hshx.sh
./hshx.sh --install
```

Validate:

```bash
./hshx.sh --check
```

Run tests if available:

```bash
python3 -m pytest -q
```

Optional tools:

```bash
sudo apt update
sudo apt install hashcat john -y
```

---

## Usage

```bash
./hshx.sh <command> [options]
```

Help:

```bash
./hshx.sh --help
```

---

## Commands

### Identify a hash

```bash
./hshx.sh identify -H "5f4dcc3b5aa765d61d8327deb882cf99"
```

### Verify a password candidate

```bash
./hshx.sh verify -H "5f4dcc3b5aa765d61d8327deb882cf99" -p "password"
```

### Verify using a wordlist

```bash
./hshx.sh wordlist -H "5f4dcc3b5aa765d61d8327deb882cf99" -w wordlist.txt --authorized
```

### Generate cracking templates

```bash
./hshx.sh template -H hashes.txt --tool hashcat
```

### Analyze hash file

```bash
./hshx.sh analyze -f hashes.txt --json --txt --out reports/hashes
```

---

## Recommended Procedure

1. Identify possible hash type:

```bash
./hshx.sh identify -H "$HASH"
```

2. Verify known candidates:

```bash
./hshx.sh verify -H "$HASH" -p "$CANDIDATE"
```

3. Generate a safe tool template:

```bash
./hshx.sh template -f hashes.txt --tool hashcat
```

4. Run cracking only in authorized labs.

---

## Output Example

```text
HSHX Hash Summary

Input        single hash
Candidates   4

Results
Severity     Hash Type        Confidence     Detail
INFO         MD5              HIGH           32 hex characters
INFO         NTLM             POSSIBLE       32 hex characters
OK           Verification     MATCH          Candidate matched locally
```

---

## Safety

HSHX must only be used for hashes you own or are authorized to test. Do not process stolen credential material.

---

## License

MIT License.
