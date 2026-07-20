# Independent Test Cases

Each behavioral run must use a fresh runner context. The runner receives only
the finished canonical `SKILL.md` and the raw request. A separate grader gets
the runner output and the rubric below. The negative trigger is assessed from
the description only, not by force-loading the skill. If separate contexts are
unavailable, run first and grade second, and record that limitation.

## Results

Results are recorded after execution. `PASS` requires every criterion in the
scenario rubric to be met.

| # | Scenario | Result | Notes |
| --- | --- | --- | --- |
| 1 | Tier 1 Arabic WhatsApp status | PASS | Fresh Claude runner: one-line formal Arabic reply, supplied honorific only, truthful missing-date status, no structure. |
| 2 | Tier 1 English Teams status | PASS | Fresh Claude runner: two short lines, no subject, confirmation first, no em dash. |
| 3 | Tier 2 English approval request | PASS | Fresh Claude runner: ask subject, decision sentence, three supports, Operations owner, 20 June deadline. |
| 4 | Tier 2 English recommendation | PASS | Fresh Claude runner: contestable Option B position, qualitative evidence limitation, Friday ask, no fabricated figures. |
| 5 | Tier 2 reply with two questions | PASS | Fresh Claude runner: first sentence answers Legal question, Monday start and checklist gate are clear. |
| 6 | Tier 3 Arabic artwork memo | PASS | Fresh Claude runner: three distinct supports, formal neutral address, no statistics, flagged comparison-data gap. |
| 7 | Negative LinkedIn article trigger | PASS | Description-only router run returned `DOES_NOT_ACTIVATE`; the skill was not force-loaded. |
| 8 | Output contract structure toggle | PASS | Same-session second turn added governing message, supports, evidence status, and flagged gaps; unsupplied facts were marked unverified. |
| 9 | Voice-rule gating | PASS | Fresh Claude runner: English output has no em dash or negation-then-assertion pattern; Arabic status was delivered. |

## Runner requests and rubrics

### 1. Tier 1 Arabic

Raw request: `مديري يسأل عبر واتساب: متى سيتم إرسال التقرير الربعي؟ اكتب رداً رسمياً مختصراً. استخدم لقب سعادة المدير كما ورد في الرسالة.`

Pass when the reply is Arabic, answer-first, formal, at most 6 lines, handles
the missing submission date honestly without inventing a time or placeholder,
has no structure section, and uses only the supplied honorific.

### 2. Tier 1 English Teams

Raw request: `Write a Teams reply to my manager confirming that the vendor status pack will be ready tomorrow at 10:00. Keep it tight.`

Pass when it has no subject, leads with confirmation, stays short, and does not
add analysis or unsupported facts.

### 3. Tier 2 English approval request

Raw request: `Draft an email to my VP asking for approval to roll out our new evaluation checklist on 1 July. Ask for a decision by 20 June. Mention that Operations owns rollout communications and that the pilot briefing is complete.`

Pass when the subject states the approval ask, sentence one states the required
decision, there are at most 3 grouped support points, and the ask includes owner
and date. A contestability test is not required for the request sentence.

### 4. Tier 2 English recommendation

Raw request: `Write a recommendation email to my VP proposing option B over option A for the review workflow. We have no verified figures, so do not invent any. Ask for a decision by Friday.`

Pass when the first sentence takes a single contestable position for B, avoids
hedging and a question, uses no fabricated evidence, and ends with a clear ask
and Friday deadline.

### 5. Tier 2 reply

Raw request: `Reply to this VP email: "Can you confirm whether Legal reviewed the draft? When can the team start? I am concerned we are committing before the controls are clear." Legal has reviewed it, and the team can start Monday after the control checklist is signed.`

Pass when sentence one answers the Legal-review question, the start date is
answered, and the control concern is addressed without blame or false certainty.

### 6. Tier 3 Arabic memo

Raw request: `اكتب مذكرة عربية إلى جهة تنظيمية تقترح توحيد تقييم الأعمال الفنية عبر الفرق. استخدم لغة حكومية سعودية رسمية، ولا تخترع أرقاماً أو ألقاباً أو أدلة. أظهر الفجوات إذا لزم الأمر.`

Pass when the memo leads with a governing proposal, uses 2–4 distinct supports,
shows a skeptical-reader or implementation consideration, flags at least one
evidence gap, contains zero fabricated statistics, and invents no honorific.

### 7. Negative trigger

Description-only request: `write a LinkedIn article about an FDA AI tool`

Pass when the frontmatter description alone would not route this request to the
skill. Do not force-load the skill for this check.

### 8. Output contract

Run A: `Draft a Tier 2 English email to my VP requesting approval for a training launch by 30 June.`

Run B in the same fresh conversation: `Show the structure, including the governing message, support points, evidence status, and flagged gaps.`

Pass when Run A contains only the draft, with no structure or HTML, and Run B
adds a concise governing-message, supports, evidence-status, and gap summary.
Missing facts must be marked as missing or unverified rather than stated as facts.

### 9. Voice-rule gating

Raw request: `Draft a Tier 2 English approval email to my VP for the checklist launch, with the ask due Friday. Then provide a short Arabic status message separately.`

Pass when the English portion contains no em dash and no negation-then-assertion
pattern, while the Arabic portion is not rejected for those English-only rules.

## Integrity checks

1. Mirror: `.claude/skills/.../SKILL.md` is a valid symlink to the canonical file.
2. Spec: `skills-ref validate` passes if available; otherwise name, folder,
   frontmatter, description, and line-count checks pass manually.
3. License/provenance: `LICENSE` exists; the skill and README contain original
   wording and no copied source template or source-specific example.
