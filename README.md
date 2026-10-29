# ProSocial plugin

ProSocial helps you improve your relationships with the people around you, and
learn about yourself along the way. This plugin brings it into Claude, ChatGPT
and Codex:

- **Take the People Skills Index (PSI) free, in the chat.** Five short sections
  show how you read people, how you sound, how you write, and how you see
  yourself. A ProSocial panel runs each section while the assistant guides you
  through it and then through every result.
- **Get help tailored to how you come across.** With your PSI complete, the
  assistant uses your profile to prepare you for a hard conversation, rework a
  message, or get ready to meet someone new.
- **Write in your own voice.** If you approve an AI Writing Fingerprint in
  ProSocial, the assistant can draft as you.

It adds one skill and connects the authenticated ProSocial MCP server at
`https://app.tryprosocial.com/mcp`, which provides these tools:

```text
open_people_skills_index
continue_people_skills_index
get_my_people_skills_profile
get_my_writing_fingerprint
```

The PSI panel needs a host that shows MCP Apps, such as Claude or ChatGPT.
Claude Code and Codex use the profile and writing tools. The tools act only
for the connected member. They cannot select another person
or change PSI scores.

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
secret. It requests only `openid` and `people_skills:read`. Connecting signs
you in to ProSocial or creates your free account. Browser session cookies,
ProSocial API keys, user IDs, and profile IDs are not accepted by the tools.

## Security and data controls

Completing OAuth turns profile sharing on, so the tools can run the PSI and
return the complete profile once the member has finished it. A member who
turned **People Skills profile sharing** off in ProSocial Settings stays off.
The AI Writing Fingerprint has its own sharing switch.

Turning profile sharing off blocks every future PSI read and session. Disconnecting ProSocial
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
