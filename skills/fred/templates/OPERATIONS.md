# {{PRODUCT_NAME}} — operations and delivery verification

**Updated:** {{DATE}}.

This file owns outstanding setup tasks and executable shared-flow verification,
including tasks for operators or suitably equipped agents. Create items during
FRED specification, not only at implementation close-out. One item may cover
several FREDs. Keep reusable procedures in project guides and link them here.

## OP-{{ID}} — {{TASK_NAME}}

**Kind:** {{SETUP_OR_FLOW_VERIFICATION}}
**Covers:** {{FRED_LINKS}}
**Owner / executor:** {{HUMAN_OR_AGENT_ROLE}}
**State:** Pending
**Blocks:** {{IMPLEMENTATION_FOR_NAMED_FREDS_OR_CLOSURE_OR_RELEASE}}
**Requires:** {{IMPLEMENTATIONS_CONTRACTS_ACCESS_OR_OTHER_OPERATION_IDS}}
**Target:** {{LOCAL_PREVIEW_PRODUCTION_OR_OTHER_TARGET}}
**Procedure guide:** {{EXISTING_GUIDE_LINK_OR_NONE}}
**Next action / blocker:** {{SPECIFIC_ACTION_OR_NONE}}

### Steps and pass condition

1. {{CONCRETE_STEP}}
2. {{CONCRETE_STEP}}

**Pass condition:** {{OBSERVABLE_RESULT_WITH_RELEVANT_ERROR_OR_PERMISSION_PATHS}}

<!-- Setup examples: configure provider/webhook, generate keys, establish wallet
or signing access. Flow examples: onboarding across identity, email, and UI.
Specify applicable environment/access/action boundaries from project guides.
Store secret values in the secret store; record only names/public identifiers. -->

### Result and evidence

**Executed:** {{DATE_AND_EXECUTOR_OR_PENDING}}
**Deployment / revision / configuration context:** {{CONTEXT_OR_PENDING}}
**Result:** {{PENDING_PASSED_FAILED_BLOCKED}}
**Evidence / follow-up:** {{LINKS_OR_PENDING}}

## Maintenance

Use Pending / Ready / Blocked / Passed / Failed for task state. Record blocker
and next action when blocked; preserve historical evidence on reruns. Record a
waived/canceled task explicitly with its reason and decision authority, never
as a pass. Closure requires the project's applicable gates, not every unrelated
operation in this file.

Code failures reopen their owning FRED; access/configuration blockers leave
correct implementation Implemented. Revalidate affected flows after relevant
code, contract, or configuration changes. Preview results do not prove production.

Passing delivery flows alone does not close FREDs: an equipped agent must also
run and record the project global check on the relevant current integration
baseline before Closed sign-off. Use the entrypoint command and working directory.
