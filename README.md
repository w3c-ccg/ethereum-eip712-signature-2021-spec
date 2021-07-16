# Ethereum EIP-712 Signature 2021

This is a specification draft for a linked data signature suite using Ethereum EIP-712.

[Linked data signatures][ld-sigs] are used to cryptographically sign and verify [linked data][] documents, such as [Verifiable Credentials][vc-data-model] (in their [linked data proof format][vc-ldp]), and [Authorization Capabilities for Linked Data (ZCAP-LD)][zcap-ld].

EIP-712 defines a way to cryptographically hash and sign a typed data structure. Its hashing (digest) algorithm is `keccak256`, and signature algorithm is `secp256k1`. The data structure type system is based on that of the [Solidity][] programming language.

Cryptocurrency wallet and browser extensions such as [Metamask][] support EIP-712 signing requests. A web application, using APIs such as [web3][], can request a user of such a wallet to sign a message using their private key. The wallet prompts the user to sign the message or reject the request. By using EIP-712, the message can be a data structure, typically appearing like a JSON object, rather than text or a byte string.

`EthereumEip712Signature2021`, the type of linked data signature defined in this specification, uses [EIP-712][] for its cryptographic operations. With this signature suite, a EIP-712 signing request can represent a request to issue a Verifiable Credential, or to present a Verifiable Credential in a Verifiable Presentation, or to sign linked documents for other purposes, such as to delegate and invoke Authorization Capabilities.

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

🚧 This linked data suite specification is under development; DO NOT use this in production without thorough review.

Breaking changes may be pushed regularly.

Latest rendered editor's draft:
https://w3c-ccg.github.io/ethereum-eip712-signature-2021-spec/
