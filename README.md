# WAD challenge

**Well done!** If you are here it means you have passed stage 0 of the challenge. *NOTE: If you have landed here before completing stage 0, please go back to [http://wad-challenge.s3-website.eu-central-1.amazonaws.com/](http://wad-challenge.s3-website.eu-central-1.amazonaws.com/). You will need some info contained there*...

## Introduction
The goal of the challenge is **decrypt** the following text:
```
&22.UJJ W$!U!MU "#UNOUO MUR|YUN KNKJ5', ,#0JW!- "#YJW7-
30H,|+# Y
```
Decrypting it you will access the final stage of the challenge and light up the IoT device.

You can use **any programming language** to complete this stage.

## The algorithm
The algorithm used to encyrpt the message was a block cipher with the following rules:

1. The alphabet is restricted between ascii codes 32 ("`space`") and 125 ("`}`") included. If you are not familiar with ASCII give a look at [http://www.asciitable.com/](http://www.asciitable.com/) and [https://en.wikipedia.org/wiki/ASCII](https://en.wikipedia.org/wiki/ASCII)
2. The algorithm encryption and decryption processes expect a key in the form of a string and a message (also a string). In pseudocode:

```java
string encrypt(string key, string message)
{
    // body
}

string decrypt(string key, string message)
{
    // body
}
```

Here are the *encryption steps*:
- The message is **split in chunks of length** `key.size`
- Each chunk is **reversed** (eg. `asdfg` --> `gfdsa`)
- For each chunk:
    - Each character is shifted upwards by `n` positions where `n` is the sum of the ASCII decimal codes of the encryption key
    - If the selected code exceeds the alphabet's length it must be reassigned from the alphabet start (have you have ever heard of modulo operator? 🤓)
- After the operation each chunk has to be **reversed back again**
- Every `key.size` chunks, a new line is added in the output

The given encrypted message was generated following the above steps. Now it is your time to write the **decryption algorithm** to reverse the process!

## Something missing?

Do you still need the encryption/decryption key? Have you deeply inspected the first stage's code? 🤓

## Bad news: that was not all...

To complete the challenge you will need a **code** to send to the IoT device. That code will be the **encryption key itself encrypted with the algorithm above**. So you have to also implement the encryption part to succeed.

```java
String code = encrypt(key, key);
```

Also review the **arp protocol**. Trust me, you will find it useful 😉
### Questions?

Feel free to ask any question, but do not expect always an answer 😉
