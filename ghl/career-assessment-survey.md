# Victory Society Career Assessment

> **Using the built assessment page (recommended):** `victory-village-assessment.html` already contains the questions, the email step, the Career Lane logic and the on-screen results. In GHL you only need the webhook workflow and the emails. Follow **"Quick setup for the assessment page"** right below, then use Part 3 and Part 4 for the email wording. Parts 1 and 2 are only needed if you build the survey inside GHL instead.

## Quick setup for the assessment page (about 10 minutes)

1. **Make the page.** In GHL, create a page at `/assessment`. Add a full-width section with 0 padding, drop in a **Custom JS/HTML** element, paste in all of `victory-village-assessment.html`, and set the page background to `#0b0907`.
2. **Make the workflow.** Go to **Automation → Workflows → Create workflow → Start from scratch**. Add the trigger **Inbound Webhook**. GHL shows you a URL; copy it.
3. **Connect the page.** In the page code, find `var WEBHOOK_URL = '';` and paste the URL between the quotes. Save and publish the page.
4. **Send one test.** Open the live page, take the assessment with your own email, then go back to the workflow trigger and click **Fetch sample request**. GHL now shows every field the page sends.
5. **Add these workflow actions:**
   - **Create/Update Contact:** map `first_name`, `last_name`, `email` and `phone` from the webhook. Map `career_lane` to a custom field called "Career Lane" (create it under Settings → Custom Fields). Map any answers you want to keep, such as `field`, `license`, `obstacle` and `salary_goal`.
   - **Add Tag:** add the tags from the webhook: `lane_tag`, `readiness_tag` and `assessment-complete`.
   - **If/Else on `readiness`:** if it's `ready`, send the results email with the Strategy Session closing; otherwise send it with the Toolkit closing. Use `{{contact.career_lane}}` in the email, or make one email per lane using the lane tag.
   - **Wait 2 days → Send email:** the follow-up from Part 4, only to contacts without a purchase tag.
6. **Test three times** with different answers (for example a nurse, a warehouse worker who wants field work, and a customer service rep who wants a desk job) and check each contact gets the right tags and email.

**What the page sends to GHL:** `first_name`, `last_name`, `email`, `phone`, `career_lane`, `lane_tag`, `readiness` (`ready` or `starting`), `readiness_tag`, `tags`, `field`, `years`, `claims_experience`, `license`, `strengths`, `work_style`, `travel`, `timeline`, `obstacle`, `salary_goal`, `source`, `submitted_at`, `page`.

---

# Building it as a GHL survey instead (optional)

**Name in GHL:** Victory Career Assessment
**Where it's used:** the "Try the Career Assessment" button on the sales page (send the survey link once it's built and it gets wired in).
**Length:** 10 questions plus a contact slide, about 3 minutes.

## How it works

1. The visitor answers 10 questions, one per slide.
2. On the last slide they give their name and email to "see my results."
3. A GHL workflow reads two answers (Q1 background and Q6 work style) and picks one of five **Career Lanes**. It tags the contact and emails them that lane's results.
4. A second answer pair (Q3 and Q4) sets a **Readiness** tag that decides whether the email pushes the $47 Toolkit or a $100 Strategy Session.
5. The visitor lands on a thank-you page that tells them their results are in their inbox.

The five lanes match the Career Map on the sales page:

| Lane | Claims roles in this lane |
|---|---|
| **A. Desk & Customer Claims** | Desk Adjuster, First Notice of Loss Rep, Auto Claims Adjuster, Claims Specialist |
| **B. Field & Property** | Field Adjuster, Property Adjuster, Catastrophe Adjuster, Auto Damage Appraiser |
| **C. Medical & Injury** | Medical Claims Reviewer, Workers' Comp Adjuster, Bodily Injury Adjuster, Nurse Case Manager |
| **D. Investigations & Compliance** | SIU Fraud Investigator, Compliance Analyst, Subrogation Specialist |
| **E. Liability & Examining** | Claims Examiner, Liability Claims Specialist, Commercial Claims Adjuster, Underwriter |

---

## Part 1: Build the survey

In GHL, go to **Sites → Surveys → Add Survey**. Use one question per slide, turn on the progress bar, and use your brand colors (background `#0b0907`, buttons `#d9a441`, font Inter).

Create a **custom field** for each question so the answers save on the contact. GHL offers this when you add a question.

### Slide 1: Intro (text element, no question)
> **What can your experience become?**
> Answer 10 quick questions. We'll show you the claims roles you're already closest to, the skills you're bringing with you, and your next step.
> Button: **Start my assessment →**

