SSH keys allow users (both human and machine) to access resources without the need for a password. GitLab supports RSA, DSA, ECDSA, and ED25519 keys and, by default, allows the use of all of these key formats.  However, DSA keys have recently discovered security vulnerabilities and should not be used.  An administrator can restrict the types of keys that are permitted and in the current environment, the only SSH keys that can be used are RSA keys.

RSA keys are certainly the most common SSH key format.  It is possible to increase the security of your keys by generating a larger key by passing the -b flag with a bit number larger than the 2040 default.  Also, the old, standard encoding format for RSA keys has been found to be insecure.  Passing the -o flag when creating your new key will encrypt your private key with a new more secure format.

*Generating a new SSH keypair*

First, open a terminal on Linux or macOS or on Windows you can use Git Bash/WSL. In the examples below the -C flag is not required. However, it adds a comment that will help you tell keys apart if you employ several different ones.

Now, to generate a new RSA key pair, run:

*NOTE: The following command will overwrite any id_rsa and id_rsa.pub file that may already exist in ${HOME}/.ssh/*

``` bash
ssh-keygen -o -t rsa -b 4096 -C "myemail@mymailservice.com"
```

Now you will be prompted to define where you wish to save your SSH key pair.  If you do not currently have a key pair, you can just hit return/enter and the default path will let your SSH agent find and use your key without further configuration.

You will then be prompted to provide a password, and while it is best practice to use one, it is not required, and pressing enter twice will skip this.

You can later add or change a password for your key pair with:

```bash
ssh-keygen -p -o -f <keyname>
```

Further details on the use of RSA and other  SSH keys formats on GitLab can be found here:

```
https://docs.gitlab.com/ee/ssh/#types-of-ssh-keys-and-which-to-choose
```
