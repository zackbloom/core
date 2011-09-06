Core
====

A node.js-based toolkit for continuous integration applications.

    +-----+   HTTP   +-----------+
    | App |----------|           | HTTP
    +-----+          |           |------ CLI Application
                     | Job Shell |      
    +-----+   HTTP   |           |------ Web Interface
    | App |----------|           |
    +-----+          +-----------+
                           

Overview
========

Core integrates with applications.  Applications might include:

- Templating language compilers (jade, sass, etc.)
- Compliers / linkers (gcc, clang, etc.)
- Testing tools (JSUnit)
- Code quality tools
- Packaging tools (ugly.js)
- Deployment tools (Chef, file ops, etc.)

Applications accept an input, and provide a data output and status output
(analogous to STDIN, STDOUT, STDERR).  Each in/out is an HTTP stream with
a MIME type, along with other common HTTP headers and allowing common HTTP
techniques such as gzip compression.  A specialized virtual type
is provided to abstract directory structures so that common apps may be
used with directories, git repos, etc. transparently.

Apps
====

- Can be written in any language which can host an HTTP server [toolkits are 
provided in node.js and other languages to come].
- Can be launched, managed and utilized locally or on one or more remote machines.
- Are HTTP-based, optionally secured with SSL.
- Can be executed alone via a standard HTTP protocol, or through core.

Core
====

The core process can be concieved of as a shell similar to Bash or Zsh.  The 
core process provides a job API to complement the API hosted by each app.  Like 
the pipe system in Unix, the job API allows you to redirect the input and 
output of processes to allow you to compose apps into jobs.  It also allows
you to find and interact with available and running apps.

Core also provides two common applications of the jobs and app APIs, one CLI, 
the other web-based.
