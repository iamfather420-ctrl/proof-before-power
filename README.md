# Proof Before Power — Local Simulation

This repository is a **local policy-engine demonstration**, not a production authorization service.

## Security boundary

- The engine's `demo.*` token is a deterministic SHA-256 checksum over public inputs. Anyone with the inputs can reproduce it.
- It is **not** a digital signature, proof of human identity, authenticated approval, or production authorization.
- The UI's account ledger and tool runner are in-memory simulation components. They do not connect to or mutate real customer accounts or production systems.
- An `ALLOW` decision means only that the demo policy obligations hold for the simulated action.
- The receipt hash detects changes to the receipt body; it does not authenticate the receipt's author or provide trusted timestamping.

A production implementation must use an authenticated identity provider, server-side policy enforcement, asymmetric signatures verified against trusted public keys, trusted time, durable audit storage, and a separately controlled execution adapter. None of those production controls are provided by this demo.

## Run

Open the static site or serve the `public` directory. Run the engine checks with:

```sh
node public/engine/proof-engine.test.mjs
```
