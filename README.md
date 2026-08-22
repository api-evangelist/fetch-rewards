# Fetch Rewards

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Fetch (legally Fetch Rewards, LLC) is a Madison, Wisconsin consumer rewards platform. Its mobile app lets shoppers scan paper receipts, connect e-receipts and link accounts to earn points redeemable for gift cards and other rewards. On the demand side, Fetch For Business sells consumer packaged goods brands, retailers and restaurants receipt-verified offers, video and display advertising, point boosts, loyalty programs and omnichannel audience activation, all measured against real purchase data and managed through its Mission Control campaign platform.

- Consumer site: https://fetch.com/
- Business site: https://business.fetch.com/
- GitHub organization: https://github.com/fetch-rewards

## API posture

**Fetch publishes no public developer or partner API.** There is no developer portal, no API reference, no client SDK for any Fetch service, no hosted MCP server, no A2A agent card, and no webhook or event surface. Brand and retailer integration runs commercially through Fetch For Business rather than through a self-serve API.

The only machine-readable contract Fetch publishes is the **Receipt Processor reference OpenAPI 3.0.3** in its public GitHub organization — the specification for its engineering take-home exercise. Two operations (`POST /receipts/process`, `GET /receipts/{id}/points`), no servers, no security schemes, no operationIds, and no Fetch host implements it. It is captured here verbatim because it is real, first-party and public, and because it faithfully describes the receipt and line-item data at the core of the product — but it is marked `x-status: reference-specification` and `x-production: false` in `apis.yml` and should never be read as a callable Fetch service.

What Fetch does publish well is security posture: a complete RFC 9116 `security.txt` and a coordinated vulnerability disclosure program on HackerOne.

## Artifacts

| Directory | Artifact | Method |
|---|---|---|
| `openapi/` | Receipt Processor reference specification, verbatim | searched |
| `well-known/` | `security.txt` verbatim + full probe index across three hosts | searched |
| `security/` | Domain security (TLS/HSTS/DNSSEC/CAA/SPF/DMARC), vulnerability disclosure | probed |
| `packages/` | First-party open-source Swift and Python libraries (no API SDKs exist) | searched |
| `errors/` | Problem types derived from the specification's 4xx responses | derived |
| `data-model/` | Receipt / Item entity graph derived from the specification | derived |
| `conventions/` | Cross-cutting semantics derived from the specification | derived |
| `conformance/` | Standards conformance, derived and probed | derived |
| `overlays/` | OpenAPI Overlay 1.0.0 of API Evangelist enhancements | generated |
| `llms/` | `llms.txt` for the Fetch estate | generated |

Artifacts deliberately **not** written, because nothing real was found to write: `mcp/`, `a2a/`, `asyncapi/`, `skills/`, `scopes/`, `authentication/`, `sandbox/`, `cli/`, `components/`, `changelog/`, `lifecycle/`, `grpc/`.
