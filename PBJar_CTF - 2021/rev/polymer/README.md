# polymer

**Author:** AOx0 :: Alejandro

This level was as easy as using strings and grep the result for flags.
So I tried:

```
strings polymer|grep 'flag'
```

![](https://i.imgur.com/jFDKU2i.png)

But there are lots of flags. So I'll just grep for the one flag (hopefully) that does not contain `n`as the first character after `{`

```
strings polymer|grep 'flag{[^n]'
```

![](https://i.imgur.com/h5hJNLD.png)

Got it