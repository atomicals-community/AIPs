---
aip: 1
title: AIP Purpose and Guidelines
status: Draft
type: Meta
author: Alex Li <@AlexV525>, neeboo <@neeboo>, brutoshi <@brutoshi>.
created: 2024-1-4
---

## What is an AIP?

AIP stands for Atomicals Improvement Proposal.
An AIP is a design document providing information to the Atomicals community,
or describing a new feature for Atomicals or its processes or environment.
The AIP should provide a concise technical specification of the feature and a rationale for the feature.
The AIP author is responsible for building consensus within the community and documenting dissenting opinions.

## AIP Rationale

We intend AIPs to be the primary mechanisms for proposing new features,
for collecting community technical input on an issue,
and for documenting the design decisions that have gone into Atomicals.
Because the AIPs are maintained as text files in a versioned repository,
their revision history is the historical record of the feature proposal.

For Atomicals implementers, AIPs are a convenient way to track the progress of their implementation.
Ideally each implementation maintainer would list the AIPs that they have implemented.
This will give end users a convenient way to know the current status of a given implementation or library.

## AIP Types

There are three types of AIP:

- A **Standards Track AIP** describes any change that affects most or all Atomicals implementations,
  such as—a change to the network protocol, a change in block or transaction validity rules, proposed application standards/conventions,
  or any change or addition that affects the interoperability of applications using Atomicals.
  Standards Track AIPs consist of three parts—a design document, an implementation,
  and (if warranted) an update to the [formal specification](https://github.com/atomicals-community/atomicals-guide).
  Furthermore, Standards Track AIPs can be broken down into the following categories:
  - **Core**: improvements requiring a consensus fork.
  - **Networking**: includes improvements around [proxy](https://github.com/atomicals/electrumx-proxy)
    and [indexer](https://github.com/atomicals/atomicals-electrumx).
  - **Interface**: includes improvements around language-level standards.
  - **Application**: application-level standards and conventions, including contract standards such as token standards,
    name registries, URI schemes, library/package formats, and wallet formats.

- A **Meta AIP** describes a process surrounding Atomicals or proposes a change to (or an event in) a process.
  Process AIPs are like Standards Track AIPs but apply to areas other than the Atomicals protocol itself.
  They may propose an implementation, but not to Atomicals's codebase; they often require community consensus;
  unlike Informational AIPs, they are more than recommendations, and users are typically not free to ignore them.
  Examples include procedures, guidelines, changes to the decision-making process,
  and changes to the tools or environment used in Atomicals development.
  Any meta-AIP is also considered a Process AIP.

- An **Informational AIP** describes an Atomicals design issue,
  or provides general guidelines or information to the Atomicals community,
  but does not propose a new feature.
  Informational AIPs do not necessarily represent Atomicals community consensus or a recommendation,
  so users and implementers are free to ignore Informational AIPs or follow their advice.

It is highly recommended that a single AIP contain a single key proposal or new idea.
The more focused the AIP, the more successful it tends to be.
A change to one client doesn't require an AIP;
a change that affects multiple clients, or defines a standard for multiple apps to use, does.

An AIP must meet certain minimum criteria.
It must be a clear and complete description of the proposed enhancement.
The enhancement must represent a net improvement.
The proposed implementation, if applicable, must be solid and must not complicate the protocol unduly.

## AIP Work Flow

### Shepherding an AIP

Parties involved in the process are you, the champion or *AIP author*, and the *AIP reviewers*.
The *AIP reviewer* is currently [@atomicals](https://github.com/atomicals) only.

Before you begin writing a formal AIP, you should vet your idea.
Ask the Atomicals community first if an idea is original to avoid wasting time on something that will be rejected based on prior research.
It is thus recommended to open a discussion thread on
[the Atomicals Community Discussions](https://github.com/orgs/atomicals-community/discussions) to do this.

Once the idea has been vetted, your next responsibility will be to present
(by means of an AIP) the idea to the reviewers and all interested parties,
invite editors, developers, and the community to give feedback on the aforementioned channels.
You should try and gauge whether the interest in your AIP is commensurate with
both the work involved in implementing it and how many parties will have to conform to it.
For example, the work required for implementing a Core AIP will be much greater than for an Application
and the AIP will need sufficient interest from the Atomicals client teams.
Negative community feedback will be taken into consideration and may prevent your AIP from moving past the Draft stage.

### Core AIPs

For Core AIPs, given that they require client implementations to be considered **Final** (see "AIPs Process" below),
you will need to either provide an implementation for clients or convince clients to implement your AIP.

> [!WARNING]
> If you are shepherding an AIP, you can make the process of building community consensus easier by making sure that
> [the Atomicals Community Discussions](https://github.com/orgs/atomicals-community/discussions) thread for your AIP includes or links to
> as much of the community discussion as possible and that various stakeholders are well-represented.

*In short, your role as the champion is to write the AIP using the style and format described below,
shepherd the discussions in the appropriate forums, and build community consensus around the idea.*

### AIP Process

The following is the standardization process for all AIPs in all tracks:

- `Idea` - An idea that is pre-draft. This is not tracked within the AIP Repository.

- `Draft` - The first formally tracked stage of an AIP in development. An AIP is merged by an AIP Editor into the AIP repository when properly formatted.

- `Review` - An AIP Author marks an AIP as ready for and requesting Peer Review.

- `Last Call` - This is the final review window for an AIP before moving to `Final`.
  An AIP editor will assign `Last Call` status and set a review end date (`last-call-deadline`), typically 14 days later.
  
  If this period results in necessary normative changes it will revert the AIP to `Review`.

- `Final` - This AIP represents the final standard.
  A Final AIP exists in a state of finality and should only be updated to correct errata and add non-normative clarifications.
  
  A PR moving an AIP from Last Call to Final **SHOULD** contain no changes other than the status update.
  Any content or editorial proposed change SHOULD be separate from this status-updating PR and committed prior to it.

- `Stagnant` - Any AIP in `Draft` or `Review` or `Last Call` if inactive for a period of 6 months or greater is moved to `Stagnant`.
  
  An AIP may be resurrected from this state by Authors or AIP Editors through moving it back to `Draft` or it's earlier status.
  If not resurrected, a proposal may stay forever in this status.

  > *AIP Authors are notified of any algorithmic change to the status of their AIP*

- `Withdrawn` - The AIP Author(s) have withdrawn the proposed AIP.
  This state has finality and can no longer be resurrected using this AIP number.
  If the idea is pursued at later date it is considered a new proposal.

- `Living` - A special status for AIPs that are designed to be continually updated and not reach a state of finality.
  This includes most notably AIP-1.

## What belongs in a successful AIP?

Each AIP should have the following parts:

- Preamble - RFC 822 style headers containing metadata about the AIP,
  including the AIP number, a short descriptive title (limited to a maximum of 44 characters),
  a description (limited to a maximum of 140 characters), and the author details.
  Irrespective of the category, the title and description should not include AIP number.
  See [below](./aip-1.md#aip-header-preamble) for details.
- Abstract - Abstract is a multi-sentence (short paragraph) technical summary.
  This should be a very terse and human-readable version of the specification section.
  Someone should be able to read only the abstract to get the gist of what this specification does.
- Motivation *(optional)* - A motivation section is critical for AIPs that want to change the Atomicals protocol.
  It should clearly explain why the existing protocol specification is inadequate to address the problem that the AIP solves.
  This section may be omitted if the motivation is evident.
- Specification - The technical specification should describe the syntax and semantics of any new feature.
  The specification should be detailed enough to allow competing, interoperable implementations for any of the current Atomicals platforms.
- Rationale - The rationale fleshes out the specification by describing what motivated the design and why particular design decisions were made.
  It should describe alternate designs that were considered and related work, e.g. how the feature is supported in other languages.
  The rationale should discuss important objections or concerns raised during discussion around the AIP.
- Backwards Compatibility *(optional)* - All AIPs that introduce backwards incompatibilities must include a section describing these incompatibilities and their consequences.
  The AIP must explain how the author proposes to deal with these incompatibilities.
  This section may be omitted if the proposal does not introduce any backwards incompatibilities,
  but this section must be included if backward incompatibilities exist.
- Test Cases *(optional)* - Test cases for an implementation are mandatory for AIPs that are affecting consensus changes.
  Tests should either be inlined in the AIP as data (such as input/expected output pairs, or included in `../assets/aip-###/<filename>`.
  This section may be omitted for non-Core proposals.
- Reference Implementation *(optional)* - An optional section that contains a reference/example implementation that people can use to assist in understanding or implementing this specification.
  This section may be omitted for all AIPs.
- Security Considerations - All AIPs must contain a section that discusses the security implications/considerations relevant to the proposed change.
  Include information that might be important for security discussions, surfaces risks and can be used throughout the life-cycle of the proposal.
  E.g. include security-relevant design decisions, concerns, important discussions,
  implementation-specific guidance and pitfalls, an outline of threats and risks and how they are being addressed.
  AIP submissions missing the "Security Considerations" section will be rejected.
  An AIP cannot proceed to status "Final" without a Security Considerations discussion deemed sufficient by the reviewers.
- Copyright Waiver - All AIPs must be in the public domain.
  The copyright waiver MUST link to the license file and use the following wording: `Copyright and related rights waived via [CC0](../LICENSE.md).`

## AIP Formats and Templates

AIPs should be written in Markdown format. There is a [template](https://github.com/atomicals-community/AIPs/blob/master/aip-template.md) to follow.

## AIP Header Preamble

Each AIP must begin with an [RFC 822](https://www.ietf.org/rfc/rfc822.txt) style header preamble, preceded and followed by three hyphens (`---`).
The headers must appear in the following order.

`aip`: *AIP number*

`title`: *The AIP title is a few words, not a complete sentence*

`description`: *Description is one full (short) sentence*

`author`: *The list of the author's or authors' name(s) and/or username(s), or name(s) and email(s). Details are below.*

`discussions-to`: *The url pointing to the official discussion thread*

`status`: *Draft, Review, Last Call, Final, Stagnant, Withdrawn, Living*

`last-call-deadline`: *The date last call period ends on* (Optional field, only needed when status is `Last Call`)

`type`: *One of `Standards Track`, `Meta`, or `Informational`*

`category`: *One of `Core`, `Networking`, `Interface`, or `Application`* (Optional field, only needed for `Standards Track` AIPs)

`created`: *Date the AIP was created on*

`requires`: *AIP number(s)* (Optional field)

`withdrawal-reason`: *A sentence explaining why the AIP was withdrawn.* (Optional field, only needed when status is `Withdrawn`)

Headers that permit lists must separate elements with commas.

Headers requiring dates will always do so in the format of ISO 8601 (yyyy-mm-dd).

### `author` header

The `author` header lists the names, email addresses or usernames of the authors/owners of the AIP.
Those who prefer anonymity may use a username only, or a first name and a username.
The format of the `author` header value must be:

> Random A. User &lt;address@dom.ain&gt;

or

> Random A. User (@username)

or

> Random A. User (@username) &lt;address@dom.ain&gt;

if the email address and/or GitHub username is included, and

> Random A. User

if neither the email address nor the GitHub username are given.

At least one author must use a GitHub username, in order to get notified on change requests and have the capability to approve or reject them.

### `discussions-to` header

While an AIP is a draft, a `discussions-to` header will indicate the URL where the AIP is being discussed.

The preferred discussion URL is a topic on [the Atomicals Community](https://github.com/orgs/atomicals-community/discussions).
The URL cannot point to Github pull requests, any URL which is ephemeral, and any URL which can get locked over time (i.e. Reddit topics).

### `type` header

The `type` header specifies the type of AIP: Standards Track, Meta, or Informational.
If the track is Standards please include the subcategory (core, networking, interface, or application).

### `category` header

The `category` header specifies the AIP's category. This is required for standards-track AIPs only.

### `created` header

The `created` header records the date that the AIP was assigned a number.
Both headers should be in yyyy-mm-dd format, e.g. 2001-08-14.

### `requires` header

AIPs may have a `requires` header, indicating the AIP numbers that this AIP depends on.
If such a dependency exists, this field is required.

A `requires` dependency is created when the current AIP cannot be understood or implemented without a concept or technical element from another AIP.
Merely mentioning another AIP does not necessarily create such a dependency.

## Linking to other AIPs

References to other AIPs should follow the format `AIP-##` where `##` is the AIP number you are referring to.
Each AIP that is referenced in an AIP **MUST** be accompanied by a relative markdown link the first time it is referenced,
and **MAY** be accompanied by a link on subsequent references.
The link **MUST** always be done via relative paths so that the links work in this GitHub repository,
forks of this repository, the main AIPs site, mirrors of the main AIP site, etc.
For example, you would link to this AIP as `./aip-1.md`.

## Auxiliary Files

Images, diagrams and auxiliary files should be included in a subdirectory of the `assets` folder for that AIP as follows:
`assets/aip-##` (where **##** is to be replaced with the AIP number).
When linking to an image in the AIP, use relative links such as `../assets/aip-1/image.png`.

## Transferring AIP Ownership

It occasionally becomes necessary to transfer ownership of AIPs to a new champion.
In general, we'd like to retain the original author as a co-author of the transferred AIP, but that's really up to the original author.
A good reason to transfer ownership is because the original author no longer has the time or interest in updating it or following through with the AIP process,
or has fallen off the face of the 'net (i.e. is unreachable or isn't responding to email).
A bad reason to transfer ownership is because you don't agree with the direction of the AIP.
We try to build consensus around an AIP, but if that's not possible, you can always submit a competing AIP.

If you are interested in assuming ownership of an AIP, send a message asking to take over,
addressed to both the original author and the AIP editor.
If the original author doesn't respond to the email in a timely manner,
the AIP editor will make a unilateral decision (it's not like such decisions can't be reversed :)).

## Style Guide

### Titles

The `title` field in the preamble:

- Should not include the word "standard" or any variation thereof; and
- Should not include the AIP's number.

### Descriptions

The `description` field in the preamble:

- Should not include the word "standard" or any variation thereof; and
- Should not include the AIP's number.

### AIP numbers

When referring to AIPs, it must be written in the hyphenated form `AIP-X` where `X` is that AIP's assigned number.

### RFC 2119 and RFC 8174

AIPs are encouraged to follow [RFC 2119](https://www.ietf.org/rfc/rfc2119.html) and
[RFC 8174](https://www.ietf.org/rfc/rfc8174.html) for terminology and to insert the following at the beginning of the Specification section:

> The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "NOT RECOMMENDED", "MAY", and "OPTIONAL"
> in this document are to be interpreted as described in RFC 2119 and RFC 8174.

## History

This document was derived heavily from [Etherum's EIP-1]((https://github.com/ethereum/EIPs).
In many places text was simply copied and modified.

## Copyright

Copyright and related rights waived via [CC0](../LICENSE.md).
