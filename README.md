<div align="center">

## Don't let autoglobals=0 get you down


</div>

### Description

A good thing to do is to never rely on autoglobals. They might just be turned off.

For those not familiar with how autoglobals work, if you call a page say test.php?foo=bar, autoglobals allow you to access foo by using $foo, rather than using $_GET['foo']. However, if autoglobals are off, $foo will give a warning, and it's value will be empty rather than 'bar'.

This little piece of code mimics autoglobals, thus preventing you from having to rewrite entire applications because they relied on autoglobals. Note that as of PHP 4.2, autoglobals are off by default.
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Networking\.be](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/networking-be.md)
**Level**          |Beginner
**User Rating**    |3.0 (12 globes from 4 users)
**Compatibility**  |PHP 3\.0, PHP 4\.0
**Category**       |[Coding Standards](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/coding-standards__8-33.md)
**World**          |[PHP](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/php.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/networking-be-don-t-let-autoglobals-0-get-you-down__8-838/archive/master.zip)





### Source Code

```
As PHP documentation specifies, you should not rely on autoglobals, so if you are a clean programmer, you probably don't need this code.
<BR>However, those off you who decided to go for the time gain offered by autoglobals might just need this.
<P>The code makes use of <b>variable variables</b>, a feature not that many languages posses. We just loop throug each variable in $_GET and $_POST, and assign it to the correspondending $variable.
<PRE>
while(list($key,$value)= each($_POST)) {
	$tmp = $key;
	$$tmp = $value;
}
while(list($key,$value)= each($_GET)) {
	$tmp = $key;
	$$tmp = $value;
}
if (isset($test)) {
	echo "Test is set: $test";
} else {
	echo "Test not set";
}
</PRE>
<P>In order to test this example, ENABLE autoglobals on your server.
Point to the page, and set the test variable (http://yourserver/test.php?test=123).
You will see that the page will say that $test is set.
<BR>Now DISABLE autoglobals. Reload the page, and you'll see that $test is still set.
Finally, comment away the two while loops and reload the page. You will now see that $test isn't set.
<P>The best use of this is to paste the code into a seperate file, and include the file at the beginning of the page that requires its functionallity.
```

