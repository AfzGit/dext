
# Table of Contents

1.  [About](#org031b3e6)
2.  [Requirements](#org45798b8)
3.  [Installation](#orge7ed034)
4.  [Usage](#orgfdf64c7)
5.  [Examples](#orga6fae74)



<a id="org031b3e6"></a>

# About

Dext (Directories by Extensions) is a script that moves (or copies) files of the same extensions into a folder


<a id="org45798b8"></a>

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


<a id="orge7ed034"></a>

# Installation

-   Using curl

    curl https://raw.githubusercontent.com/AfzGit/dext/main/dext --output dext
    chmod a+x dext
    sudo mv dext /usr/bin/


<a id="orgfdf64c7"></a>

# Usage

-   USAGE:
    -   dext [OPTIONS]
    -   dext [OPTIONS] DIRECTORY

-   OPTIONS:
    -   -h    Show this help message
    -   -u    Show total Unique extension
    -   -v    Verbose mode
    -   -i    Interactive mode
    -   -c    Copy mode (default is Move)
    -   -d    Dry run
    -   -f    Force move/copy files (no prompts)


<a id="orga6fae74"></a>

# Examples

dext ~/Downloads/           # Move
dext -i -v -c ~/Downloads/  # Interactive and verbose copy
dext -f ~/Downloads/        # Force move
dext -f -c ~/Downloads/     # Force copy
dext -d ~/Downloads/        # Dry run

