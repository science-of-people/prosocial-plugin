# ProSocial plugin

Connect Claude to your measured ProSocial People Skills Index (PSI) profile.
The plugin adds one personalization skill and one authenticated, read-only MCP
tool:

```text
get_my_people_skills_profile
```

The tool reads the connected member's current PSI profile from:

```text
https://app.tryprosocial.com/mcp
```

It cannot select another person or change profile data.

## Install in Claude

After Anthropic approves the public listing, add the community marketplace and
install ProSocial:

```text
/plugin marketplace add anthropics/claude-plugins-community
/plugin install prosocial@claude-community
```

To test a checkout of this standalone repository before approval, run:

```bash
claude --plugin-dir .
```

Then open `/mcp` in Claude Code and connect ProSocial.

## Requirements and OAuth

- Claude Code 2.1.239 or later is required for the packaged OAuth settings.
- Local Claude Code uses `http://localhost:52991/callback`. Port 52991 must be
  available during sign-in. Stop the process that uses it and retry if the port
  is busy.
- Claude and Claude Desktop use Anthropic's cloud OAuth callback.
- Claude Code cloud sessions do not use the local callback in this package. Add
  ProSocial as a Claude connector before using it in a cloud session.

The public OAuth client uses authorization code with PKCE and has no client
secret. It requests only `openid` and `people_skills:read`. Browser session
cookies, ProSocial API keys, user IDs, and profile IDs are not accepted by the
tool.

## Security and data controls

Profile sharing is off by default. The connected member must enable **People
Skills profile sharing** in ProSocial Settings and complete OAuth before the
tool can return a complete PSI profile.

Turning profile sharing off blocks every future read. Disconnecting ProSocial
in the AI host stops that host from requesting new tokens. Neither control can
remove profile details already used in a conversation or saved memory.

PSI measures trainable people skills. It is not a personality test. The plugin
must not use PSI to infer protected traits, mental health, intelligence,
morality, employability, compatibility, or a fixed limitation.

## Validate

From this standalone repository root:

```bash
claude plugin validate . --strict
```

The source package also includes a Codex manifest. OpenAI and Codex installation
is available through their respective plugin distribution surfaces.

## Support and policies

- Website: https://app.tryprosocial.com
- Support: https://support.tryprosocial.com
- Privacy: https://tryprosocial.com/privacy/
- Terms: https://tryprosocial.com/terms/
