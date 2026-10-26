# Client Intake & Workflow Hardening

Beyond the contact form: keeping a request understandable from first submission to operator review, without treating a repeated submission as a new job or confusing one client's working area with another's.

This is a documentation showcase of Sheila Studios' own intake infrastructure. It brings together three connected engineering cases: public versus operator access, duplicate handling and workflow validation, and client-scoped file handling. These are not three paid customer engagements.

## What the work demonstrates

- **Follow the request, not just the page.** Public intake and operator review use separate serving surfaces, with an explicit handoff into a review queue.
- **Make retries unsurprising.** A matching normalized request returns the existing record rather than creating another lead or newly treating that repeat as an authentication failure.
- **Validate decisions where they happen.** The server checks whether an operator action is allowed for the record's kind and current status; hiding a button is not the enforcement boundary.
- **Check the working boundary.** Client-lane helpers check binding identity and permitted paths, including selected symbolic-link and file-identity failure cases.

The implementation uses Python, browser-facing HTML/CSS/JavaScript and file-backed records. This repository explains the work; it does not distribute the private application, offer an installable package or promise a currently available hosted product.

## Read the case

[Case study and synthetic request journey](CASE-STUDY.md) explains the decisions and tradeoffs. [Evidence and limits](EVIDENCE.md) separates historical verification reports from the source inspection used for this showcase. [Rights and credit](RIGHTS.md) defines the publication boundary.

Historical records report successful checks of the deployed prototype and focused regression suites. This documentation review did not rerun them or inspect today's deployment. It is not a security certification, a performance benchmark or a claim of complete client isolation.

## Relevant work

This case is relevant to intake workflows, operator dashboards, retry bugs and small automation systems whose apparent success can conceal the wrong record or state transition. The deliverable is an understandable workflow and evidence-qualified engineering account, not a claim that adding a form solves the whole service.

Other Sheila Studios showcases: [The Entropy Engine](https://github.com/sheilastudios/rp-host) and [Infinite Manuscript](https://github.com/sheilastudios/infinite-manuscript).

## Discuss related work

[Use Sheila Studios' guided intake](https://sheilastudios.com/intake) to discuss an intake, operator-workflow or troubleshooting project. This is a project conversation, not an offer of this private application as a hosted service.
