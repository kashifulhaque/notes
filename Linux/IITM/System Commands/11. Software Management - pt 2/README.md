# Software Management - pt. 2

Date: January 16, 2022
Lecture #: 2
Lecture URL: https://youtu.be/ctn_s7SDTV0
Notion URL: https://21f1003586.notion.site/Software-Management-b0cd46d7790f479aacf4378fbe9611cf
Type: 📒 Lecture
Week #: 4

Only sudoers can install/upgrade/remove packages → `/etc/sudoers`

We can view the `sudoers` file by typing `sudo cat /etc/sudoers`

This will ask for the user password and depending on the `su` status of the user, it will either display the file or show an error like `user is not in the sudoers file. This incident will be reported.`

### How can a superuser find out the failed `sudo` attempt by non-su?

Go to `/var/log`

Look for `auth.log` file, these events are reported in this file

### Sources for packages

Location: `/etc/apt`

File → `sources.list` → Contains repo URLs for Ubuntu pkgs

Folder → `sources.list.d` → Contains repo URLs for 3rd party pkgs

### To get updates

`sudo apt-get update`

### To upgrade the pkgs (if an upgrade is available)

`sudo apt-get upgrade`

You can pass the `-y` flag to not get bugged by the Y/N prompt

### To remove older, usually obsolete pkgs

`sudo apt autoremove`

### To remove a specific pkg

`sudo apt-get remove <pkg-name>`

### Installing/Updating

- Install a package
    - `apt-get install <pkg-name>`
- Reinstall a package
    - `apt-get reinstall <pkg-name>`

### Removing/Cleaning up

- Remove packages that were automatically installed to satisfy a dependency and not needed
    - `apt-get autoremove`
- Clean local repository of retrieved package files
    - `apt-get clean`
- Purge package files from the system
    - `apt-get purge package`

### Package management in Ubuntu using `dpkg`

Text info regarding packages found at `/var/lib/dpkg`

Files: `arch, available, status`

Folder: `info`

### Using `dpkg`

- List all the packages whose names match the pattern
    - `dpkg -l pattern`
- List installed files that came from packages
    - `dpkg -L package`
- Report the status of packages
    - `dpkg -s package`
- Search installed packages for a file
    - `dpkg -S pattern`
- A tool to query the `dpkg` database
    - `dpkg-query`
    - Example usage
        - `dpkg-query -W -f=’${Section} ${binary:Package}\n’`

### Installing a `deb` package

`dpkg -i filename.deb`

By default, use package management pointing to a reliable repository

Uninstalling packages using `dpkg` is ***NOT*** recommended