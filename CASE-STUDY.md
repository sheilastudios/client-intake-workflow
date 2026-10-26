# From a submitted form to a defensible next step

The useful unit of an intake system is not a successful form submission. It is a request that an operator can find, understand and move forward without losing its history or crossing a client's boundary.

Sheila Studios' internal workflow joined a public form and confirmation page to an operator queue and record detail view. The engineering work then addressed what happened between those screens: repeated submissions, actions that did not fit the record's state, and file access tied to a particular client.

## 1. Separate submission from operator authority

The public and operator surfaces were separated into distinct servers. The public routing code exposes selected public pages and intake handling; the operator server owns queue, detail and review-action handling. The historical case account reports that operator pages were unavailable through the public surface and that unauthenticated requests to the protected deployment were refused.

Those are two different boundaries. Separating handlers reduces accidental exposure through the public application. Deployment authentication decides who may reach the operator application. An origin check in application code does not establish operator identity, and the source review for this showcase does not reverify the historical deployment's authentication configuration.

The operator workflow also retains a next-step description and action history. A visible status is more useful when it can be traced to what someone actually selected, rather than inferred from a polished confirmation screen.

## 2. Recognize a repeat before applying new-request checks

A historical defect made an exact resubmission look like an authentication problem. The correction recognizes the existing request before applying the authentication path for a nonduplicate submission. A match returns the existing record's identity and status, rather than manufacturing another lead.

Here, "exact" means equality over the application's selected normalized request fields, not identical HTTP bytes and not fuzzy similarity. A changed request is not automatically covered. Duplicate recognition is neither identity verification nor permission to change the original record.

The related workflow defect was a disallowed escalation from an authentication-held inbox record. The server now obtains the allowed action set for the record's kind and status before updating it. This complements the interface's available choices; the check does not depend on a user clicking the intended button.

There was a separate operational lesson: the historical account records stale running processes after code changes. Correct source and a corrected live process are different claims. The account reports a restart and subsequent checks, but this showcase has not independently repeated that deployment verification.

## A synthetic worked journey

**The following is a newly authored illustration of expected behavior derived from the inspected source. It was not executed for this showcase and is not a client record or historical test receipt.**

Suppose a requester has an existing contact record and sends a changed debugging request without the verification required for that update. The example starts with an inbox record on authentication hold. It illustrates a recoverable next step, not automatic acceptance of the work.

| Step | Illustrated input or decision | Expected result and boundary |
|---|---|---|
| Submit | A changed request lacks the required verification. | Record remains on authentication hold rather than advancing to substantive review. |
| Resubmit | The requester repeats the same normalized request. | Return the existing held record; do not create a new lead or treat the repeat as newly authenticated. |
| Inspect | An operator opens the record and next-step guidance. | The unresolved verification requirement remains visible. Inspection alone does not resolve it. |
| Reject a transition | An attempt is made to advance that held inbox record directly to substantive review. | The server rejects an action outside the allowed set before saving that transition. |
| Take a permitted step | The operator chooses follow-up for missing details. | Record the action and move to an awaiting-details workflow status. This does not establish verified identity, send a message by itself or accept a paid engagement. |

An illustrative operator-facing outcome, written for this case study rather than copied from the application:

> Existing request found. Verification remains unresolved. Follow-up selected and recorded; substantive review has not been approved.

The distinction in the last step matters. A workflow status can change while an underlying requirement remains unresolved. A truthful explanation should not collapse the two into "cleared."

## 3. Keep client work attached to its actual boundary

The client-lane helper associates work with a client and a session binding, then checks requested paths against the permitted working surface. The inspected implementation rejects selected invalid binding files and directories, checks file identity when opening a binding, and distinguishes ordinary working areas from protected management areas.

The inspected regression definitions include permitted own-client paths, refused other-client paths, refused management paths, and refusal of symbolic-link bindings even when a forced rebind is requested. These are specific implementation and fixture claims, not proof that every program on the machine is confined by these helpers or that every possible filesystem race has been eliminated.

This work is connected to intake, but not identical to it. Advancing a lead's workflow status does not, on its own, prove that a fully isolated client environment was provisioned. The status change and the client-lane enforcement helpers have distinct responsibilities.

## What carries over

The reusable engineering practice is to check the consumer of each decision: the duplicate path, the state-changing operation, the file actually opened and the process actually serving the request. A plausible interface is not enough evidence that those consumers agree.

The result is a concrete internal implementation with historical verification reports and inspectable regression definitions. There is no measured revenue, time-saving or customer-conversion claim attached to it. See [EVIDENCE.md](EVIDENCE.md) for exactly what was and was not checked.
