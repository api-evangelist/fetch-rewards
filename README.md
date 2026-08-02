# Fetch Rewards

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
