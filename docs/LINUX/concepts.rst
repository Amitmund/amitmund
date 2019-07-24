Few Linux Concepts:
=====

Few links:
-----

https://tobert.github.io/


Transparent Hugepages (THP)
-----

https://tobert.github.io/tldr/cassandra-java-huge-pages.html


Many applications seem to be having trouble with a Linux feature called "Transparent Hugepages". When enabled, the Linux kernel will try to allocate memory in bigger chunks - typically 2MB - rather than 4K at a time. This can impact performance by reducing the load on CPU caches (TLB) used for managing ranges of addresses. As you can imagine, managing memory on a 128GB machine in 4KB pages requires a fair bit of work. Using 2MB pages reduces the number of pages being tracked by a factor of 512!

So, with that said, it sounds like huge pages are a Good Thing, but they can cause surprises when enabled in the background. Many applications assume the page size on Linux is 4096 and allocate memory based on that assumption. That's not such a bad thing since the OS still reports a page size of 4096. Where it gets ugly is when Linux decides to defrag 4K pages into 2MB pages. In order to do so, it has to lock the memory being moved which almost always ends up being visible in the applications whose pages are being migrated. On most Redhat variants including RHEL and CentOS, THP defrag is enabled by default and you probably want to disable it via a setting in sysfs.


