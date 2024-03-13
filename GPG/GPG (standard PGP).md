### Generate new key

```shell
$ gpg --full-gen-key
```

```shell
gpg (GnuPG) 2.4.3; Copyright (C) 2023 g10 Code GmbH
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Please select what kind of key you want:
   (1) RSA and RSA
   (2) DSA and Elgamal
   (3) DSA (sign only)
   (4) RSA (sign only)
   (9) ECC (sign and encrypt) *default*
  (10) ECC (sign only)
  (14) Existing key from card
Your selection? 1
RSA keys may be between 1024 and 4096 bits long.
What keysize do you want? (3072) 4096
Requested keysize is 4096 bits
Please specify how long the key should be valid.
         0 = key does not expire
      <n>  = key expires in n days
      <n>w = key expires in n weeks
      <n>m = key expires in n months
      <n>y = key expires in n years
Key is valid for? (0) 6m
Key expires at Sun Sep  8 17:34:21 2024 CEST
Is this correct? (y/N) y
```

### Find Keys

```shell
$ gpg --list-keys
```

### To add an expire date to gpg key
Key for your email
```shell
$ gpg --edit-key <PUBLIC KEY>
$ expire
```
command help to display helper


### Error message with gpg
For this message error
```shell
data_pass git:(feature/API-2419/redirection-homepage-internaute-for-authorizationdefinition) ✗ git commit
error: gpg failed to sign the data:
[GNUPG:] KEY_CONSIDERED <PUBLIC KEY> 2
[GNUPG:] BEGIN_SIGNING H8
[GNUPG:] PINENTRY_LAUNCHED 16448 curses 1.2.1 - xterm-256color - - 501/20 0
gpg: signing failed: Inappropriate ioctl for device
[GNUPG:] FAILURE sign 83918950
gpg: signing failed: Inappropriate ioctl for device

fatal: failed to write commit object
```

enter this cmd 
```shell
$ export GPG_TTY=$(tty)
```


[GitHub doc](https://docs.github.com/fr/authentication/managing-commit-signature-verification/generating-a-new-gpg-key)
