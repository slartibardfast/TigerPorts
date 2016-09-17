# MPTigerRepo
A local repository of ports that are configured for MacOSX 10.4 Tiger and shadow newer, often incompatible versions of ports.

MacOSX 10.4 (Tiger) has some incompatabilities with some of the newest ports available on MacPorts. The goal of project is to generate a "local repository" of portfiles and associated patches that will in some cases modify the existing portfiles to work on Tiger, and in other cases will bring back older versions of ports that still work on Tiger but can't easily be found in the current MacPorts portfile distribution.

To use a local repository, you designate a folder to be your local MacPorts repository (collection of portfiles and patches). Then you index them using "sudo portindex" from the base directory. I use "/opt/myports" as the base directory for my local repository, and run "sudo portindex" from that directory.

Finally, you need to add the local repository to your macports sources file (usually "/opt/local/etc/macports/sources.conf"), putting your local repository AHEAD of the Macports repository:

-----
file:///opt/myports
rsync://rsync.macports.org/release/tarballs/ports.tar [default]
--------

Then, when you look for ports, you will find your own local portfiles before you find the official macports portfiles. That's how this process works.

