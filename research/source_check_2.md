# Second source check of site/index.html ("AI labs should stop working on P = NP", draft)

Checked Tue 2026-11-24 by a second reader (Claude, Opus 5.5). One reader, no helpers.
Read-only; this file is the only thing written. The page checked is the version of `site/index.html` dated
23 Nov 18:20 on disk.

**Independence.** I read the page and every source myself before opening `source_check.md` (step 4). Sections
1-5 were written from my own reads; section 6 was added after I opened the first check.

**How the passages were obtained.** Every source was downloaded with `curl` through a per-request
research gate, each into its own scratch directory, and its text extracted locally (PyMuPDF for
PDFs, a plain tag-stripping pass for HTML). Passages below are copied from that text. Superscripts flatten in
extraction ("2 64" for 2^64); I write them as 2^64. Search engines were used only to find URLs; no verdict here
rests on a search summary.

**Verdicts:** MATCHES, OVERSTATED, WRONG, SECONDARY ONLY, NOT OPENED (with what refused).

**Tally: 64 rows. 4 WRONG, 10 OVERSTATED, 5 SECONDARY ONLY, 4 NOT OPENED, 41 MATCHES.**
Most of the WRONG rows are citations, not facts: the fact is right and the cited source does not carry it, or
the cited source has been withdrawn.

---

## 1. Wrong and overstated (with the wording I would use)

