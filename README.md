
# Table of Contents

1.  [About](#org9b8edf8)
2.  [Requirements](#orgf6f54bf)
3.  [Installation](#org88723e8)
4.  [Usage](#org3df9450)
5.  [Examples](#orgdfb8c60)



<a id="org9b8edf8"></a>

# About

Dext (Directories by Extensions) is a script that moves (or copies) files of the same extensions into a folder


<a id="orgf6f54bf"></a>

# Requirements

-   curl
    -   Debian
        -   `sudo apt install curl`
    -   Arch
        -   `sudo pacman -S curl`
-   sed
    -   Debian
        -   `sudo apt install sed`
    -   Arch
        -   `sudo pacman -S sed`


<a id="org88723e8"></a>

# Installation

-   Using curl

    curl https://raw.githubusercontent.com/AfzGit/dext/main/dext --output dext
    chmod a+x dext
    sudo mv dext /usr/bin/


<a id="org3df9450"></a>

# Usage

USAGE:
   dext [OPTIONS]
   dext [OPTIONS] DIRECTORY

OPTIONS:
   -h
       Show this help message
   -u
       Show total Unique extension
   -v
       Verbose mode
   -i
       Interactive mode
   -c
       Copy mode (default is Move)
   -d
       Dry run
   -f
       Force move/copy files (no prompts)


<a id="orgdfb8c60"></a>

# Examples

dext ~/Downloads/           # Move
dext -i -v -c ~/Downloads/  # Interactive and verbose copy
dext -f ~/Downloads/        # Force move
dext -f -c ~/Downloads/     # Force copy
dext -d ~/Downloads/        # Dry run

