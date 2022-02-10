# rough_file_set_operation

## Description
This script performs set operations on two files passed as arguments.
The lines in each file are used as elements of the set.
Duplicate items will be deleted in the output.

rough_file_set_operation is installed as a `rfso` command.

## Install

```
make
    install      install tgen on PREFIX directory.
    uninstall    uninstall tgen from PREFIX directory.
```

## Usage

```
Usage: rfso [OPTION]...

[OPTION]
    -m <mode>
         Specifies the mode of set operation. <"difference" or "intersection">
    -a <filepath> or ':stdin'
         Specifies the file path. Left side of set operation.
         If ':stdin' is specified, the value of the standard input will be reflected.
    -b <filepath> or ':stdin'
         Specifies the file path. Right side of set operation.
         If ':stdin' is specified, the value of the standard input will be reflected.
    -h
         Show this message
```

## Example
* sample_a.txt
```
aaaaaa
bbbbbb
bbbbbb
cccccc
dddddd
eeeeee
eeeeee
eeeeee
```

* sample_b.txt
```
aaaaaa
eeeeee
eeeeee
eeeeee
ffffff
```

* sample_c.txt
```
bbbbbb
cccccc
gggggg
```

### Command
#### Intersection
```bash
$ rfso -m 'intersection' -a sample_a.txt -b sample_b.txt

# aaaaaa
# eeeeee
```

```bash
$ rfso -m 'intersection' -a sample_b.txt -b sample_a.txt

# aaaaaa
# eeeeee
```

#### Difference
```bash
$ rfso -m 'difference' -a sample_a.txt -b sample_b.txt

# bbbbbb
# cccccc
# dddddd
```

```bash
$ rfso -m 'difference' -a sample_b.txt -b sample_a.txt

# ffffff
```

#### Pipe mode
```bash
$ rfso -m 'difference' -a sample_a.txt -b sample_b.txt | rfso -m 'intersection' -a ':stdin' -b sample_c.txt

#bbbbbb
#cccccc
```

```bash
$ rfso -m 'difference' -a sample_a.txt -b sample_b.txt | rfso -m 'difference' -a ':stdin' -b sample_c.txt

#dddddd
```

```bash
$ rfso -m 'difference' -a sample_a.txt -b sample_b.txt | rfso -m 'intersection' -a sample_c.txt -b ':stdin'

#bbbbbb
#cccccc
```

```bash
$ rfso -m 'difference' -a sample_a.txt -b sample_b.txt | rfso -m 'difference' -a sample_c.txt -b ':stdin'

#gggggg
```
