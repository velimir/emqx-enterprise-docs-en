
.. _installation:

============
Installation
============

The *EMQ X* broker is cross-platform, it can be deployed on Linux, FreeBSD and Windows.

.. NOTE::

    It is recommended to deploy EMQ X on Linux for production environment.

.. _install_download:

Get free trial License files
----------------------------

Log in to https://emqx.io to get free trial License files

*EMQ X* Package Download
-------------------------

Each version of the EMQ X broker will release packages of CentOS, Ubuntu, Debian, openSUSE, FreeBSD, macOS, Windows platform and Docker images.

Download address: https://www.emqx.io/downloads#enterprise

.. _emqx.io: https://www.emqx.io/downloads#enterprise

CentOS
------

+ CentOS6.X
+ CentOS7.X

Install via Repository
>>>>>>>>>>>>>>>>>>>>>>>

1.  Delete the old EMQ X

    .. code-block:: console

        $ sudo yum remove emqx emqx-edge emqx-ee

2.  Install the required dependencies

    .. code-block:: console

        $ sudo yum install -y yum-utils device-mapper-persistent-data lvm2

3.  Set up a stable repository, taking the CentOS7 as an example.

    .. code-block:: console

        $ sudo yum-config-manager --add-repo https://repos.emqx.io/emqx-ee/redhat/centos/7/emqx-ee.repo

4.  Install the latest version of EMQ X

    .. code-block:: console

        $ sudo yum install emqx-ee

    .. NOTE::If prompted to accept the GPG key, please verify that the key's fingerprint matches fc84 1ba6 3775 5ca8 487b 1e3c c0b4 0946 3e64 0d53 and accept the fingerprint if it matches.


5.  Install a specific version of EMQ X

    1.  Query available version

        .. code-block:: console

            $ yum list emqx --showduplicates | sort -r

            emqx-ee.x86_64                    4.0.0-1.el7                     emqx-ee-stable

    2.  Install a specific version based on the version string in the second column, such as 3.1.0

        .. code-block:: console

            $ sudo yum install emqx-ee-4.0.0

6.  Import License file

    .. code-block:: console

        $ cp /path/to/emqx.lic /etc/emqx/emqx.lic

7.  Start EMQ X

    +   Directly start

        .. code-block:: console

                $ emqx start
                emqx v3.2.0 is started successfully!

                $ emqx_ctl status
                Node 'emqx@127.0.0.1' is started
                emqx 4.0.0 is running

    +   systemctl start

        .. code-block:: console

                $ sudo systemctl start emqx

    +   service start

        .. code-block:: console

                $ sudo service emqx start

8.  Configuration file path

    + Configuration file path: ``/etc/emqx``

    + Log file path: ``/var/log/emqx``

    + Data file path: ``/var/lib/emqx`

Install via rpm
>>>>>>>>>>>>>>>>

1.  Select the CentOS version via `emqx.io`_ and download the rpm package for the EMQ X version to be installed.

2.  Install EMQ X

    .. code-block:: console

           $ sudo rpm -ivh emqx-ee-centos7-v3.2.0.x86_64.rpm

3.  Import License file

    .. code-block:: console

        $ cp /path/to/emqx.lic /etc/emqx/emqx.lic

4.  Start EMQ X

    +   Directly start

        .. code-block:: console

                $ emqx start
                emqx v3.2.0 is started successfully!

                $ emqx_ctl status
                Node 'emqx@127.0.0.1' is started
                emqx 4.0.0 is running

    +   systemctl start

        .. code-block:: console

                $ sudo systemctl start emqx

    +   service start

        .. code-block:: console

                $ sudo service emqx start

5.  Configuration file path

    + Configuration file path: ``/etc/emqx``

    + Log file path: ``/var/log/emqx``

    + Data file path: ``/var/lib/emqx`

Install via zip Package
>>>>>>>>>>>>>>>>>>>>>>>>

1. Select the CentOS version via `emqx.io`_ and download the zip package for the EMQ X version to be installed.

2.  Unzip package

    .. code-block:: console

       $ unzip emqx-centos7-v3.1.0.zip

