> ⚠️  ALERT: For more feature rich `dext` with cross-platform support, sorting by time, size, and extension, recursive directory sorting, please have a look at the newer: [files-sort-py](https://github.com/AfzGit/Files-Sort-py)

# Dext

**Dext** automatically organizes files into directories based on their file extensions.

For example:

```text
Downloads/
├── image.jpg
├── video.mkv
├── document.pdf
├── photo.jpg
└── movie.mkv
````

becomes:

```text
Downloads/
├── jpg/
│   ├── image.jpg
│   └── photo.jpg
├── mkv/
│   ├── video.mkv
│   └── movie.mkv
└── pdf/
    └── document.pdf
```

Dext can either **move** or **copy** files and safely handles filename conflicts by automatically generating unique filenames.

---

## Features

* Organizes files by extension
* Move files by default
* Copy files with `-c`
* Detect unique extensions with `-u`
* Dry-run mode with `-d`
* Verbose output with `-v`
* Force mode with `-f`
* Safely handles filename collisions
* Interactive collision handling
* Supports filenames containing spaces and special characters

---

## Installation

Just grab `dext` file from the respository, make it executable, and store it in your `$PATH`

### Using `curl`

```bash
curl https://raw.githubusercontent.com/AfzGit/dext/main/dext --output dext
chmod +x dext
sudo mv dext /usr/local/bin/
```

### Using `git` 

Clone the repository:

```bash
git clone https://github.com/AfzGit/dext.git
chmod +x dext/dext
sudo mv dext/dext /usr/local/bin/
rm -r -f dext/ # Remove cloned repository
```

---

# Usage

```text
dext [OPTIONS]
dext [OPTIONS] DIRECTORY
```

If no directory is specified, Dext operates on the current directory.

### Examples

Organize the current directory:

```bash
dext
```

Organize another directory:

```bash
dext ~/Downloads
```

Copy instead of move:

```bash
dext -c ~/Downloads
```

Show what Dext would organize without changing anything:

```bash
dext -d ~/Downloads
```

Force the operation without confirmation:

```bash
dext -f ~/Downloads
```

List the extensions found in a directory:

```bash
dext -u ~/Downloads
```

Enable verbose output:

```bash
dext -v ~/Downloads
```

Options can be combined:

```bash
dext -v -c ~/Downloads
```

---

# Options

| Option | Description                                                                |
| ------ | -------------------------------------------------------------------------- |
| `-h`   | Show help                                                                  |
| `-u`   | Show the unique extensions found                                           |
| `-v`   | Verbose mode                                                               |
| `-c`   | Copy files instead of moving them                                          |
| `-d`   | Dry-run mode                                                               |
| `-f`   | Force operation; skip confirmations and automatically rename all conflicts |

---

# Default Behavior

Dext normally asks for confirmation before creating the extension directories:

```text
-> Make 3 directories of the above extensions? [Y/n]
```

It then asks whether the files should be moved:

```text
-> Move all files? [Y/n]
```

Pressing **Enter** accepts the default `Y`.

---

# Filename Conflicts

Dext will never intentionally overwrite an existing destination file when organizing files.

For example, if:

```text
Downloads/
├── movie.mkv
└── mkv/
    └── movie.mkv
```

Dext needs to move `movie.mkv` into the existing `mkv` directory.

Instead of overwriting the existing file, Dext generates a unique name:

```text
mkv/
├── movie.mkv
└── movie (1).mkv
```

If necessary, it continues:

```text
movie.mkv
movie (1).mkv
movie (2).mkv
movie (3).mkv
```

---

# Interactive Conflict Handling

When a filename conflict requires Dext to generate a new name, Dext asks:

```text
Rename "movie.mkv" → "movie (1).mkv"? [Y/n/a/s]
```

The options are:

| Input        | Action                                  |
| ------------ | --------------------------------------- |
| `Y` or Enter | Rename this file                        |
| `n`          | Skip this file                          |
| `a`          | Rename this and all remaining conflicts |
| `s`          | Skip this and all remaining conflicts   |

# Force Mode

Use:

```bash
dext -f
```

to run Dext without confirmation prompts.

Force mode:

* Automatically creates the required directories
* Automatically moves/copies the files
* Automatically accepts all filename conflict renames
* Does not ask interactive collision questions

For example:

```text
movie.mkv
movie.mkv
movie.mkv
```

could result in:

```text
movie.mkv
movie (1).mkv
movie (2).mkv
```

Basically: "Do the operation and never ask me anything."

---

# Dry Run

Use:

```bash
dext -d
```

to see what Dext detects without making changes.

Example:

```text
=== 3 Unique Extensions in /Downloads ===

[jpg, mkv, pdf]

[1/3] jpg
============
image.jpg
photo.jpg
============

[2/3] mkv
============
movie.mkv
episode.mkv
============

[3/3] pdf
============
document.pdf
============
```

Dext does not create directories or move/copy files in dry-run mode.

---

# Copy Mode

By default Dext **moves** files.

Use:

```bash
dext -c
```

to copy them instead.

For example:

```bash
dext -c ~/Downloads
```

leaves the original files in place while placing copies in the extension directories.

---

# Unique Extensions

Use:

```bash
dext -u
```

to display the unique extensions detected without organizing the files.

Example:

```text
=== 5 Unique Extensions in /Downloads ===
[jpg, mkv, mp3, pdf, txt]
```

---

# Verbose Mode

Use:

```bash
dext -v
```

to show the files as they are moved or copied.

For example:

```bash
dext -v ~/Downloads
```

This is particularly useful when processing a large directory.

---

# Requirements

Runs without any external dependencies on modern Linux distros.

* Bash 4.0 or newer
* Standard Unix utilities such as `cp`, `mv`, `mkdir`, and `sort`

Bash 4+ is required because Dext uses associative arrays and namerefs for safe filename tracking.

> Note: One thing I'd specifically **not** document anymore is `-i`: it has been removed because collision prompts are now part of normal Dext behavior. `-f` is the explicit way to suppress those prompts and choose **rename-all** automatically.

