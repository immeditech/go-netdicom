[![GoDoc](https://godoc.org/github.com/grailbio/go-netdicom?status.svg)](https://godoc.org/github.com/grailbio/go-netdicom) [![Build Status](https://travis-ci.org/grailbio/go-netdicom.svg?branch=master)](https://travis-ci.org/grailbio/go-netdicom.svg?branch=master)

# Golang implementation of DICOM network protocol.

See doc.go for (incomplete) documentation.  See storeclient and storeserver for
examples.

Inspired by https://github.com/pydicom/pynetdicom3.

## Fork

Maintained by Immeditech AG, based on `segmed/go-netdicom` (itself a fork of
`grailbio/go-netdicom`). Licensed under Apache-2.0 (see `LICENSE` and `NOTICE`).

Changes made in this fork:

- Module path renamed to `github.com/immeditech/go-netdicom`.
- DICOM data model switched to `github.com/immeditech/go-dicom` (our renamed
  fork of `segmed/go-dicom`), pinned as a normal `require`. This keeps the
  module self-contained: consumers can import it without a `replace` directive.

The library is kept generic — no application-specific logic. Integrations plug
in via the `CEcho` / `CFind` / `CStore` callbacks of `ServiceProviderParams`.

Status as of 2022-18-05:
- C-MOVE works on the client side

Status as of 2017-10-02:

- C-STORE, C-FIND, C-GET work, both for the client and the server. Look at
  sampleclient, sampleserver, or e2e_test.go for examples.  In general, the
  server (provider)-side code is better tested than the client-side code.

- Compatibility has been tested against pynetdicom and Osirix MD.

TODO:

- Documentation.

- Better SSL support.

- Implement the rest of DIMSE protocols, in particular N-* commands.

- Better message validation.

- Remove the "limit" param from the Decoder, and rely on io.EOF detection instead.