3.  Import License file

    .. code-block:: console

        $ cp /path/to/emqx.lic /path/to/emqx/etc/emqx.lic

4.  Start EMQ X

    .. code-block:: console

        $ ./bin/emqx start
        emqx v3.2.0 is started successfully!

        $ ./bin/emqx_ctl status
        Node 'emqx@127.0.0.1' is started
        emqx 4.0.0 is running

Ubuntu
------

+ Bionic 18.04 (LTS)
+ Xenial 16.04 (LTS)
+ Trusty 14.04 (LTS)
+ Precise 12.04 (LTS)

Install via Repository
>>>>>>>>>>>>>>>>>>>>>>>

1.  Delete the old EMQ X

    .. code-block:: console

        $ sudo apt remove emqx emqx-edge emqx-ee


2.  Install the required dependency

    .. code-block:: console

        $ sudo apt update && sudo apt install -y \
            apt-transport-https \
            ca-certificates \
            curl \
            gnupg-agent \
            software-properties-common

3.  Add the GPG key for EMQ X

    .. code-block:: console

        $ curl -fsSL https://repos.emqx.io/gpg.pub | sudo apt-key add -

    Validate key

    .. code-block:: console

        $ sudo apt-key fingerprint 3E640D53

        pub   rsa2048 2019-04-10 [SC]
            FC84 1BA6 3775 5CA8 487B  1E3C C0B4 0946 3E64 0D53
        uid           [ unknown] emqx team <support@emqx.io>

4.  Add the EMQ X repository.

    .. code-block:: console

        $ sudo add-apt-repository \
            "deb [arch=amd64] https://repos.emqx.io/emqx-ee/deb/ubuntu/ \
            $(lsb_release -cs) \
            stable"

5.  Update apt package index

    .. code-block:: console

        $ sudo apt update

6.  Install the latest version of EMQ X

    .. code-block:: console

        $ sudo apt install emqx-ee

    .. NOTE:: In the case where multiple EMQ X repositories are enabled, and the apt install and apt update commands is not specified with a version number, the latest version of EMQ X is installed. This could be a problem for users with stability needs.

7.  Install a specific version of EMQ X

    1.  Query available version

        .. code-block:: console

            $ sudo apt-cache madison emqx-ee

            emqx-ee |      4.0.0 | https://repos.emqx.io/emqx-ee/deb/ubuntu bionic/stable amd64 Packages

    2.  Install a specific version using the version string from the second column, such as 4.0.0

        .. code-block:: console

            $ sudo apt install emqx-ee=4.0.0

8.  Import License file

    .. code-block:: console

        $ cp /path/to/emqx.lic /etc/emqx/emqx.lic

9.  Start EMQ X

    +   Directly start

        .. code-block:: console

                $ emqx start
                emqx v3.2.0 is started successfully!

                $ emqx_ctl status
                Node 'emqx@127.0.0.1' is started
                emqx 4.0.0 is running

    +   systemctl start

        .. code-block:: console

                $ sudo systemctl start emqx

    +   service start

        .. code-block:: console

                $ sudo service emqx start

10.  Configuration file path

    + Configuration file path: ``/etc/emqx``

    + Log file path: ``/var/log/emqx``

    + Data file path: ``/var/lib/emqx`

Install via deb Package
>>>>>>>>>>>>>>>>>>>>>>>>

1.  Select the Ubuntu version via `emqx.io`_ and download the deb package for the EMQ X version to be installed.

2.  Install EMQ X

    .. code-block:: console

           $ sudo dpkg -i emqx-ee-ubuntu18.04-v3.2.0_amd64.deb

3.  Import License file

    .. code-block:: console

        $ cp /path/to/emqx.lic /etc/emqx/emqx.lic

4.  Start EMQ X

    +   Directly start

        .. code-block:: console

                $ emqx start
                emqx  is started successfully!

                $ emqx_ctl status
                Node 'emqx@127.0.0.1' is started
                emqx 4.0.0 is running

    +   systemctl start

        .. code-block:: console

                $ sudo systemctl start emqx

    +   service start

        .. code-block:: console

                $ sudo service emqx start

5.  Configuration file path

    + Configuration file path: ``/etc/emqx``

    + Log file path: ``/var/log/emqx``

    + Data file path: ``/var/lib/emqx`

