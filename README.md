MacOS Virtual Machine
=====================

VMWare machine configuration file. We added things like:
```
### Additional settings for MacOS Big Sur
smbios.reflectHost = "TRUE"
hw.model = "MacBookPro14,3"
board-id = "Mac-551B86E5744E2388"
smc.version = "0"
```
according to [this article](https://www.wikigain.com/install-macos-big-sur-on-vmware-windows-pc/).

**Tip #1**: On Windows, use [Auto Locker](https://github.com/paolo-projects/auto-unlocker/releases) instead of (actually as recommended by) [macOS Unlocker V3 for VMware](https://github.com/paolo-projects/unlocker) for a smooth operation.
Ask somebody with a Mac to help with downloading and [creating installation image](https://www.wikigain.com/create-macos-big-sur-iso-image/) of MacOS.
Then in the future, you can use the Virtual Machine to download MacOS yourself.

**Tip #2**: Nowadays, you should have plenty of RAM. So avoid memory swapping:
```
### Prevent creation of vmem files
### https://gist.github.com/extremecoders-re/cf8d829c108d58bfbb2e3c1f4121d7e1
prefvmx.minVmMemPct = "100"
MemTrimRate = "0"
mainMem.useNamedFile = "FALSE"
sched.mem.pshare.enable = "FALSE"
prefvmx.useRecommendedLockedMemSize = "TRUE"
```

**Tip #3**: Use different disk images for different stuffs for ease of management.

For example: We have
 * `BigMac.vmdk` for the OS
 * `BigMacXcode.vmdk` for Xcode installation (look [here](https://github.com/light-tech/XcodeVM) if you need a non-App-Store Xcode installation method on Windows that saves you a couple of hours)
 * `BigMacData.vmdk` for personal data (your projects)
 * `BigMacLLVM.vmdk` to [compile LLVM](https://github.com/light-tech/LLVM-On-iOS/)

This way, we can keep each `vmdk` size managable; discarding and replacing them as desired.