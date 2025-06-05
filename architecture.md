# Architecture: DAO Series Activation Protocol

## Overview

DAO Series Activation Protocol enables the creation of decentralized networks for managing real assets through legally structured DAO entities.
It introduces a two-layer model:

1. **Genesis Layer** – the base registry and control layer for initiating Master DAO nodes;
2. **Master DAO** – a reproducible, Series-enabled DAO structure registered in the legal system (e.g., Delaware Series LLC).

Each Master DAO can later spawn DAO Series to manage specific real assets.

This approach enables protocol-based horizontal scalability of Master DAO nodes within a decentralized network and vertical scalability of DAO Series under each node.
All Master DAOs are formed under Delaware law. Initiators may be located anywhere in the world, while real assets managed by DAO Series may be physically located across various countries and regions. Ownership and governance are unified through protocol-defined rules.

---

## 1. Genesis Layer

### Purpose

* Acts as the protocol-level validator and coordinator of Master DAO creation;
* Ensures name uniqueness, jurisdictional alignment, and legal traceability.

### Key Functions

* `checkAndReserveLegalName(name, jurisdiction)`
* `submitDeploymentIntent(...)`
* `confirmRegistration(...)`
* Stores IPFS hashes of DAO agreements and registration proofs.

### On-chain Data Example

```json
{
  "dao_name": "Reeblink Master DAO",
  "jurisdiction": "Delaware",
  "reserved_by": "0xInitiatorAddress",
  "agreement_hash": "ipfs://Qm...",
  "registration_proof": "ipfs://Qx...",
  "status": "active"
}
```

---

## 2. Master DAO

### Purpose

* A legally registered DAO node (Delaware Series LLC Master entity);
* Can spawn DAO Series with digital governance;
* Owns or governs real assets through protocol-defined structures.

### Key Parameters

* DAO name and jurisdiction;
* Operating agreement hash (immutable reference);
* Manager address (EOA or multisig);
* Contract link to Genesis record.

### Smart Contract Components

* `MasterDAO.sol` (upgradeable or minimal proxy);
* Optional: Series Factory for DAO Series creation.

---

## 3. CLI / Deployment Tool

The CLI tool acts as a bridge between initiators and the protocol. It supports:

* Name reservation via Genesis Layer;
* Operating agreement auto-generation from templates;
* IPFS publishing of legal docs;
* Submission of `DeploymentIntent`;
* Status tracking and legal proof confirmation.

---

## 4. Legal Document Workflow

The protocol includes a standardized legal operating agreement template that:

* Fills in dynamic fields (DAO name, jurisdiction, initiator address);
* Can be downloaded by a certified agent (secretary);
* Is submitted to the state registry (e.g., Delaware);
* Returns registration proof uploaded to IPFS/Arweave;
* Finalized through `confirmRegistration` on Genesis Layer.

---

## 5. DAO Series (Planned Stage)

Although Series creation is not included in this MVP, the protocol is designed for:

* DAO Series issuance via Master DAO;
* NFT or token-bound representations of real assets;
* Global asset location support under unified governance logic.

---

## Token Architecture Note

While the MVP does not include a network token, the protocol is designed to support:

* Future token issuance tied to real assets within DAO Series;
* Integration of usage-based or rent-generating assets;
* Tokenomics for revenue distribution and liquidity.

A full decentralized real asset network requires a token representing the value of a discrete unit of a real asset that is in use and generating verifiable financial flow.

---

## Status

This document describes the architecture covered by the MVP scope.
Token mechanics, DAO Series activation, and on-chain revenue handling are reserved for future phases.

See also: `roadmap.md`
