# Ethereum EIP-712 Signature 2021

This is a specification draft for a linked data signature suite using Ethereum EIP-712.

## Abstract

[Linked data signatures][ld-sigs] are used to cryptographically sign and verify
[linked data][] documents, a category that includes [Verifiable
Credentials][vc-data-model] (in their [linked data proof format][vc-ldp]), and
[Authorization Capabilities for Linked Data (ZCAP-LD, often referred to
colloquially as "ZCaps")][zcap-ld]. EIP-712 defines a way to cryptographically
hash and sign a typed JSON data structure.

In terms of cryptographic primitives, this signing stuite uses the hashing
(digest) algorithm `keccak256`, and the key types and signature algorithm
`secp256k1`, both of which are familiar and extensively supported in the
Ethereum ecosystem and, thus, most of the blockchain ecosystems branching out
from it. Similarly, the data structure type system is based on that of the
[Solidity][] programming language. Using this signature suite, an EIP-712
signing request can represent a request:
1. to issue (or "self-issue") a Verifiable Credential, or 
2. to present one or more Verifiable Credentials in a Verifiable Presentation,
3. to sign linked documents for other purposes, such as to or delegate or
   invoke Authorization Capabilities.

## Context

The world of blockchain-centric web applications, variously dependent on
traditional DNS and web architectures, is often referred to as "Web3" or "Web
3.0", because it centers data control and trust on permissionless data networks
like blockchains, rather than heirarchically-distributed (and CA-based)
authorities and clouds. Web3 applications tend to focus on cryptocurrency
"wallets" that manage keypairs controlling blockchain accounts. Very few
cryptocurrency wallets, particularly in the ecosystems of wallets based on the
Ethereum Virtual Machine (EVM, i.e., the distributed and chain-centric parser
for the [Solidity][] smart contract language), hold or parse verifiable
credentials, much less compile and sign conformant Verifiable Presentations,
with or without selective disclosure capabilities.

Cryptocurrency wallets (whether browser-extension-, mobile-app-, and/or
smart-contract-based) do, however, support multiple signing formats. The most
widely used of these is [EIP-191][], which allows a straightforward bytestring
to be displayed to the user and then prefixed and signed in the wallet. This
unstructured string cannot be used to sign Verifiable Credentials or Verifiable
Presentations, nor can it reach feature parity or compatibility with nuanced
authorization systems like OAuth, which is the token/signing format on which
OpenID Connect is based. For this, structured data objects need to be passed to
a wallet to be parsed and signed; complex authorization (and informed consent)
require the wallet to both parse and display that structured data.

The most widely-adopted standard for passing and parsing structured data to be
signed by wallets is [EIP-712][], which is supported by [Metamask][] and many
other major Ethereum ecoystem wallets. A web application, using APIs like
[web3][] which have quickly becomes common across the web3 development
environment and foundational to web3 user experiences, can request a user of a
supporting wallet to sign a message using their private key, and pass that
message (along with security and authorization metadata) as a structured JSON
object rather than a string. 

*Note: If a wallet supports the signing specification for [EIP-712][] but does
not parse the object to display it more intuitively to the wallet end-user, the
structured data object with whitespace stripped out may be displayed to the
end-user as a string for consent by analogy to EIP-191 signing. This is not
recommended practice for wallets, and would be unacceptable for most verifiable
credential use-cases.*

## Related specifications and References



References:
- [Ethereum Improvement Proposals - EIP-191: Signed Data Standard][EIP-191]
- [Ethereum Improvement Proposals - EIP-712: Ethereum typed structured data hashing and signing][EIP-712]
- [Metamask Blog - EIP712 is here: What to expect and how to use it][eip712-article]
- [W3C CCG - Linked Data Proofs - Linked Data Signatures][ld-sigs]
- [W3C CCG - Linked Data Glossary - Linked Data][linked data]
- [Wikipedia - MetaMask][Metamask]
- [MetaMask Docs -  Sign Typed Data v4][metamask-signing]
- [Wikipedia - Solidity (programming language)][Solidity]
- [W3C Verifiable Credentials Data Model (VC Data Model)][vc-data-model]
- [W3C VC Data Model - Linked Data Proofs][vc-ldp]
- [GitHub - ChainSafe/web3.js - Ethereum JavaScript API][web3]
- [W3C CCG - Authorization Capabilities for Linked Data (ZCAP-LD)][zcap-ld]

[EIP-191]: https://eips.ethereum.org/EIPS/eip-191
[EIP-712]: https://eips.ethereum.org/EIPS/eip-712
[Metamask]: https://en.wikipedia.org/wiki/MetaMask
[Solidity]: https://en.wikipedia.org/wiki/Solidity
[eip712-article]: https://medium.com/metamask/eip712-is-coming-what-to-expect-and-how-to-use-it-bb92fd1a7a26
[ld-sigs]: https://w3c-ccg.github.io/ld-proofs/#linked-data-signatures
[linked data]: https://www.w3.org/TR/ld-glossary/#linked-data
[metamask-signing]: https://docs.metamask.io/guide/signing-data.html#sign-typed-data-v4
[vc-data-model]: https://www.w3.org/TR/vc-data-model/
[vc-ldp]: https://www.w3.org/TR/vc-data-model/#linked-data-proofs
[web3]: https://github.com/ChainSafe/web3.js/
[zcap-ld]: https://w3c-ccg.github.io/zcap-ld/

## Maturity Warning

🚧 This linked data suite specification is under development; DO NOT use this in production without thorough review.

**Breaking changes may be pushed regularly.**

Latest rendered editor's draft:
https://w3c-ccg.github.io/ethereum-eip712-signature-2021-spec/
