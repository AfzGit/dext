
# Table of Contents

1.  [About](#org673d72e)
2.  [Requirements](#orge32e026)
3.  [Installation](#orgec4e642)
4.  [Usage](#orge79668d)
5.  [Examples](#org3486f9e)



<a id="org673d72e"></a>

# About

Dext (Directories by Extensions) is a script that moves (or copies) files of the same extension into a folder.

The main goal of this script is to make sense out of large number of messy and unorganized files by sorting them (according to their file extensions) in folders.

Dext moves files by default unless copy option is provided (-c).


<a id="orge32e026"></a>

# Requirements

-   curl (only for installation)
    -   Debian
        -   `sudo apt install curl`
    -   Arch
        -   `sudo pacman -S curl`
-   sed
    -   Debian
        -   `sudo apt install sed`
    -   Arch
        -   `sudo pacman -S sed`


<a id="orgec4e642"></a>

# Installation

-   Using curl

``` sh
    curl https://raw.githubusercontent.com/AfzGit/dext/main/dext --output dext
    chmod a+x dext
    sudo mv dext /usr/bin/

```

<a id="orge79668d"></a>

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


<a id="org3486f9e"></a>

# Examples

-   dext ~/Downloads/
    - Move files into directories based on file extensions
-   dext -i -v -c ~/Downloads/
    - Enable Interactive and Verbose Copy
-   dext -f ~/Downloads/
    - Force move
-   dext -f -c ~/Downloads/
    - Force copy
-   dext -d ~/Downloads/
    - Dry run

Note: I am not responsible for any damages you encounter using this script
