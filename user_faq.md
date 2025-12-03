# Vigil User FAQ

*Answers to common questions from the people who use Vigil every day*

---

## Getting Started

### How do I create my first workflow?

Creating a workflow is like building with blocks. Here's the basic process:

1. **Start with a trigger** — What kicks off this workflow? Maybe it's "30 days after a notice was sent" or "when a payment is received."
2. **Add your steps** — Drag modules onto the canvas and connect them in order. For example: *Generate Notice → Route for Approval → Mail Document*.
3. **Configure each step** — Click on any step to set its details (which template to use, who approves it, etc.).
4. **Test it** — Run a sandbox execution to make sure it works the way you expect.
5. **Publish** — When you're confident, publish the workflow to make it live.

We recommend starting with the guided tutorials in the Learning Center, which walk you through building your first workflow step-by-step.

---

### Do I need technical skills or coding knowledge?

**No coding required.** If you can create a filter in Excel or set up a rule in Outlook, you have all the skills you need.

Vigil uses a visual interface where you connect steps by dragging and dropping. Configuration happens through forms and dropdowns—not code. You'll be selecting options like "Send via USPS First Class" or "Route to Supervisor for Approval," not writing scripts.

That said, the more you understand your own processes, the better your workflows will be. You're the expert on how violations should be handled—Vigil just gives you the tools to make it happen.

---

### Can I see examples of workflows others have built?

Yes! Vigil includes two ways to learn from existing work:

- **Template Library** — A collection of pre-built workflow templates for common scenarios (first notice mailings, payment plan setups, hearing scheduling, etc.). You can use these as-is or as a starting point for your own version.

- **Inherited Workflows** — Depending on your jurisdiction, some workflows may already be defined at the state or regional level. These appear automatically in your workspace and run for all partners in that geography. You can view how they're built, even if you can't edit them directly.

Between templates and inherited workflows, you'll rarely need to start from a blank canvas.

---

### What if I make a mistake—can I undo it?

**Yes, and it's hard to accidentally break anything in production.** Here's why:

- **Draft mode** — All new workflows and edits start as drafts. Nothing affects live data until you explicitly publish.
- **Sandbox testing** — You can run "fake" executions that simulate the workflow without touching real violations or generating real mail. Test as much as you want.
- **Version history** — Every published version is saved. If something goes wrong, you can roll back to any previous version with a few clicks.
- **Staging environment** — For major changes, you can test in our QA/Staging environment before anything reaches production.

Think of it like editing a Google Doc with "Suggesting" mode on—you can experiment freely, and nothing is final until you say it is.

---

## Capabilities

### What steps/modules are available?

Vigil launches with a core set of modules that cover the most common workflow needs:

| Module | What It Does |
|--------|--------------|
| **Generate Document** | Creates letters, notices, or forms from your templates |
| **Send Correspondence** | Mails documents physically (USPS) or digitally (email, portal) |
| **Manual Review** | Pauses the workflow and routes the item to a person for approval or decision |
| **Calculate Fines** | Applies rules-based logic to determine fine amounts, late fees, etc. |
| **Conditional Routing** | Branches the workflow based on conditions ("If rental vehicle, then...") |
| **Wait/Delay** | Pauses execution for a specified time ("Wait 14 days, then continue") |
| **Update Record** | Changes data on the violation record (status, flags, notes) |
| **Trigger Another Workflow** | Kicks off a separate workflow, enabling powerful chaining |

New modules are added regularly based on user feedback. If you need something that doesn't exist yet, see "What if I need a step that doesn't exist?"

---

### Can I customize how a step works?

Yes—each step has configurable options that you control.

For example, the **Calculate Fines** step doesn't have one fixed formula. When you add it to your workflow, you configure *which* calculation rules apply: base fine amount, late fee schedule, reduction for early payment, caps for specific violation types, etc.

Similarly, **Generate Document** lets you choose the template and map in data fields. **Manual Review** lets you specify which team or role should review, and what options they have (Approve / Reject / Escalate).

You're not locked into generic behavior—you configure each step to match your jurisdiction's requirements.

---

### What if I need a step that doesn't exist yet?

**Request it!** Vigil is designed to grow based on what users actually need.

Here's how new modules get built:

