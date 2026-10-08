# Standards and sources

The fields behind the icons in [the list](README.md), and the sourced
detail for every entry. Where a claim could not be traced to the vendor's own site, docs or trust
center, it is marked **unverified**.

## Type: Enterprise, Open source, or Open core

- **Enterprise** — closed source, run by a vendor. You cannot self-host it or inspect its code.
- **Open source** — source published under an OSI-approved license; you can self-host it.
- **Open core** — some parts open source, others closed or paid. The entry says which.
- **To be decided** — used only when a tool's license is not stated anywhere we can check.

## Fields

Every tool is described on these fields where information is available. `unverified` means we
could not confirm the claim from the vendor's own materials — not that the answer is "no."

| Code | Field | What it means |
|---|---|---|
| **BAA** | Business Associate Agreement | 🟢 self-serve (signed in-app/on signup) · 🟡 on request (contact sales/support) · 🔴 not offered |
| **Trains** | Trains on your data | 🔴 yes · 🟡 opt-out / de-identified only · 🟢 no · ⚪ unclear |
| **Retain** | Data retention | Stated policy, briefly, or ⚪ unclear |
| **Host-self** | Self-hostable | ✅ / ❌ |
| **OSS** | Open source | License name, or ❌ |
| **E2EE** | End-to-end encryption (sessions/messages) | ✅ / ❌ / ⚪ unclear (encrypted-in-transit/at-rest ≠ E2EE) |
| **Export** | Data export in an open format | ✅ / ❌ / ⚪ unverified |
| **Cert** | SOC 2 / HITRUST | Which, if any |
| **Hosted** | Where data lives | Cloud/region if stated |
| **Big Tech** | Runs on AWS / Google / Microsoft | Named provider, or ⚪ unverified — relevant if you're trying to keep a client's data out of a specific Big Tech company's hands |

Sources for every claim below are linked inline. "Vendor's own site" means their docs, security
page, trust center, or terms — not a review site, comparison blog, or compliance-consultant
summary (those show up constantly in search results and often restate or misstate the vendor's
actual position).

---

## EHR / practice management (including built-in telehealth)

