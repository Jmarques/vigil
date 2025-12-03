# Vigil Stakeholder FAQ

*Answers to strategic, technical, and organizational questions from leadership*

---

## Strategic & Business Questions

### Why should we invest in Vigil instead of the current platform rewrite roadmap?

The current roadmap proposes a 2-year effort to rewrite our Ruby on Rails monolith in Python microservices—while preserving the same database schema and rebuilding the same functionality. At the end of that investment, we would have:

- The same 6-9 month partner onboarding timeline
- The same 235+ configuration settings per partner
- The same rigid system that forces 50-80% of correspondence into manual workarounds
- Zero new capabilities for our operations teams

Vigil takes a different approach: instead of rebuilding what we have in a different language, we built what our users actually need. The initial platform was developed by a small team (2-3 engineers) over nine months. The result:

| Metric | Current System | Post-Rewrite (Projected) | Vigil |
|--------|---------------|--------------------------|-------|
| New partner onboarding | 6-9 months | 6-9 months | Minutes to weeks |
| Engineering effort for new workflow | Weeks to months | Weeks to months | Zero (user-configured) |
| Manual workaround rate | 50-80% | 50-80% | Target: <10% |
| Time to build | Exists | 2 years | 9 months |

The rewrite optimizes for technical architecture. Vigil optimizes for user outcomes. We chose outcomes.

---

### What's the expected ROI? How do we measure success?

**Immediate, quantifiable savings:**

- **Manual workarounds:** We currently spend an estimated **$700,000/year** on manual processes for citation document handling alone—just one slice of the manual work. Vigil directly automates these workflows.
  
- **Partner onboarding engineering cost:** Florida required 9 months of dedicated development time to onboard. At fully-loaded engineering costs, that's a significant six-figure investment *per complex partner*. Vigil reduces this to weeks of configuration work by operations staff.

- **Opportunity cost:** Every month we can't onboard a new partner is revenue we're not capturing. Cutting onboarding from 9 months to 6 weeks means partners go live 7+ months sooner.

**Success metrics we're tracking:**

| Metric | Baseline | 12-Month Target |
|--------|----------|-----------------|
| Average partner onboarding time | 6-9 months | <6 weeks |
| Workflows handled manually | 50-80% | <20% |
| Time to deploy new workflow type | Weeks-months | Days |
| User-created workflows in production | 0 | 50+ |
| Engineering tickets for workflow changes | ~XX/month | <10/month |

The rewrite has no ROI—it delivers the same capabilities at significant cost. Vigil pays for itself within the first year through reduced manual labor and faster partner onboarding alone.

---

### What's the risk if we don't do this?

**Competitive risk:** We're in the school bus stop-arm enforcement space today, but the goal is expansion into broader violation processing. Every month we're stuck with a system that takes 9 months to onboard a partner is a month competitors can move faster. Our current architecture is a growth bottleneck.

**Operational risk:** Our teams have built an entire shadow system of spreadsheets and manual processes because our software doesn't serve them. This is fragile, error-prone, and doesn't scale. We're one key employee departure away from losing critical institutional knowledge that only exists in Excel files.

**Strategic risk:** The proposed 2-year rewrite delivers no new capabilities. That's two years of continued manual workarounds, two years of slow partner onboarding, two years of our operations teams working around us instead of with us. And at the end, we'd still have a rigid system—just written in Python.

The real risk isn't "what if Vigil fails?" It's "what if we spend two years rebuilding what we already have while the market moves on?"

---

### How does this affect our ability to expand beyond school bus stop-arm violations?

This is exactly why Vigil matters.

Our current system has 235+ configuration settings per partner—and it *still* can't handle the variation we encounter in just one violation type. Expanding into red-light cameras, speed enforcement, parking violations, or other domains would require even more configuration sprawl, more edge cases, more manual workarounds.

Vigil's modular architecture is designed for this expansion:

- **New violation types** become new workflow templates, not new code branches
- **Jurisdiction-specific rules** are configured by users, not hardcoded by engineers
- **New capabilities** are added as modules that benefit all violation types

The current system (or its proposed rewrite) would require engineering involvement for every new violation type, every new jurisdiction, every new partner requirement. Vigil lets us scale by empowering users, not by scaling engineering headcount.

---

## Technical & Feasibility Questions

### How long did Vigil take to build?

