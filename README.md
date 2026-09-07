### Ziwei Guo — Founder, [Witnora](https://witnora.com)

**Safeguards for AI agents handling refunds and order cancellations.**

I build Witnora to help teams put clear limits around AI actions that affect real customers. We check agreed permissions **before an action runs**, control execution through a customer-owned boundary, and **independently check the result** in the business system. A signed receipt connects the permission, execution, and observed result.

**[See a refund walkthrough](https://witnora.com/demo/shopify-refund-assurance)** · **[Explore the open-source framework](https://github.com/witnora/witnora-framework)** · **[Contact me](mailto:ziwei@witnora.com)**

The walkthrough is a recorded test-mode replay of retained evidence; it issues no new refunds.

I'm looking for early design partners to test **one refund or cancellation workflow at a time**. I build the product and work directly on integrations and technical support.

<details>
<summary><strong>For engineers: verify the evidence yourself</strong></summary>

The Python verifier and test vectors are open under Apache-2.0. After obtaining the source, verification runs locally with no Witnora account or network connection.

```bash
git clone --depth 1 https://github.com/witnora/witnora-framework
cd witnora-framework/packages/witnora-verifier-python
python -m unittest discover -s tests
PYTHONPATH=src python -m witnora_verifier.cli conformance ../../test-vectors/witnora-v0.2-conformance
```

- [Offline verifier (Python)](https://github.com/witnora/witnora-framework/tree/main/packages/witnora-verifier-python) — canonical JSON, Ed25519 signatures, and conformance tests.
- [Trust bootstrap](https://github.com/witnora/witnora-framework/blob/main/docs/security/trust-bootstrap.md) — pin trusted roots separately; an evidence packet cannot authorize its own root.

Signature verification checks record integrity and authenticity relative to the trusted key. Outcome verification depends on the separate observation and its configured scope.

</details>

Coverage applies only to connected, explicitly configured action paths. Witnora does not guarantee all future agent behavior or claim third-party certification.