1. **Submit a request** — Use the "Request a Module" form in Vigil, or bring it up in a User Committee meeting.
2. **The committee reviews it** — Our User Committee (volunteer users from across teams) meets regularly with the development team to prioritize requests.
3. **Development builds it** — If approved, the dev team builds the module and adds it to the library.
4. **Everyone benefits** — Once a module exists, it's available to all users. Your request might solve a problem for dozens of other people too.

This process is intentionally fast—we're aiming for weeks, not months. And because you're working directly with developers (not through three layers of project managers), your feedback actually shapes what gets built.

---

### Can workflows handle exceptions or special cases?

Absolutely. Workflows aren't just straight lines—they can branch, loop, and adapt.

**Conditional Routing** lets you build "if/then" logic directly into the workflow:
- *"If the vehicle is a rental → route to the Fleet Team instead of mailing"*
- *"If this is a third offense → escalate to supervisor review"*
- *"If the fine exceeds $500 → require manager approval before sending"*

You can also combine conditions, handle multiple branches, and route exceptions to manual review when automation isn't appropriate.

The goal is to handle the routine cases automatically while still giving you control over the edge cases.

---

### Can I set up workflows that require manual approval at certain points?

Yes—this is one of Vigil's most-used features.

The **Manual Review** step pauses the workflow and creates a task for a specific person or team. The reviewer sees all the relevant information and can:
- **Approve** — Workflow continues to the next step
- **Reject** — Workflow stops (or branches to a rejection path you've defined)
- **Request Changes** — Send it back with notes
- **Escalate** — Route to someone with more authority

You decide where these checkpoints go. Some workflows might have manual review on every item; others might only flag exceptions for human eyes.

---

## Day-to-Day Use

### How do I know if my workflow is working correctly?

Vigil gives you visibility at every level:

- **Execution Log** — See every workflow run: when it started, which steps completed, where it currently is, and whether it succeeded or failed.
- **Step-by-Step Detail** — Click into any execution to see exactly what happened at each step, including the data that was processed.
- **Dashboard Metrics** — Track overall health: how many executions today, success rate, average processing time, items waiting for review.
- **Alerts** — Configure notifications for failures or anomalies ("Alert me if more than 5 workflows fail in an hour").
- **Violation Page** — See workflow activity from the violation's perspective. Every workflow that has touched a violation appears in its activity timeline. (See "Can I see everything that's happened to a specific violation?" below.)

You won't be left wondering whether things are working. If something's off, you'll know—and you'll have the details to understand why.

---

### Can I see everything that's happened to a specific violation?

Yes—the **Violation Page** is your single source of truth for any individual violation.

Instead of piecing together information from multiple screens, you can see the complete story in one place:

- **Activity Timeline** — Every workflow that has run (or is currently running) on this violation, with timestamps and outcomes
- **Documents** — All letters, notices, and forms generated for this violation
- **Status Changes** — A history of how the violation's status has evolved (and why)
- **Financial Activity** — Fines assessed, fees applied, payments received, refunds issued
- **Evidence** — Photos, videos, and other supporting materials
- **Scheduled Actions** — Upcoming workflow steps that are waiting on a timer or condition ("Second notice scheduled in 12 days")

When someone calls asking "Why did I get this letter?" or "What's happening with this ticket?"—the Violation Page has your answer. You can trace exactly which workflow generated which document, when it was sent, and what triggered it.

Think of it as the violation's complete biography—past, present, and future.

---

### Can I test a workflow before it goes live?

Yes—and you should! Vigil offers multiple ways to test safely:

1. **Sandbox Executions** — Run your workflow with "fake" data that never touches production. The execution appears in a separate sandbox view, not in your live data. Test as many times as you want.

2. **Draft Mode** — Workflows stay in draft until you explicitly publish. Edit, adjust, and refine without any risk to live operations.

3. **Staging Environment** — For high-stakes workflows, you can deploy to our Staging environment first. This mirrors production but keeps test data completely separate.

**Our recommendation:** Build → Sandbox test → Peer review → Publish as minor version → Monitor → Promote to major version once proven.

---

### What happens if something goes wrong mid-workflow?

Vigil is designed to fail gracefully and recover cleanly.

**When a step fails:**
1. The workflow pauses at that step
2. The failure is logged with details (what went wrong, which record, when)
3. You're notified (if you've configured alerts)
4. The item appears in your "Needs Attention" queue

