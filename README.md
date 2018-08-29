# UKERN - Release (Public repo)
![UKERN Logo](https://ukern.exploitation.cool/ukern.png)

## About
UKERN is a sandboxed kernel "emulator" that operates from within userland.

UKERN aims to provide a kernel like environment with kernel like features regardless of the restrictions that an OS enforces, in this case Apple's iOS.


## Functionality
- Emulate processes and tasks
- Act on file system events
- Emulate binaries compiled for UKERN in dylib form and execute (arbitrary) code
- Fake user permissions
- Fake a rootfilesystem (just like docker does)
- Interpose calls and handle them accordingly with debugging information
- Abuse dlopen and dlsym to load and emulate real mach-o binaries

## Fake processes
- Thread based
- Fake process ID allocated and managed by XNU (iOS kernel)
- Process Listing implementation
- Kill processes, control their fake address space and fake fork
- System() implementation
- Fake mach_vm_write and mach_vm_read operations

## Fake Mach-O Loader
- Load any signed dylib
- Lookup main function in dylib and construct function pointers
- Detect architectures and find debug info of the binary being spawned
- Find classes in binary being spawned

## Fake User
- Fake home directory
- Fake authorization checks
- Multi-user support

## Cryptography
- RSA implementations
- OpenSSL
- SHA algorithms
- MD5 algorithms
- Checksumming

## Services
- Cycript server
- HTTP Webserver
- Telnet server
- FTP server
- (planned) Dropbear SSH server
- Netcat server (defaults to root access, for debugging only)


## File System
- Fake rootfs container
- Fake userpermissions (fake vnodes)
- Detect FS operations (read, write, sync, etc.)
- FileManagement implementations
- FileInformation implementations

## Reporting Vulnerabilities
Send an e-mail to s.voigtlander@jailed.ml

The public disclosure due is 90 days.

Notable vulnerabilities will get an identifier UKV-2018-???


## Security Consent

### UKV-2018-0001
A local attacker might be able to corrupt kernel memory resulting in a Denial of Service due to a memory issue in the function walker.

This issue has been addressed by improved memory handling.

UKERN before commit "522ba0524e898846202fed2e39782fe747d3a3cc" is affected.

The risk of this vulnerability is medium.


## Developing for UKERN
- Coming soon
