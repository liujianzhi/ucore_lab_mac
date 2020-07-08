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

> The following steps are to explain the changes to the standard code for running on Mac. <B>!!!!!If you use my code, there is no need to make the following changes!!!!!</B>

  Debugging ucore_lab needs change every code in Makfile like

  ``` makefile
  TERMINAL        :=gtk-Terminal
  $(V)$(TERMINAL) -e "$(bash)"
  ```

  Into 

  ``` makefile
  TERMINAL        :=osascript
  $(V)$(TERMINAL) -e 'tell app "Terminal" to do script "cd $(mkdir);$(bash)"'
  ```
  And add this code on the top of Makefile

  ``` makefile
  mkdir	:=$(shell pwd)/$(lastword $(MAKEFILE_LIST))
  mkdir   :=$(shell dirname $(mkdir))
  ```


  Because the gtk-Terminal is not support for Mac. We use apple script to create another termainal window.

