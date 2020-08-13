---
title: ssh
parent: Foundations
nav_order: 6
---

# ssh
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Installing `ssh`

SSH is essential to accessing remote machines. We will be doing that several times a day, so let's setup things properly.

```sh
which ssh
  /usr/bin/ssh

ls -lah ~/.ssh
  ls: /Users/<USER>/.ssh: No such file or directory

mkdir ~/.ssh

touch ~/.ssh/config
```

Copy the following to `~/.ssh/config`:

```yaml
# cluster: master node
Host cluster-master
    Hostname <IP_ADDRESS>
    User <USER_NAME>
    Port <PORT>

# cluster: internal node (goes through cluster-master)
Host cluster-node
    Hostname <NODE_NAME>
    ProxyJump <USER_NAME>@<IP_ADDRESS>:<PORT>
    User <USER_NAME>

# your typical aws ec2 instance
Host aws-ec2-instance
    Hostname <EC2_IP_ADDRESS|EC2_HOSTNAME>
    IdentityFile ~/.ssh/<PEM_FILENAME>.pem
    User ec2-user
    # useful if running jupyter lab or notebook remotely
    # jupyter notebook runs on port 8888 remotely but will be accessible locally at 9999
    LocalForward 9999 localhost:8888
    # useful if running a simple webserver remotely
    # python3 -m http.server runs on port 8000 remotely but will be accessible locally at 9999
    LocalForward 9000 localhost:8000

# LocalForward above is equivalent to -L localhost:9999:localhost:8888
# https://unix.stackexchange.com/questions/433923/ssh-port-forwarding-via-jump-host-ssh-config-files-and-only-ssh-targethost
```

Now we can type `ssh aws-ec2-instance` or `ssh cluster-master` and have everything ready out of the box.

## Existing keys

You may also want to copy private/public keys that you have previously generated. They are pairs of files like `aws-key.pem`/`aws-key.pub` and `id_rsa`/`id_rsa.pub` that you may have in your backups. See [https://help.github.com/en/github/authenticating-to-github/checking-for-existing-ssh-keys](https://help.github.com/en/github/authenticating-to-github/checking-for-existing-ssh-keys).

```sh
tree .ssh
  .ssh
  ├── aws-key.pem
  ├── aws-key.pub
  ├── config
  ├── id_rsa
  ├── id_rsa.pub
  └── known_hosts

  0 directories, 6 files

```

<mark>While convenient, please note that the reuse of old keys can be risky!</mark> 

Old keys could have been leaked in your backup, and their bit size could be smaller than the best practice nowadays. In terms of bit size, `4096` is probably much better than `2048` in the context of a macOS laptop/desktop. For more information, read: https://danielpocock.com/rsa-key-sizes-2048-or-4096-bits/.

```sh
# ref: https://serverfault.com/questions/325467/i-have-a-keypair-how-do-i-determine-the-key-length
/usr/local/opt/openssl@1.1/bin/openssl rsa -in .ssh/<KEY_FILE>.pem -text -noout | grep "RSA"
  RSA Private-Key: (2048 bit, 2 primes)

# ref: https://security.stackexchange.com/questions/42268/how-do-i-get-the-rsa-bit-length-with-the-pubkey-and-openssl
ssh-keygen -lf .ssh/<KEY_FILE>.pub
  2048 SHA256:<FINGERPRINT> no comment (RSA)

ssh-keygen -lf .ssh/<KEY_FILE>
  2048 SHA256:<FINGERPRINT> <COMMENTS> (RSA)

ssh-keygen -lf .ssh/<KEY_FILE>.pub
  2048 SHA256:<FINGERPRINT> <COMMENTS> (RSA)
```

## Generating new keys

Simply follow the instructions from [https://help.github.com/en/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent](https://help.github.com/en/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent):

```sh
# -t is type, -b is bit size, -C is comment
ssh-keygen -t rsa -b 4096 -C "<USER> @ <MACHINE_NAME>"
```

During the `ssh-keygen` steps above, please create a passphrase:

> With SSH keys, if someone gains access to your computer, they also gain access to every system that uses that key. To add an extra layer of security, you can add a passphrase to your SSH key.

For more info, see [https://help.github.com/en/github/authenticating-to-github/working-with-ssh-key-passphrases](https://help.github.com/en/github/authenticating-to-github/working-with-ssh-key-passphrases).

## Using `ssh-agent` and `Keychain Access` to store your passphrase

If you don't want to reenter your passphrase every time you use your SSH key, you can add your key to the SSH agent, which manages your SSH keys and remembers your passphrase.

When adding your SSH key to the agent, use the default macOS `ssh-add` command, and not an application installed by macports, `brew`, or some other external source.

```sh
# start the ssh-agent in the background
eval "$(ssh-agent -s)"
  > Agent pid 59566

ssh-add -K ~/.ssh/id_rsa
```

Also, make sure to add the top of `.ssh/config`:

```yaml
# sensible defaults for passphrase usage
# (you can leave them comment out if you decided not to use a passphrase)
Host *
  AddKeysToAgent yes
  UseKeychain yes
  IdentityFile ~/.ssh/id_rsa

# [...]
```

## Appending your public key to the `authorized_keys` file on a remote server

First, upload (using `scp`) the `<KEY_FILE>.pub` file to your remote server. 

Then use `cat` to append its content to `~/.ssh/authorized_keys`:

```sh
cd ~/.ssh

ls | grep authorized_keys
  authorized_keys

cat <KEY_FILE>.pub >> authorized_keys

cat authorized_keys
  [...]
  ssh-rsa <FINGERPRINT> <COMMENTS>
```

More information on this can be found at [https://wiki.qnap.com/wiki/SSH:_How_To_Set_Up_Authorized_Keys](https://wiki.qnap.com/wiki/SSH:_How_To_Set_Up_Authorized_Keys).