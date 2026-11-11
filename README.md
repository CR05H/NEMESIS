🐉 NEMESIS - Autonomous Vulnerability Chaining & Exploitation Engine

Version: 1.0.0

Author: Omar Emad

License: MIT

Python
OS
Status


📖 Overview

NEMESIS is a definitive, single-file ethical hacking tool designed to simulate autonomous attack chains. Unlike traditional scanners that merely list vulnerabilities, NEMESIS actively chains them together to achieve full exploitation, generates polymorphic payloads to bypass WAFs, and maps out the fastest path to Domain Admin in Active Directory environments.

It combines OSINT, Vulnerability Chaining, Polymorphic Mutation, and Zero-Day Fuzzing into a single cohesive workflow.


✨ Key Features

1. 🧬 Vulnerability Chaining Engine

NEMESIS doesn't just find one bug; it finds multiple low-severity issues and links them to create a high-severity exploit chain.


    Example: SSRF $\rightarrow$ Internal Redis Access $\rightarrow$ RCE via CONFIG SET.


2. 🎭 Polymorphic Payload Mutator

Automatically generates obfuscated payloads to evade static signatures and WAFs.


    Algorithms: XOR, Base64, Hex, Rot13.

    Dynamic Keys: Randomized encryption keys for each execution.


3. 🗺️ Autonomous AD Pathfinding

Simulates Active Directory enumeration to identify the fastest route from initial foothold to Domain Admin.


    Identifies cached credentials.

    Detects Kerberoastable accounts.

    Calculates lateral movement paths via SMB/LDAP.


4. 🐛 Zero-Day Fuzzer Integration

Integrates symbolic execution concepts to fuzz API endpoints and identify memory corruption or logic flaws.

5. 🚀 Self-Bootstrapping

The tool automatically detects your Linux distribution (Ubuntu, Arch, Fedora) and installs necessary system dependencies (nmap, whois, jq) if they are missing.


📦 Installation

NEMESIS is a single-file Python script. No complex virtual environments are required, but root/sudo privileges are recommended for full network scanning capabilities.

Method 1: Quick Setup (Recommended)

bash
 Copy

# Clone or download the file
git clone https://github.com/omar-emad/nemesis.git
cd nemesis

# Make executable
chmod +x nemesis.py

# Run with sudo for full privileges
sudo ./nemesis.py


Method 2: Manual Dependency Install

If you prefer not to use the built-in bootstrap, ensure you have Python 3.8+ and run:

bash
 Copy

pip install -r requirements.txt


(Note: requirements.txt contains standard library modules only, as NEMESIS is designed to be lightweight.)


🚀 Usage

Run the tool from your terminal:

bash
 Copy

sudo ./nemesis.py


Interactive Workflow


    Bootstrap Check: The tool checks for system dependencies and installs them if prompted.

    Target Input: Enter the target URL or IP address (e.g.,

    https://target.com
    ).

    Execution Phases:
        Phase 1: Scans for vulnerabilities and builds an attack graph.
        Phase 2: Generates a polymorphic payload.
        Phase 3: Maps the AD path to Domain Admin.
        Phase 4: Fuzzes for zero-day exploits.

    Summary: Displays the final exploit chain and results.


Example Output

text
 Copy

[?] Enter target website URL: https://example.com

[*] Starting Nemesis against https://example.com...

----------------------------------------
 PHASE 1: VULNERABILITY CHAINING 
----------------------------------------
[*] Scanning https://example.com for low-severity vulnerabilities...
[+] Found SSRF: CVE-2023-XXXX
[+] Found Redis Instance: CVE-2023-YYYY
[+] CHAIN ESTABLISHED:
    1. Trigger SSRF on Public Web Server
    2. Proxy Request to Internal Redis
    3. Execute Command via Redis WRITE DB

----------------------------------------
 PHASE 2: POLYMORPHIC PAYLOAD GENERATION 
----------------------------------------
[*] Generating Polymorphic Payload...
[+] Mutated via XOR Key: 0xA3

... [Output Truncated] ...



🏗️ Architecture

The tool is structured into modular classes for easy extension:


    Bootstrap: Handles OS detection and dependency installation.

    VulnerabilityChainer: Simulates finding and linking CVEs.

    PolymorphicMutator: Applies encryption/obfuscation to payloads.

    ADPathfinder: Calculates attack paths in Active Directory.

    ZeroDayFuzzer: Simulates fuzzing engines for API endpoints.

    NemesisEngine: Orchestrates the entire workflow.



📝 Credits


    Lead Developer: Omar Emad

    Design & Logic: Autonomous Attack Graphs



⚠️ Disclaimer

NEMESIS is designed for educational purposes and ethical hacking.

Use this tool only on systems you own or have explicit permission to test.

The author is not responsible for any misuse of this software.


📄 License

This project is licensed under the MIT License - see the LICENSE file for details.