# ROPInjector - Rite Of Passage ROP Injector
Rite Of Passage ROP Injector. Injects a ROP into target process. It allows to choose either regular ROP (that uses VirtualProtect) or a Rite Of Passage ROP that bypasses most endpoint exploit protections. It performs injection using the following steps:
* Allocate Read/Write memory on target process.
* Write the shellcode that that memory.
* Create a new thread on target process.
* Inject a ROP to the new thread
* ROP will modify protection of the shellcode memory (using either a call to VirtualProtect or a Rite Of Passage call to NtProtectVirtualMemory).
* Next, the ROP will run the shellcode.
* Shellcode creates a mutex named "PWN3D!" and terminates the thread.

# Work In Progress
This is still a preliminary version intended as a POC. The code works only on x64 processes and tested against Windows 10 (should also work on Windows 8.1 but not tested).

# Usage
You can use either
ROPInjector.exe [ProcessId]
To inject a normal ROP (using VirtualProtect).
Or Use
ROPInjector.exe [ProcessId] RiteOfPassage
To inject a Rite Of Passage ROP.

# Compilation
Project was created with Visual Studio 2015.
