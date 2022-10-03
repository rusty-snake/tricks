---
layout: post
title:  "Caesar cipher in the terminal"
author: "rusty-snake"
#tags:
---

[Caesar cipher](https://en.wikipedia.org/wiki/Caesar_cipher):

> In cryptography, a Caesar cipher, also known as Caesar's cipher, the shift cipher, Caesar's code
> or Caesar shift, is one of the simplest and most widely known encryption techniques. It is a type
> of substitution cipher in which each letter in the plaintext is replaced by a letter some fixed
> number of positions down the alphabet. For example, with a left shift of 3, D would be replaced
> by A, E would become B, and so on. The method is named after Julius Caesar, who used it in his
> private correspondence.

You can easily use it in the terminal with the help of `tr`.

Obfuscate `Hello World`:

~~~ console
$ echo "Hello World" | tr A-Za-z W-ZA-Vw-za-v
Dahhk Sknhz
~~~

And undo it by flipping the arguments of `tr`:

~~~ console
$ echo "Dahhk Sknhz" | tr W-ZA-Vw-za-v A-Za-z
Hello World
~~~

If you also want to obfuscate capitalization, you need to mix it a bit more:

~~~ console
$ echo "Hello World" | tr A-Za-z w-zA-Ma-vN-Z
DnuuO fORum
~~~

Of course this is not a cryptographically secure encryption but it is a nice
gimmick to obfuscate the content of texts.

---

Did you know that you can use `echo "Hello World" | rev` to obfuscate text in
your terminal?
