# Qore json module

**The `develop` branch is retired.** Qore 3.0 and later ship the `json` module and the 16 user
modules that were developed here as part of Qore itself, so current development of all of them is
in the [Qore repository](https://github.com/qoretechnologies/qore). This branch has no code and
builds nothing.

The repository itself is not retired: the release branches below are still maintained, because
Qore and Qorus releases on those release lines depend on the module.

## Release branches

Branches are named after the **Qore** release line they support, not the module version:

| Branch | Qore release line | json module version |
| --- | --- | --- |
| `2.x` | Qore 2.x | 1.9.2 |
| `1.19.x` | Qore 1.19.x | 1.8.3 |
| `1.12.x` | Qore 1.12.x | 1.8.2 |
| `0.9.x`, `0.9.4`, `0.9.3`, `0.8.13`, `0.8.12`, `master`, … | earlier Qore releases | see the branch |

A fix for one of these release lines goes to its branch here, as a pull request against that
branch, and is built and released from there. Every other change goes to the Qore repository.

## Where the code is in Qore 3.0 and later

| What | Where it is in the Qore repository |
| --- | --- |
| `json` binary module (JSON, CBOR, TOON, JSON Schema, SAX parser, stream writer, JWT, JSON-RPC client) | `modules/json/` |
| C++ API for other binary modules to parse and generate JSON (`QoreJsonApi`) | `include/qore/QoreJsonApi.h` |
| The 16 user modules listed below | `qlib/` |
| Tests | `examples/test/modules/json/` and `examples/test/qlib/<Module>/` |

The user modules: `A2aClient`, `A2aClientDataProvider`, `A2aServerHandler`, `FhirRestClient`,
`FhirRestDataProvider`, `JsonFileDataProvider`, `JsonLd`, `JsonRpcClientIo`, `JsonRpcConnection`,
`JsonRpcHandler`, `McpClient`, `McpClientDataProvider`, `McpServerHandler`, `NdjsonDataProvider`,
`OneRecordClient` and `OneRecordServerHandler`.

## What this means for you

### On Qore 3.0 and later

- **Nothing to install.** `%requires json` works out of the box, and so does every user module
  listed above. Module names and APIs are unchanged.
- **Remove the dependency.** Packages no longer need to require `qore-json-module`; Qore's
  `qore-stdlib` package provides it and replaces earlier versions.
- **Drop the conditionals.** `%try-module json` and `%ifdef NoJson` guards are no longer needed,
  because json is always present. Use a plain `%requires json`.

### On earlier Qore releases

Nothing changes. Build and install the module from the branch for your Qore release line.

## History

The last code on `develop` is commit `506102d384cc40144b8d0c6a23471cd57cd41884`
(json module 1.12.0); the full history stays in this repository. The move into Qore is recorded in
[qoretechnologies/qore#5366](https://github.com/qoretechnologies/qore/issues/5366) and in
`design/json-module-migration.md` in the Qore repository.

## Licensing

The module source is dual-licensed LGPL 2.1 / MIT and keeps that licensing in the Qore tree; the
license texts are on each release branch and in the Qore repository.
