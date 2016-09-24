# TigerPorts
A local repository of ports that are configured for MacOSX 10.4 Tiger and shadow newer, often incompatible versions of ports.

MacOSX 10.4 (Tiger) has some incompatabilities with some of the newest ports available on MacPorts. The goal of project is to generate a "local repository" of portfiles and associated patches that will in some cases modify the existing portfiles to work on Tiger, and in other cases will bring back older versions of ports that still work on Tiger but can't easily be found in the current MacPorts portfile distribution.

To use a local repository, you designate a folder to be your local MacPorts repository (collection of portfiles and patches). Then you index them using "sudo portindex" from the base directory. In this case, you could go to the /opt directory, and clone the TigerPorts git repository right there. If that works for you, then use "/opt/TigerPorts" as the base directory for the local repository, and run "sudo portindex" from that directory.

Finally, you need to add the local repository to your macports sources file (usually "/opt/local/etc/macports/sources.conf"), putting your local repository AHEAD of the Macports repository:

file:///opt/TigerPorts

rsync://rsync.macports.org/release/tarballs/ports.tar [default]

Then, when you look for ports, macports will find the tigerports portfiles before the official macports portfiles. That's how this process works. Other port searches and requests will pass through tigerports and use the macports repository.

qt4-mac --> an older version that still works on Tiger

libassuan --> a minor edit that allows it to compile on Tiger

mysql56 --> removed some ATOMIC functions that are not compatible with PPC, however be aware that this version only passes about 90% of the mysql test suite. You might want to stick with mysql55; it passes over 98% of the test suite.

tmuc --> older version that compiles and runs on Tiger