**Rollback (the safety net):**
Each step can have a configured rollback action. If Step 4 fails, Vigil can automatically undo Steps 1-3 to return the violation to its original state. Think of it like a transaction—either the whole thing succeeds, or it's like it never happened.

You configure how aggressive rollback should be: fully automatic, manual approval required, or somewhere in between.

**No silent failures.** You'll always know what happened and have clear options for how to fix it. And if you're investigating a specific violation, its page shows the complete history—including any workflow failures and rollbacks.

---

### Can I modify a workflow that's already running?

Yes, and Vigil handles this intelligently through **versioning**:

- **Minor version changes** (small tweaks, wording updates): Publish the change, and in-progress executions will pick up the new version at their next step. No disruption.

- **Major version changes** (structural changes, new logic): Publish the change, and it only applies to *new* executions. Anything already in progress continues on the old version until it completes.

This means you can fix a typo in a letter template immediately (minor version), but if you're restructuring the whole workflow, existing items finish under the old rules while new items use the new rules.

You're never stuck choosing between "break everything in progress" and "wait until the queue is empty."

---

## Collaboration & Permissions

### Can I share workflows with my team?

Workflows are automatically visible within your organizational scope. What you can see depends on where you sit in the hierarchy:

- **Partner-level users** see workflows for their partner
- **Jurisdiction-level users** see workflows across all partners in their jurisdiction
- **State-level users** see everything in the state

You can also explicitly share workflows with specific colleagues for feedback or collaboration—useful when you want a peer to review your work before publishing.

---

### Can I copy and modify someone else's workflow?

Yes! If you can view a workflow, you can duplicate it as a starting point for your own.

This is especially useful when:
- A neighboring jurisdiction has solved a similar problem
- You want to create a variation of a template
- You're building something similar to an existing workflow but with different rules

The copy becomes yours to modify—your changes don't affect the original.

**Note:** You cannot copy or modify inherited workflows from higher levels (e.g., state-mandated workflows). Those are view-only for a reason—they ensure consistency across all jurisdictions.

---

### Who can approve or publish workflows?

Publishing permissions follow your organizational role:

| Role | Can Create/Edit | Can Publish | Scope |
|------|-----------------|-------------|-------|
| **Workflow Builder** | ✓ | ✗ (submit for review) | Own workflows |
| **Workflow Approver** | ✓ | ✓ (minor versions) | Team/Partner workflows |
| **Workflow Admin** | ✓ | ✓ (minor + major) | Jurisdiction or State |

In practice, this means:
- Anyone can build and test workflows in draft/sandbox mode
- Publishing requires review from someone with appropriate authority
- Major changes (new major versions) require admin approval

This structure lets you experiment freely while ensuring proper oversight before anything goes live.

---

## Getting Help

### Where can I learn more?

Vigil launches with extensive learning resources:

- **Learning Center** — In-app tutorials, from "Your First Workflow" to advanced techniques
- **Video Library** — Short how-to videos for every module and common scenarios
- **Live Workshops** — Regular training sessions (recorded for later viewing)
- **Documentation** — Searchable reference docs for when you need the details

Start with the "Vigil Fundamentals" workshop—it covers everything you need to be productive in about an hour.

---

### What if I have feedback or ideas?

**We want to hear from you.** Vigil is built *for* you, and it gets better when you tell us what's working and what isn't.

**User Committee** — A group of volunteer users meets regularly with the Vigil development team. This is the fastest path to getting your voice heard. If you're interested in joining, reach out to [Committee Contact].

**In-App Feedback** — Every screen has a feedback button. Bug reports, feature requests, and "this is confusing" notes all go directly to the team.

**Your input matters.** For the first time, developers are working directly with users—not through intermediaries. Your feedback shapes what gets built next.

---

## Quick Reference

| I want to... | Do this... |
|--------------|------------|
| Create a new workflow | Click **+ New Workflow** from your dashboard |
| Test without affecting live data | Use **Sandbox Execution** from the workflow editor |
| See what's failing | Check the **Needs Attention** queue |
| See everything about a violation | Open the **Violation Page** for that record |
| Request a new module | Use **Request a Module** form or raise it in User Committee |
| Roll back a bad publish | Go to **Version History** → Select version → **Restore** |
| Learn a new feature | Visit the **Learning Center** |

---

*Questions not answered here? Use the in-app feedback button or ask in the User Committee Slack channel.*

---

**Vigil**
*Your workflows. Your way.*
