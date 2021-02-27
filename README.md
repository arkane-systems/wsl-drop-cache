# wsl-drop-caches
Periodically drop the WSL caches when load is low.

This is a systemd-based implementation of [validatedev / drop-cache-if-idle](https://github.com/validatedev/drop-cache-if-idle), using the same underlying python script, but modified to run from a systemd timer and to be installed using an apt package.

## Why?

To quote the original author:

> In WSL2 (Windows Subsystem for Linux, version 2), there's a bug https://github.com/microsoft/WSL/issues/4166. Due to that issue, WSL2 doesn't return the cache, instead, the amount of cache grows until the WSL2 instance's assigned RAM is full. Well, you can simply drop the cache. But, there would be a problem for the speed of your process. Instead, the script makes sure that the WSL2 instance is idle, then drops the cache. With that approach, we could eliminate the speed issue, for some of the cases.
> 

And this is the simple-to-install-and-use version for [genie/systemd](https://github.com/arkanesystems/genie) users.

# Installation

 1. Set up the WSL Transdebian repository [following the instructions here](https://arkane-systems.github.io/wsl-transdebian/), if you have not already done so.

 2. `apt install wsl-drop-caches`

 3. Either restart WSL, or `sudo systemctl start wsl-drop-caches`.