Install via zip Package
>>>>>>>>>>>>>>>>>>>>>>>>

1.  Select the Ubuntu version via  `emqx.io`_ and download the zip package for the EMQ X version to be installed.

2.  Unzip the package

    .. code-block:: console

       $ unzip emqx-ee-ubuntu18.04-v3.2.0.zip

3.  Import License file

    .. code-block:: console

        $ cp /path/to/emqx.lic /path/to/emqx/etc/emqx.lic

4.  Start EMQ X

    .. code-block:: console

        $ ./bin/emqx start
        emqx v3.2.0 is started successfully!

        $ ./bin/emqx_ctl status
        Node 'emqx@127.0.0.1' is started
        emqx 4.0.0 is running

Debian
-------

+ Stretch (Debian 9)
+ Jessie (Debian 8)

Install via Repository
>>>>>>>>>>>>>>>>>>>>>>>

1.  Delete the old EMQ X

    .. code-block:: console

        $ sudo apt remove emqx emqx-edge emqx-ee

2.  Install the required dependency

    .. code-block:: console

        $ sudo apt update && sudo apt install -y \
            apt-transport-https \
            ca-certificates \
            curl \
            gnupg-agent \
            software-properties-common

3.  Add the GPG key for EMQ X

    .. code-block:: console

        $ curl -fsSL https://repos.emqx.io/gpg.pub | sudo apt-key add -

    Validate the key

    .. code-block:: console

        $ sudo apt-key fingerprint 3E640D53

        pub   rsa2048 2019-04-10 [SC]
            FC84 1BA6 3775 5CA8 487B  1E3C C0B4 0946 3E64 0D53
        uid           [ unknown] emqx team <support@emqx.io>

4.  Add the EMQ X repository.

    .. code-block:: console

        $ sudo add-apt-repository \
            "deb [arch=amd64] https://repos.emqx.io/emqx-ee/deb/debian/ \
            $(lsb_release -cs) \
            stable"

5.  Update apt package index

    .. code-block:: console

        $ sudo apt update

6.  Install the latest version of EMQ X

    .. code-block:: console

        $ sudo apt install emqx-ee

    .. NOTE:: In the case where multiple EMQ X repositories are enabled, and the apt install and apt update commands is not specified with a version number, the latest version of EMQ X is installed. This is a problem for users with stability needs.

7.  Install a specific version of EMQ X

    1.  Query available version

        .. code-block:: console

            $ sudo apt-cache madison emqx

            emqx-ee |      4.0.0 | https://repos.emqx.io/emqx-ee/deb/ubuntu bionic/stable amd64 Packages

    2.  Install a specific version using the version string from the second column, such as 4.0.0

        .. code-block:: console

            $ sudo apt install emqx-ee=4.0.0

8.  Import License file

    .. code-block:: console

        $ cp /path/to/emqx.lic /etc/emqx/emqx.lic

9.  Start EMQ X

    +   Directly start

        .. code-block:: console

                $ emqx start
                emqx v3.2.0 is started successfully!

                $ emqx_ctl status
                Node 'emqx@127.0.0.1' is started
                emqx 4.0.0 is running

    +   systemctl start

        .. code-block:: console

                $ sudo systemctl start emqx

    +   service start

        .. code-block:: console

                $ sudo service emqx start

