---
title: "Character Sets"
date: 2021-11-02
layout: default
---


https://www.smashingmagazine.com/2012/06/all-about-unicode-utf8-character-sets/

https://www.honeybadger.io/blog/php-character-encoding-unicode-utf8-ascii/

# Character Encoding for PHP Developers: Unicode, UTF-8 and ASCII

## ASCII
7-bit encoding
lower case and upper case Latin letters, along with each numerical digit, common punctuation marks, spaces, tabs and other control characters

Using a number to represent a letter.

1001000

## The Eighth Bit
Then moved to 8-bits which allowed 246 values.
Therefore spare values 128-255 never standardised = different codepages.

Late 1990s, attempt to standadise ISO-8859-1 up to ISO-8859-16.

Code pages = character sets

```<meta charset="ISO-8859-5"> ```

## Unicode to the rescue!

The first 128 Unicode code points are the same as ASCII. The range 128-255 contains currency symbols and other common signs and accented characters (aka characters with diacritical marks), and much of it is borrowed ISO-8859-1. After 256 there are many more accented characters. After 880 it gets into Greek letters, then Cyrillic, Hebrew, Arabic, Indic scripts, and Thai. Chinese, Japanese and Korean start from 11904 with many others in between.

So — internally, modern Web browers use Unicode.

## UTF-8 To The Rescue

Browsers can use Unicode but not everything else does.
That is why we use UTF-8.

0-127 as ASCII, 192-247 as Shift keys, and 128-192 as the key to be shifted.
Any number over 127 needs two numbers.


<meta charset="UTF-8">
default_charset = "UTF-8"

mb_detect_encoding($string, 'UTF-8', true);
