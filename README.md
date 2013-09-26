null-docker
===========

I would prefer an empty directory, but this is the best I can do.

Quick Usage
-----------

  $ docker run bencord0/null ip a

Long Usage
----------

  $ git clone https://github.com/bencord0/null-docker.git
  $ cd null-docker
  $ git archive HEAD | docker import - bencord0/null

  $ docker run bencord0/null /bin/ip -6 addr show

Notes
-----
The first (non comment) line of a Dockerfile is a reference to ubuntu. I'm not a big ubuntu fan,
so when I make docker containers, I'm going to base them from nothing but the bare minimum that
docker containers need to run.

Binaries for /lib/{ld-linux-x86-64.so.2,libc.so.6,libdl.so.2} and /bin/ip are taken from a
Gentoo machine. Everything else is either a directory or a symlink.

The presence of /etc/resolv.conf is not needed to spawn a docker container.
The /usr/bin symlink is still important, no idea why.
/dev/null needs to exist, but an empty file will do.

All other FHS directories can be empty, and are therefore not tracked by git.
This isn't a problem since a Dockerfile ADD command will create those directories as needed.
