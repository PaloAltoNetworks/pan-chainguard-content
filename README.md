# pan-chainguard-content - Certificate Content for pan-chainguard

`pan-chainguard-content` provides pre-generated, up-to-date content
which can be used to simplify the deployment of
[pan-chainguard](https://github.com/PaloAltoNetworks/pan-chainguard).

## Execution Process

+ Run daily at 11:00 UTC

+ Use `pan-chainguard` **main** branch

+ Get latest *CCADB All Certificate Information* CSV file

+ Run `sprocket.py` with sources Mozilla, Apple, Microsoft and Chrome
  to create a new custom root fingerprints CSV file

+ Run `chain.py` to create:
  + a new intermediate fingerprints CSV file
  + a new certificate tree JSON file

+ Run `chainring.py` to create a certificate tree HTML document

+ Run `link.py` to create a new certificate archive from the previous
  archive

## Certificate Archive

The new certificate archive can be used directly by the `guard.py`
program if you use a root store with all vendor sources.

Or if your root store uses a subset of vendor sources, the archive can
be used as old certificates by the `link.py` program to create a new
archive for your custom root store.

### Download Certificate Archive Using `curl`

```
  $ curl -LO https://raw.githubusercontent.com/PaloAltoNetworks/pan-chainguard-content/main/latest-certs/certificates-new.tgz

```
