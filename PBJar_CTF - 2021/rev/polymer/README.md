# polymer

**Author:** AOx0 :: Alejandro

This level was as easy as using strings and grep the result for flags.
So I tried:

```
strings polymer|grep 'flag'
```

![](https://i.imgur.com/jFDKU2i.png)

But there are lots of flags. So I'll just look for the one flag (hopefully) that does not contain `n`as the first character after `{`

```
strings polymer|grep 'flag{[^n]'
```

![](https://i.imgur.com/h5hJNLD.png)

Got it



### Deep explanation

`strings` - A command that prints everything printable/readable by humans that a file contains

`polymer` - the name of the file

`|` - pipe. Redirects the output of the strings command to grep so I can filter it out

`grep` - command to search for patterns

`'flag{[^n]' ` - Look for strings containing `flag{` + Any character but `n` with the negation operator `^`