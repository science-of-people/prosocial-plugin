# ProSocial plugin: technical details

The plugin adds one skill, `personalize-with-prosocial`, and connects the
authenticated ProSocial MCP server at `https://app.tryprosocial.com/mcp`. The
server provides these tools:

```text
open_people_skills_index
continue_people_skills_index
get_my_people_skills_profile
get_my_writing_fingerprint
```

The PSI panel is an MCP App. It needs a host that shows MCP Apps, such as
Claude on the web and desktop, or ChatGPT. The voice section needs microphone
access, which Claude's phone apps do not give MCP Apps, so take that section
on the web or desktop. Claude Code and Codex use the profile and writing
tools. The tools act only for the connected member. They cannot select
another person or change PSI scores.

## Install

- Claude, Claude Desktop and the Claude phone apps: add ProSocial from
  **Customize > Plugins**, then connect it on the plugin's **Connectors** tab.
- Claude Code: run `/plugin directory`, or test a checkout of this repository
  with `claude --plugin-dir .` and connect ProSocial from `/mcp`.
- ChatGPT and Codex: install ProSocial from OpenAI's plugin directory.

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

Turning profile sharing off blocks every future PSI read and session.
Disconnecting ProSocial in the AI host stops that host from requesting new
tokens. Neither control can remove profile details already used in a
conversation or saved memory.

PSI measures trainable people skills. It is not a personality test. The plugin
must not use PSI to infer protected traits, mental health, intelligence,
morality, employability, compatibility, or a fixed limitation.

## Validate

From the repository root:

```bash
claude plugin validate . --strict
```
