# Contributing

This list stays useful only if entries are accurate and sourced. Please read this
before opening a pull request.

## Proposing a tool

Open a pull request (or issue) that includes:

1. **Category** it belongs in (or propose a new one, briefly justified).
2. **One-line description** of what it does.
3. **A filled-in STANDARDS row** (see `standards.md` for the fields) — every field
   filled with either a fact + source link, or `unverified`.
4. **Source links for every factual claim**, pointing to the vendor's own site,
   docs, trust center, or a signed agreement — not a blog post, review site, or
   marketing claim repeated secondhand. If you can't find a primary source for a
   claim, mark it `unverified` rather than guessing or omitting it silently.
5. Where the tool sits stage-wise (GA, beta, pre-launch) if that's relevant to
   trusting the claims.

## Evidence required

- **BAA claims**: link to the page where the vendor states BAA availability
  (self-serve signup flow, or a sales/compliance page describing the process).
- **"Trains on your data" claims**: link to the specific privacy policy or trust
  page section, quoted or paraphrased accurately. Silence on the topic is not
  evidence of "no" — mark it `unclear` unless the vendor states a position.
- **Certifications (SOC 2, HITRUST, etc.)**: link to the vendor's trust page or
  a public report/badge, not a claim made only in sales copy.
- **Self-hosting / open source**: link to the repo and license file.

Claims that can't be traced to one of these will be removed or marked
`unverified` on review.

## Conflict of interest

Say so, plainly, in the pull request, if you:

- built, work for, invest in, or are paid by a tool you're proposing or editing,
- have a competing product in the same category (as the maintainer does — see
  the disclosure in the Footnotes at the bottom of `README.md`).

A conflict of interest doesn't disqualify an entry — inaccurate or one-sided
treatment does. Entries from an interested party get extra scrutiny on sourcing
and are held to the same "no unsourced claims" rule as everyone else.

## Removing or downgrading a tool

If a vendor changes its BAA terms, has a breach, sunsets a product, or you find
a sourced claim that contradicts an existing entry, open a PR with the source
and update the row. Don't just delete — note what changed and when, briefly, so
the history is legible.

## Scope: therapist-targeted products only

A product is listed only if it is **marketed specifically to therapists / mental-health
clinicians as the end user**, judged from the vendor's own site. Evidence is a link to the page
where the vendor names therapists, counselors, social workers, psychologists or behavioral-health
clinicians as its audience.

Out of scope for the main list: general-purpose tools (email, payments, e-signature, scheduling,
general video, hosting, generic transcription) and products for many health disciplines or all of
healthcare, even if therapists use them and even if they sign a BAA. Proposals of that kind are
welcome only as a one-line mention in the "Related" section at the bottom of the list. One exception: dictation (voice-to-text) tools need not be therapist-specific, since any clinician-grade dictation tool serves a therapist equally well. A tool that lists therapists among many other disciplines is borderline; say so in
the pull request and let the maintainer decide.