The initial platform was built in **9 months** by a core team of 2-3 engineers:

- **Months 1-6:** Core workflow engine, visual builder, trigger system, and foundational modules (document generation, correspondence, manual review, conditional routing)
- **Months 7-9:** Testing infrastructure, sandbox environment, first production pilots, iteration based on user feedback

This was possible because we focused ruthlessly on the workflow abstraction rather than trying to rebuild every feature of the existing system. Vigil doesn't replace the entire violation processing platform—it provides a flexible layer for the parts that need flexibility.

---

### Can we reuse any existing code or infrastructure?

Selectively. We're intentionally *not* inheriting the architectural decisions that caused our current problems:

- **Mailing infrastructure:** Vigil's Send Correspondence module integrates with our existing mail vendor (Cathedral) via their API
- **Authentication/authorization:** Leverages existing SSO infrastructure through Microsoft Azure

**What we're deliberately leaving behind:**

- **Database schema:** We're building a new schema designed for workflow flexibility, not preserving the existing MySQL structure that bakes in rigid assumptions. We're also moving to a database-per-state architecture for better isolation and scalability.
- **Document templates:** The current templates are locked in inDesign files on an external XMPie server managed by contractors—inaccessible to both users and developers. Vigil uses a new templating approach that puts control back in-house.

This is a feature, not a limitation. The goal isn't to preserve everything—it's to preserve what works and replace what doesn't.

---

### What happens to the current system during and after transition?

Vigil is designed for incremental adoption, not a risky big-bang cutover.

**During transition:**
- The current system continues operating for existing partners and workflows
- New partners onboard directly into Vigil, avoiding legacy configuration entirely
- High-value manual workarounds migrate to Vigil workflows opportunistically
- **Data synchronization:** During the transition period when both systems coexist, we'll need synchronization between the legacy database and Vigil's new schema. This is a known challenge we're planning for—likely a one-way sync from legacy to Vigil for violations that need to be accessible in both systems.

**Long-term:**
- As workflows migrate to Vigil, the legacy system handles less and less
- We can deprecate legacy workflow code incrementally, module by module
- No artificial deadline to "finish migration"—we migrate what makes sense, when it makes sense

This isn't a rewrite. It's a *bypass*. We're not rebuilding the old road—we're building a new one and letting traffic shift naturally.

---

### How do we ensure quality and reliability when users are building their own workflows?

This was a core design concern. Vigil has multiple layers of protection:

**Before publication:**
- **Sandbox testing:** Users test workflows with simulated data that never touches production
- **Draft mode:** All work stays in draft until explicitly published
- **Validation rules:** The platform prevents structurally invalid workflows (orphaned steps, missing required config, circular dependencies)
- **Peer review:** Publishing permissions require appropriate approval based on role and scope

**In production:**
- **Version control:** Every published version is saved; instant rollback to any prior version
- **Automatic rollback:** Steps can define rollback actions; if Step 4 fails, Steps 1-3 can automatically undo
- **Execution logging:** Complete audit trail of every workflow run, every step, every decision
- **Alerting:** Configurable notifications for failures, anomalies, or threshold breaches

**Governance:**
- **Role-based permissions:** Not everyone can publish; major changes require admin approval
- **Inherited workflows:** State-level or jurisdiction-level workflows can be mandated and locked from local modification
- **Module library is controlled:** Users assemble from approved modules; they can't introduce arbitrary code

Users build workflows; they don't write code. The modules themselves are engineering-built and tested. Users are composing from safe building blocks, not programming from scratch.

---

### Why not microservices? Isn't a monolith an architectural liability?

**The short version for non-technical readers:** Microservices is an architectural pattern that makes sense when you have many independent teams building features that can operate completely separately. We don't have that situation. Our violation processing steps are tightly connected—a single violation touches documents, fines, correspondence, reviews, and payments in sequence. Splitting these into separate services would add complexity without solving any problem we actually have.

**The technical details:**

Microservices solve specific problems: independent scaling, independent deployment, team autonomy across bounded contexts, fault isolation. These benefits come with costs: distributed system complexity, network latency, data consistency challenges, operational overhead.

For violation processing workflows, we don't have the problem microservices solve:

- We don't need independent scaling of "fine calculation" separate from "document generation"
- We don't have 10 teams that need to deploy independently
- Our domain doesn't decompose into clean bounded contexts—a single violation touches documents, fines, correspondence, reviews, and payment in tightly coupled sequences