### Q1. What's your current or most recent field? *(single choice, required)*
- Customer service or call center
- Banking, finance or insurance sales
- Nursing or healthcare
- Warehouse, logistics, construction or trades
- Government or public sector
- Retail or hospitality
- Administrative or office support
- Military
- Other

### Q2. How many years of work experience do you have? *(single choice)*
- Less than 2 years
- 2–5 years
- 6–10 years
- More than 10 years

### Q3. What's your experience with insurance claims? *(single choice, required)*
- None, I'm brand new to claims
- Some: I've worked near claims (insurance office, billing, collections)
- I've worked in claims before
- I'm working in claims now

### Q4. Do you have an adjuster license? *(single choice, required)*
- No
- I'm studying for it now
- Yes, one state license
- Yes, more than one (or a Designated Home State license)

### Q5. Which of these do you already do well? *(multiple choice, pick up to 3)*
- Calming down upset or frustrated people
- Reviewing documents and catching details
- Working with numbers, money or budgets
- Understanding medical terms and treatment
- Inspecting things in person or hands-on work
- Spotting things that don't add up
- Following rules, policies and regulations
- Juggling a lot of open cases at once

### Q6. What kind of work day do you want? *(single choice, required)*
- At a desk, remote or in an office
- Out in the field, visiting homes and sites
- A mix of desk and field
- Traveling to disaster areas for big paydays (catastrophe work)

### Q7. Are you open to travel? *(single choice)*
- No travel
- Some local travel
- Overnight travel is fine
- I can deploy for weeks at a time

### Q8. When do you want to be working in your new role? *(single choice)*
- As soon as possible (0–3 months)
- In 3–6 months
- In 6–12 months
- I'm just exploring

### Q9. What's getting in your way the most? *(single choice)*
- I don't know which roles I actually qualify for
- I'm applying but not getting interviews
- My resume doesn't show my value
- I don't have a license yet
- I'm not sure how to explain my background
- I get interviews but no offers

### Q10. What salary are you aiming for? *(single choice)*
- Under $45,000
- $45,000–$60,000
- $60,000–$80,000
- $80,000+

### Final slide: See your results *(contact fields)*
> **Your results are ready.** Where should we send your Career Lane report?

- First name *(required)*
- Last name
- Email *(required)*
- Phone *(optional)*
- Checkbox *(required)*: "I agree to receive my results and career tips from Victory Society by email. I can unsubscribe anytime."

Button: **Send my results →**

**After submit:** in survey settings, set **On submit → Redirect to URL** to a thank-you page (for example `thevictoryvillage.com/assessment-results`) that says: "Check your inbox. Your Career Lane report is on its way." Add the $47 Toolkit button on that page.

---

## Part 2: Pick the Career Lane (the workflow logic)

**Automation → Workflows → Create workflow → Start from scratch**
**Trigger:** Survey Submitted, filtered to *Victory Career Assessment*.

Add an **If/Else** with these branches, checked in this order. The first one that matches wins.

| Order | If… | Lane |
|---|---|---|
| 1 | Q1 = Nursing or healthcare | **C. Medical & Injury** |
| 2 | Q6 = Out in the field **or** Traveling to disaster areas | **B. Field & Property** |
| 3 | Q1 = Warehouse, logistics, construction or trades **and** Q6 = A mix of desk and field | **B. Field & Property** |
| 4 | Q1 = Government or public sector **or** Military | **D. Investigations & Compliance** |
| 5 | Q1 = Banking, finance or insurance sales | **E. Liability & Examining** |
| 6 | Q5 includes "Spotting things that don't add up" **and** "Following rules, policies and regulations" | **D. Investigations & Compliance** |
| 7 | Everything else | **A. Desk & Customer Claims** |

In each branch:
1. **Add Tag:** `assessment-lane-a` (or b, c, d, e).
2. **Update Custom Field** "Career Lane" to the lane name.

### Readiness (second If/Else, after the lane step)

| If… | Tag | What the email recommends |
|---|---|---|
| Q3 = "I've worked in claims before" or "working in claims now", **or** Q4 = has a license | `assessment-ready` | **$100 Strategy Session** (Job Placement Strategy or Positioning) |
| Q9 = "applying but not getting interviews" or "interviews but no offers" | `assessment-ready` | **$100 Strategy Session** (Job Placement Strategy) |
| Everything else | `assessment-starting` | **$47 Victory Toolkit** |

Then:
- **Add Tag** `assessment-complete`.
- **Send Email:** the results email for their lane (Part 3). Use the readiness tag to choose which closing block to include, or make 10 versions (5 lanes × 2 readiness levels).
- **Wait 2 days → Send Email:** a follow-up to anyone without a purchase tag (Part 4).

---

## Part 3: Results emails

