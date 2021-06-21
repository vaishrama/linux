### Step 1: Ensure/Double Check Permissions on Sensitive Files

1. Permissions on `/etc/shadow` should allow only `root` read and write access.

    - Command to inspect permissions: sudo ls -l shadow  

    - Command to set permissions (if needed): sudo chmod g-r shadow

2. Permissions on `/etc/gshadow` should allow only `root` read and write access.

    - Command to inspect permissions: sudo ls -l gshadow    

    - Command to set permissions (if needed): sudo chmod g-r gshadow

3. Permissions on `/etc/group` should allow `root` read and write access, and allow everyone else read access only.

    - Command to inspect permissions:sudo ls -l group

    - Command to set permissions (if needed):none

4. Permissions on `/etc/passwd` should allow `root` read and write access, and allow everyone else read access only.

    - Command to inspect permissions:sudo ls -l passwd

    - Command to set permissions (if needed):none

### Step 2: Create User Accounts

1. Add user accounts for `sam`, `joe`, `amy`, `sara`, and `admin`.

    - Command to add each user account (include all five users):
    sudo adduser joe
    sudo adduser amy
    sudo adduser sara
    sudo adduser admin
    sudo adduser sam


2. Ensure that only the `admin` has general sudo access.

    - Command to add `admin` to the `sudo` group: sudo usermod -G sudo admin

### Step 3: Create User Group and Collaborative Folder

1. Add an `engineers` group to the system.

    - Command to add group:addgroup engineers

2. Add users `sam`, `joe`, `amy`, and `sara` to the managed group.

    - Command to add users to `engineers` group (include all four users):
    sudo usermod -a -G engineers sam
    sudo usermod -a -G engineers joe
    sudo usermod -a -G engineers amy
    sudo usermod -a -G engineers sara
 
3. Create a shared folder for this group at `/home/engineers`.

    - Command to create the shared folder:sudo mkdir ./engineers

4. Change ownership on the new engineers' shared folder to the `engineers` group.

    - Command to change ownership of engineer's shared folder to engineer group:
    sudo chown :engineers engineers

### Step 4: Lynis Auditing

1. Command to install Lynis:sudo apt install lynis

2. Command to see documentation and instructions: lynis audit system

3. Command to run an audit: sudo lynis audit system

### Step 5:
1. Command to install chkrootkit: sudo apt install chkrootkit

2. Command to see documentation and instructions: sudo chkrootkit

3. Command to run expert mode: sudo chkrootkit -x
