# Checking the ssh connection:
* `echo $SSH_CONNECTION`

# Configure the SSH Client
* `hostname`: print the hostname
* `ssh`:
    * `ssh 192.168.56.105`: ssh to remote machine with ip `192.168.56.105` and with the user as current `hostname`
        * `Public key` must be accepted, so it can encrypt the `ssh` connection with it
        * It'll copy the `pub_key` to the `.ssh/known_hosts` directory
* **Add aliases for remote ssh hosts**
    * aliases are stored in `.ssh/config` file
    * Example: You can access `server1` as the `root` user by just `ssh server1`
    ```
    Host server1
      Hostname 192.168.103.99
      Port 22
      User root
    ```

# Using Key Based Authentication
* You can generate ssh private key by running `ssh-key -t rsa`
* Authenticate certain ssh host, we copy the public key to the target user of the server
    * `ssh-copy-id -i id_rsa.pub server1`
* We can pre-authenticate to the private key by:
    * `ssh-agent`
    * `ssh-add`: add the cached credentials to the `ssh-agent`. When run without arguments, it adds the files `~/.ssh/*`
    * On server you can change `PermitRootLogin` in `/etc/ssh/sshd_config` to `without-password` to only allow root logins if they're pre-authenticated

# Secure Copy Protocol (SCP)
* You can copy files securely through machines via SCP
    * From host to server1: `scp /etc/hosts server1:/tmp`
    * From server2 to host: `scp server2:/tmp/hosts /tmp`