Every email uses the same frame. Fill in the lane block.

**Subject:** {{contact.first_name}}, your Career Lane: [Lane name]
**Preview text:** The claims roles your experience already points to.

> Hi {{contact.first_name}},
>
> Thanks for taking the Victory Career Assessment. Based on your answers, your strongest starting lane is:
>
> ## [Lane name]
>
> [Lane block]
>
> [Closing block]
>
> Victoria
> Victory Society

### Lane blocks

**A. Desk & Customer Claims**
> Your background in working with people, staying calm and handling a lot at once is exactly what desk claims teams hire for.
> **Roles to target:** Desk Adjuster · First Notice of Loss Rep · Auto Claims Adjuster · Claims Specialist
> **Skills you're bringing:** de-escalation, clear communication, problem solving, multitasking
> **Where it can lead:** Field Adjuster, Team Lead, Quality Analyst, Claims Manager

**B. Field & Property**
> You like hands-on work and being out of the office. Field and property claims reward people who can inspect, document and talk with homeowners on site, and catastrophe work can pay well during storm season.
> **Roles to target:** Field Adjuster · Property Adjuster · Catastrophe Adjuster · Auto Damage Appraiser
> **Skills you're bringing:** attention to detail, safety awareness, equipment know-how, working independently
> **Where it can lead:** Large Loss Adjuster, Independent Adjuster, Heavy Equipment Adjuster, Field Team Lead

**C. Medical & Injury**
> Your medical knowledge is rare in claims, and injury and workers' comp teams need it. You can read a treatment plan, spot what doesn't fit and advocate clearly.
> **Roles to target:** Medical Claims Reviewer · Workers' Comp Adjuster · Bodily Injury Adjuster · Nurse Case Manager
> **Skills you're bringing:** medical knowledge, clinical documentation, patient advocacy, calm under pressure
> **Where it can lead:** Clinical Review Lead, Litigation Specialist, Medical Claims Manager, Claims Director

**D. Investigations & Compliance**
> You follow rules, work cases and notice when something doesn't add up. That's the core of investigations and compliance work.
> **Roles to target:** SIU Fraud Investigator · Compliance Analyst · Subrogation Specialist · Claims Examiner
> **Skills you're bringing:** regulations and policy, case management, records and documentation, sound judgment
> **Where it can lead:** Fraud Unit Lead, Regulatory Compliance Manager, Litigation Specialist, Claims Manager

**E. Liability & Examining**
> Your comfort with numbers, risk and detail fits the analytical side of claims, where you evaluate coverage, liability and payments.
> **Roles to target:** Claims Examiner · Liability Claims Specialist · Commercial Claims Adjuster · Underwriter
> **Skills you're bringing:** financial analysis, fraud detection, compliance, client relationships
> **Where it can lead:** Large Loss Adjuster, Risk Manager, Claims Manager, Claims Director

### Closing blocks

**If tagged `assessment-starting` (recommend the Toolkit)**
> **Your next step:** the Victory Toolkit gives you the AI Victory Coach, job matching for your lane, and an application tracker so you can start applying with focus instead of guessing.
> **[Get the Victory Toolkit — $47/month →]** (link: `https://buy.stripe.com/8x28wO80u6Hl6s2f9AdMI01`)
> Cancel anytime.

**If tagged `assessment-ready` (recommend a Strategy Session)**
> **Your next step:** you already have experience to work with. A 1:1 Strategy Session with Victoria looks at your exact situation and shows you what to change so you start landing interviews and offers. Only 10 sessions open each quarter.
> **[Book a Strategy Session — $100 →]** (link: `https://api.leadconnectorhq.com/widget/booking/BWLUOaYsIjb80FvxDmVh`)

---

## Part 4: Follow-up email (2 days later, if they haven't bought)

**Subject:** Did you look at your Career Lane, {{contact.first_name}}?
> Hi {{contact.first_name}},
>
> Most people who take the assessment are surprised by how many claims roles they already qualify for. Your lane was **{{contact.career_lane}}**.
>
> If you're not sure where to start, reply to this email with the role you're most curious about and I'll point you in the right direction.
>
> [Same closing block as their results email]
>
> Victoria

---

## Part 5: Hook it up to the website

When the survey is published in GHL:
1. Copy its **share link** (Survey → Share), or its embed code if you'd rather show it on its own page.
2. Send it over, and the "Try the Career Assessment" button on the sales page gets pointed at it.

## Before launch: test it
- Take the assessment 3 times with your own email, choosing answers for different lanes (for example a nurse, a warehouse worker who wants field work, and a customer service rep who wants a desk job).
- Check that each contact gets the right lane tag and the matching email, and that the follow-up email waits 2 days.