10.  Configuration file path

    + Configuration file path: ``/etc/emqx``

    + Log file path: ``/var/log/emqx``

    + Data file path: ``/var/lib/emqx`

Install via deb Package
>>>>>>>>>>>>>>>>>>>>>>>>

1.  Select the Debian version via `emqx.io`_ and download the deb package for the EMQ X version to be installed.

2.  Install EMQ X

    .. code-block:: console

           $ sudo dpkg -i emqx-ee-debian9-v3.2.0_amd64.deb

3.  Import License file

    .. code-block:: console

        $ cp /path/to/emqx.lic /etc/emqx/emqx.lic

4.  Start EMQ X

    +   Directly start

        .. code-block:: console

                $ emqx start
                emqx v3.2.0 is started successfully!

                $ emqx_ctl status
                Node 'emqx@127.0.0.1' is started
                emqx 4.0.0 is running

    +   systemctl start

        .. code-block:: console

                $ sudo systemctl start emqx

    +   service start

        .. code-block:: console

                $ sudo service emqx start

5.  Configuration file path

    + Configuration file path: ``/etc/emqx``

    + Log file path: ``/var/log/emqx``

    + Data file path: ``/var/lib/emqx`

Install via zip Package
>>>>>>>>>>>>>>>>>>>>>>>>

1.  Select the Debian version via `emqx.io`_ and download the zip package for the EMQ X version to be installed.

2.  Unzip the package

    .. code-block:: console

       $ unzip emqx-ee-debian9-v3.2.0.zip

3.  Import License file

    .. code-block:: console

        $ cp /path/to/emqx.lic /path/to/emqx/etc/emqx.lic

4.  Start EMQ X

    .. code-block:: console

        $ ./bin/emqx start
        emqx v3.2.0 is started successfully!

        $ ./bin/emqx_ctl status
        Node 'emqx@127.0.0.1' is started
        emqx 4.0.0 is running

macOS
------

Install via zip Package
>>>>>>>>>>>>>>>>>>>>>>>>

1.  Select the EMQ X version via `emqx.io`_and download the zip package to install.

2.  Unzip the package

    .. code-block:: console

       $ unzip emqx-macos-v3.1.0.zip

3.  Import License file

    .. code-block:: console
     
        $ cp /path/to/emqx.lic /path/to/emqx/etc/emqx.lic

4.  Start EMQ X

    .. code-block:: console

        $ ./bin/emqx start
        emqx v3.2.0 is started successfully!

        $ ./bin/emqx_ctl status
        Node 'emqx@127.0.0.1' is started
        emqx 4.0.0 is running



Windows
--------

1.  Select the Windows version via `emqx.io`_ and download the .zip package to install.

2.  Unzip the package

3.  Import License file

    .. code-block:: console

        $ cp /path/to/emqx.lic /path/to/emqx/etc/emqx.lic

4.  Open the Windows command line window, change the directory to the program directory, and start EMQ X.

    .. code-block:: console

        cd emqx/bin
        emqx start

openSUSE
---------

+ openSUSE leap

Install via Repository
>>>>>>>>>>>>>>>>>>>>>>>

1.  Delete the old EMQ X

    .. code-block:: console

        $ sudo zypper remove emqx emqx-edge emqx-ee

2.  Download the GPG public key and import it.

    .. code-block:: console

        $ curl -L -o /tmp/gpg.pub https://repos.emqx.io/gpg.pub
        $ sudo rpmkeys --import /tmp/gpg.pub

3.  Add repository address

    .. code-block:: console

        $ sudo zypper ar -f -c https://repos.emqx.io/emqx-ee/redhat/opensuse/leap/stable emqx-ee

4.  Install the latest version of EMQ X

    .. code-block:: console

        $ sudo zypper in emqx-ee

5.  Install a specific version of EMQ X

    1. Query available version

        .. code-block:: console

            $ sudo zypper pa emqx

            Loading repository data...
            Reading installed packages...
            S | Repository | Name | Version  | Arch
            --+------------+------+----------+-------
              | emqx-ee    | emqx-ee | 4.0.0-1 | x86_64

    2.  Use Version column to install a specific version, such as 3.1.0

        .. code-block:: console

            $ sudo zypper in emqx-ee-4.0.0

6.  Import License file

    .. code-block:: console

        $ cp /path/to/emqx.lic /etc/emqx/emqx.lic

