# rough_file_set_operation

## Description
This script performs set operations on two files passed as arguments.
The lines in each file are used as elements of the set.

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
    -m <mode>        Specifies the mode of set operation. <"difference" or "intersection">
    -a <filepath>    Specifies the file path. Left side of set operation.
    -b <filepath>    Specifies the file path. Right side of set operation.
    -h               Show this message
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


