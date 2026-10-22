# Security policy

## Reporting a vulnerability

Email **admin@footval.com** with "SECURITY" in the subject, a description, the affected component
(this repository's manifests and skills, or the hosted server at `https://api.footval.com/mcp`) and
steps to reproduce. Please do not open a public issue for a vulnerability. We aim to acknowledge
reports within a few business days.

## Scope and design

- This repository contains client configuration, plugin manifests and agent skills. It ships no
  credentials and no server code.
- The hosted MCP server exposes 15 tools, all annotated `readOnlyHint: true` and
  `destructiveHint: false`. None of them writes, posts, buys or deletes anything.
- Authentication is OAuth 2.1 against FootVal's own authorization server (dynamic client
  registration, client ID metadata documents, PKCE S256, scope `footval.read`, OpenID Connect), or
  a personal `fvk_` API key that the user can revoke at any time from
  <https://footval.com/en/mcp#account>. Tokens are opaque and checked on every call, so
  disconnecting an app ends its access immediately.

## Supported versions

Only the latest commit of this repository and the current hosted server are supported.
