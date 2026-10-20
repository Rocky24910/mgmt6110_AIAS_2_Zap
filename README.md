# Who Holds the Pen: Human-AI task map (MGMT 6110 group project)

A 2x2 map placing tasks from 3 businesses (modern farm, AI strategist, necklace jeweller), together with the School Mail Sentinel agent developed for MGMT 6110 Problem Set 5.

Each task is placed according to whether it has one right answer and whether people and AI must work together. The current website presents 13 tasks across 4 categories. The original group's map and project resources are preserved below.

**Personal PS5 website:** https://mgmt6110-ps5-school-mail-sentinel.vercel.app/

**Personal GitHub repository:** https://github.com/Rocky24910/mgmt6110_AIAS_2_Zap

---

## 1. Problem Set 5: School Mail Sentinel

School Mail Sentinel is a Gmail-based automation built for the individual Human-AI Collaboration assignment. It detects new emails matching a subject search query and sends an automated notification to my personal test inbox.

### Agent Card

- **The job:** Detect matching test emails and notify a postgraduate student to review them.
- **The trigger:** Gmail — New Email Matching Search, using `subject:PS5-URGENT`.
- **The tools:** Gmail New Email Matching Search (trigger) and Gmail Send Email (action).
- **It must never:** Send notifications to anyone other than my personal test inbox, or automatically reply to, forward, or delete emails.
- **Where a person checks:** The student reviews the alert and original email in Gmail, then decides what action to take.

### Testing and Improvement

The workflow was tested using real emails and Zapier run history.

1. Three initial live runs completed successfully for Assignment B, Assignment C, and Assignment D.
2. A tricky case used `Weekly Lecture Notes` as the subject and included `PS5-URGENT` only in the body. No new Zap History run appeared during the observation period, consistent with the subject-based search condition.
3. An initial limitation was identified: the notification body did not identify the original email.
4. The Gmail trigger's dynamic `Subject` field was inserted into the notification body.
5. The updated version was published as `Fix - Dynamic Email Subject`.
6. A post-fix live run successfully displayed `PS5-URGENT Fix Verification E` in the notification.

The combined Zap History JSON is submitted separately through eLearn and is not included in this public repository.

### Human-AI Collaboration Analysis

**Quadrant 03 — AI alone, with checks (bottom left).**

The email-matching task has a verifiable right answer: an email either matches the search condition or it does not. The screening can be automated without a person handling each message.

Human responsibility remains essential. The student checks the original email, interprets its context, and decides what action to take. The task's placement describes the screening work, not the entire process of responding to a school email.

### Human-AI Collaboration Log

- **Delegated to AI:** I used ChatGPT to plan the workflow, draft the Agent Card, explain the Gmail search trigger, and prepare the analysis and test plan.
- **What I checked:** I configured the Zap, reviewed the trigger and action test results, inspected successful Zap History records, and checked the delivered alert emails.
- **Issue identified and corrected:** The initial notification was generic. I inserted the original email's dynamic Subject field, published an updated version, and verified the result with a new live email.
- **Tricky case:** A body-only keyword test did not produce a new run during the observation period. This was consistent with the configured subject-only search rule, although one test cannot guarantee that every possible edge case is handled.
- **Time and cost:** Zapier displayed a seven-day Professional trial notice during the work. Therefore, I do not claim that all activity was completed on the Free plan.

### Three-Sentence Reflection

School Mail Sentinel fits "AI alone, with checks" because its email-matching task has a clear rule and can run without a person handling each message. Its main limitation is that a successful notification does not determine the importance of an email or decide what the student should do, and the initial generic message lacked useful context. I improved the workflow by adding the original email subject to the alert, and I would next test more edge cases and verify the plan's eligibility before relying on it for ongoing use.

---

## 2. Deploy to Vercel

The personal PS5 website is deployed from this GitHub repository:

https://mgmt6110-ps5-school-mail-sentinel.vercel.app/

To deploy from the repository root:

```bash
npx vercel --prod
