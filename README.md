### Run ucore_lab on mac

---

This manual will guide you run ucore_lab on macOS Catalina.

First, make sure you have installed Xcode or CommandLineTools.

``` bash
xcode-select --install
```



Then install [Homebrew](brew.sh). (make sure you are using .., otherwise below opreations will extrrrrrrremely slow.)

``` bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
```



Minimal install necessary tools.

``` bash
brew install i386-elf-gdb gdb cgdb qemu
```



Then you could run ucore_lab. 

Debugging ucore_lab needs change every code in Makfile like

``` makefile
$(V)$(TERMINAL) -e "gdb -q -x tools/gdbinit"
```

Into 

``` makefile
gdb -q -x tools/gdbinit
```



