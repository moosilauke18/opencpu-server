OpenCPU on Docker
=================

This directory contains dockerfiles based on various platforms. Containers are automatically published at [dockerhub](https://hub.docker.com/u/opencpu/).


How to use
----------

Docker version 1.0 or higher is required on the host. The containers expose 3 ports: either 80 or 8004 can be used for HTTP, and port 443 can be used for HTTPS. Depending in which ports are mapped (via the `-p` flag), you can access:

    http://localhost/ocpu/
    http://localhost:8004/ocpu/
    https://localhost/ocpu/

The examples below assume that we use the [opencpu/base](https://registry.hub.docker.com/u/opencpu/base/) container. To start as the server as an executable

    docker run -t -p 80:80 -p 8004:8004 opencpu/base

Alternatively, to start in background as a daemon:

    docker run -t -d -p 80:80 -p 8004:8004 opencpu/base

Alternatively, to start with an interactive shell:

    docker run -t -i -p 80:80 -p 8004:8004 opencpu/base sh -c 'service opencpu restart && /bin/bash'

OpenCPU and RStudio
-------------------

The [opencpu/rstudio](https://registry.hub.docker.com/u/opencpu/rstudio/) container runs an installation with both `opencpu` and `rstudio-server`. For example:

    docker run -t -p 80:80 -p 8004:8004 opencpu/rstudio

Apache is automatically setup to proxy the `/rstudio/` path to the rstudio server:

    http://localhost/ocpu/
    http://localhost/rstudio/
    http://localhost:8004/ocpu/
    http://localhost:8004/rstudio/

It seems like rstudio server currelty needs a restart (`rstudio-server restart`) after initiating the container.

Portmapping
-----------

Each `-p from:to` command maps a port from the container to the host. Not all ports are required. For example if you only want to use port 8004 (because the host has something else running on port 80) simply use:

    docker run -t -p 8004:8004 opencpu/base

Note that **http does not support cross-port redirects**. I.e. mapping `-p 1234:8004` won't work. It might look like it works because it connects, but the http headers (e.g. Location) will contain an incorrect server address. This has nothing to do with docker or opencpu, it is how http works. To proxy http to another host or port you need to use a reverse proxy server that rewrites the headers such as nginx.

Security
--------

Docker has its own security model and disables other Linux based security modules such as AppArmor or SELinux. So be aware that the execution environment of the OpenCPU API within the container is entirely unrestricted.

Help and Feedback
-----------------

I am new to this too, so please share your questions, problems and suggestions on the [mailing list](https://www.opencpu.org/help.html) or [twitter](https://twitter.com/opencpu).
