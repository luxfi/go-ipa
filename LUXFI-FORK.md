# LUXFI-FORK

This is a luxfi-maintained fork of [crate-crypto/go-ipa](https://github.com/crate-crypto/go-ipa).

## Pin

* Upstream branch: `master`
* Commit SHA: `53bbb0ceb27adb011950fd0fce885ad6d4516f84` (2024-07-24)
* License: Apache-2.0 or MIT (see `LICENSE-APACHE`, `LICENSE-MIT`, `NOTICE`)

## Why this fork exists

go-ipa provides Bandersnatch + IPA primitives in Go. luxfi consumes the KAT
vectors and Bandersnatch curve params for:

* `luxcpp/crypto/banderwagon/` — first-party C++ port (LP-137 #101)
* `luxcpp/crypto/ipa/` — IPA + Pedersen + Verkle (LP-137 sibling #104)
* `lux/crypto` Go layer — replaces `github.com/crate-crypto/go-ipa` via
  go.mod replace directive

Owning the fork pins the Bandersnatch parameters (q, A, D, generators) so
upstream parameter churn cannot silently invalidate Pedersen commitments
already on chain.

## Sync policy

* Track upstream `master` snapshots only.
* Pull into `sync/<yyyy-mm-dd>` branches. Re-run Bandersnatch + IPA KATs in
  luxcpp/crypto/{banderwagon,ipa}. Merge to `master` only when KATs match.
* Curve parameter changes are a hard stop — open an issue, do not merge.

## Maintainer

luxfi crypto team. Contact via the `luxfi/crypto` repo.
