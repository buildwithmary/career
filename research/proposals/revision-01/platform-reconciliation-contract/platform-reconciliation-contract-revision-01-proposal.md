# When is a platform request actually ready?

Revision: 01 | Domain: Platform engineering | Researched: 2026-11-03

Owner: Research Analyst. Execution: [CARA-2](/CARA/issues/CARA-2).

Status: research proposal awaiting independent technical review and explicit human topic decision. Production and publishing are not approved.

## Relevance

A successful API write can be mistaken for usable infrastructure. Teams need a contract for readiness and failure recovery.

## Intended audience

Platform engineers and backend developers building self-service infrastructure; familiarity with Kubernetes objects.

## Original technical angle

Original teaching proposal: follow a fictional PreviewEnvironment request through Accepted, Provisioning, Ready, and Failed. Ask which observations justify each transition after a controller restart. These are proposed application states, not Kubernetes-defined statuses.

## Claim-to-evidence mapping

| Claim | Technical statement | Primary evidence |
|---|---|---|
| P1 | A custom resource stores structured data; a controller adds reconciliation behavior. | S1, Custom controllers |
| P2 | Controllers work toward desired state and can act on external systems. | S2, Controller pattern and Direct control |

## Primary sources and freshness

- S1: [Kubernetes: Custom Resources](https://kubernetes.io/docs/concepts/extend-kubernetes/api-extension/custom-resources/). Living unversioned URL; retrieved 2026-11-03. Use conceptual sections only; pin target cluster documentation before any implementation.
- S2: [Kubernetes: Controllers](https://kubernetes.io/docs/concepts/architecture/controller/). Living unversioned URL; retrieved 2026-11-03. No release-specific API fields used.

## Educational takeaway

Separate request acceptance from observed readiness; define who reports progress and which evidence supports a ready signal.

## Proposed scope if approved

A three-frame state walkthrough; a controller-restart thought experiment; a readiness contract worksheet. Proposal only, no implementation.

## Limits and review checks

Reconciliation is not an instant completion guarantee. No cluster-version compatibility or external-provider idempotency is asserted; those require validation if approved.

Reviewer: check claim scope against the named sections, source freshness, audience fit, and whether the original exercise teaches the takeaway. Record technical verdict separately from the human topic decision. No experiments were run and no paid resources were provisioned.
