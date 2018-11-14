
Mac How to
=====

Mounting ntfs on mac
-----

::

  $ df -ah
  Filesystem      Size   Used  Avail Capacity  iused    ifree %iused  Mounted on
  /dev/disk1     233Gi  228Gi  4.1Gi    99% 59886590  1061888   98%   /
  devfs          186Ki  186Ki    0Bi   100%      642        0  100%   /dev
  map -hosts       0Bi    0Bi    0Bi   100%        0        0  100%   /net
  map auto_home    0Bi    0Bi    0Bi   100%        0        0  100%   /home

  /dev/disk2s1   932Gi  908Gi   23Gi    98%   111606 25128162    0%   /Volumes/Expansion Drive


  $ sudo umount /Volumes/Expansion\ Drive/

  $ sudo mkdir /usbNTFS/

  $ sudo mount -t ntfs -o rw,auto,nobrowse /dev/disk2s1 /usbNTFS/ 
  # Note: With my current testing, we need to have no browse options also to have write access.

  $ cd /usbNTFS/


  $ open . 

.. Note:: The disk mount point for your external hard disk might be different.
          Please make a note of the same and do the changes as per the same.