# navtag
Path shortcut manager CLI for Unix-like systems.

## Features
- List, add and remove shortcuts
- Resolve shortcut labels to their path
- Resolve paths including shortcut labels to their total path
- Shell extension: shortcut support for the majority of built-in commands
- Path / label tab-completion for extended commands

## Quickstart
1. Clone this repository to any destination
2. Enter the cloned repo and run:
```shell
./install.sh
```
3. If you want to add the extension commands to your shell, follow the instructions generated by install.sh
## Useage
From here on, `$mfp` is equivalent to the path to the shortcut file.
### List shortcuts:
```shell
navtag $mfp -l
```
### Add shortcut:
```shell
navtag $mfp -a <label> <path>
```
### Remove shortcut:
```shell
navtag $mfp -d <label>
```
### Translate shortcut labels:
```shell
navtag $mfp -t [label]
```
## Shell extension
The following commands are implemented in commands.sh, using `navtag`.
They shall be used for managing and manipulating the shortcuts.
This is a summary on the usage of every command:
- `marks`: list all shortcuts
- `mark <label> [path]`: create a shortcut for given the optional path and label. The default path is the current working directory
- `unmark <label>`: remove shortcut with given label

The following list are all implemented built-in commands which support shortcuts:
- cd
- cp
- mv
- mc
- mkdir
- touch

## Examples:
Here are some small examples given a file structure and shortcuts like below:
```shell
.
├── dir1
│   └── dir1.1
│       └── file1.txt
├── dir2
│   └── file2.txt
└── file3.txt
```
```shell
$ marks
Mark file: /some/path/file.txt
LABEL : PATH
------------
d11 : dir1/dir1.1
d2 : dir2
```
### Add new shortcut (for current directory)
```shell
mark my_shortcut
```
### Enter dir2
```shell
cd d2
```
or
```shell
cd d2/
```
### Move file1.txt to dir2
```shell
mv d11/file1.txt d2/.
```
### Copy file3.txt to dir1.1 as file4.txt
```shell
cp file3.txt d11/file4.txt
```
