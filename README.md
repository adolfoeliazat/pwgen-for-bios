Console Pwgen For BIOS
============================

About
---------------------------

This code is based on python programs from [Dogbert&#39;s Blog](http://dogber1.blogspot.com/2009/05/table-of-reverse-engineered-bios.html) and research by Asyncritus, which is itself a [fork](https://github.com/bacher09/pwgen-for-bios).

It can calculate recovery password for bios from a service tag hash.

Supported BIOS types:
* Compaq - 5 decimal digits
* Dell	- serial number for series -595B, -D35B. -2A7B and -1D3B
* Fujitsu-Siemens - 5 decimal digits, 8 hexadecimal digits, 5x4 hexadecimal digits, 5x4 decimal digits
* Hewlett-Packard - 5 decimal digits, 10 characters
* Insyde H20 (generic) - 8 decimal digits
* Phoenix (generic) - 5 decimal digits
* Sony - 7 digit serial number
* Samsung - 12 hexadecimal digits

The main difference for the fork is that it can be ran from console directly :

Linux
```bahs
node biosPwd.js 07088120410C0000
```
Windows
```batch
node.exe biosPwd.js 07088120410C0000
```
In order to get the code/serial, either the BIOS itself will provide it, or you can try the PC's serial number written somewhere on the caseback.

You will need Node.js for that:

Linux
```bash
sudo aptitude install nodejs || echo 'you know what to do'
```
[Windows](https://nodejs.org/dist/v6.11.0/node-v6.11.0-win-x86.zip)

Mitigation
---------------------------
Even if your model doesn't have a backdoor/escrow password, it can still be reset by disconnecting CMOS battery.

One of the mitigations is to use NVRAM to store BIOS/UEFI passwords (already implemented for top HP/Dell models), but it can still be bypassed by short-circuiting associated jumpers (can burn motherboard), plus your password have to be strong.

A sure way to at least detect such tampering is to use TPM (Trusted Platform Module).

Finally, you shouldn't rely on BIOS for your security.