7.  Start EMQ X

    +   Directly start

        .. code-block:: console

                $ emqx start
                emqx v3.2.0 is started successfully!

                $ emqx_ctl status
                Node 'emqx@127.0.0.1' is started
                emqx 4.0.0 is running

    +   systemctl start

        .. code-block:: console

                $ sudo systemctl start emqx

    +   service start

        .. code-block:: console

                $ sudo service emqx start

8.  Configuration file path

    + Configuration file path: ``/etc/emqx``

    + Log file path: ``/var/log/emqx``

    + Data file path: ``/var/lib/emqx`

Install via rpm Package
>>>>>>>>>>>>>>>>>>>>>>>>

1.  Select openSUSE via  `emqx.io`_ and download the rpm package for the EMQ X version to be installed.

2.  Install EMQ X and change the path below to the path where you downloaded the EMQ X package.

    .. code-block:: console

           $ sudo rpm -ivh emqx-ee-opensuse-v3.2.0.x86_64.rpm

3.  Import License file

    .. code-block:: console

        $ cp /path/to/emqx.lic /etc/emqx/emqx.lic

4.  Start EMQ X

    +   Directly start

        .. code-block:: console

                $ emqx start
                emqx v3.2.0 is started successfully!

                $ emqx_ctl status
                Node 'emqx@127.0.0.1' is started
                emqx 4.0.0 is runnin

    +   systemctl start

        .. code-block:: console

                $ sudo systemctl start emqx

    +   service start

        .. code-block:: console

                $ sudo service emqx start

5.  Configuration file path

    + Configuration file path: ``/etc/emqx``

    + Log file path: ``/var/log/emqx``

    + Data file path: ``/var/lib/emqx`

Install via zip Package
>>>>>>>>>>>>>>>>>>>>>>>>

1.  Select openSUSE via `emqx.io`_ and download the zip package for the EMQ X version to be installed.


2.  Unzip the package

    .. code-block:: console

       $ unzip emqx-ee-opensuse-v3.2.0.zip

3.  Import License file

    .. code-block:: console

        $ cp /path/to/emqx.lic /path/to/emqx/etc/emqx.lic

4.  Start EMQ X

    .. code-block:: console

        $ ./bin/emqx start
        emqx v3.2.0 is started successfully!

        $ ./bin/emqx_ctl status
        Node 'emqx@127.0.0.1' is started
        emqx 4.0.0 is running

FreeBSD
--------

+ FreeBSD 12

Install via zip Package
>>>>>>>>>>>>>>>>>>>>>>>>

1.  Select FreeBSD via `emqx.io`_  and download the zip package for the EMQ X version to be installed.

2.  Unzip the package

    .. code-block:: console

       $ unzip emqx-ee-freebsd12-v3.2.0.zip

3.  Import License file

    .. code-block:: console

        $ cp /path/to/emqx.lic /path/to/emqx/etc/emqx.lic

4.  Start EMQ X

    .. code-block:: console

        $ ./bin/emqx start
        emqx v3.2.0 is started successfully!

        $ ./bin/emqx_ctl status
        Node 'emqx@127.0.0.1' is started
        emqx 4.0.0 is running

Docker
-------

.. _Docker Hub: https://hub.docker.com/r/emqx/emqx

1.  Get docker image

    +   Through `Docker Hub`_

        .. code-block:: console

            $ docker pull emqx/emqx-ee:v3.2.0

    +    Download the docker image via `emqx.io`_ and load it manually

        .. code-block:: console

            $ wget -O emqx-ee-docker-v3.2.0.zip https://www.emqx.io/downloads/enterprise/v3.2.0/emqx-ee-docker-v3.2.0-amd64.zip
            $ unzip emqx-ee-docker.zip
            $ docker load < emqx-ee-docker-v3.2.0

2.  Start the docker container

    .. code-block:: console

        $ docker run -d -\
            -name emqx-ee \
            -p 1883:1883 \
            -p 8083:8083 \
            -p 8883:8883 \
            -p 8084:8084 \
            -p 18083:18083 \
            -v /path/to/emqx.lic:/opt/emqx/etc/emqx.lic
            emqx/emqx-ee:v3.2.0

For more information about EMQ X Docker, please check `Docker Hub`_ .
