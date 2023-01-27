## _Objective_
Quick data analysis of a text file.

    Show file's size in bytes?
    Count words, chars, lines too.
    
```
$ file=/tmp/data
$ wc $file
$ wc -m $file #(chars)
$ wc -l $file
$ wc -w $file
$ wc -L $file #(length of longest line)
$ wc -c $file

$ wc $file1 $file2
# outputs summed-up values
```
