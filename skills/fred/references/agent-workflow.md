# Agent workflow

## Every session

1. **Read the project entrypoint** (`docs/agent-guides/00-AGENT-ENTRYPOINT.md` or `AGENTS.md`). That file is the contract for *this* repo.
2. Follow its “do not”, verify commands, and “where things live” map.
3. If the task is build/implement/next-slice: read **OPEN-FRED-INDEX** execution table (not directory listing).
4. Open the FRED named by the user or the first open row whose dependencies are implemented (or an allowed fake).
5. Read architecture **only via links** from the entrypoint or that FRED.

## Picking work

- User named a FRED → that FRED, still respect listed dependencies.
- User said “next” → first open index row with deps satisfied.
- Draft FRED → deepen contracts against shipped deps before coding.

Do not start a later FRED because the filename number is higher.

## While implementing

- Stay inside the FRED’s surfaces and non-goals.
- Prefer application/command boundaries the entrypoint names; do not bypass them from agents or UI.
- After the slice: run the **project’s** verify commands from the entrypoint (placeholders in the template, not this skill’s invented scripts).
- Update the FRED’s task/acceptance checkboxes as you go.

## Close-out

Move the file, repair links, update the index. See [methodology.md](methodology.md).

## If FRED docs are absent

Offer bootstrap ([bootstrap.md](bootstrap.md)). If the user declines, still avoid inventing a parallel spec system in chat.

## Teammates without the skill

Point `AGENTS.md` / README at the entrypoint so `@`-attach is unnecessary.
