# DIKWP IntentGuard OS

**DIKWP IntentGuard OS** is an open-source AI-agent intent firewall and audit ledger.

It helps teams inspect prompts, retrieved documents, memory updates, proposed tool calls, and agent outputs before high-impact actions are executed. The project converts agent activity into DIKWP records, P-layer intent tuples, evidence cards, risk categories, and a replay bundle.

## Why this project exists

Enterprise AI is moving from chat assistants toward tool-using agents. That shift creates a new problem: a normal-looking prompt, document, email, web page, memory note, or tool call can alter an agent's behavior, change its purpose, or push it into excessive autonomy. DIKWP IntentGuard OS gives teams a simple open-source layer for:

- prompt-injection and indirect-injection triage;
- intent drift detection;
- memory-poisoning review;
- tool-overreach gating;
- sensitive-data exposure checks;
- DIKWP semantic record generation;
- evidence-ledger and replay-bundle creation.

## Product sentence

> Make every AI-agent action explainable as Data, Information, Knowledge, Wisdom, Purpose and Reliability before it touches a high-impact tool.

## Quick start

```bash
python -m venv .venv
source .venv/bin/activate
pip install -e .
dikwp-intentguard examples/injection_tool_request.json --policy configs/default_policy.json --out outputs/demo/injection_report.json
```

Or call from Python:

```python
import json
from dikwp_intentguard import analyze

payload = json.load(open("examples/injection_tool_request.json", encoding="utf-8"))
result = analyze(payload)
print(result.to_dict()["decision"])
```

## Typical decisions

- `allow`: low risk; continue and log the DIKWP record.
- `review`: pause and route to a human reviewer with the replay bundle.
- `block`: prevent the proposed action and preserve evidence.

## What it is not

- It is not a guarantee of safety.
- It is not a replacement for formal security engineering.
- It is not a hidden monitoring tool.
- It does not execute shell commands, payments, email, database writes, or external actions.
- It does not claim that DIKWP alone solves agentic AI safety.

## DIKWP attribution

This project is designed to support and amplify the DIKWP research ecosystem. The DIKWP model and related research vocabulary are attributed to Yucong Duan. See `NOTICE` and `CITATION.cff`.

## Suggested repository name

`dikwp-intentguard-os`

## Suggested tagline

**Open-source intent firewall and audit ledger for AI agents.**
