### Ziwei Guo — Founder, [Witnora](https://witnora.com)

Witnora adds an assurance layer around AI agent actions that change real systems:
check authority **before** the write, execute through a boundary the customer controls,
read the result back through a **separate** read-only path, and keep a signed receipt
that can be verified offline.

**Don't take my word for it.** The verifier and its test vectors are open (Apache-2.0),
and the check runs with no account and no network:

```bash
git clone --depth 1 https://github.com/Kakarottoooo/witnora-framework
cd witnora-framework/packages/witnora-verifier-python
python -m unittest discover -s tests
PYTHONPATH=src python -m witnora_verifier.cli conformance ../../test-vectors/witnora-v0.2-conformance
# {"overall":"PASS","passed":174,"failed":0,"networkUsed":false,...}
```

- [Offline verifier (Python)](https://github.com/Kakarottoooo/witnora-framework/tree/main/packages/witnora-verifier-python) — an independent canonical-JSON and Ed25519 implementation
- [Trust bootstrap](https://github.com/Kakarottoooo/witnora-framework/blob/main/docs/security/trust-bootstrap.md) — a root carried inside an evidence packet cannot authorize itself; pin it out of band
- [Recorded test-mode refund walkthrough](https://witnora.com/demo/shopify-refund-assurance) — replays retained evidence, issues no new refunds

**What this does not claim:** coverage of action paths that were never declared,
guarantees about future agent behavior, or any third-party certification.

I build this and run the integrations myself. If an agent on your team writes to a
system of record — refunds, cancellations, billing or account changes, payouts — I'd
like to hear how you check the result today: ziwei@witnora.com
