### _ Basic Text Handling _

The `$ diff ` command == tells me ==
* what changes need to be made for the _1st file to be like 2nd one_.
* line1# a/c/d line2# of two files, where a = append, c = change and d = delete.
* > and < shows necessary changes to be made.

```
diff --color=always stationery1 stationery2

diff -y stationery* # side by side
diff -c #
diff -u #

# to just query difference
diff -q stationery*
```

* To ignore case-sensitivity,

```
cat stationery2 | tr \[:lower:] \[:upper:] > stationery2_upper

diff stationery2 stationery2_upper
# all different

diff -i stationery2 stationery2_upper
# blank, why? Insensitive comparision
```

* To ignore blank lines,

```
diff -B -s stationery2 stationery3
```
and also see if they are identical --

**NOTE** _-s_ & _-q_ report comparision result: identical or different files.

* To ignore whitespaces,

```
diff -w -s stationery1 stationery1_whitespaces
```
and also see if they are identical --

* To compare two directory's contents:

```
diff -r /bin /sbin | less
```

Also
```
diff -r /bin /sbin | grep -i "only in /bin" | cut -d':' -f2 | less
```
