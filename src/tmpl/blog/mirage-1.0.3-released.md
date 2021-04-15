We've had a lot of people trying out MirageOS since the [1.0 release](/blog/announcing-mirage10) last week, and so we've been steadily cutting point releases and new libraries to OPAM as they're done.
The most common build error by far has been people using outdated OPAM packages.  Do make sure that you have at least [OPAM 1.1](http://opam.ocaml.org/doc/Quick_Install.html) installed, and that you've run `opam update -u` to get the latest package lists from the [package repository](https://github.com/ocaml/opam-repository).

[MirageOS 1.0.3](https://github.com/mirage/mirage/releases/tag/1.0.3) improves
Xen configuration generation, cleans up HTTP support, and adds support for FAT
filesystems.  Here are some of the libraries we've released this week to go along with it:

* [mirage-www](https://github.com/mirage/mirage-www) (update): the live website now runs on the 1.0 tools.  Explanation of how to build it in various configurations is available [here](/wiki/mirage-www).
* [alcotest](https://github.com/samoht/alcotest) (new): a lightweight and colourful test framework built over [oUnit](http://ounit.forge.ocamlcore.org/).  The interface is simpler to facilitate writing tests quickly, and it formats test results nicely.
* [mirage-block-xen.1.0.0](https://github.com/mirage/mirage-block-xen) (new): is the stable release of the Xen `Blkfront` driver for block devices.  The library supports both frontend and backend operation, but only the frontend is plumbed through to Mirage for now (although the backend can be manually configured).
* [mirage-block-unix.1.2.0](https://github.com/mirage/mirage-block-unix) (update): fixed some concurrency bugs and added support for buffered I/O to improve performance.
* [fat-filesystem.0.10.0](https://github.com/mirage/ocaml-fat) (update): copies with more sector sizes, uses buffered I/O on Unix, and adds a `KV_RO` key/value interface as well as a more complicated filesystem one.
* [mirage-fs-unix.1.0.0](https://github.com/mirage/mirage-fs-unix) (update): implements the `KV_RO` signature as a passthrough to a Unix filesystem.  This is convenient during development to avoid recompile cycles while changing data.
* [mirage-xen.1.0.0](https://github.com/mirage/mirage-platform) (update): removed several distracting-but-harmless linker warnings about code bloat.
* [cohttp.0.9.14](https://github.com/mirage/ocaml-cohttp) (update): supports Server-Side Events via better channel flushing, has a complete set of HTTP codes autogenerated from [httpstatus.es](https://github.com/citricsquid/httpstatus.es) and exposes a platform-independent `Cohttp_lwt` module.
* [cow.0.8.1](https://github.com/mirage/ocaml-cow) (update): switch to the [Omd](https://github.com/pw374/omd) library for Markdown parsing, which is significantly more compatible with other parsers.
* [ezjsonm.0.2.0](https://github.com/samoht/ezjsonm) (new): a combinator library to parse, select and manipulate JSON structures.
* [ezxmlm.1.0.0](https://github.com/avsm/ezxmlm) (new): a combinator library to parse, select and transform XML tags and attributes.
* [mirage-http-xen](https://github.com/mirage/mirage-http-xen) and [mirage-http-unix](https://github.com/mirage/mirage-http-unix) provide the HTTP drivers on top of Cohttp for MirageOS. Although they are very similar at the moment, they will diverge as the Unix variant gains options to use kernel sockets instead of only the network stack.

We're making great progress on moving our personal homepages over to MirageOS.  The first two introductory wiki posts are also now available:
* [Building a hello world example](/wiki/hello-world) takes you through the basic steps to build a Unix and Xen binary.
* [Building the MirageOS website](/wiki/mirage-www) lets you build this website with several variants, demonstrating the Unix passthrough filesystem, the OCaml FAT filesystem library, and how to attach a network stack to your application.

As always, please feel free to report any issues via the [bug tracker](https://github.com/mirage/mirage/issues) and ask questions on the [mailing list](mailto:mirageos-devel@lists.xenproject.org).