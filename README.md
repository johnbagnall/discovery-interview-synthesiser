# Discovery Interview Synthesiser — Claude Skill

A Claude skill that transforms raw user research and discovery interview notes into structured
product intelligence — ready to paste into a PRD, opportunity solution tree, or stakeholder deck.

---

## What it does

Paste in raw notes, bullet summaries, or full verbatim transcripts — single or multiple
interviews at once. Get back:

| Output | What it contains |
|---|---|
| 📋 **Interview Snapshot** *(multi only)* | Quick-orientating table of interviewees, roles, and key themes before synthesis begins |
| 🎯 **Jobs to Be Done** | What users are trying to accomplish, with context, success criteria, prevalence count, and evidence |
| 😤 **Pain Points** | Typed (functional / emotional / social / financial), with severity, workarounds, prevalence, and quotes |
| 💡 **Opportunity Signals** | HMW-format opportunities with confidence level, prevalence count, and linked pain/job |
| 🔁 **Behavioural Patterns** | What users actually do vs. what they say, with prevalence in multi mode |
| 📣 **Standout Verbatims** | The 3–5 quotes worth putting in a stakeholder deck |
| ⚠️ **Research Gaps** | Honest about what the data cannot tell you |

After synthesis, it offers follow-on actions: generating an opportunity solution tree, writing a
problem brief, suggesting follow-up questions, or scoring pain points with RICE.

---

## Single vs. multiple interviews

The skill automatically detects how many interviews you've pasted and switches modes.

**Single interview** — standard synthesis with evidence quotes attributed to the interviewee
by name or role where available.

**Multiple interviews** — every JTBD, pain point, opportunity, and behavioural pattern gets
a prevalence count: `[3 of 5 interviewees]`. The output opens with an Interview Snapshot table
that orients the reader before the synthesis. Interviewees are assigned IDs (P1, P2…) if not
already named. Confidence levels on opportunities are calculated from prevalence rather than
just emotional signal.

The skill reads each interview separately before synthesising across them, to avoid early
transcripts anchoring the reading of later ones.

---

## Input formats supported

- Raw verbatim transcripts (with or without speaker labels / timestamps)
- Bullet-point interview notes
- Paraphrased summaries
- Mixed formats across multiple interviews in one paste

In transcript mode, direct quotes are treated as verbatims. In notes/summary mode, evidence
is clearly marked as paraphrased so PMs don't accidentally present it as a direct quote.

**Input** (paste raw notes like this):

```
Interview with Sarah, mid-market ops manager, 45 mins

- Uses 3 different tools to get one report out. "It takes me half a day every Monday 
  and I could be doing literally anything else."
- Doesn't trust the numbers until she's cross-checked them manually in a spreadsheet
- Her manager asks for the same report in two different formats for two different audiences
- Tried using the built-in export but "it always breaks the formatting and then I have 
  to fix it in Excel anyway"
- Would love something that just runs automatically — "I just want it to be there 
  when I wake up"
- Mentioned that a colleague in another team has a different tool that apparently does 
  this, but they're on a different contract
```

**Output:**

---

### 🎯 Jobs to Be Done

**Job:** Produce a weekly operational report without manual assembly

**Context:** Every Monday morning, before the working day begins

**Success looks like:** The report is ready, accurate, and formatted correctly without the user touching it

**Evidence:** *"I just want it to be there when I wake up"* — Sarah

**Frequency signal:** High (weekly recurring job)

---

### 😤 Pain Points

**Pain:** Cross-tool data assembly (Functional)

**Description:** Users must visit multiple tools to compile data for a single report, with no automated aggregation.

**Severity:** Critical

**Workarounds:** Manual copy-paste into a master spreadsheet; estimated half-day per week.

**Evidence:** *"It takes me half a day every Monday and I could be doing literally anything else."*

---

*(and so on for all sections)*

---

## Installing the skill

1. Download `discovery-interview-synthesiser.skill`
2. In Claude.ai, go to **Profile → Skills → Install from file**
3. Select the `.skill` file

Once installed, trigger it by pasting interview notes and asking Claude to synthesise them —
or just say *"pull out the themes"*, *"what are the pain points here"*, or *"find the JTBDs"*.

---

## Design decisions

**Why typed pain points?**
Functional, emotional, social, and financial pains require different solution strategies. A PM
who only captures functional pains will miss the emotional anxieties that often drive churn.

**Why confidence levels on opportunities?**
A single offhand comment and a recurring pattern from eight interviews are not the same thing.
Confidence levels force honest prioritisation and flag where more research is needed.

**Why does it ask for product context first?**
Identical user statements mean different things in a B2B analytics tool vs. a consumer app.
Without context, the synthesiser risks misclassifying signals.

**Why flag inferred insights?**
PMs often pass off their own interpretation as user evidence. The `(inferred)` tag keeps the
line between data and inference explicit, which matters when you're presenting to a sceptical
stakeholder.

**Why a Research Gaps section?**
Good synthesis includes knowing what you don't know. The gaps section surfaces the follow-up
questions worth taking back into the field — and prevents PMs from over-indexing on a small
or unrepresentative sample.

---

## Contributing

PRs welcome. If you improve the JTBD extraction logic, add domain-specific variants (B2B SaaS,
consumer, developer tools), or build a multi-interview aggregation layer, open a PR with a
before/after example.

---

## Licence

MIT
