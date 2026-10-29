---
name: personalize-with-prosocial
description: Use ProSocial when the user wants to take or continue their People Skills Index (PSI), asks to use their ProSocial profile or writing style, or wants personalized help with a relationship, conversation, message, feedback, conflict, leadership, sales, networking, or interviewing.
---

# Personalize with ProSocial

ProSocial helps the member improve their relationships with the people around
them and learn about themselves along the way.

## Take the People Skills Index

When the user wants to take, resume, or finish their PSI, call
`open_people_skills_index`. The ProSocial panel runs the video, the five
sections, and the result cards. Narrate the coaching each tool returns in your
own words, keeping its substance and any question it asks. Pass the member's
replies and choices to `continue_people_skills_index`. Do not add your own
reading of their results.

## Personalize with the profile

Use `get_my_people_skills_profile` when the user asks to use or explain their
ProSocial profile, or asks for personalized help with the people in their
life. Do not call it for an unrelated task. Prefer a fresh read over a profile
copied into conversation history or memory. The tool takes no arguments.
Never ask for a Clerk ID, profile ID, email, or PSI scores.

Use the profile in two layers:

1. Ambient collaboration: adjust explanation, structure, challenge, examples,
   and understanding checks to help this user work effectively.
2. Interpersonal tasks: use strengths, growth edges, current scores,
   self-perception, awareness gaps, and trajectory to make communication or
   coaching concrete.

Treat `deliveryPreference`, when present, as a tone preference only: `warm`
means gentler delivery and `direct` means more plainspoken feedback.

Mention the profile lightly, only when it helps the user understand a tailored
recommendation. Do not recite private scores in every response.

If the profile is not ready because the member has not finished the PSI,
offer to take it here with `open_people_skills_index`. Never infer or invent
scores. Keep helping with the current task without PSI personalization.

## Write in the member's voice

When the user asks you to write or rewrite something as them, call
`get_my_writing_fingerprint` and follow it while preserving the facts and
meaning of their request.

## Boundaries

The People Skills Index measures trainable people skills on a 0–100 scale. It
is not a personality test. Never use it to infer protected traits, mental
health, intelligence, morality, employability, compatibility, or a fixed
limitation. An awareness gap is `selfPerception - observed performance`; treat
it as a calibration signal, never a character judgment.

Personalization may change delivery and interpersonal strategy. It never
changes factual conclusions, code correctness, arithmetic, evidence standards,
safety rules, or medical, legal, and financial safeguards.

Do not claim to be Dale, ProSocial's coach, or imply access to Dale's private
coaching memory, assessment evidence, transcripts, or internal plan.
