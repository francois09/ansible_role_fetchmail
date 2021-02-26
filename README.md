Fetchmail
=========

Simple role to install and configure fetchmail

Requirements
------------

No requirements

Role Variables
--------------

By default the role didn't install fetchmail nor configure

* `fetchmail__install` Install or not (Default: False)
* `fetchmail__configure` Configure or not (Default: False)
* `fetchmail__fetchlist`
   * `server` FQDN of mail server (eg. mail.free.fr)
   * `protocol` used protocol (eg. POP3)
   * `user` mail server username (eg. johndoe@free.fr)
   * `password` mail server pasword (eg. mys3cr3tp4ssw0rd)
   * `local_user` local username (eg. johndoe)
   * `ssl_fingerprint` server fingerprint. See below to get it
   * `expunge` number of mail red before a "commit" is done

Dependencies
------------

None

Example Playbooks
-----------------

Play with:

```
- hosts: all
  name: Setup Fetchmail
  roles:
    - role: fetchmail
```

`expunge` can be used in case of slow or non stable internet link. For example, if you set `expunge 10`, mail is flushed every 10 mails read.

`ssl_fingerprint` can be obtained with following commands:

```
export SERVER=<your.mail.server>
export PORT=995
openssl s_client -connect $SERVER:$PORT -showcerts | openssl x509 -fingerprint -noout -md5
```

License
-------

GPLv3

Author Information
------------------

François TOURDE


