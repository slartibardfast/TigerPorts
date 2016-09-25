# TigerPorts
A local repository of MacPorts ports that are configured for MacOSX 10.4 Tiger and shadow newer, incompatible versions of ports.

MacOSX 10.4 (Tiger) has some incompatabilities with some of the newest ports available on MacPorts. The goal of project is to generate a local collection of portfiles and associated patches that will in some cases modify the existing portfiles to work on Tiger, and in other cases will bring back older versions of ports that still work on Tiger but can't easily be found in the current MacPorts portfile distribution. Tiger-specific fixes to existing ports will be submitted to MacPorts for consideration into the main repository, and if these fixes are accepted, then the version in TigerPorts will no longer be required and will be removed.

To use a local repository, you designate a folder to be your local MacPorts repository (collection of portfiles and patches). In this case, you could go to the /opt directory, and clone the TigerPorts git repository right there `sudo git clone https://github.com/ken-cunningham-webuse/TigerPorts.git` That makes `/opt/TigerPorts` the base directory for the local repository, and when you run `sudo portindex` from inside that directory, you update the port index MacPorts uses to find the Portfiles.

Finally, you need to add the local repository to your macports sources file (usually `/opt/local/etc/macports/sources.conf`), putting your local repository AHEAD of the Macports repository:
```
file:///opt/TigerPorts
rsync://rsync.macports.org/release/tarballs/ports.tar [default]
```
Then, when you look for ports, macports will find the tigerports portfiles before the official MacPorts portfiles. That's how this process works. Other port searches and requests will pass through tigerports and use the full untouched MacPorts repository.

Here are some instructions from the macports website <https://guide.macports.org/chunked/development.local-repositories.html>. The only thing I'd update in these instructions is to use `/opt/TigerPorts` due to permissions issues, but you can use other locations as well if you need to (like `/Users/Shared/TigerPorts`, for example).

You might wonder why there are not very many ports in TigerPorts -- and that is because in general, almost all of the 20,000 ports on MacPorts "just work" and don't need to be replaced with older versions or modified to work on Tiger. You will be surprised, I think how many current versions of software compile and run very nicely on Tiger just "out of the box". Xorg-Server and all the applications, Apache2, Mysql55, and many many more. I'll keep a list of ports that I know of that have been successfully build on MacOSX Tiger here in the directory as well.

Some examples of what is in TigerPorts:

```
qt4-mac --> an older version that still works on Tiger, and allows many qt4 applications to install and work.
libassuan --> a minor edit that allows it to compile on Tiger
mysql56 --> removed some ATOMIC functions that are not compatible with PPC, and this port now builds, installs, and runs on Tiger (and Leopard PPC, probably). However be aware that this version only passes about 90% of the mysql test suite. You might want to stick with mysql55 for Tiger, as it passes over 98% of the test suite.
tmux --> older version that compiles and runs on Tiger
```
If you have any contributions to make to this collection, please feel free to add, suggest, or put in a pull request!
