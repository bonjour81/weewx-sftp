# weewx-sftp

Generator for weewx that uploads data using sftp.  Copy everything from a
designated local directory to a remote directory, using the sftp protocol.

This generator is intended to be functionally equivalent to the FTP generator
in weewx, but using a different protocol.

The sftp protocol is not the same as the ftps protocol!  The ftps protocol
is supported by the standard FTP generator in weewx.  This generator uses sftp,
which requires the pysftp module.

Based on the FTP generator in weewx, with help from the SFTP generator
implemented by davies-barnard.

## Pre-requisites

This extension requires the `pysftp` python module.  It can be installed using
the system package manager such as `yum` or `apt`, or using `pip`.  Use the
appropriate installation method for your operating system and configuration!
For example, if you use `pip` then you can install it like this:

```
sudo pip install pysftp
```

## Installation

1) Download the generator

```
wget -O weewx-sftp.zip https://github.com/matthewwall/weewx-sftp/archive/master.zip
```

2) Install the generator

```
sudo wee_extension --install weewx-sftp.zip
```

3) Set the SFTP parameters in the weewx configuration file

```
[StdReport]
    [[SFTP]]
        skin = sftp
        user = username
        password = password
        server = host.example.com
        port = 22
        path = weewx    # upload location will be http://www.example.com/weewx
        local_root = /var/www/html/weewx
```

4) Re-start weewx

```
sudo /etc/init.d/weewx start
```
