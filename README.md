# Penvire backend

> **Status:** early development, not ready for production use.

The backend services of Penvire, an open-source platform for penetration testing consultancies.

## What goes here

The product services, from tenants and engagements to evidence, findings and reporting. Authentication uses proven components: Keycloak as the bundled identity provider, or any OpenID provider that meets the documented requirements. Penvire never ships hand-written authentication.

## Related

- [penvire-contracts](https://github.com/Penvire/penvire-contracts): API and event contracts
- [penvire-client](https://github.com/Penvire/penvire-client): web UI
- [penvire-docs](https://github.com/Penvire/penvire-docs): architecture and decisions

## License

[AGPL-3.0](LICENSE)

## Contributing

Commits must be signed and follow [Conventional Commits](https://www.conventionalcommits.org/). Pull requests are merged with a merge commit.

## Security

See the [Penvire security policy](https://github.com/Penvire/.github/blob/main/SECURITY.md).