| Tool | Type | BAA | Trains | Retain | Host-self | OSS | E2EE | Export | Cert | Hosted | Big Tech |
|---|---|---|---|---|---|---|---|---|---|---|---|
| **[limn](#limn)** | Open core (limn-os, the locally hosted app, is open source, license to be announced; the client portal is paid, as a self-host license or a hosted co-op plan) | 🟡 planned, not yet live | 🟢 no (see below) | text to Claude held 30 days then deleted; audio never leaves the server | ✅ | 🟡 limn-os open source (license to be announced); client portal closed | ⚪ not yet built | ⚪ not yet built | 🔴 none (pre-launch) | Vultr (signed BAA) | Amazon not in the audio path; see caveat below |
| **[SimplePractice](https://www.simplepractice.com/baa/)** | Enterprise | 🟢 self-serve, all paid plans ([BAA page](https://www.simplepractice.com/baa/)) | 🟢 no, for its AI Note Taker feature — de-identified transcripts are used only for product/prompt improvement, never used to train the underlying model, never shared commercially ([AI in therapy](https://www.simplepractice.com/blog/ai-in-therapy/)) | ⚪ unverified exact window — ToS reportedly states data retained no more than 64 days post-termination, then de-identified; verify current wording directly before citing as firm | ❌ | ❌ | ⚪ unverified — encryption in transit/at rest claimed, "end-to-end" phrase not confirmed | ✅ — vendor instructs exporting data before cancellation ([cancellation article](https://support.simplepractice.com/hc/en-us/articles/11462507018253)) | HITRUST certified per trust-center references (page is JS-rendered; open directly to confirm exact wording before treating as fully vendor-confirmed) | AWS confirmed for the AI feature specifically (AWS Bedrock); core platform hosting unverified | **AWS confirmed** (AI feature runs on AWS Bedrock + Anthropic's Claude) |
| **[TherapyNotes](https://www.therapynotes.com/features/security/)** | Enterprise | 🟢 self-serve, folded directly into Terms of Service, all subscription levels ([BAA article](https://support.therapynotes.com/hc/en-us/articles/30661265032219)) | 🟢 no, for its "TherapyFuel" AI notes feature — data not sold, stays in TherapyNotes' system, not used to train outside AI models; any AI subprocessor must be under a BAA barring training use ([HITRUST-for-AI announcement](https://blog.therapynotes.com/therapynotes-achieves-hitrust-ai-security-certification-for-therapyfuel)) | ⚪ unverified exact window — tied to BAA/legal terms; account "abandoned" after 60 days non-payment | ❌ | ❌ | ⚪ unverified — "end-to-end" phrase not confirmed | ✅ — vendor instructs exporting data before cancelling | **HITRUST certified**, including an AI-specific HITRUST certification for TherapyFuel specifically ([announcement](https://blog.therapynotes.com/therapynotes-achieves-hitrust-ai-security-certification-for-therapyfuel)) | ⚪ unverified | ⚪ unverified |
| **TheraNest** (rebranded **Ensora Mental Health**, under Ensora Health) | Enterprise | ⚪ unverified process — offered, but Ensora's own request flow wasn't directly confirmed; check [ensorahealth.com](https://ensorahealth.com/security/) directly before citing | ⚪ unverified for the base product; their "Ensai" AI assistant is described (per secondary sources referencing Ensora's own materials) as BAA-covered with a non-training policy — not independently confirmed on the security page fetched | ⚪ unverified | ❌ | ❌ | ❌/⚪ AES-256 at rest via AWS KMS, TLS in transit — not E2EE ([security page](https://ensorahealth.com/security/)) | ⚪ unverified | HITRUST e1 certified for TheraNest/Ensora Mental Health specifically ([announcement](https://ensorahealth.com/blog/ensora-mental-health-achieves-hitrust-e1-certification/)) | AWS confirmed — "AWS Key Management Service for RDS database volume encryption" ([security page](https://ensorahealth.com/security/)) | **AWS confirmed** |
| **[Owl Practice](https://owlpracticesuite.com/)** | Enterprise | 🟢 listed as available in site footer; process not verified | ⚪ unverified — no AI-training statement found on the homepage | ⚪ unverified | ❌ | ❌ | ⚪ unverified | ⚪ unverified | ⚪ HIPAA badge only; no SOC 2/HITRUST stated | ⚪ unverified | ⚪ unverified |
| **[Sessions Health](https://www.sessionshealth.com/)** | Enterprise | ⚪ not addressed on homepage; confirm directly | ⚪ unverified — markets an "AI Assist" documentation feature, no training statement on the page | ⚪ unverified | ❌ | ❌ | ❌/⚪ AES-256 at rest and in transit claimed; not E2EE | ⚪ unverified | SOC 2 Type II and HITRUST referenced on site (Trust Center link; open directly to confirm) | "U.S.-based servers" (provider not named) | ⚪ unverified |
| **[TheraPlatform](https://www.theraplatform.com/)** | Enterprise | ⚪ not stated on the homepage; confirm directly | ⚪ unverified — advertises "AI therapy notes," no training statement | ⚪ unverified | ❌ | ❌ | ❌/⚪ encrypted at rest and in transit claimed; not E2EE | ⚪ unverified | ⚪ "regular audits" claimed; no named certification | ⚪ unverified | ⚪ unverified |

TheraPlatform's homepage also lists speech, OT and PT clinicians, so it is borderline; kept because
its lead audience and built-in video and therapy aids are mental-health focused. Jane App was
removed: its own homepage sells to counselling, massage, physio and chiropractic alike.

### `limn`

**Honest stage: pre-launch / alpha.** Not publicly sold yet. [`limn`](https://limn.dev) is
in two parts. **limn-os**, the app a practice hosts on its own machine, is open source (license
to be announced) and free. The **client portal** is the paid part: either a self-host license
bought once, or hosting by the maintainer on a shared co-op server for a monthly co-op fee.

- **Positioning, and its limit:** the plan is to keep Amazon out of the parts under `limn`'s
  direct control — hosting and speech-to-text run on Vultr (self-hosted Whisper) under a signed
  Vultr BAA, with no AWS anywhere in that path. **This is not the same as "no Amazon anywhere."**
  Anthropic (whose Claude API `limn` plans to use for AI features) lists Amazon Web Services
  among its own subprocessors. So: audio never touches Amazon, and the text that reaches Claude
  is de-identified first — but Claude's own infrastructure is not Amazon-free, and a strict
  Amazon boycotter should know that before choosing `limn` on those grounds alone. Amazon is also
  a major investor in Anthropic, which is a separate reason the same boycotter might object.
- **De-identification design (not yet built):** the plan is to strip names, places, dates, and
  other identifiers on the Vultr server before any text reaches Claude, and restore them when the
  answer comes back — so what briefly sits at Anthropic (protected under its BAA, not used for
  training, deleted after 30 days per Anthropic's HIPAA-ready terms) barely points to a real
  person. This is a design intent, not a shipped feature.
- **Where it doesn't yet meet this list's fields:** no BAA is live yet (planned, not signed
  with customers), no SOC 2/HITRUST (pre-launch, no customers to audit for), data export and
  E2EE for the client portal aren't built. Listing `limn` here before those exist is the
  disclosure trade-off stated at the top of this document.

---

## Open-source practice management

Source under an OSI license, self-hosted. Verify maturity yourself before trusting client data to
either.

| Tool | Type | BAA | Trains | Retain | Host-self | OSS | E2EE | Export | Cert | Hosted | Big Tech |
|---|---|---|---|---|---|---|---|---|---|---|---|
| **[My Practice](https://github.com/dholbach/my-practice)** | Open source (AGPL-3.0) | 🔴 n/a — you self-host, so you are the covered entity | 🟢 no AI at all; nothing to train | you set the policy | ✅ Docker | ✅ AGPL-3.0 ([repo](https://github.com/dholbach/my-practice)) | ⚪ clinical notes encrypted at the application layer (Fernet) plus disk encryption; not E2EE in the messaging sense | ⚪ unverified | 🔴 none | your own hardware | Built by Daniel Holbach, a Berlin psychotherapist, from late 2025 for his own private-pay practice; used daily since early 2026. Django / PostgreSQL / Docker. About 917 commits, 1,400+ tests, 6 stars (as of 2026-09-29). Features: encrypted clinical notes, invoicing, calendar and bank import, analytics. **No client portal, no AI, single-practitioner setup**; Germany/GDPR orientation. |
| **[Synari EHR](https://github.com/gheetdufa/synari-ehr)** (also [synari.org](https://synari.org/)) | Open source (AGPL-3.0) | 🔴 n/a when self-hosted (you are the covered entity; its docs say you need BAAs with your own hosting and service providers). **Hosted version: search results say a hosted offer exists ("70% off for new customers"), but no BAA statement was found; synari.org renders only the word "Synari" and the repo says no commercial hosting is offered, so treat hosted BAA as unverified** | 🟢 no training by Synari; the AI assistant (drafts notes from typed notes, dictation or a consented recording) is **off unless you configure an OpenAI-compatible provider of your choosing**, so the provider's terms and BAA then apply; no specific transcription vendor is named | session audio deleted when the note is signed; other retention set by you | ✅ Docker, single-server guide | ✅ AGPL-3.0 ([repo](https://github.com/gheetdufa/synari-ehr)) | ⚪ clinical data and stored files encrypted with key rotation, encrypted backups; not E2EE | ⚪ SimplePractice import claimed; export unverified | ⚪ **no certification.** `docs/hipaa/controls-matrix.md` maps controls to the HIPAA Security Rule (marketing also cites HITRUST and SOC 2 mapping); a matrix is not an audit | wherever you host it (hosted service: unverified) | your choice when self-hosted. Also claimed: per-practice data isolation, every record access audited (tamper-evident, hash-chained log), required staff 2FA, no clinical content in emails or texts, recording needs every participant's consent. Features: scheduling, client portal, telehealth (LiveKit), reminders, invoicing, AutoPay, claims with clearinghouse and eligibility checks, transcription. **Single commit, 0 stars as of 2026-09-29 — early-stage, unproven.** Closest to `limn` in aim (a self-hostable, privacy-first therapy practice platform), so the disclosure at the top applies with extra force. |

---

## AI notes / scribes

Only tools whose own site targets therapists / behavioral-health clinicians.

| Tool | Type | BAA | Trains | Retain | Host-self | OSS | E2EE | Export | Cert | Hosted | Big Tech |
|---|---|---|---|---|---|---|---|---|---|---|---|
| **[Upheal](https://www.upheal.io/privacy-and-compliance)** | Enterprise | 🟢 self-serve, available directly on site | 🟡 opt-in only — "never uses your sessions to train...without explicit permission" | ⚪ unverified | ❌ | ❌ | ⚪ unclear — "record-level encryption," not stated as E2EE | ⚪ unverified | SOC 2 Type II | AWS, region unstated | **AWS confirmed** |
| **[Mentalyc](https://www.mentalyc.com/security)** | Enterprise | 🟢 self-serve, generated in-profile | 🟢 no — "session data is never used to train AI models" | audio deleted once note is ready; transcripts anonymized, user-deletable | ❌ | ❌ | ⚪ unclear — AES-256, not stated as E2EE | ⚪ unclear — notes downloadable, no full export mechanism described | SOC 2 Type II | AWS, US data residency stated | **AWS confirmed** |
| **[Eleos](https://eleos.health/security/)** | Enterprise | 🟢 available, linked on security page | 🟡 partial — may retain **de-identified audio** to improve accuracy; states data is never sold/licensed | dashboard data kept a stated-but-unspecified number of days, then de-identified/deleted on request | ❌ | ❌ | ⚪ unclear | ⚪ unverified | SOC 2 Type II + HITRUST | AWS, continental US only | **AWS confirmed** |
| **[Blueprint](https://www.blueprint.ai/privacy-security)** | Enterprise | 🟢 automatic, part of ToS | ⚪ **caveat** — security page says "never used to train AI models," but Blueprint's own Platform Services Agreement is reported to reserve the right to use *de-identified* data "for the development of models, features, or functionality." The two statements aren't fully reconciled from what's public — read their current ToS before relying on the plain "never" claim | ⚪ unverified — "standard professional and legal retention expectations," no specific window | ❌ | ❌ | ❌/⚪ "industry-standard encryption in transit and at rest," not E2EE | ⚪ unverified | SOC 2 Type II, annual audits | US-based, provider not named | ⚪ unverified — not disclosed |
| **[Supanote](https://www.supanote.ai/)** | Enterprise | 🟢 BAA linked from the site | ⚪ unverified — states data is encrypted and inaccessible to Supanote; no training statement | recordings "immediately deleted after scribing" (own claim) | ❌ | ❌ | ❌/⚪ "fully encrypted," not stated as E2EE | ⚪ unverified | ⚪ none stated on the homepage (a separate security site exists; not fully read) | "HIPAA and PHIPA compliant databases," provider not named | ⚪ unverified |
| **[AutoNotes](https://www.autonotes.ai/)** | Enterprise | 🟢 available per site | ⚪ unverified | ⚪ unverified | ❌ | ❌ | ⚪ unverified | ⚪ unverified | ⚪ SOC 2 mentioned in passing; unconfirmed | ⚪ unverified | ⚪ unverified |

Removed: Freed (general-medicine scribe, not marketed to therapists). Quill was not added: its
site could not be reached, so nothing could be verified.

---

## Payments (therapist-specific)

| Tool | Type | BAA | Trains | Retain | Host-self | OSS | E2EE | Export | Cert | Hosted | Big Tech |
|---|---|---|---|---|---|---|---|---|---|---|---|
| **[Ivy Pay](https://www.talktoivy.com/ivypay)** | Enterprise | 🟢 claimed as automatic/included in ToS for covered entities — this is Ivy Pay's own marketing claim; independent confirmation of a legally executed BAA (vs. a template shown post-signup) wasn't possible this pass | ⚪ unverified | ⚪ unverified — privacy policy discusses deletion-on-request, no stated period | ❌ | ❌ | ⚪ unclear — TLS/SSL only mentioned (transport, not E2EE) | ⚪ unverified | ⚪ unverified — no SOC 2/HITRUST claim found | ⚪ unverified | ⚪ unverified — **its compliance claims overall are thinly documented compared to Square's** |

Stripe and Square were removed as general-purpose payment processors.

---

## Intake & client matching

Practice-growth tools for the front door of a therapy practice (inquiries, follow-up, matching a
client to a clinician).

| Tool | Type | Notes |
|---|---|---|
| **[Breksey](https://breksey.com/)** | Enterprise | Self-described "operating system for therapy practices," aimed at practices of 5+ clinicians (supports 1–25+): inquiry capture across channels, automated follow-up, AI-assisted client–clinician matching (its assistant "Brian," with a human in the loop), referral tracking, directory-profile management, and optional billing, credentialing, marketing and website services. CEO Maya Topitzer, Mesa, Arizona. Platform $300/month for up to 15 clinicians ([pricing](https://breksey.com/pricing)). The homepage says only "HIPAA-aligned," which is not a BAA. No BAA is mentioned on the homepage or pricing page, and no certification, hosting provider or AI-training statement was found; the privacy and security pages tried returned 404, and no terms page was located. **Adjacent to limn, a competing practice-management product, so the disclosure at the top applies.** |

---

## Licensure, supervision hours & CEUs

Trackers for pre-licensure supervision hours and continuing education, marketed to therapists.
These mostly should not need client PHI (hours and categories, not clinical content). None of the
four states its BAA or privacy policy on the pages checked. If you enter client names or initials, treat it as
PHI. **Disclosure, specific to this category:** supervision-hours tracking is a feature planned for
`limn`, so `limn` overlaps with every row below; weigh these entries with that in mind.

| Tool | Type | Notes |
|---|---|---|
| **[Confirm](https://confirmmyhours.com/)** (Confirm My Hours) | Enterprise | Tracks supervised hours toward LMFT / LPCC / LCSW licensure, fills the board's Experience Verification forms (supervisor still signs), and tracks CEUs per license with renewal clocks; says it supports all 50 states, built by a supervising LMFT, free during beta (site tagline: "licensure hours and CEUs, handled"). **Overlaps limn's planned supervision-hours feature.** The site renders by JavaScript; its privacy and terms pages returned no readable text, so BAA, training, retention, hosting and certifications are all unverified. |
| **[Track Your Hours](https://www.trackyourhours.com/)** | Enterprise | Marketed to LMFT, LCSW, LPCC, LMHC and LPC trainees (California, New York, Texas); 30-day free trial. Homepage names no BAA, hosting, encryption or export; privacy policy not read. |
| **[Time2Track](https://time2track.com/track-LPC-counseling-hours)** | Enterprise | Counseling, psychology and MFT trainees and training programs; "secure" cloud storage claimed. No BAA, hosting or export statement on the page checked. |
| **[License Trail](https://www.licensetrail.com/)** | Enterprise | Counselors, MFTs, social workers and psychologists, all 50 states; says it "never store[s] client identifying information"; board-ready PDF export with an integrity hash. No BAA, hosting or certification stated. |

---

## Directories and matching

Directories are lead-generation, not PHI-handling systems in the same sense as the tools above —
most explicitly do not sign a BAA because a public listing plus an inbound-message inbox isn't
positioned as a covered function. Listed briefly: BAA status and privacy-policy link only.

| Directory | Type | BAA | Notes |
|---|---|---|---|
| **[Psychology Today](https://docs.psychologytoday.com/directory/privacy-policy/en/v1.0.22)** | Enterprise | 🔴 no BAA for the directory/profile itself — their BAA applies only to the separate "Sessions" video product, not the listing | Messages from potential clients route to your email; treat as a public-facing lead channel, not a secured inbox |
| **[Zencare](https://zencare.co/policy/business-associate-agreement)** | Enterprise | ⚪ **unclear scope** — Zencare publishes a standalone BAA policy page, which suggests some Zencare product offers one, but it wasn't confirmed whether that covers the free directory listing or only a paid practice-management add-on. Don't cite "Zencare offers a BAA" for the plain directory without checking scope directly. | Privacy policy: [zencare.co/policy/privacy-policy](https://zencare.co/policy/privacy-policy) |
| **[TherapyDen](https://www.therapyden.com/privacy-policy)** | Enterprise | 🔴 no — no mention of BAA/HIPAA/PHI anywhere in TherapyDen's own privacy policy | Discloses third parties: Stripe (payments), Brevo (email), Google Analytics, Cloudflare; states it does not sell/rent/trade personal information; profiles are public by design, and TherapyDen notes third-party data brokers can scrape public listings (a general directory risk, not something TherapyDen itself does) |
| **[Inclusive Therapists](https://www.inclusivetherapists.com/about/privacy)** | Enterprise | 🔴 no — no mention of BAA/HIPAA/PHI in its own privacy policy | Client match-request data goes to matched providers and site admins, deleted from site storage within 90 days of a match (or sooner on request); states data is never sold or shared with law enforcement absent legal process; notable for explicitly welcoming clinicians located outside the US |
| **[MyWellbeing](https://www.mywellbeing.com/)** | Enterprise | ⚪ no BAA or HIPAA statement on its homepage; it also runs a telehealth platform for affiliated practices, so ask directly | Questionnaire-based matching (3 matches) plus a searchable provider directory; affiliated practices are described as independently owned by licensed clinicians |

---

---

## Insurance networks, billing services and clearinghouses (added 2026-10-02)

"Snippet" means the vendor's site refused automated reading, so the fact comes from a search-result excerpt of the vendor's own page; re-check before relying on it.

| Tool | Facts and sources |
|---|---|
| Alma | BAA part of membership terms ([help center](https://support.helloalma.com/hc/en-us/articles/360047494354-Alma-Business-Associate-Agreement), snippet). $125/month or $1,140/year ([membership overview](https://support.helloalma.com/hc/en-us/articles/22200117802907-Membership-Overview), snippet). Tagline from [helloalma.com/for-providers](https://helloalma.com/for-providers/). |
| Grow Therapy | Free, free credentialing, weekly pay ([providers page](https://growtherapy.com/providers/), snippet). Signs BAAs "with all third parties who process PHI"; certification claim is its host's (AWS) SOC 2 ([trust page](https://growtherapy.com/legal/trust/)). |
| Headway | Free credentialing, no membership fee ([provider page](https://provider.headway.co/?page_variant=insurance-credentialing), snippet). Provider BAA unverified; help center mentions only vendor BAAs ([HIPAA article](https://help.headway.co/hc/en-us/articles/360058922872-HIPAA-compliance-and-PHI), snippet). |
| Rula | Free to join (rula.com FAQ, snippet). BAA and certifications unverified. |
| SonderMind | ISO 27001 (snippet). BAA, provider cost unverified. |
| TheraThink | Mental-health billing service. $35/month per tax ID + NPI for its clearinghouse (Office Ally); percentage of allowed amount on paid claims; credentialing $130 commercial, $270 Medicare/Medicaid ([FAQ](https://therathink.com/faq/)). |
| Availity | Free for payers that sponsor it ([Essentials Plus](https://www.availity.com/essentials-plus/)). Business Associate / Trading Partner Agreement ([PDF](https://essentials.availity.com/availity/documents/availity_business_associate_trading_partner_agreement.pdf), snippet). HITRUST CSF ([blog](https://www.availity.com/blog/modernizing-your-edi-solution-vendor-selection/)). |
| Claim.MD | $30/month + $0.30–0.50 per claim; $60 and $120 tiers ([pricing](https://www.claim.md/pricing), snippet). HITRUST r2 ([news](https://www.claim.md/news/claimmd-maintains-hitrust-r2-certification-and-strongly-encourages-vendors-to-adopt-similar-security-practices-to-strengthen-protection-of-sensitive-claims-data), snippet). BAA unverified. |
| Eligible | Clients must sign a BAA ([FAQ](https://eligible.com/community/eligible-new-customer-faq/), snippet). Price, certifications, current ownership unverified. |
| Inovalon | Acquired ABILITY Network 2018 ([news](https://www.inovalon.com/news/inovalon-completes-previously-announced-acquisition-of-ability-network/), snippet). HITRUST, SOC 2 Type 2 ([values page](https://www.inovalon.com/our-company/vision-values/), snippet). BAA unverified. |
| Office Ally | Standard BAA form ([PDF](https://cms.officeally.com/OfficeAlly/Forms/OA-Business-Associate-Agreement-91917.pdf)); its own pages conflict on whether signing is required ([HIPAA page](https://cms.officeally.com/hipaaprivacy)). Free to participating payers; $44.95/month per tax ID + NPI if any non-participating payer; eligibility $10/month for 100 ([pricing](https://cms.officeally.com/products/pricing)). HITRUST, SOC 2 Type 2 ([certifications](https://cms.officeally.com/certifications)). All snippet. |
| Optum EDI Network | Formerly Change Healthcare; EHNAC-certified ([EDI page](https://business.optum.com/en/operations-technology/network-connectivity/medical/edi.html)). 2024 ransomware: deployed 21 Feb 2024; about 190 million people affected, the largest U.S. health-care breach ([HHS FAQ](https://www.hhs.gov/hipaa/for-professionals/special-topics/change-healthcare-cybersecurity-incident-frequently-asked-questions/index.html), snippet; [UnitedHealth statement](https://www.unitedhealthgroup.com/newsroom/2024/2024-04-22-uhg-updates-on-change-healthcare-cyberattack.html)). BAA, price unverified. |
| pVerify | Eligibility only, not claims. From $125/month for 500 checks, 1-year terms ([pricing](https://pverify.com/pricing/)). SOC 2 Type II ([announcement](https://pverify.com/pverify-announces-successful-soc2-compliance-examination/), snippet). |
| Stedi | Signs a BAA ([pricing FAQ](https://www.stedi.com/pricing)). Claims $0.30–0.10, no monthly minimum (same page). SOC 2, HITRUST r2 ([blog](https://www.stedi.com/blog/stedi-achieves-hitrust-r2-certification)). |
| TriZetto Provider Solutions | "SOC 2, EHNAC and HITRUST certified platform" ([homepage](https://www.trizettoprovider.com/)). BAA, price unverified. |
| Waystar | Signs BAAs with clients per its SEC filings ([filing](https://investors.waystar.com/node/7446/html), snippet). SOC 2, HITRUST CSF ([press release](https://www.waystar.com/news/waystar-achieves-hitrust-csf-certification-to-manage-risk-improve-security-posture-and-meet-compliance-requirements/)). Price not public. |

---

## Added 2026-10-02: EHRs, AI notes, measurement, directories, websites, resources

| Tool | Facts and sources |
|---|---|
| ICANotes | Behavioral health EHR ([homepage](https://www.icanotes.com/)). BAA offered for covered entities ([blog](https://www.icanotes.com/2026/01/27/ambient-ai-scribe-mental-health/), snippet). "No client data is shared with outside systems" ([AI page](https://www.icanotes.com/ai-powered-documentation/)); training statement unverified. Notes Only $55/month, Non-Prescribing $75, Prescribing $213 + $99 activation; AI Scribe $49/user ([pricing](https://www.icanotes.com/pricing/)). |
| TherapyAppointment | "HIPAA aligned with executed BAA" ([homepage](https://therapyappointment.com/)). "We have no plans to use your clients' data for AI training" ([security](https://therapyappointment.com/security-and-compliance)). $10–59/month by session volume; AI notes $0.59 each ([pricing](https://therapyappointment.com/pricing/)). |
| Valant | Will not train AI on customer data without prior written consent ([AI Services Addendum](https://go.valant.io/rs/966-BJH-134/images/Valant_AI_Services_Addendum-v2025.121.pdf), snippet). HITRUST i1 ([blog](https://www.valant.io/resources/blog/valant-earns-hitrust-i1-certification-strengthening-data-security-for-behavioral-health-providers/), snippet). BAA unverified. Quote-based pricing ([plans](https://www.valant.io/plans-pricing/)). |
| Twofold | General medical scribe with a therapy note taker ([therapy page](https://www.trytwofold.com/solutions/therapy-ai-note-taker)) — borderline under the scope rule. "Every Twofold account receives a signed BAA"; does not train on audio, transcripts, notes or PHI; does not store raw audio; HITRUST listed; $69/month billed annually ([homepage](https://www.trytwofold.com/)). |
| Greenspace | SOC 2 Type II; hosted on Aptible ([FAQ](https://greenspacehealth.com/en-us/faqs/)). Basic $24.99/month, Premium $39.99 ([providers](https://greenspacehealth.com/en-us/providers/)). BAA unverified. |
| NovoPsych | BAA takes effect when you accept the Terms of Service ([homepage](https://www.novopsych.com/); [BAA](https://novopsych.com/business-associate-agreement-hippa/)). NovoNote data not used to train AI ([NovoNote security](https://novopsych.com/novonote-security/), snippet). Free plan; Pro price varies by region ([pricing](https://www.novopsych.com/pricing)). |
| Open Path Collective | Free for clinicians; clients pay $65 once; sessions $40–70 in the US ([homepage](https://openpathcollective.org/); [therapist FAQ](https://openpathcollective.org/faqs-from-therapists/), snippet). No BAA found (referral directory). |
| Therapy for Black Girls | Listing $25/month or $300/year; licence required ([start here](https://therapyforblackgirls.com/start-here/)). No BAA found. |
| Brighter Vision | Websites for therapists ([websites](https://www.brightervision.com/websites/), snippet). HIPAA package is a BAA with Hushmail, not Brighter Vision ([HIPAA email](https://www.brightervision.com/hipaa-compliant-email/), snippet). $99–349/month, $100 setup ([pricing](https://www.brightervision.com/pricing/), snippet). |
| Therapist Aid | "For therapists, by therapists"; free plan plus paid Professional plan, price unverified ([plans](https://www.therapistaid.com/plans)). Stores no client records. |
| Pocket | Added 2026-10-03 after a social-media ad headed "For therapists overwhelmed by rewriting their notes." Its own site sells a general AI recorder ([homepage](https://heypocket.com/), [product page](https://heypocket.com/pages/pocket)): "end-to-end encryption", "Enterprise-grade encryption ... in transit and at rest", "Your data is never sold or shared." No HIPAA, BAA, therapist page or AI-training statement found on heypocket.com. A HIPAA/SOC 2 claim appears only on a competitor's blog (Heidi Health), so it is unverified. |
| Pocket Scribe | Added 2026-10-04. "The AI Solution for Medical Note Dictation"; testimonials from family medicine, psychiatry and emergency medicine, no therapist page ([homepage](https://www.mypocketscribe.com/)). Claims "100% HIPAA-compliant", SOC 2 Type II, encryption in transit and at rest, cloud on MedStack; under enterprise agreements "patient data is not stored, retained, or used to train AI models"; mentions a BAA only in passing ("HIPAA isn't just signing a BAA") ([HIPAA page](https://www.mypocketscribe.com/hipaa)). Speech-to-text partner named as Deepgram (homepage). $33/month resident, $65 standard, $99 Scribe Max; no BAA mentioned on [pricing](https://www.mypocketscribe.com/pricing). |

---

## Dictation tools (added 2026-10-04)

Dictation tools need not be therapist-specific (maintainer's rule, 2026-10-04). "Snippet" = search-result excerpt of the vendor's own page.

| Tool | Facts and sources |
|---|---|
| Augnito | Title "Enhance Clinical Documentation with Voice AI" ([augnito.ai](https://augnito.ai/)). HIPAA, ISO 27001, SOC 2, GDPR badges ([site](https://wp.augnito.ai/)). BAA, training, cloud provider unverified; Spectra Lite 992 INR, Professional 2,999 INR (snippet). |
| Dragon Medical One | Microsoft Azure, data stays in its geography; in-memory recognition ([security white paper](https://learn.microsoft.com/en-us/industry/healthcare/dragon-copilot/whitepapers/security)). HITRUST CSF (snippet). $99/month 1-year, $89 2-year, $79 3-year plus service fee (snippet, [Nuance support](https://dragon.nuance.com/support-product-healthcare)). Customer BAA unverified. LTSR version ends 31 Dec 2026 ([dragonmedicalone.nuance.com](https://dragonmedicalone.nuance.com/)). |
| Dragon Professional | Locally installed Windows recognition (snippet, data sheet); Dragon Anywhere (cloud) not for HIPAA data per its licence (snippet). Price unverified. |
| Fluency Direct | Solventum Cloud Platform, 250+ EHRs ([product page](https://www.solventum.com/en-us/home/health-information-technology/solutions/fluency-direct/), snippet). BAA, training, certifications unverified; enterprise pricing. |
| Heidi Dictate | Executes BAAs on request (snippet). "We don't use any of your sensitive health information for model training"; does not store audio; SOC 2 Type 2, ISO 27001 ([privacy FAQ](https://www.heidihealth.com/legal/data-privacy-security-faqs)); MSA allows de-identified data to improve services (snippet, [MSA](https://www.heidihealth.com/en-us/legal/master-of-service-agreement)). Free tier; paid US price unverified. |
| MacWhisper | Local transcription on the Mac; optional cloud services ([macwhisper.com](https://macwhisper.com/)). No HIPAA/BAA mention. Pro €64 once. |
| OpenWhispr | MIT licensed (GitHub OpenWhispr/openwhispr). BAA for Business/Enterprise on request; "Customer data is not used for AI training" ([HIPAA page](https://openwhispr.com/use-cases/hipaa-compliant)). Free local; Pro $80/year; Business $160/user/year ([pricing](https://openwhispr.com/pricing)). SOC 2 / ISO 27001 snippet only. |
| Philips SpeechLive | Regional Microsoft Azure; "handled in compliance with HIPAA and GDPR" (snippet). Pro $17.90 + $25.90/user/month speech recognition, billed annually ([pricing](https://www.speechlive.com/us/pricing/)). BAA not found. |
| Suki | "We sign Business Associate Agreements (BAA) ... with our customers"; Google Cloud; trains on de-identified data; audio and transcripts deleted after 30 days ([security FAQ](https://developer.suki.ai/documentation/faqs/security)). SOC 2 (snippet). Price not public. |
| Superwhisper | BAA on request for Enterprise; "We never train models on customer content, and neither do our providers"; SOC 2 Type II ([enterprise](https://superwhisper.com/for-enterprise)). Local models on free and Pro. Pro $8.49/month ([plans](https://superwhisper.com/docs/billing/plans)). |
| Wispr Flow | Individuals can sign a BAA in app settings; with BAA, zero retention and no training ([HIPAA docs](https://docs.wisprflow.ai/articles/4218718535-hipaa-compliance-healthcare-use)); training on by default for Free/Pro otherwise (snippet). "Transcription always occurs on the cloud" ([data controls](https://wisprflow.ai/data-controls)). SOC 2 Type II, ISO 27001; Pro $15/month ([pricing](https://wisprflow.ai/pricing)). Its docs conflict on which plans can sign a BAA. |
