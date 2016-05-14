diet cpRemote Backup
====================

cpRemote works well but could work better: if you configure 7-days backup, it duplicates files from Monday to Tuesday, eating twice the storage and requiring file to be transfered every day during the 7 days period. This script should be run **before** `cpremotebackup` to prevent duplicated files on the backup server.

It has been tested on cpRemote 8.3 with 7 days Backup Retention. It will take a week to reclaim your disk space.

**How does it work?**
: It simply creates hard links (`cp -al`) of previous day's home directory instead of having to rsync everything back from the origin server. It has been inspired by [rdiff-backup](http://www.nongnu.org/rdiff-backup/).

Installation
------------

Just run the following commands as root:

1. Make sur Enable 7 days Backup Retention is enabled in cpRemote
2. `cd /usr/local/cpanel/scripts/`
3. `wget https://raw.github.com/cahri/dietcpremotebackup/master/dietcpremotebackup`
4. `chmod 755 dietcpremotebackup`
5. edit crontab (`crontab -e`) and add `/usr/local/cpanel/scripts/dietpcpremotebackup && ` before `/usr/local/cpanel/scripts/cpremotebackup`

Version history
---------------

* 1.0.0: initial release

License
-------

The MIT License (MIT)

Copyright (c) 2016 Julien Tessier, Cahri SARL

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.