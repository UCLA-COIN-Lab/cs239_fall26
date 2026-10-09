# Project instructions

Applies throughout this repository. Grant details come from
[resource_email.pdf](resource_email.pdf), dated September 3, 2026.

## Costs and approval

- **Default: no additional monetary cost beyond the sponsored TPUs.** This covers
  every action, command, code path, service, and recommendation, including steps
  the user is asked to run. Prefer work that adds no cost.
- Other GCP services remain billable. Verify that supporting compute, storage,
  disks, networking/egress, monitoring, and APIs add no charges, or obtain the
  approval below. Quota, billing alerts, assumed free tiers, and the email's
  conditional $300 introductory credit do not establish free usage.
- If spending is necessary, complete safe, no-cost preparation first. Explain
  the need and feasible free alternatives; provide an itemized USD estimate from
  current pricing sources, including quantities, duration, one-time/recurring
  and indirect costs, total or range, assumptions, and a proposed spending cap.
- **Ask and wait for explicit approval of the paid action and spending cap before
  execution or asking the user to run it, even in YOLO/full-autonomy mode or with
  tool approvals disabled.** Silence, credentials, and general instructions to
  proceed are not spending approval. Renew approval before expanding its scope
  or exceeding its cap.
- Proceed only with verified no-cost coverage or explicit spending approval;
  otherwise pause the affected step, explain why, and continue no-cost work.
  Approved exceptions apply throughout this file; never fall back automatically
  to unapproved paid resources.

## Sponsored TPU allocation

**Project number: `72596944750`.** Verify the associated project ID when needed;
do not rely on the default project.

| TPU generation | Provisioning type | Zone | Quota in chips |
| --- | --- | --- | ---: |
| v4 | Spot | `us-central2-b` | 32 |
| v5e | Spot | `us-central1-a` | 64 |
| v6e | Spot | `us-east1-d` | 64 |
| v4 | On-demand | `us-central2-b` | 32 |
| v5e | Spot | `europe-west4-b` | 64 |
| v6e | Spot | `europe-west4-a` | 64 |

- Coverage lasts **180 days**, only for **new TPUs in the listed zones**. Verify
  the actual start and expiration before use; the email gives no exact expiry
  timestamp, and recreating resources does not restart the term.
- Quotas are per row and measured in **chips**. Verify accelerator-to-chip counts;
  account for existing TPUs and queued requests before allocating more.
- Quota does not guarantee capacity; Google may reclaim both at any time.

## Resource checks and periodic reminders

- **Check existing allocations at each session's start**, before/after resource
  changes, and periodically during cloud work, using authorized, no-cost,
  read-only access. Check the sponsored project and any explicitly authorized
  additional projects across relevant zones, including unsponsored zones.
- Include running/stopped TPUs, Queued Resources, CPU/GPU VMs, disks, snapshots,
  buckets, networking, and other supporting services. Distinguish quota from
  allocations; do not double-count a queued request and its associated TPU.
- Keep a timestamped summary: resource name, project/zone, status, size/chips,
  purpose/owner when known, cost coverage, and verified used/remaining quota.
  Flag idle or unexpected resources, abandoned requests, and approaching expiry;
  report possible unapproved charges immediately.
- **Remind the user what is in use** when cloud work starts, after material
  allocation changes, and about every **30 minutes** of active work while
  resources remain allocated. At wrap-up, report remaining/queued resources,
  completed cleanup, and any cleanup still needed. Keep reminders brief.
- Report incomplete checks, missing access, and the last verified timestamp;
  never infer "no resources" or "no charges" from failed or partial checks. Do
  not imply monitoring continues after the session or enable paid monitoring
  without approval.

## TPU workflow and reliability

- Before remote work, verify project, active grant, TPU generation/zone/type,
  chip count, remaining quota, and supporting costs. Enforce these checks in
  provisioning code; reject configurations outside sponsorship or paid approval.
- Use **TPU VMs and the Queued Resource API**. Verify current quota flags rather
  than assuming "spot" and "preemptible" are interchangeable. Prefer sponsored
  on-demand v4 in `us-central2-b` when suitable, then sponsored spot capacity.
- Make jobs resumable; bound resource counts, retries, and runtime. Stop queued
  and running work before sponsorship expires unless paid continuation is
  approved, and stay within any approved spending cap. Checkpoints and transfers
  follow the same cost rules.
- For exhausted quota, inspect unused **TPUs and Queued Resources**. Clean up
  task-owned resources after completion, failure, or cancellation; preserve
  needed results and do not delete resources used by other work.
- Start with a small optimized reference model/tutorial before scaling. The
  email links performance, profiling, troubleshooting, TPU v4, and three-part
  **PyTorch/XLA performance debugging** guides; review setup costs before use.

## Program expectations and help

- TRC expects shared research and detailed feedback to Google. Keep experiments
  reproducible. The email also lists Google's AI Principles, Terms and
  Conditions, and Privacy Policy; do not publish, send feedback, or accept terms
  on the user's behalf without explicit authorization.
- Help: the email's troubleshooting guide and FAQ, `trc-support@google.com`, and
  `#tpu-research-cloud` on the Google Developer Community Discord server.