| # | Claim as the page words it | Verdict | Passage read | URL | Wording I would use |
|---|---|---|---|---|---|
| 1 | Margin: "HAWK, 28 July: effective key strength halved." | OVERSTATED. A cryptographer reads "key strength" as bits of security, and those were not halved. What halved is the lattice dimension (block size) the attack must reduce. | Anthropic's announcement to the NIST pqc-forum, 28 Jul: "an improved key recovery attack against HAWK-n that reduces to SVP in dimension n/2 + 1 ... lowers the key-recovery cost of HAWK-512 from 2^150 to 2^108 and of HAWK-1024 from 2^288 to 2^182 ... recovers a HAWK-256 secret key end-to-end in a few hours on a single server." HAWK team, 29 Jul: "their attack approximately halves the block size required in lattice reduction". Blog: HAWK-256 "was thought to be 2^64 but was demonstrated by Mythos to be 2^38"; "effectively cutting its key strength in half" is the blog's own phrase. | https://groups.google.com/a/list.nist.gov/g/pqc-forum/c/2r2u6SbHun4/m/S-ZUsHNICQAJ ; https://www.anthropic.com/research/discovering-cryptographic-weaknesses | "HAWK, 28 July: the lattice an attacker must reduce shrank to half its dimension (for HAWK-512, estimated key-recovery cost 2^150 → 2^108); its designers withdrew it from NIST's third round the next day." |
| 2 | Margin: "Its designers withdrew it from NIST's third round the next day." Linked to s1. | WRONG as a citation. The fact is right; s1 (Anthropic's blog) does not say it, and nothing in the source list does. | HAWK team on pqc-forum, Jul 29 2026: "As such, we withdraw our candidate HAWK from NIST's ongoing additional signature scheme standardisation process." hawk-sign.info: "HAWK is withdrawn / 29 July 2026". NIST round-3 page: "The submission team has withdrawn HAWK from the additional digital signatures standardization process." s1 says only "HAWK is one of the remaining third round candidates". | pqc-forum as row 1 ; https://hawk-sign.info/ ; https://csrc.nist.gov/projects/pqc-dig-sig/round-3-additional-signatures | Keep the sentence. Add to s1: "the HAWK team's withdrawal, NIST pqc-forum, 29 July 2026" (or hawk-sign.info, or NIST's round-3 page). |
| 3 | "They believed something stronger as well. The Exponential Time Hypothesis ... But a conjecture **the whole field leaned on** is gone" | OVERSTATED. The page's own source (Aaronson) says experts did *not* broadly believe ETH. OpenAI says "widely believed". | Aaronson §: "ETH is an ambitious strengthening of P ≠ NP. Even assuming P ≠ NP, there's by no means a consensus in the field that ETH is true—let alone still further strengthenings, like the Strong Exponential Time Hypothesis". OpenAI: "The ETH has been widely believed to be true, and has been used in hundreds of papers". | https://www.scottaaronson.com/papers/pnp.pdf ; https://openai.com/index/building-scientific-understanding-with-academic-communities/ | "Many of them believed something stronger as well ..." and "But a conjecture that hundreds of papers leaned on is gone". A complexity theorist will catch "whole field" at once. |
| 4 | "The 1974 pause also had a set end." | OVERSTATED. The 1974 letter set a condition and a meeting, not an end date. (This wording was the first check's suggestion; see section 6.) | Berg et al., letter, *Science* 26 July 1974: "that until the potential hazards of such recombinant DNA molecules have been better evaluated or until adequate methods are developed for preventing their spread, scientists throughout the world join with the members of this committee in voluntarily deferring the following types of experiments"; "an international meeting of involved scientists from all over the world should be convened early in the coming year to review scientific progress in this area". (OCR text.) | https://collections.nlm.nih.gov/ocr/nlm:nlmuid-101584644X283-doc (NLM scan of the *Science* letter; PNAS 71:2593 carries the same letter) | "The 1974 pause also came with a fixed next step: an international meeting the following year to review it." (That it was lifted after Asilomar in 1975 is from memory; I did not open an Asilomar source.) |
| 5 | Timeline: "Public-key cryptography, found at GCHQ" 1970 → 1976, "found again in 6 years" | OVERSTATED if "found" means discovered, which is how the bar reads. Merkle had the idea independently in 1974. Six years is the gap to *publication*. | Merkle's own account: "In the Fall of 1974, as an undergraduate, I enrolled in CS244 ... I submitted a proposal for what would eventually become known as Public Key Cryptography -- which Hoffman rejected." His CACM paper: "Received August 1975; revised September 1977", published April 1978. Ellis: "The Possibility of Secure Non-Secret Digital Encryption, CESG Report, January 1970"; Diffie and Hellman "suggested the possibility in their paper of April 1976". | https://www.ralphmerkle.com/1974/ ; https://ralphmerkle.com/1974/PuzzlesAsPublished.pdf ; https://www.cryptocellar.org/cesg/ellis.pdf | Either draw the bar 1970 → 1974 and label it "found again in 4 years (Merkle; published by Diffie and Hellman, 1976)", or keep 1970 → 1976 and label it "published again in 6 years". The shorter gap also helps the page's point. Note the 1974 date rests on Merkle's own later account and a proposal he scanned in 2005. |
| 6 | "**Twice on record** a piece of mathematics that mattered to cryptography was held inside a closed group." | OVERSTATED. "On record" claims the list is complete. The timeline itself has three items, and Ellis records a fourth (Williamson's key exchange, CESG Jan 1974, published by Diffie and Hellman 1976). A cryptographer can name others (wartime cryptanalysis kept secret for decades). | Ellis: "A couple of months later Malcolm Williamson came to me with a different scheme ... The method was published in reference 8 by Diffie and Hellman. This was identical to Williamson's version". | https://www.cryptocellar.org/cesg/ellis.pdf | "In the two best-documented cases, a piece of mathematics that mattered to cryptography was held inside a closed group." Or "At least twice ...". |
| 7 | Margin: "Its organiser **promised** to publish them later 'with a statement of the original date of the paper'." | OVERSTATED (minor). Weart reports an expectation, not a promise. | Weart: "Breit added that he expected ultimately to publish the papers in book form or otherwise, with a statement of the original date of the paper and with a suitable acknowledgment of the public spirit of the authors." | https://aip.brightspotcdn.com/PTO.v29.i2.23_1.online.pdf | "Its organiser said he expected to publish them later ..." |
| 8 | s22: "NIST IR 8547 (initial public draft) ... November 2024" | WRONG as a citation now. The draft was withdrawn on 27 Oct 2026 and replaced by the final report, which keeps the passage the page uses. | Draft PDF, page 1: "Withdrawn Draft ... Withdrawal Date October 27, 2026 ... followed by ... Stage Final ... Publication Date October 2026". Final, §: "there is a pressing threat. Encrypted data remains at risk because of the “harvest now, decrypt later” threat in which adversaries collect encrypted data now with the goal of decrypting it once quantum technology matures." | https://nvlpubs.nist.gov/nistpubs/ir/2024/NIST.IR.8547.ipd.pdf ; https://nvlpubs.nist.gov/nistpubs/ir/2026/NIST.IR.8547.pdf | "NIST IR 8547, 'Transition to Post-Quantum Cryptography Standards', October 2026" with the 2026 URL. |
| 9 | s12: "Future of Life Institute, newsletter, September 2023" | WRONG (minor date). The issue is dated 1 October 2023; only the URL says September. | Header: "Future of Life Institute Newsletter: Our Pause Letter, Six Months Later ... Maggie Munro ... October 01, 2023". Quotation matches: "Despite this, a pause never materialized". | https://newsletter.futureoflife.org/p/fli-newsletter-september-2023 | "Future of Life Institute, newsletter, 1 October 2023". |
| 10 | Unfolding step 2: "Any such proof means a known, explicit method already finds a key, or any other answer that can be checked, **though absurdly slowly**." | OVERSTATED (minor), because ambiguous. Without "in polynomial time", "absurdly slowly" reads as exponential, which is the opposite of what Levin's search gives. | Aaronson, fn 4: "If we know P = NP, then we know this particular algorithm will find a valid solution, whenever one exists, in polynomial time ... Admittedly, however, the polynomial or constant factor will be so enormous as to negate this algorithm's practical use." | https://www.scottaaronson.com/papers/pnp.pdf | "... already finds a key, or any other answer that can be checked, in polynomial time, though with overheads so vast that it is useless." |
| 11 | "Almost nothing is left standing but codes whose secret is as long as the message." | OVERSTATED (minor). The margin beside it names quantum key distribution as a survivor, and QKD's secret is not pre-shared at message length. Information-theoretic authentication (Wegman–Carter MACs) and secret sharing also survive (my knowledge, not from a page source). | Aaronson: "The only exceptions are cryptosystems like the one-time pad and quantum key distribution, which don't rely on any computational assumptions (but have other disadvantages, such as the need for huge pre-shared keys or for special communication hardware)." | as row 10 | "Almost nothing is left standing but the one-time pad, whose key is as long as the message, and quantum key distribution, which needs its own hardware." |
| 12 | "Not yet, because today only the labs can do this." | OVERSTATED as a statement of fact. The hardest results did come from unreleased lab models, but one of the five lines of work was carried forward outside a lab with a released model. | Gao (Clemson), arXiv 2608.00222, AI disclosure: "The main idea and framework are due to the author, and Claude Fable 5 assisted in the proofs and in the writing of the paper." Quanta: Buckmaster (NYU) and Alpöge worked "with help from a variety of AI models, including those of OpenAI." Against: Navier–Stokes ran "on an advanced model not available to the public"; ETH by "internal" models at both labs. | https://arxiv.org/pdf/2608.00222 ; https://quantamagazine.org/ai-has-solved-one-of-maths-1-million-millennium-prize-problems-20260908 | "Not yet, because today the hardest of these results have come only from unreleased models inside the labs." |
| 13 | Bullets: "forge the signature on a software update, and so put their own code on any device that accepts updates"; "do all of it without a trace" | OVERSTATED (minor, argument more than fact). A valid signature does not deliver the update; the forger still needs a way onto the update channel, and a forged update is itself a trace. Passive reading of recorded traffic is traceless. No source on the page covers this; it is my reading. | — | — | "... and so make any device that trusts that signature accept their code"; "do much of it without a trace". |
| 14 | Status bar: "Its facts and quotations were checked against their sources once, on 23 November 2026. A second reader has not been over them." | WRONG as of this file. | — | — | "... checked against their sources on 23 November 2026 and again, independently, on 24 November." |

## 2. Secondary only

| # | Claim as the page words it | Verdict | Passage read | URL | Note / wording |
|---|---|---|---|---|---|
| 15 | Margin: "Jacobian conjecture, 19 July" | SECONDARY ONLY for the date. The primary (Alpöge's post) was not opened; the date comes from a later paper. A 21 July blog says "a couple days ago". | Gao, arXiv 2608.00222v2: "On July 19, 2026, the conjecture was refuted in dimension three by an explicit counterexample announced by L. Alpöge [11]." J. D. Cook, posted 21 July 2026: "A couple days ago, Levent Alpöge, a mathematician working at Anthropic, discovered a counterexample". | https://arxiv.org/pdf/2608.00222 ; https://www.johndcook.com/blog/2026/07/21/jacobian-conjecture/ | A search summary (not opened, Smithsonian 403) says 20 July; probably time zone (a guess). s18's link is Gao, a secondary account; add a primary if one exists. |
| 16 | Margin: "The SIKE break of 2022 reached its designers about a week before the paper, on 22 and 30 July." | Dates MATCH primary sources. "Reached its designers" is an inference: the Microsoft page records a prize claim to Microsoft, not a notice to the SIKE team. Microsoft researchers were among the SIKE submitters (my knowledge; not on any page I opened). | Microsoft: "The award for solving the $IKEp217 challenge was $50,000 USD and was claimed on July 22, 2022. $IKEp217 was solved by Wouter Castryck and Thomas Decru." ePrint 2022/975: "2022-07-30: received". | https://www.microsoft.com/en-us/msrc/sike-cryptographic-challenge ; https://eprint.iacr.org/2022/975 | "The SIKE break of 2022 was in Microsoft's hands, as a claim on its SIKE prize, eight days before the paper (22 and 30 July)." Microsoft was a SIKE co-designer. The Castryck quotation that would settle it (CACM) refused me too (row 21). |
| 17 | "When a cipher is broken today, its designers are usually told first, and the paper follows within days or weeks." | SECONDARY ONLY: a pattern drawn from two cases (SIKE, HAWK), with no source for "usually". | HAWK: "we shared our attack with the authors of HAWK in June and coordinated disclosure to the public NIST mailing list at the same time our results were released" (about six weeks). | Anthropic blog | "... its designers are often told first" is safer. |
| 18 | "Restraint that held ... mirror bacteria since 2024", and "they were the ones who asked for it" | SECONDARY ONLY. JCVI's summary supports the call, not that it held or who could do the work. It also says nobody can yet do the work, so a hard reader will say this restraint has not been tested. | JCVI: "The path to mirror bacteria is not inevitable. To get there would require significant financial investment and technological advancements over a decade or more. Interest in mirror bacteria is currently academic." "We recommend preventing the creation of mirror bacteria". | https://www.jcvi.org/research/risks-mirror-bacteria | Consider "mirror bacteria since 2024, a restraint still untested because nobody can yet make them". |
| 19 | "Restraint that failed, on our reading of the cases, was open-ended and asked of rivals who could not check one another." | SECONDARY ONLY (it is the page's own synthesis, and is framed as such). FLI part checked: "a pause never materialized - if anything, the “arms race” between AI corporations has only intensified". | as row 9 | Fine as framed. |

## 3. Not opened

| # | Claim | Verdict | What refused | Note |
|---|---|---|---|---|
| 20 | "one lab had told its system in so many words to research an 'unconditional refutation' of the conjecture's stronger form"; margin "The published prompt names the Strong Exponential Time Hypothesis." | NOT OPENED | https://ethdiscussion.blog/2026/11/12/openai-prompt-that-led-to-the-eth-refutation/ returned HTTP 403. Not retried by another route. OpenAI's ETH preprint (github.com/openai/math, `preprints/The-Exponential-Time-Hypothesis-is-False-October-25-2026/`, paper and README) does not contain the prompt. | Only the first checker read this; their quotation is in section 6. |
| 21 | Castryck's account that the SIKE team was informed on 22 July (bears on row 16) | NOT OPENED | https://cacm.acm.org/news/nist-post-quantum-cryptography-candidate-cracked returned 403. | One of the two pages that refused before; it refused again. |
| 22 | The CISA/NSA/NIST quantum-readiness factsheet ("harvest now, decrypt later") | NOT OPENED | https://media.defense.gov/2023/Aug/21/2003284212/-1/-1/0/CSI-QUANTUM-READINESS.PDF returned 403. | The other page that refused before. Not needed now: NIST IR 8547 (final) carries the claim (rows 8 and 46). |
| 23 | xAI's current framework (bears on row 48) | NOT OPENED | https://media.x.ai/v1/website/xai-frontier-artificial-intelligence-framework-30-june-2026-99c40684.pdf returned 404 (URL from a search result). I read xAI's 31 Dec 2025 framework instead. | |

## 4. Matches

### 4a. The five results (dates, details, sources; the ruling itself not reopened)

| # | Claim | Passage read | URL | Note |
|---|---|---|---|---|
| 24 | Jacobian: "false in three dimensions and above" | Gao: "produces counterexamples in every dimension greater than two". J. D. Cook: "It can trivially be extended to all n > 3 ... The conjecture remains open for n = 2." | arXiv 2608.00222 ; johndcook.com | |
| 25 | s18: "the lab's own statement that its model resolved it is in the first source above" | s1: "earlier this month we announced that Claude Fable 5 resolved the Jacobian Conjecture". | Anthropic blog | s1 links Wikipedia for this, not an Anthropic announcement. |
| 26 | HAWK, 28 July; "broken a post-quantum signature scheme" (detail) | Blog "Published Jul 28, 2026". HAWK-256 key recovered "in a few hours on a single server" (pqc-forum). Blog: "For larger keys, HAWK therefore remains impractical to attack." | as row 1 | The ruling stands; row 1 gives the scope a cryptographer will want in the margin. |
| 27 | Navier–Stokes, 8 September: "blow-up in finite time with smooth forcing, formalised in Lean" | OpenAI, September 8, 2026: "a Lean formalization that an initially smooth fluid at rest can develop a singularity in a finite time. The fluid has a smooth force applied to it, and its energy remains finite". | https://openai.com/index/navier-stokes-solution ; https://github.com/openai/NavierStokesAndEuler | OpenAI: "We do not intend to claim the Millennium Prize for this result." |
| 28 | ETH, October: "formalised in Lean"; "two labs' AI systems proved it false" | OpenAI: "Our AI found its natural language disproof for the ETH on October 16th, 2026 and then subsequently we formalized the result in Lean on October 17th". Anthropic preprint (Oct 27): "We refute the Exponential Time Hypothesis ... has been formalized in Lean 4." | openai.com (s2) ; https://hexagonmath.org/2610.00577v1 | |
| 29 | RH, 20 November: "formalised in Lean, for Dirichlet L-functions as well" | Lean FRO/Mathlib: "On November 20, 2026, Levent Alpöge released a proof of the Riemann Hypothesis as a Lean library"; "We hereby certify that both the statement and the proof of the Riemann Hypothesis are correct." Sutherland: theorems 3–5 cover "every Dirichlet L-function"; "Scope. "GRH" here means Dirichlet L-functions: all moduli and all characters." PDF creation date 2026-11-20. | https://leanprover-community.github.io/blog/posts/riemann-hypothesis/ ; https://math.mit.edu/~drew/grh/ ; https://alpo.ge/remark.pdf | Sutherland's page (updated 2026-11-24 05:25 UTC) still has one lake comparator run "in progress". Hard readers will also know Nature reports a rival all-human proof posted the same day (Masullo, via Vakil); the page does not need it, but should not be surprised by it. |
| 30 | "Each of these was a triumph, and none of them put anything at risk." | Anthropic: "they do not currently affect any production systems". TechCrunch (Williams on OpenAI's ETH result): "they were reasonably confident that this didn't … imply any breaks." | s1 ; TechCrunch | |

### 4b. "If P = NP"

| # | Claim | Passage read | URL | Note |
|---|---|---|---|---|
| 31 | "Nearly all of modern security assumes it is not"; password, key, signature are "quick to check" | Aaronson: "in most cryptography, the problem of finding the decryption key is an NP search problem: that is, we know mathematically how to check whether a valid key has been found." | pnp.pdf | |
| 32 | Bullets: read almost any message incl. recorded ones; recover any private key | Aaronson: "essentially all the cryptography that we currently use on the Internet ... would be broken if P = NP (and if, moreover, the algorithm were efficient in practice ...)". Cook: "If P = NP, these assumptions are all false." | pnp.pdf ; pvsnp.pdf | "a practical method" in the text covers the caveat. |
| 33 | "The new standards built to survive quantum computers fall with the old ones." | Follows: lattice and hash-based schemes rest on computational hardness; key recovery is an NP search problem (Aaronson passage above). | — | My reasoning from the passage, which no page source states for PQC specifically. |
| 34 | Cook margin quotation | "Specifically, an algorithm solving 3-SAT in n^2 steps could be used to factor 200-digit numbers in a few minutes." Word for word. | https://www.claymath.org/wp-content/uploads/2022/06/pvsnp.pdf | |
| 35 | Aaronson margin quotation (internet crypto; one-time pad and QKD) | "essentially all the cryptography that we currently use on the Internet"; "The only exceptions are cryptosystems like the one-time pad and quantum key distribution". | pnp.pdf | The page drops "like", outside the quoted fragment. Fine. |
| 36 | "If it held, P ≠ NP would follow." | Aaronson: "Conjecture 23 (Exponential Time Hypothesis) Any deterministic algorithm for 3Sat takes Ω(c^n) steps, for some constant c > 1. ETH is an ambitious strengthening of P ≠ NP." | pnp.pdf | Correct: 2^Ω(n) for 3-SAT rules out a polynomial algorithm. And refuting ETH says nothing formal about P vs NP, as the page says. |
| 37 | "The Exponential Time Hypothesis says that the hardest problems are not merely slow to solve but exponentially slow." | OpenAI ETH paper: ETH "postulates that deciding 3-SAT on n variables requires 2^Ω(n) time in the worst case." | https://raw.githubusercontent.com/openai/math/main/preprints/The-Exponential-Time-Hypothesis-is-False-October-25-2026/paper.pdf | A loose gloss (ETH is about 3-SAT, carried to other NP-complete problems by reductions). Acceptable for a lay page. |
| 38 | "If the opposite is proved, that P ≠ NP, nothing breaks." | Logic: everything rests on P ≠ NP or stronger. | — | |

### 4c. "October was the warning shot"

| # | Claim | Passage read | URL | Note |
|---|---|---|---|---|
| 39 | "Most experts believe no such method exists. In the last poll, in 2019, 88 percent of those who answered expected P ≠ NP." Margin: "109 of 124; among those he counts as experts, 99%." | "I got 124 respondents"; "2019 109 (88%)"; "The Experts: 99% NO, 1% YES." | https://www.cs.umd.edu/users/gasarch/papers/poll3.pdf | Gasarch: "the poll was conducted in 2018". "In the last poll, published in 2019" is more precise. Whether it is the last poll I did not check. |
| 40 | "Hundreds of papers were built on it." | OpenAI: "has been used in hundreds of papers to derive conditional computational hardness results". | openai.com (s2) | |
| 41 | "the method is far too slow to use"; margin "its advantage begins near 2^(8.6 × 10^9) variables" | Majdoddin, arXiv 2610.41622: "for general 3-SAT, in the number n of variables, our estimate drops to 2^(8.6·10^9) variables from 2^(2.2·10^12)." | https://arxiv.org/abs/2610.41622 | Two precision notes: the analysis is of *Anthropic's* algorithm ("Lowered crossover points of Anthropic's subexponential 3-SAT algorithm"), and 2^(8.6e9) is that paper's own lowered estimate. Say "by one analysis of Anthropic's version". |
| 42 | "no cipher fell" | TechCrunch, as row 30. | TechCrunch | |
| 43 | Williams quotation; "told a reporter afterwards"; "He went on: 'but one's weight may vary.'"; "Quoted in TechCrunch, 27 October 2026"; "One of the reviewers" | "“Every computer scientist should probably put a little more weight on the plausibility of P = NP, but one’s weight may vary,” Williams said." Dated "10:08 AM PDT · October 27, 2026". OpenAI: "This work will be verified and shepherded by a group led by ... Ryan Williams (MIT)." | https://techcrunch.com/2026/10/27/frontier-ai-labs-say-their-models-refuted-the-exponential-time-hypothesis-what-does-that-mean/ | "He went on" is the same sentence, which is fine. |
| 44 | Aaronson: "Once we knew that an algorithm existed, we'd have a massive inducement to try to find it." | "Even then, however, once we knew that an algorithm existed, we'd have a massive inducement to try to find it." | pnp.pdf | |

### 4d. Disclosure, the ask, and replies

| # | Claim | Passage read | URL | Note |
|---|---|---|---|---|
| 45 | SIKE dates, 22 and 30 July | as row 16 | Microsoft ; ePrint | |
| 46 | Margin: "'Harvest now, decrypt later': NIST names it as a pressing threat." Body: "adversaries collect encrypted data now in the hope of reading it later" | Draft and final both: "there is a pressing threat. Encrypted data remains at risk because of the “harvest now, decrypt later” threat in which adversaries collect encrypted data now with the goal of decrypting it once quantum technology matures." | NIST IR 8547 (both) | Matches; cite the final (row 8). The threat NIST names is quantum; the page's use for a P = NP break is a fair extension. |
| 47 | "As far as we have found, no lab's published safety framework mentions a mathematical result." | Read the frameworks themselves; see section 5. None names a mathematical or cryptographic result as something to hold back or handle specially. | section 5 | "mentions" is loose: Meta's names "mathematical reasoning" as a benchmark domain. Safer: "names a mathematical result as something to hold back". |
| 48 | "The Frontier Model Forum's 2026 survey of its members' cyber thresholds does not." | FMF report, "DATE February 13, 2026". Its only crypto content is evaluation: "solving cryptographic puzzles"; "testing an AI system's ability to break encryption algorithms". No mathematical result. | FMF PDF (s13) | |
| 49 | "One lab has written that 'it would be prudent to consider how researchers should react ...'" | "But as we develop increasingly powerful cryptanalytic results, it would be prudent to consider how researchers should react if a language model were to discover vulnerabilities in cryptosystems where attacks do have an immediate real-world impact." | s1 | Word for word. |
| 50 | "Each lab should say so in the safety framework it already publishes." | FMF: "Each member firm of the Frontier Model Forum (FMF) has published a frontier AI framework that identifies advanced cyber threats as a key risk." | FMF PDF | |
| 51 | "People have worked on this problem since at least 1971" | Aaronson: "The problem was explicitly posed in the early 1970s in the works of Cook and Levin"; fn 5 on Cook's 1967 course notes; Nash 1955 in the abstract. | pnp.pdf | "at least" covers the earlier dates. |
| 52 | Fortnow: it "will make the whole internet look like a footnote in history." | "True but what we will gain from P = NP will make the whole internet look like a footnote in history." | https://lance.fortnow.com/papers/files/pnp-cacm.pdf | Used in context. |
| 53 | "In the late 1970s cryptographers were warned that publishing might bring prosecution, and a law to restrict their research was drafted, before a voluntary review was agreed." | "Meyer's letter asserted that the IEEE and the authors of the relevant papers might be subject to prosecution"; "NSA documents and Hellman's recollection both suggest that Inman first tried to get a law drafted ... Inman's proposed bill was 'dead on arrival.'"; "Inman organized a voluntary system of prepublication review". | https://stanfordmag.org/contents/keeping-secrets | The warning came from an NSA employee writing on his own, and "suggest" is the source's hedge on the bill. Fine as worded. |
| 54 | Navier–Stokes: "ten thousand agents running for 88 hours on a model the public cannot use" | OpenAI: "on the order of 10,000 concurrent agents"; "about 88 hours after the first agents were launched". Quanta: "running on an advanced model not available to the public". | openai.com ; Quanta | |
| 55 | Cost "six to ten million dollars for the proof alone and fifteen to twenty for the whole effort"; "NPR's estimate from the lab's public prices" | NPR: "According to OpenAI's pricing for its most advanced publicly available model, the solution to the Navier-Stokes problem cost the company somewhere around $6-$10 million to compute. (Overall, the company says it used 300 billion tokens, closer to $15-20 million, looking for solutions.)" | https://www.npr.org/2026/09/22/nx-s1-5968588/openai-navier-stokes-problem-mathematicians-learn-little | |
| 56 | "The Exponential Time Hypothesis fell to internal research models at two labs." Margin quotes "Discovered by an internal research Claude model" | Preprint: "The result was discovered by an internal research Claude model". OpenAI: "discoveries produced by our internal models". | hexagonmath ; openai.com | |
| 57 | "The Riemann hypothesis fell inside a lab, to one of its own mathematicians working with its model." Margin: "A mathematician at the … company" (Nature) | Nature, 20 Nov: "The Anthropic announcement came on 20 November from Levent Alpöge, a mathematician at the San Francisco, California, company." Remark: "I believe I have, working with Claude, discovered a proof". | https://www.nature.com/articles/d41586-026-03812-7 ; alpo.ge | |
| 58 | Fortnow 2014: "If you can find an algorithm so can others." | "If you can find an algorithm so can others so you should just take the credit or someone else will discover it." | https://blog.computationalcomplexity.org/2014/04/should-you-reveal-p-np-algorithm.html | Words match. In context, Fortnow argues for publishing after warning companies ("Then I would just publish the algorithm"); a reader who follows the link will see that. |

### 4e. "Mathematics kept back has been found again"

| # | Claim | Passage read | URL | Note |
|---|---|---|---|---|
| 59 | "The RSA method, found at GCHQ" 1973 → 1977, "4 years" | Ellis: "C C Cocks, A Note on Non-Secret Encryption, CESG Report, 20 November 1973"; RSA memo "4/4/77"; "This is essentially the RSA Algorithm." | ellis.pdf | 3 years 4 months, rounded. |
| 60 | "Differential cryptanalysis, known at IBM" 1974 → 1990, "16 years" | Coppersmith: DES "was developed by an IBM team around 1974"; "The design took advantage of knowledge of certain cryptanalytic techniques, most prominently the technique of “differential cryptanalysis,” which were not known in the published literature"; ref. Biham and Shamir, CRYPTO '90. | https://people.clarkson.edu/class/cs456/CoppersmithDES.pdf | |
| 61 | "Both times the secret held, and both times outsiders found the same thing by themselves." | Ellis: "subsequent rediscovery of the NSE techniques"; Coppersmith: "After discussions with NSA, it was decided that disclosure of the design considerations would reveal the technique". | ellis.pdf ; Coppersmith | |
| 62 | "In 1940 the physicists' own committee held back fission papers." | Smyth ¶3.3: the "Reference Committee" ... "This arrangement was very successful in preventing publication"; "this whole arrangement was a purely voluntary one". | https://www.atomicarchive.com/resources/documents/smyth-report/smyth_iii.html | |
| 63 | "The 2023 pause letter, by its organisers' own account, paused nothing." | "Despite this, a pause never materialized". | FLI newsletter | Date fix in row 9. |
| 64 | s11: "Confronting risks of mirror life", Science, December 2024 | JCVI: "Science (New York, N.Y.). 2024-12-20; 386.6728: 1351-1353." | jcvi.org | Did not open the *Science* paper. |

## 5. The frameworks themselves (the item the first check left open)

Question: does any frontier lab's current published safety framework name a mathematical or cryptographic
result as something it would hold back or handle specially? I searched each text for cryptograph*,
cryptanaly*, cipher, encrypt*, mathemat*, theorem, NP, P = NP (after stripping zero-width characters, which
hid words in two of the PDFs).

| Lab | Document read (as current as I could find) | What it says on mathematics or cryptography |
|---|---|---|
| Anthropic | Responsible Scaling Policy v3.4, "Effective July 8, 2026" (https://assets.claude.com/0bacdc8440ea96e62a8766d99ebe1d4eea6d5f3a.pdf, linked as "Version 3.4" from anthropic.com/rsp). Also the August 2026 Risk Report (anthropic.com/aug-2026-risk-report). | RSP: no hit on any of those words. Risk Report: one irrelevant hit ("complex ciphers that monitors would struggle to decode"), and one use of a hard Lean theorem as a test task. Neither mentions HAWK, ETH or any result. |
| OpenAI | Preparedness Framework v2, "Last updated: 15th April, 2025" (still the governing framework: OpenAI's August 2026 cyber posts say they "will evolve" it and cite it). Frontier Governance Framework, 28 May 2026 (PDF). Also "Managing frontier AI risk", 18 Nov 2026. | PF v2: only "data encryption" as a security control. FGF: nothing. The 18 Nov post lists the Navier–Stokes proof as a research illustration, not as something to hold back. |
| Google DeepMind | Frontier Safety Framework v3.1, 17 Apr 2026 (frontier-safety-framework_3-1.pdf) | No hit. |
| Meta | Meta Superintelligence Scaling Framework v2.1, "October 2026" (research.meta.ai/static/meta-superintelligence-scaling-framework) | Only "mathematical reasoning" as one of the benchmark domains used to judge whether AI progress is accelerating. No result. |
| xAI | Frontier AI Framework of 31 Dec 2025 (data.x.ai). The 30 June 2026 version's URL returned 404 (row 23). | "cryptography" only as one of six CTF evaluation categories. |
| Frontier Model Forum | Cyber report, 13 Feb 2026 (s13) | Row 48. |

Verdict: the page's claim holds for every framework I could open, including two newer than the FMF report
(Meta's October 2026, Anthropic's July 2026). Not read: Microsoft, Amazon, NVIDIA, Cohere and other FMF or
Seoul-commitment signatories, and xAI's June 2026 text.

## 6. Where I disagree with the first check, and what I checked that it could not

The first check was made against an earlier version of the page; several of its rows (Corrigan-Gibbs on GCHQ,
"priority survived", "every lock there is", "of theorists", the FLI FAQ link, "is remembered as a threat")
have since been fixed, and the fixes match what I read.

**Disagreements**

1. **Row 3 (its suggested wording "The 1974 pause also had a set end").** I disagree. The Berg letter defers the
   experiments "until the potential hazards ... have been better evaluated or until adequate methods are
   developed", and proposes a meeting "early in the coming year". That is a condition and a review, not a set
   end. My row 4.
2. **Row 7 (its suggested margin "effective key strength halved").** The phrase is Anthropic's, but it is not
   what a cryptographer will hear. The security in bits went 2^150 → 2^108 (HAWK-512) and 2^288 → 2^182
   (HAWK-1024); the block size halved. My row 1. The first check also cited NIST for the withdrawal, but the
   page's source list still does not carry it (my row 2).
3. **Row 8 (Levin).** The first check's wording kept "in polynomial time"; the page dropped it, so "absurdly
   slowly" now reads as exponential. My row 10.
4. **Row 34 ("codes whose secret is as long as the message").** It rated this MATCHES because "almost" covers
   QKD. I rate it a minor OVERSTATED, because the margin right beside it names QKD and QKD is not a code with a
   message-length pre-shared secret. Small.
5. **Row 48 ("Twice on record").** It called this defensible. I think "on record" claims a complete list, and
   the page's own timeline and Ellis's history hold more than two items. My row 6.
6. **New page text the first check did not see:** "They believed something stronger as well" and "a conjecture
   the whole field leaned on" contradict the page's own source, Aaronson (my row 3).

**Checked here that it listed as not checked**

- **Merkle (its row 49 and NOT CHECKED).** Checked: Merkle's own account puts his public-key proposal in fall
  1974; CACM received August 1975. The six-year bar is six years to publication, four to independent
  discovery (my row 5).
- **The frameworks (its row 6 and NOT CHECKED).** Read; section 5. The claim holds as far as I could read.
- **Harvest now, decrypt later (its row 19).** The page now cites NIST IR 8547's draft, which says it; but the
  draft was withdrawn on 27 Oct 2026, and the final report (Oct 2026) keeps the passage (my row 8).
- **The two pages that answered 403 (CACM SIKE item, CISA/NSA factsheet).** Tried once each through the gate;
  both 403 again. Not retried (rows 21, 22).
- **HAWK's withdrawal.** Read in the HAWK team's own pqc-forum post, 29 July 2026.
- **The technical statements.** ETH implies P ≠ NP: correct (row 36). Levin's search: correct, with the row 10
  wording. What survives: the one-time pad and QKD per Aaronson; information-theoretic MACs and secret sharing
  also survive (my knowledge, not from a page source).

**Where I could not follow it:** its row 55 quotes the published prompt ("Research an unconditional refutation of
the deterministic Strong Exponential Time Hypothesis (SETH)"). That page answered me 403, so I cannot
independently confirm the page's "unconditional refutation" sentence (row 20).

## NOT CHECKED

I did not open: the published ETH prompt (403), the CACM SIKE item (403), the CISA/NSA factsheet (403), the
Smithsonian Jacobian article (403), xAI's June 2026 framework (404), Alpöge's posts on X, the *Science*
mirror-life paper itself, any Asilomar 1975 source, and the frameworks of Microsoft, Amazon, NVIDIA and other
signatories. I read in part only: Aaronson's survey (the sections on cryptography, ETH and Levin), Gao's paper
(abstract, introduction, disclosure), Weart and Coppersmith (the passages cited), the Anthropic Risk Report and
the OpenAI frameworks (searched, not read through), and Nature's article (the open part). I did not read the
Lean files, the Anthropic HAWK and AES papers, or OpenAI's ETH proof beyond its first pages, and I did not
check whether Gasarch has run a poll since 2019. Statements I mark as my own knowledge (Microsoft's SIKE
co-authorship, Wegman–Carter MACs, Asilomar ending the 1974 deferral) are from memory, not from a page read
today.
