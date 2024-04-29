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


### Gpg Agent
Description. gpg-agent is **a daemon to manage secret (private) keys independently from any protocol**. It is used as a backend for gpg and gpgsm as well as for a couple of other utilities. This code should only be run once per user session to initially fire up the agent.

```shell
$ gpg-agent --deamon
$ gpg-agent         

gpg-agent[4843]: gpg-agent running and available
```

### To add Default configuration to ask for password:

Open gpg-agent.conf in nano
```shell
~ nano ~/.gnupg/gpg-agent.conf

```

Add the following line : 
```nano
 default-cache-ttl 34560000 
 max-cache-ttl 34560000
 ```
 
Then reload gpg-agent

```shell
 ~ gpg-connect-agent reloadagent /bye 

OK
```


## Documentations 

[GitHub doc](https://docs.github.com/fr/authentication/managing-commit-signature-verification/generating-a-new-gpg-key)
[Oh no, I forgot my PGP private key’s passphrase](https://estebansastre.com/oh-no-i-forgot-my-private-keys-passphrase/)
[Gpg how to revoke a key or user id](https://gpgtools.tenderapp.com/kb/gpg-keychain-faq/how-to-revoke-a-key-or-user-id#forgotten-password)


### Revoke Certificate

Since 2015 a revocation certificate is automatically created during key creation. Should you ever loose access to your secret key or forget your password, you can still revoke your key.

The revocation certificates are stored on your mac:

1. open new finder window  
2. press SHIFT + CMD + G (**⇧⌘G**)  
3. paste `~/.gnupg/openpgp-revocs.d` into the field

This folder holds all revocation certificates which have been created. The file name consists of the last 16 digits from your fingerprint allowing you to learn which cert is for which key.

==**Important:**== We recommended, to create a backup of all revocation certificates and store that in a secure location.

### Store keychain in mac 
https://gist.github.com/koshatul/2427643668d4e89c0086f297f9ed2130
