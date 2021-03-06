# Swift Programming Language Evolution
[![Swift](https://img.shields.io/badge/Swift%204%20stage%202-Open%20to%20requests-brightgreen.svg)](#swift_stage)


**Before you initiate a pull request**, please read the process document. Ideas should be thoroughly discussed on the [swift-evolution mailing list](https://swift.org/community/#swift-evolution) first.

This repository tracks the ongoing evolution of Swift. It contains:

* Goals for upcoming Swift releases (this document).
* The [Swift evolution review status][proposal-status] tracking proposals to change Swift.
* The [Swift evolution process](process.md) that governs the evolution of Swift.
* [Commonly Rejected Changes](commonly_proposed.md), proposals which have been denied in the past.

This document describes goals for the Swift language on a per-release
basis, usually listing minor releases adding to the currently shipping
version and one major release out.  Each release will have many
smaller features or changes independent of these larger goals, and not
all goals are reached for each release.

Goals for past versions are included at the bottom of the document for
historical purposes, but are not necessarily indicative of the
features shipped. The release notes for each shipped version are the
definitive list of notable changes in each release.
<a name="swift_stage"></a>
## Development major version:  Swift 4.0

Expected release date: Late 2017

The Swift 4 release is designed around two primary goals: to provide
source stability for Swift 3 code and to provide ABI stability for the
Swift standard library. To that end, the Swift 4 release will be
divided into two stages.

Stage 1 focuses on the essentials required for source and ABI
stability. Features that don't fundamentally change the ABI of
existing language features or imply an ABI-breaking change to the
standard library will not be considered in this stage. **Swift 4 is
currently only considering proposals that fit in Stage 1**.

Stage 2 will commence once the implementation work on the Stage 1
features is cresting, and can contain a few other large and small
features. We expect that stage 2 will commence some time in Spring
2017.

The high-priority features supporting Stage 1's source and ABI
stability goals are:

* Source stability features: the Swift language will need [some
  accommodations](https://github.com/apple/swift-evolution/blob/master/proposals/0141-available-by-swift-version.md)
  to support code bases that target different language versions, to
  help Swift deliver on its source-compatibility goals while still
  enabling rapid progress.

* Resilience: resilience provides a way for public APIs to evolve over
  time, while maintaining a stable ABI. For example, resilience
  eliminates the [fragile base class
  problem](https://en.wikipedia.org/wiki/Fragile_base_class) that
  occurs in some object-oriented languages (e.g., C++) by describing
  the types of API changes that can be made without breaking ABI
  (e.g., "a new stored property or method can be added to a class").

* Stabilizing the ABI: There are a ton of small details that need to
  be audited and improved in the code generation model, including
  interaction with the Swift runtime. While not specifically
  user-facing, the decisions here affect performance and (in some rare
  cases) the future evolution of Swift.

* Generics improvements needed by the standard library: the standard
  library has a number of workarounds for language deficiencies, many
  of which manifest as extraneous underscored protocols and
  workarounds. If the underlying language deficiencies remain, they
  become a permanent part of the stable ABI. [Conditional
  conformances](https://github.com/apple/swift-evolution/blob/master/proposals/0143-conditional-conformances.md),
  [recursive protocol
  requirements](https://github.com/apple/swift/blob/master/docs/GenericsManifesto.md#recursive-protocol-constraints-),
  and [where clauses for associated
  types](https://github.com/apple/swift-evolution/blob/master/proposals/0142-associated-types-constraints.md)
  are known to be in this category, but it's plausible that other
  features will be in scope if they would be used in the standard
  library.

* String re-evaluation: String is one of the most important
  fundamental types in the language. Swift 4 seeks to make strings more
  powerful and easier-to-use, while retaining Unicode correctness by
  default.

* Memory ownership model: an (opt-in) Cyclone/Rust-inspired memory
  ownership model is highly desired by systems programmers and for
  other high-performance applications that want predictable and
  deterministic performance. This feature will fundamentally shape the
  ABI, from low-level language concerns such as "inout" and low-level
  "addressors" to its impact on the standard library. While a full
  memory ownership model is likely too large for Swift 4 stage 1, we
  need a comprehensive design to understand how it will change the
  ABI.

## Previous releases

* [Swift 3.0](releases/swift-3_0.md) - Released on September 13, 2016
* [Swift 2.2](releases/swift-2_2.md) - Released on March 21, 2016

[proposal-status]: https://apple.github.io/swift-evolution/
