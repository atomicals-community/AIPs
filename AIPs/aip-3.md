---
aip: 3
title: Remove duplicate bytes field `$d` for Atomicals
status: Draft
type: Standards Track
category: Application
author: Alex Li <@AlexV525>.
created: 2024-1-11
---

## Abstract

This proposal is targeting to remove the duplicate bytes field (`$d`) from Atomicals queries.

## Motivation

The first implementation is `$d`, which represents `data`, without accuracy.
Then in the commit `95759812`, `$b` was added to represent `bytes`, which is more accurate.
The `$b` and `$d` are identical, but they are both provided during serializations.
This raises the cost of the amount of data in each query.

## Specification

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "NOT RECOMMENDED", "MAY", and "OPTIONAL"
in this document are to be interpreted as described in RFC 2119 and RFC 8174.

Applications should use `$b` for serializations instead. `$d` is removed for all Atomicals queries.
`$b` is the hex string of the raw bytes. It occurs with mint info and the state of Atomicals.

## Backwards Compatibility

Applications should migrate from any `$d` usages to `$b` before/after the proposal.
The usage of `$b` is the same as `$d`.

## References

- https://github.com/atomicals/atomicals-electrumx/commit/9575981251543742a1a6d9f6b3cf1635698c6328
- https://github.com/atomicals/atomicals-electrumx/blob/1cc2d7238cd9ad9e349432e058f3917fcdda98b9/electrumx/lib/util_atomicals.py#L1141-L1142

## Copyright

Copyright and related rights waived via [CC0](../LICENSE.md).
