# Configure the SSH Client
* `hostname`: print the hostname
* `ssh`:
    * `ssh 192.168.56.105`: ssh to remote machine with ip `192.168.56.105` and with the user as current `hostname`
        * `Public key` must be accepted, so it can encrypt the `ssh` connection with it
        * It'll copy the `pub_key` to the `.ssh/known_hosts` directory
* **Add aliases for remote ssh hosts**
    * aliases are stored in `.ssh/config` file
    * Example: You can access `du-conv-3` as the `root` user by just `ssh du-conv-3`
    ```
    Host du-conv-3
      Hostname 192.168.103.99
      Port 22
      User root
    ```