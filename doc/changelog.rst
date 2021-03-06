Changelog
=========

1.2
***

Fixed regressions
-----------------

* *camisole* < 1.0 fallbacks to JSON parsing when receiving unsupported
  content types (eg. curl's default form-encoded); 1.0 ≤ *camisole* < 1.2 used
  to require that a valid content-type header be present on the request,
  including JSON requests. *camisole* ≥ 1.2 restores the original behavior, so
  curl(1) can be used without any specific header, as the documentation
  command-line examples imply.

1.1
***

New features
------------

* Add support for the D language.

1.0
***

Breaking changes
----------------

* The HTTP API now requires a ``Content-type`` header (``application/json`` or
  ``application/msgpack``)
* ``cg-mem`` limit is renamed ``mem`` (#31)
* ``mem`` limit is renamed ``virt-mem`` (#31)
* ``time-wall`` meta property is renamed ``wall-time`` (#32)
* Default ``$ camisole serve`` port was ``8080`` and is now ``42920``
* Removed Brainfuck, F# and VisualBasic.NET. New criteria for built-in
  languages: being included in the Archlinux default packages, for easier
  deployment.

New features
------------

* The ``$ camisole benchmark`` was implemented
* The HTTP API now accepts both JSON and MessagePack payloads and outputs either
  JSON or MessagePack; as such, source code, stdin, stderr and stdout can now
  contain any binary data when using MessagePack
* Some camisole features can now be configured through a YAML config file

Other
-----

* The default HTTP payload size limit was raised from 2 MB to 50 MB
* *Box allocation* from the isolation backend (isolate) was refactored to use a
  more robust approach, preventing some races conditions