The proposed rewrite would add microservices complexity without microservices benefits. We'd have distributed system headaches *and* the same rigid workflow logic, just spread across service boundaries.

Vigil takes a different approach: a well-structured modular monolith where the *workflow abstraction* provides flexibility. The architecture serves the goal (adaptable workflows) rather than serving an architectural principle (microservices) that doesn't fit our problem.

If we later identify components that genuinely benefit from service extraction—say, document rendering becomes a shared capability across multiple product lines—Vigil's modular design makes that extraction straightforward. We're not precluding microservices; we're just not cargo-culting them.

---

## Organizational Questions

### What resources and team structure does Vigil need going forward?

**Core platform team (ongoing):**
- 2-3 engineers for platform maintenance, new module development, and performance optimization
- 1 product owner embedded with operations teams to prioritize module development

**Compared to the alternative:**
The proposed rewrite requires 10+ engineers for 2 years to deliver equivalent functionality. Vigil required 2-3 engineers for 9 months to deliver *superior* functionality. The math speaks for itself.

**User support:**
- Learning Center content and training workshops (created; ongoing maintenance)
- User Committee (volunteer users + dev team; meets regularly for feedback and prioritization)

The goal is a sustainable, small team—not a large team that becomes its own bureaucracy.

---

### What happens when users need a workflow step that doesn't exist yet?

This is expected and planned for. The module library grows based on user needs:

1. **User submits request** via in-app form or User Committee
2. **User Committee reviews** and prioritizes (volunteer users + dev team, meeting regularly)
3. **Dev team builds module** (targeting weeks, not months)
4. **Module is added to library** and becomes available to all users

Because modules are self-contained and follow standard interfaces, adding a new module doesn't require touching existing code. This is how Vigil gets *more powerful* over time without getting more complex.

**Key principle:** We don't build modules speculatively. We build them when users need them. This keeps the platform focused and avoids feature bloat.

---

### What's the training and change management plan?

**Training resources (available now):**
- **Learning Center:** In-app tutorials from "Your First Workflow" to advanced techniques
- **Video library:** Short how-to videos for every module
- **Live workshops:** "Vigil Fundamentals" covers everything needed to be productive (~1 hour)
- **Documentation:** Searchable reference for detailed specifications

**Adoption approach:**
- Start with volunteers and enthusiastic early adopters, not forced rollout
- Begin with new partner onboarding (greenfield, no migration complexity)
- Target high-pain manual workarounds (users *want* these automated)
- Build internal champions who help train their peers

**Change management reality:**
Our operations teams are already building their own solutions—in spreadsheets, in email threads, in manual processes. They're not resistant to change; they're desperate for tools that actually work. Vigil meets them where they are.

The harder change management challenge would be telling them "we're doing a 2-year rewrite and nothing will improve until 2027."

---

### Who owns Vigil? How does this fit into our organizational structure?

**Product ownership:** Violation Processing Operations, with embedded product and engineering support

**Why ops owns it:** Vigil's value comes from being close to the work. The people who understand violation processing workflows should drive what gets built. Engineering provides the platform and modules; operations provides the direction.

**Governance model:**
- **User Committee:** Cross-functional group of power users who prioritize requests and provide feedback
- **Platform team:** Small engineering team responsible for core platform and module development
- **Executive sponsor:** [VP of Operations / appropriate leader] for strategic alignment and resource decisions

This is a deliberate inversion of our current model, where engineering owns workflow logic and operations submits tickets into a queue. Vigil puts control where domain expertise lives.

---

## Quick Reference

| Question | Short Answer |
|----------|--------------|
| Why not the rewrite? | 2 years, no new capabilities, same problems |
| What's the ROI? | $700K+ annual savings on one manual process alone; 7+ months faster partner revenue |
| What about microservices? | Wrong solution for our problem; complexity without benefit |
| How do we ensure quality? | Sandbox testing, version control, role-based publishing, automatic rollback |
| What team do we need? | 2-3 engineers ongoing vs. 10+ for the rewrite |
| What about the current system? | Incremental bypass, not risky big-bang migration |
| How do we expand to new violation types? | New templates and modules, not new code branches |

---

*Questions not addressed here? Raise them directly—this is a conversation, not a decree.*

---

**Vigil**  
*Your workflows. Your way.*
