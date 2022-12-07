# <img src="https://cdn.rawgit.com/theupdateframework/artwork/3a649fa6/tuf-logo.svg" height="100" valign="middle" alt="TUF"/> A Framework for Securing Software Update Systems

----------------------------
[The Update Framework (TUF)](https://theupdateframework.io/) is a framework for
secure content delivery and updates. It protects against various types of
supply chain attacks and provides resilience to compromise.

go-tuf-metadata is started from the idea of providing a Go implementation of TUF that is heavily influenced by the
design decisions made in [python-tuf](https://github.com/theupdateframework/python-tuf).

## About The Update Framework

----------------------------
The Update Framework (TUF) design helps developers maintain the security of a
software update system, even against attackers that compromise the repository
or signing keys.
TUF provides a flexible
[specification](https://github.com/theupdateframework/specification/blob/master/tuf-spec.md)
defining functionality that developers can use in any software update system or
re-implement to fit their needs.

TUF is hosted by the [Linux Foundation](https://www.linuxfoundation.org/) as
part of the [Cloud Native Computing Foundation](https://www.cncf.io/) (CNCF)
and its design is [used in production](https://theupdateframework.io/adoptions/)
by various tech companies and open source organizations.

Please see [TUF's website](https://theupdateframework.com/) for more information about TUF!

## How to use it

----------------------------

See the [basic_repo.go](examples/basic_repo.go) example which demonstrates how to *manually* create and
maintain repository metadata using the low-level Metadata API.

The example highlights the following functionality supported by the metadata API:

* creation of top-level metadata
* target file handling
* consistent snapshots
* key management
* top-level delegation and signing thresholds
* metadata verification
* target delegation
* in-band and out-of-band metadata signing
* writing and reading metadata files
* root key rotation

## Roadmap

----------------------------

### :white_check_mark: - Implement the `metadata` API

* The `metadata` API provides access to a Metadata file abstraction that closely
follows the TUF specification’s document formats. This API handles de/serialization
to and from files and bytes, covers also the process to create and verify metadata
signatures and makes it easier to access and modify metadata content. It is purely
focused on individual pieces of Metadata and provides no concepts like “repository”
or “update workflow”.

### :white_check_mark: - Recreate the `basic_repo.py` example

* The example demonstrates how to *manually* create and
maintain repository metadata using the low-level Metadata API.

### :white_check_mark: - Implement the `trustedmetadata` package

* A `TrustedMetadata` instance ensures that the collection of metadata in it is valid
and trusted through the whole client update workflow. It provides easy ways to update
the metadata with the caller making decisions on what is updated.

### :white_check_mark: - Implement client API - `config` package

* The `config` package is used to store ``Updater`` configuration.

### :white_check_mark: - Implement client API - `fetcher` package

* The `fetcher` package defines an interface for abstract network download.

### :construction: - Implement client API - `updater` package

* The `updater` package provides an implementation of the TUF client workflow.
It provides ways to query and download target files securely, while handling the
TUF update workflow behind the scenes. It is implemented on top of the Metadata API
and can be used to implement various TUF clients with relatively little effort.

### :soon: - Implement repository API (standalone package built on top of metadata, to be split into several other tasks)

## Documentation

----------------------------

* [Introduction to TUF's Design](https://theupdateframework.io/overview/)

* [The TUF Specification](https://theupdateframework.github.io/specification/latest/)

## Contact

----------------------------

Questions, feedback, and suggestions are welcomed on the [#tuf](https://cloud-native.slack.com/archives/C8NMD3QJ3) channel on
[CNCF Slack](https://slack.cncf.io/).

We strive to make the specification easy to implement, so if you come across
any inconsistencies or experience any difficulty, do let us know by sending an
email, or by reporting an issue in the GitHub [specification
repo](https://github.com/theupdateframework/specification/issues).
