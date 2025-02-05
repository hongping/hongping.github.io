---
layout: post
title: Handling Hardware Development Environment
draft: false
---

Being a hobbyist hardware developer, I have my own development environment for my off-work projects. Basically, the environment is simple - install Verilator as root into the system path and done. But things get a little complicated when I wanted to try out different version of Verilator. It is not that it can't be done, but it will involve modifying my makefile. And things will get complicated once more tools are involved, for e.g. RISC-V compiler versions, cocotb versions, etc. Hence it prompted me to find a better setup - a setup where the tooling is isolated from the makefiles.

```makefile
_makefile_path := $(realpath $(dir $(lastword $(MAKEFILE_LIST))))

export VERILATOR_ROOT ?= /tool/verilator/v5.016

OUTDIR ?= $(_makefile_path)/output
TARGET ?= simv

_cpp_top = $(_makefile_path)/verif/tb/testbench.cpp
_src = $(wildcard $(_makefile_path)/verif/tb/*.sv) \
	   $(wildcard $(_makefile_path)/src/*.sv)

$(OUTDIR)/$(TARGET): $(_cpp_top) $(_src)
	$(VERILATOR_ROOT)/bin/verilator --cc --exe --build -j 0 -Wall $(_cpp_top) $(_src) --timing -Mdir $(OUTDIR) -o $(TARGET)

run: $(OUTDIR)/$(TARGET)
	@$(OUTDIR)/$(TARGET)

all: run
```  

In order not to hardcode tool versioning into the makefiles, I need to have the shell properly setup with the required tools. I.e. in the makefile, I just need to call the tool, and assuming the tool path is being added to the environment variable PATH. 

There are many ways to achieve this. For e.g., I can code a shell script file to populate the tools I want and source it.

```csh
setenv PATH $PATH\:/tool/verilator/v5.016/bin
```

However, this approach does not allow me to revert, or switch to another version in the *same* shell. Meaning, I need to invoke another shell and source another shell script file to get it setup to another version. Imagine if I need to setup 10 tools, I need to source 10 different shell script files. And anytime I wish to change to a tool, I need to redo this again. This approach doesn't seem to make my life any easier.

While trying to install the latest version of Verilator, I read through the documentation and I noticed this:

> Note after installing (see Installation), you need to add the path to the bin directory to your PATH. Or, if you use modulecmd, you’ll want a module file like the following:
```module
set install_root /CAD_DISK/verilator/{version-number-used-above}
unsetenv VERILATOR_ROOT
prepend-path PATH $install_root/bin
prepend-path MANPATH $install_root/man
prepend-path PKG_CONFIG_PATH $install_root/share/pkgconfig
```

What is modulecmd? A little research into this, and I found what I want. Modulecmd is basically a 
