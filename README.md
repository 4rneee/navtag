# navtag
Path shortcut manager CLI for Unix-like systems.

## Features
- List, add and remove shortcuts
- Translate shortcut labels to paths
- Translate paths including shortcut label to paths

## Quickstart
1. Clone this repository to any destination
2. Enter cloned repo and run:
```shell
./install.sh
```
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
The following list is a summary on the usage of every command:
- `marks`: list all shortcuts
- `mark <label>`: create a shortcut for current working directory with given label
- `unmark <label>`: remove shortcut with given label
- `cdx`: execute cd after translating every input path
- `mvx`: execute mv after translating every input path
- `cpx`: execute cp after translating every input path
- `mkx`: execute mkdir after translating every input path
- `mcx`: execute mkdir then cd after translating every input path

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
cdx d2
```
or
```shell
cdx d2/
```
### Move file1.txt to dir2
```shell
mvx d11/file1.txt d2/.
```
### Copy file3.txt to dir1.1 as file4.txt
```shell
cpx file3.txt d1.1/file4.txt
```
