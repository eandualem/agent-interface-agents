# Contributing an agent

Open a pull request against `main` with one definition under `agents/<area>/<agent>/`. For example, a caption reviewer could live in `agents/video/caption-reviewer/`. Use descriptive lowercase names. Choose the primary area for its folder and add other relevant areas as tags.

| Path within the definition | What to include |
| --- | --- |
| `AGENTS.md` | What the agent does, the inputs it needs, how it works, and what a good result looks like. |
| `agent.json` | The runtime, model, effort, tags and applicable policy files. |
| `skills/<skill>/SKILL.md` | The complete skill and any scripts, examples or other files it needs, stored inside that skill’s folder. |
| `policies/<policy>.md` | The reusable text for each policy named in the configuration. |

For example, a contributor could use this `agent.json`:

```json
{
  "runtime": "claude",
  "model": "claude-opus-5-5",
  "effort": "high",
  "tags": ["video", "captions"],
  "policies": ["policies/accessibility.md"]
}
```

Include only skills and policies that apply. Use an empty policy list when none apply. Keep instructions in AGENTS.md and omit runtime-specific startup files. Use regular files and relative paths within the definition so someone with a fresh checkout can use it. Check that each configured policy and every skill support file exists.

To try a definition, copy its folder to an empty working directory. Select the runtime, model and effort from `agent.json` in your launcher. Give that runtime the local `AGENTS.md` and the listed policy files as instructions, and expose the bundled skill folders through its local skill mechanism. Run the example from the PR and compare the result with the expected outcome. The JSON describes these settings for the launcher or operator.

Describe the reusable method in your own words or include material you have permission to share. Use synthetic examples. Keep credentials, account details, private work history, internal instructions and identifying metadata out of the entire contribution, including commit messages and PR text.

In your PR, explain who the agent helps and how you tested it. A small example with an input and expected outcome lets reviewers try the definition. Outside contributors can open a PR directly from a fork.
