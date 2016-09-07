# Ansible Role: Pure-FTPd

Installs Pure-FTPd on Debian/Ubuntu Linux.

This role installs and configures the latest version of Pure-FTPd from the Pure-FTPd via apt (on Debian-based systems).  You will likely need to do extra setup work after this role has installed Pure-FTPd.

## Requirements

None.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    ftp_root: "/var/ftp"

A directory path at which to scope the FTP server access.

    ftp_user: "ftp"

The system-level user that the FTP daemon performs operations under.  This user is setup without login permissions (can't ssh into system) but owns all of the files uploaded via the FTP server.

    ftp_group: "ftp-sys-group"

The system-level group that the FTP daemon performs operations under.  This is the group assigned to all files uploaded via the FTP server.

    virtual_users:
      - name: "ftp"
        dir: "/var/ftp" # optional

A list of user definitions virtual FTP users. If left empty, defaults to a single user with the username `ftp` and password `ftp`.  `name` is a required filed.  `dir` is optional and defaults to the value of `ftp_root`.

## Dependencies

None.

## Example Playbook

    - hosts: server
      roles:
        - { role: robgmills.pure-ftpd }

## License

MIT / BSD

## Author Information

This role was created in 2016 by [Rob Mills](https://robgmills.com/).
