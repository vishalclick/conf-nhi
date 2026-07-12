# draft-chandwani-wimse-nhi-attestation-binding

**Binding Non-Human Identity Credentials to Remote Attestation Evidence**

This repository contains the source for an IETF Internet-Draft that
defines a framework for gating Non-Human Identity (NHI) credential
issuance and renewal — e.g. SPIFFE SVIDs and OAuth 2.0 tokens — on
fresh remote attestation evidence (Intel TDX, SGX, confidential GPU),
using the RATS (Remote ATtestation ProcedureS) Entity Attestation
Token model.

- **Latest draft**: [draft-chandwani-wimse-nhi-attestation-binding-00](draft-chandwani-wimse-nhi-attestation-binding-00.md)
- **Status**: Individual submission, not yet adopted by a working group
- **Intended WG**: [WIMSE](https://datatracker.ietf.org/wg/wimse/about/) (Workload Identity in Multi-System Environments)
- **Related work**: [RFC 9334 (RATS Architecture)](https://datatracker.ietf.org/doc/rfc9334/), [draft-kykdxy-rats-tdx-cgpu-ear-profile](https://datatracker.ietf.org/doc/draft-kykdxy-rats-tdx-cgpu-ear-profile/)

## Problem

Existing NHI credentialing (SPIFFE/SPIRE, OAuth workload tokens)
authenticates the *container* of identity — a keypair, a certificate,
a bearer token — but not the *runtime state* of the workload holding
it. A credential issued at bootstrap remains valid even if the
workload's attested environment is later tampered with, replaced, or
compromised, until the credential's natural expiry.

This draft proposes closing that gap by making credential issuance
and renewal conditional on a verified RATS Attestation Result, not
just a one-time bootstrap check.

## Repository structure

```
.
├── README.md
├── draft-chandwani-wimse-nhi-attestation-binding-00.md   # kramdown-rfc source (source of truth)
├── draft-chandwani-wimse-nhi-attestation-binding-00.xml  # generated XML (via kdrfc)
├── draft-chandwani-wimse-nhi-attestation-binding-00.txt  # generated plaintext RFC format
└── CHANGELOG.md
```

> Generated `.xml` and `.txt` files are build artifacts. Edit the
> `.md` source and regenerate rather than hand-editing the outputs.

## Building the draft

This draft is written in [kramdown-rfc](https://github.com/cabo/kramdown-rfc) markdown.

```bash
# Install tooling
gem install kramdown-rfc

# Generate .txt and .xml from the markdown source
kdrfc draft-chandwani-wimse-nhi-attestation-binding-00.md
```

This produces the official I-D `.txt` and `.xml` formats required for
Datatracker submission.

## Submitting / updating the draft

1. Edit the `.md` source and bump the revision number in the front
   matter (`-00` → `-01`, etc.) and filename.
2. Regenerate with `kdrfc`.
3. Submit via the [IETF Datatracker](https://datatracker.ietf.org/submit/).
4. Announce the revision on the [WIMSE WG mailing list](https://mailarchive.ietf.org/arch/browse/wimse/).

## Contributing

Feedback, issues, and pull requests are welcome — particularly on:

- Security Considerations (Section 7) — this is the section that
  will get the most scrutiny in review
- Alignment with `draft-ietf-wimse-arch` terminology as that document
  evolves
- Composite evidence handling for confidential GPU attestation

Per IETF norms, substantive technical contributions to the draft text
should also be visible on the WIMSE mailing list, not only in GitHub
issues/PRs, so they're part of the public IETF record.

## License

Contributions to IETF Internet-Drafts are governed by
[BCP 78](https://www.rfc-editor.org/info/bcp78) and the
[IETF Trust Legal Provisions](https://trustee.ietf.org/license-info/).
By contributing, you agree your contributions are made under these
terms.

## Author

Vishal Chandwani — vishalclick@gmail.com
