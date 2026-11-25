# What is actually dangerous: P vs NP, cryptography, and AI mathematics

Research file compiled 2026-11-23 from public sources. Every claim carries a URL. How quotes were obtained is marked, because it changes how far to trust the exact wording:

- **[primary text]**: I pulled the text out of the source document myself (PDF or HTML) and copied it. The wording is exact.
- **[fetch]**: a web-fetch tool returned the quote. It is normally verbatim, but spot-check it before you print it.
- **[secondary]**: the quote reached me through a news report, not from the speaker's own document.
- **[memory]**: from my background knowledge, not re-verified today.

This file reports evidence. It takes no side on the proposal, but where the evidence cuts against the proposal it says so.

---

## 0. Summary for a drafter (read this first)

1. **The event that has actually happened is not P = NP.** On 26 October 2026 OpenAI said an internal model had refuted the Exponential Time Hypothesis (ETH). Within hours Anthropic released its own independent refutation, credited to an internal Claude model. Both claim 3-SAT can be solved in time 2^o(n). Neither claim is fully refereed. Both are *galactic*: on the reported figures, the algorithm only beats brute force on instances with more than about 10^10,000 variables (outcome (c) below, but for a weaker statement than P = NP). Experts say this does not settle P vs NP. Ryan Williams, one of the appointed reviewers, said researchers should give P = NP "somewhat more weight". (Section 5.)
2. **Deployed public-key cryptography does not rest on NP-completeness.** Factoring and discrete log are in NP ∩ coNP, so they are believed not to be NP-complete. The lattice problems under the new NIST standards are, at the approximation factors cryptography uses, also in NP ∩ coNP. A proof that P ≠ NP would not make any of these schemes safe. A practical P = NP algorithm would break all of them, but each can also fall to a *specific* attack while P vs NP stays open. That has happened repeatedly: SIKE in 2022, Rainbow in 2022, small-characteristic discrete log in 2013. (Sections 3 and 4.)
3. **So the proposal, as worded, mostly targets the wrong thing.** Research aimed at proving P ≠ NP (lower bounds) breaks nothing. Experts treat a non-constructive or galactic P = NP as nearly harmless in practice. The realistic hazard is an *efficient attack on a specific deployed assumption*, found by people or by AI systems that are now explicitly pointed at open problems and at cryptanalysis. One lab has already written that the field should consider how to react if a model found such an attack. (Sections 4, 5 and 6.)
4. **The strongest objection a drafter will meet:** the leading writers on P vs NP (Fortnow, Aaronson, Cook) describe a *practical* P = NP as hugely beneficial overall. Fortnow wrote that it "will make the whole internet look like a footnote in history." And the community norm since at least 2014 has been to warn the affected parties, then publish. (Sections 2 and 6.)

---

## 1. What experts believe

### 1.1 Gasarch's polls (SIGACT News Complexity Theory Column)

Three polls exist. I found no published fourth poll.

| Poll (published / conducted) | Respondents | P ≠ NP | P = NP | Resolved before 2100 | "Never" resolved |
|---|---|---|---|---|---|
| 2002 / 2001 | 100 | 61 (61%) | 9 (9%) | 62% | 5% |
| 2012 / 2011 | 152 | 126 (83%) | 12 (9%) | 53% | 3% |
| 2019 / 2018 | 124 | 109 (88%) | 15 (12%) | 66% | 9% |

Source: Gasarch, "The Third P =? NP Poll", SIGACT News Complexity Theory Column 100, March 2019. [primary text] https://www.cs.umd.edu/users/gasarch/papers/poll3.pdf

Further figures from the 2019 poll [primary text, same PDF]:
- **Respondents Gasarch counts as experts** ("people who are known to have seriously thought about the problem"): "The Experts: 99% NO, 1% YES" on P = NP. On timing: "Experts: 55% before 2100, 45% after 2100."
- **Most popular decade for resolution:** 2020–2029, with 26 respondents (22%).
- **"If someone shows P=NP, will this have a big effect on practical computing?"** 68 YES (58%), 50 NO (42%). The comments split as follows:
  - Scott Aaronson: "The practical impact would come not from the result itself, but from the new ideas needed to achieve it."
  - András Salamon: "If someone produces an algorithm that decides SAT in quadratic time, yes ... If someone gives a nonconstructive proof, or one with a polynomial with degree that depends on the cardinality of some large finite group, not so much."
  - John Tromp: "Crypto will be all but dead."
- **The 3 a.m. question** (asked only of those who believe P ≠ NP): sages say it has been resolved but not which way. 72 (80%) still said P ≠ NP and 17 (20%) said P = NP. Salamon's comment there names "Moshe Vardi, Donald Knuth, Richard Lipton, and Emanuele Viola [serious people who think P=NP]". Note that the bracketed gloss is Gasarch's editorial insertion.
- **Knuth, commenting in the poll:** "I can't wait for people to realize that P=?NP is only a question about the existence of a polynomial time algorithm, not about the knowledge of one."
- **Tom Schaefer, commenting in the poll:** "Will P=?NP be resolved by a human, or by a machine operating autonomously? I lean toward the latter."

Gasarch's blog post announcing the 2019 poll says "P≠NP is at about 80%". The article's own table gives 88%. Cite the table. [fetch] https://blog.computationalcomplexity.org/2019/03/third-poll-on-p-vs-np-and-related.html

### 1.2 Notable dissenters

- **Donald Knuth.** This is the computer scientist in the lead, and the lead is correct. In "Twenty Questions for Donald Knuth" (InformIT, 20 May 2014, Q17, asked by Andrew Binstock) [fetch]:
  - "I've come to believe that P = NP"
  - "I don't believe that the equality P = NP will turn out to be helpful even if it is proved"
  - "such a proof will almost surely be nonconstructive"
  - "Although I think M probably exists, I also think human beings will never know such a value."

  His model is the Robertson–Seymour theorem, for which "The algorithm exists, but it's not known to be discoverable in finite time." https://www.informit.com/articles/article.aspx?p=2213858&seqNum=17
- **Aaronson's comment on Knuth** [primary text]: Knuth "has explicitly speculated that P = NP will be proven in that way. To me, however, it's unclear whether he speculates this because there's a positive reason for thinking it true, or just because it would be cool and interesting if it were true." Aaronson also names Richard Lipton as professing agnosticism. Source: Aaronson, "P =? NP" (survey, status as of 2017; published in *Open Problems in Mathematics*, Springer, 2016 [memory for venue]). https://www.scottaaronson.com/papers/pnp.pdf
- **Ryan Williams (MIT), October 2026, after the ETH refutation claim:** he said every computer scientist should probably put a little more weight on P = NP, "one's weight may vary". [secondary: TechCrunch, 27 Oct 2026] https://techcrunch.com/2026/10/27/frontier-ai-labs-say-their-models-refuted-the-exponential-time-hypothesis-what-does-that-mean/
- **Bill Gasarch, 1 November 2026:** "Just my opinion: I think SAT is not in P." [fetch] https://blog.computationalcomplexity.org/2026/
- **Lance Fortnow, 4 November 2026:** "I still believe P v NP requires new techniques that AI won't come up with on its own." [fetch] https://blog.computationalcomplexity.org/2026/

---

## 2. The outcomes, separated

### (a) P ≠ NP is proved

- **Practical effect.** 81% of 2019 poll respondents said a proof of P ≠ NP would *not* have a big effect on practical computing. Hal Gabow: "We already have put our faith in P≠NP." [primary text] https://www.cs.umd.edu/users/gasarch/papers/poll3.pdf
- **It would not secure cryptography.** Fortnow (CACM, September 2009) [primary text]: "Proving P ≠ NP would not be the end of the story ... Cryptography for example would require that a problem like factoring (not believed to be NP-complete) is hard for randomly drawn composite numbers." Also: "Assuming P≠NP is not enough to get public-key protocols, instead we need strong average-case assumptions about the difficulty of factoring or related problems." https://lance.fortnow.com/papers/files/pnp-cacm.pdf
- **Impagliazzo's five worlds** ("A Personal View of Average-Case Complexity", 17 April 1995) [primary text]. P ≠ NP rules out only Algorithmica. Three worlds are still consistent with P ≠ NP but have no public-key cryptography:
  - Heuristica: NP is "intractable in the worst-case, but tractable on average for any samplable distribution".
  - Pessiland: "the worst of all possible worlds ... there are hard average-case problems, but no one-way functions".
  - Minicrypt: "one-way functions exist, but public key cryptography is impossible".

  https://cseweb.ucsd.edu/~russell/average.ps
- **Aaronson's reading of a proof** [primary text]: "If 3Sat is ever placed outside P, it seems like a good bet that the proof will place many other problems inside P". In other words, a lower-bound proof might come with new algorithms. https://www.scottaaronson.com/papers/pnp.pdf
- **Bottom line for the proposal:** outcome (a) carries no identified hazard in the sources. It is the outcome 88–99% of polled theorists expect.

### (b) P = NP is proved non-constructively

- Knuth expects this outcome and expects it not to be "helpful" (see 1.2).
- **The technical catch a cryptographer will raise: a non-constructive proof does not stay non-constructive for search problems.** Aaronson [primary text], citing Levin's universal search, describes an algorithm that dovetails over all Turing machines M1, M2, ... and halts "when and if any Mi outputs a valid solution to one's NP search problem. If we know P = NP, then we know this particular algorithm will find a valid solution, whenever one exists, in polynomial time ... Admittedly, however, the polynomial or constant factor will be so enormous as to negate this algorithm's practical use." So outcome (b) at once becomes a case of outcome (c) for every NP search problem, including key recovery. https://www.scottaaronson.com/papers/pnp.pdf
- **Aaronson's response to the "constructivity objection"** [primary text]: "once we knew that an algorithm existed, we'd have a massive inducement to try to find it. The same is true if, for example, the first proof of P = NP only gave an n^1000 algorithm, but we suspected that an n^2 algorithm existed." So (b) and (c) would trigger an intense search for (d). Same URL.

### (c) P = NP with a galactic algorithm

- **Cook (Clay problem statement)** [primary text]: "a computer program requiring n^100 steps could never be executed on an input even as small as n = 10." https://www.claymath.org/wp-content/uploads/2022/06/pvsnp.pdf
- **The term "galactic"**, as glossed in the 2019 poll [primary text]: "Lipton and Regan in a Blog Post coined 'Galactic' to mean an algorithm in poly time but you would never actually run it either due to large degree or large constants." Mitch Harris (poll comment) expected P = NP to be practically "interplanetary" rather than galactic. https://www.cs.umd.edu/users/gasarch/papers/poll3.pdf
- **A live example of the galactic pattern (October 2026).** The ETH refutations are a galactic *subexponential* algorithm, not a polynomial one. Anthropic's method reportedly would not beat brute force until problems exceed 10^10,000 variables [secondary: Dataconomy, 4 Nov 2026] https://dataconomy.com/2026/11/04/openai-and-anthropic-claim-ai-disproved-the-exponential/. A follow-up preprint lowers the crossover for general 3-SAT to about 2^(8.6·10^9) variables, from 2^(2.2·10^12) (Majdoddin, arXiv:2610.41622, 30 Oct 2026) [fetch] https://arxiv.org/abs/2610.41622. This matters because the theory community has just watched one galactic breakthrough of exactly the kind described in (c), and it broke nothing deployed (see 5.2).
- **Cryptographic consequence of (c):** none directly, but a galactic result signals that an attack may be possible. Daniel Lokshtanov, on the ETH result, said it does not directly affect cryptography but should worry some designers of cryptosystems. [secondary: Dataconomy] same URL.

### (d) P = NP with a practical algorithm

- **Gödel to von Neumann, 20 March 1956**, in the translation quoted by Aaronson [primary text]: "If there actually were a machine with [running time] ∼ Kn (or even only with ∼ Kn^2) ... this would have consequences of the greatest magnitude. That is to say, it would clearly indicate that, despite the unsolvability of the Entscheidungsproblem ... the mental effort of the mathematician in the case of yes-or-no questions could be completely ... replaced by machines." https://www.scottaaronson.com/papers/pnp.pdf . Lipton's site uses a different translation, "the mental work of a mathematician concerning Yes-or-No questions could be completely replaced by a machine" [fetch]. https://rjlipton.com/the-gdel-letter/
- **Cook** [primary text]:
  - "If P = NP, these assumptions are all false. Specifically, an algorithm solving 3-SAT in n^2 steps could be used to factor 200-digit numbers in a few minutes."
  - "Although a practical algorithm for solving an NP-complete problem (showing P = NP) would have devastating consequences for cryptography, it would also have stunning practical consequences of a more positive nature".
  - Such an algorithm would let a computer "find a formal proof of any theorem that has a proof of reasonable length ... Such theorems may well include all of the CMI prize problems."

  https://www.claymath.org/wp-content/uploads/2022/06/pvsnp.pdf
- **Fortnow (CACM 2009)** [primary text]:
  - "Many focus on the negative, that if P = NP then public-key cryptography becomes impossible. True but what we will gain from P = NP will make the whole internet look like a footnote in history."
  - Transportation "scheduled optimally".
  - "Learning becomes easy by using the principle of Occam's razor".
  - "One could find short fully logical proofs for theorems".
  - His own position: "Complexity theorists generally believe P≠ NP and such a beautiful world cannot exist."

  https://lance.fortnow.com/papers/files/pnp-cacm.pdf
- **Aaronson** [primary text]: "essentially all the cryptography that we currently use on the Internet ... would be broken if P = NP (and if, moreover, the algorithm were efficient in practice ...)". He names the exceptions, "the one-time pad and quantum key distribution, which don't rely on any computational assumptions". https://www.scottaaronson.com/papers/pnp.pdf
- **Fortnow, 4 November 2026** [fetch]: "Outside of breaking codes, what could you do with P = NP that you couldn't do today using other means?" He also invokes "Optiland", a world where "we got all of the goodies of P = NP, without losing cryptography", and says recent results are a step towards it. https://blog.computationalcomplexity.org/2026/

**What breaks under (d)** is detailed in 3.4.

---

## 3. What cryptography rests on

### 3.1 Factoring and discrete log are not known to be NP-complete

The lead was right.

- **Cook** [primary text]: the decision version of factoring, L_fact, and its complement are both in NP, "Thus Lfact is a good example of a problem in NP that seems unlikely to be either in P or NP-complete." https://www.claymath.org/wp-content/uploads/2022/06/pvsnp.pdf
- **The standard consequence** [memory, textbook]: if any problem in NP ∩ coNP were NP-complete, then NP = coNP and the polynomial hierarchy collapses. That is why experts do not expect factoring or discrete log to be NP-complete. Both also fall to Shor's quantum algorithm (1994), which no NP-complete problem is believed to do.
- **Aaronson** [primary text]: discrete log has "worst-case/average-case equivalence ... However, despite decades of work, no one has been able to show worst-case/average-case equivalence for any NP-complete problem". https://www.scottaaronson.com/papers/pnp.pdf
- **Consequence for the proposal:** a fast algorithm for factoring or discrete log would break RSA and elliptic-curve cryptography *without* saying anything about P vs NP. P = NP is sufficient for these breaks but not necessary.

### 3.2 The post-quantum standards

- **13 August 2024:** NIST finalised three standards. https://www.nist.gov/news-events/news/2024/08/nist-releases-first-3-finalized-post-quantum-encryption-standards
  - FIPS 203, ML-KEM ("Module-Lattice-Based Key-Encapsulation Mechanism", from CRYSTALS-Kyber).
  - FIPS 204, ML-DSA (module-lattice signatures, from Dilithium).
  - FIPS 205, SLH-DSA (hash-based, from SPHINCS+, "based on a different math approach than ML-DSA").
- **FIPS 206 (FN-DSA, from Falcon, lattice-based):** NIST submitted the draft for approval on 28 August 2025. I found no confirmation that the final standard has been published (secondary sources; see Section 7). https://www.encryptionconsulting.com/education-center/fn-dsa-fips-206/
- **11 March 2025:** NIST selected HQC (code-based) as a backup KEM "based on different math than ML-KEM ... if a weakness were discovered in ML-KEM". https://www.nist.gov/news-events/news/2025/03/nist-selects-hqc-fifth-algorithm-post-quantum-encryption
- **NIST IR 8547, "Transition to Post-Quantum Cryptography Standards":** initial draft 12 November 2024, final 27 October 2026 [fetch]. The final abstract ties it to Executive Order 14412 and OMB M-26-15. The often-quoted dates (quantum-vulnerable algorithms deprecated after 2030, disallowed after 2035) come from the draft and from secondary coverage of the final. I did not read them in the final text myself. https://csrc.nist.gov/pubs/ir/8547/final ; https://csrc.nist.gov/pubs/ir/8547/ipd ; https://postquantum.com/security-pqc/nist-ir-8547-final/

### 3.3 How well studied are the lattice assumptions?

- **The foundations:** LWE and SIS reduce from *worst-case* lattice problems. This is a property factoring lacks. See Peikert, "A Decade of Lattice Cryptography", Foundations and Trends in TCS 10(4), 2016. https://eprint.iacr.org/2015/939
- **Not NP-hard at the relevant approximation factors:** Aharonov and Regev showed that approximating SVP and CVP within √n is in NP ∩ coNP (JACM 52(5), 2005). The approximation factors that cryptography relies on are polynomial and at least this large, so by the same reasoning as for factoring these problems are not expected to be NP-hard [memory for that inference; the theorem is in the paper]. https://cims.nyu.edu/~regev/papers/cvpconp.pdf
- **A recent scare that came to nothing.** In April 2024 Yilei Chen claimed a polynomial-time *quantum* algorithm for LWE with certain parameters. Within about ten days Hongxun Wu and Thomas Vidick found a bug, and Chen wrote that "Step 9 of the algorithm contains a bug, which I don't know how to fix" [secondary]. https://scottaaronson.blog/?p=7946 ; https://thequantuminsider.com/2024/04/20/update-scientists-spot-mistake-in-proposed-pqc-cracking-algorithm/
- **An AI-found lattice result (July 2026).** Anthropic reports that Claude Mythos Preview found an attack on HAWK, a NIST additional-signature candidate based on the Lattice Isomorphism Problem, that halves its effective key size. The attack is "specific to HAWK" and "does not impact other NIST post-quantum signature candidates or lattice-based cryptography in general" [fetch]. https://www.anthropic.com/research/discovering-cryptographic-weaknesses
- **Fair characterisation:** structured (module) lattices have had roughly 15 to 25 years of concentrated cryptanalysis, depending on where you start counting. Factoring has had decades more. That is why NIST added HQC and SLH-DSA as hedges based on different mathematics.

### 3.4 Would P ≠ NP make cryptography safe? No.

- Cryptography needs one-way functions, which are an *average-case* object. Aaronson [primary text]: "It would be laughable to advertise a cryptosystem on the grounds that there exist messages that are hard to decode!" Also: "It's a longstanding open problem whether P ≠ NP implies" average-case hardness. https://www.scottaaronson.com/papers/pnp.pdf
- Fortnow 2009 (quoted in 2(a)) and Impagliazzo's Heuristica, Pessiland and Minicrypt (also in 2(a)) say the same.
- The implication runs in one direction only. A one-way function implies P ≠ NP: Aaronson [primary text], "If you believe ... that there's any cryptographic one-way function ... then that's enough for P ≠ NP." The converse is open.

### 3.5 What exactly breaks under outcome (d)

Breaks:
- **Public-key encryption, key exchange and signatures** of every computational kind: RSA, (EC)DH, ECDSA, ML-KEM, ML-DSA, HQC. Recovering the secret key is an NP search problem. Sources: Fortnow, "If P = NP then public-key cryptography is impossible" [primary text], https://lance.fortnow.com/papers/files/pnp-cacm.pdf ; Aaronson, "in most cryptography, the problem of finding the decryption key is an NP search problem" [primary text], https://www.scottaaronson.com/papers/pnp.pdf
- **Symmetric key recovery** (AES and the like) from a few known plaintext–ciphertext pairs. This is also an NP search problem. Cook names DES specifically [primary text]. https://www.claymath.org/wp-content/uploads/2022/06/pvsnp.pdf
- **Hash functions:** preimages, second preimages and collisions are all NP search problems, so SLH-DSA falls too [memory, standard].
- **Proof of work:** finding a nonce under a target is likewise an NP search problem [memory]. Bitcoin's *signatures* are elliptic-curve and fall under the public-key item above.

Survives:
- The one-time pad and quantum key distribution (Aaronson, above).
- Fine-grained "puzzle" schemes with only a polynomial gap between honest work and attack, such as Merkle puzzles [memory, not checked today].
- Gasarch (blog, 13 Jan 2020): "We now have the technology to do private key really well" with one-time pads [fetch]. https://blog.computationalcomplexity.org/2020/01/what-would-you-do-if-you-showed-pnp-i.html

Unrecoverable:
- **Traffic already recorded.** A commenter on the same post: "there's no way to retroactively switch to private key" [fetch].

Beyond cryptography (benefits as well as harms):
- Optimisation and scheduling, learning by finding the smallest consistent program, and short formal proofs (Fortnow; Cook).
- Cook's point that this "would transform mathematics" and might include "all of the CMI prize problems". Note that the Riemann hypothesis is a CMI prize problem, and Section 5 bears on it.

---

## 4. The nearer hazard

### 4.1 A specific assumption falls to a new classical algorithm while P vs NP stays open

There is precedent.

- **SIDH/SIKE, July 2022.** Castryck and Decru (KU Leuven), "An efficient key recovery attack on SIDH": "Our Magma implementation breaks SIKEp434, which aims at security level 1, in about ten minutes on a single core" [fetch]. Under an assumption about the endomorphism ring, the running time is heuristically polynomial. SIKE was a NIST round-4 KEM candidate. https://eprint.iacr.org/2022/975
- **Rainbow, February 2022.** Beullens, "Breaking Rainbow Takes a Weekend on a Laptop", recovered keys for the security-level-1 parameters in about 53 hours. Rainbow was a round-3 *finalist* for signatures and was not standardised [secondary]. https://eprint.iacr.org/2022/214
- **Discrete log in small-characteristic finite fields, 2013.** Barbulescu, Gaudry, Joux and Thomé gave a heuristic quasi-polynomial algorithm, an enormous jump from L(1/4) [fetch]. This was a classical, theory-level collapse of a discrete-log setting. https://eprint.iacr.org/2013/400
- **The quantum threat to RSA and ECC is advancing on a separate track.** Gidney (May 2025) estimates RSA-2048 could be factored in under a week with fewer than a million noisy qubits, against 20 million in the 2019 estimate. https://arxiv.org/abs/2505.15917
- **Richard Lipton (2009)** [fetch]:
  - "I think at a minimum there should be plans on how to react quickly if modern cryptography is destroyed."
  - "If you think that it is impossible that P=NP, then you will not plan for the failure of your crypto assumptions."
  - In a comment reply: "if someone figures out how to factor, for example, they might choose not to tell anyone–no?"

  https://rjlipton.com/2009/09/15/theory-has-bet-on-pnp/
- **The point for the drafter:** every real break above came from targeted cryptanalysis of one structured problem. None came from progress on P vs NP.

### 4.2 Harvest now, decrypt later

- CISA, NSA and NIST, "Quantum-Readiness: Migration to Post-Quantum Cryptography" (21 August 2023), warns that adversaries may be collecting encrypted data now to decrypt later ("catch now, break later"). The NSA page returned HTTP 403 to my fetch, so the wording comes from secondary reports of that document (Section 7). https://www.nsa.gov/Press-Room/Press-Releases-Statements/Press-Release-View/Article/3498776/post-quantum-cryptography-cisa-nist-and-nsa-recommend-how-to-prepare-now/ ; https://www.aha.org/fbi-tlp-alert/2023-08-23-quantum-readiness-migration-post-quantum-cryptography
- **The same logic applies to a classical break.** Any break of a key-exchange assumption, whether quantum, classical-specific or P = NP, exposes *recorded* past traffic, which cannot be re-protected. This is the strongest part of the hazard case, and it does not depend on P vs NP [inference from the sources above].

### 4.3 How the community handles a break today

- **SIKE:** Castryck said "On July 22, we informed the SIKE team about our attack, and on July 30, we posted our corresponding paper online" [secondary, CACM news; the CACM page returned 403 to my fetch]. That is roughly eight days' notice to the designers, then full public release with code. The SIKE team then stated that SIKE and SIDH "are insecure and should not be used" (NIST round-4 page) [secondary]. https://cacm.acm.org/news/nist-post-quantum-cryptography-candidate-cracked ; https://csrc.nist.gov/projects/post-quantum-cryptography/post-quantum-cryptography-standardization/round-4-submissions
- **AI-found breaks (July 2026):** Anthropic says it "followed responsible disclosure procedures". It "shared our attack with the authors of HAWK in June and coordinated disclosure to the public NIST mailing list", and gave advance copies to US government and industry partners [fetch]. https://www.anthropic.com/research/discovering-cryptographic-weaknesses
- **Software vulnerabilities found by AI:** Project Glasswing (Anthropic, 7 April 2026) reports bugs to maintainers and publishes "cryptographic hashes of the details" of unpatched flaws, to "reveal the specifics after a fix is in place" [fetch]. https://www.anthropic.com/glasswing
- **The ETH refutation:** OpenAI's science lead, Dan Roberts, reportedly told Ryan Williams they had checked for cryptographic impact and were "reasonably confident that this didn't" imply breaks [secondary: TechCrunch]. https://techcrunch.com/2026/10/27/frontier-ai-labs-say-their-models-refuted-the-exponential-time-hypothesis-what-does-that-mean/ . A preprint from Ruhr University Bochum and MPI-SP (29 October 2026) reportedly applied the claimed algorithm to elliptic curves and found a slightly subexponential attack that helps only at astronomical sizes, with no effect on deployed curves [secondary: Dataconomy; I could not locate the preprint]. https://dataconomy.com/2026/11/04/openai-and-anthropic-claim-ai-disproved-the-exponential/

---

## 5. AI and research mathematics, as of 23 November 2026

### 5.1 The Riemann hypothesis claim (20 November 2026)

**Who and what.** Levent Alpöge, a mathematician at Anthropic, posted a short "Remark" on 20 November 2026. Its first page says [primary text]: "I believe I have, working with Claude, discovered a proof of the Riemann Hypothesis. In fact, the method easily extends much further, resolving the so-called Generalized Riemann Hypothesis". It also says "Claude and I have also formalized the arguments without assumptions" and "It being obviously inappropriate to attempt to post some massive unreadable travesty of 'slop', I decided to only present Lean." A footnote reads: "I of course amused myself, and hit 250,000+ pages." The Lean files are linked as alpo.ge/lean.tar.gz.part01–14. The Remark's timeline puts the final step ("GRH") on 16 November 2026. https://alpo.ge/remark.pdf

**Which model.** The Remark says only "Claude". Wikipedia's Riemann hypothesis article describes it as "an unreleased research version of Anthropic's Claude" [fetch]. Quanta (20 November) reported that Anthropic had not officially announced the result [fetch]. So the lead's "unreleased model" detail has secondary support but is not stated in the primary document.

**Size.** "More than 17 million lines of Lean code", per The Conversation, republished by Phys.org on 23 November 2026 [fetch]. https://phys.org/news/2026-11-sacred-mathematics-riemann-hypothesis-ai.html . Sutherland's verification page reports 175,187 compiled modules and a 61.6 GB kernel export. https://math.mit.edu/~drew/grh/

**Verification status on 23 November 2026:**
- **Lean FRO and Mathlib Initiative, joint statement of 21 November 2026** [fetch]:
  - "We hereby certify that both the statement and the proof of the Riemann Hypothesis are correct."
  - "We have full confidence that Alpöge's proof of the Riemann Hypothesis is correct."
  - The statement checked is Mathlib's `RiemannHypothesis`. Statement fidelity was checked with `comparator` and `con-leche --compare`.
  - Kernels used: Lean's kernel, con-leche, con-ron and others, run "on an inert export".

  https://leanprover-community.github.io/blog/posts/riemann-hypothesis/
- **Andrew Sutherland (MIT), verification page last updated 23 November 2026, 23:45 UTC** [fetch]:
  - Passed: full compile with zero errors; only the axioms `propext`, `Classical.choice` and `Quot.sound`; kernel acceptance by nanoda, the default Lean kernel and the paranoid kernel; "Comparator v4.33.0 reported 'Your solution is okay!' on 23 November".
  - Pending: a `lake comparator` run under Lean v4.36.0.
  - Scope: Dirichlet L-functions only, not Dedekind, Hecke or automorphic L-functions.

  https://math.mit.edu/~drew/grh/
- **Human understanding:** none yet.
  - Wikipedia: "A natural language proof has yet to be published as of 23 November 2026" [fetch]. https://en.wikipedia.org/wiki/Riemann_hypothesis
  - Daniel Litt: "exceedingly likely to be correct" and "No human understands it yet" [secondary, via The Conversation/Phys.org].
  - Maksym Radziwiłł: "this doesn't answer it at all" on the question "why?" He also said the write-up contains "nonsensical statements" [secondary, via Quanta]. https://www.quantamagazine.org/update/169569/
  - Scientific American (Moskowitz, 20 November, updated 21 November) quotes Sutherland: "Honestly the chance that anything is fishy here is approximately zero" [fetch]. https://www.scientificamerican.com/article/the-ai-riemann-hypothesis-proof-is-almost-certainly-true-independent-mathematicians-attest/
- **Other coverage I did not open:** Nature (Castelvecchi, 20 November), https://www.nature.com/articles/d41586-026-03812-7 (login wall); The Guardian (21 November); USA Today (21 November).

**The separate human proof, posted the same day.** Alessandro Masullo, a Stanford postdoc, posted a 940-page manuscript claiming the generalized Riemann hypothesis. It was posted by Ravi Vakil, AMS president, who called it "all human, with no AI". Quanta reports Brian Conrad had been reviewing it for months, and that many number theorists are withholding judgement because an earlier Masullo proof did not hold up [fetch]. https://www.quantamagazine.org/update/169569/ . The Conversation/Phys.org reports "potential problems were found within hours" [fetch]. https://phys.org/news/2026-11-sacred-mathematics-riemann-hypothesis-ai.html . I could not find Vakil's post directly.

**Also in the Remark:** Alpöge and Tristan Buckmaster claim a variant of the Navier–Stokes problem (Quanta) [fetch].

### 5.2 AI and complexity theory: the ETH refutation (October 2026)

This is the item most relevant to the proposal.

- **OpenAI, 26 October 2026** [fetch]: "our system has recently proved that the ETH is false, a result that was subsequently verified in Lean." It released this alongside a local smoothing / Kakeya result and a QCD existence proof. Review of the ETH result is led by Russell Impagliazzo, Ramamohan Paturi and Ryan Williams. The page does not mention cryptography or security. https://openai.com/index/building-scientific-understanding-with-academic-communities/
- **The prompt.** OpenAI's prompt asked the model to "Research an unconditional refutation of the deterministic Strong Exponential Time Hypothesis (SETH)" [fetch, posted 12 November 2026]. The labs are explicitly pointing models at central complexity conjectures. https://ethdiscussion.blog/2026/11/12/openai-prompt-that-led-to-the-eth-refutation/
- **Anthropic, "A 2^{o(n)} Time Algorithm for 3-SAT" (v1, 27 October 2026)** [fetch]: "found on October 16 by an internal Claude research model" with no human input, and formalised in Lean 4. https://hexagonmath.org/2610.00577v1
- **Claimed bounds.** Both claim 2^O(n log log n / log n) for 3-SAT. OpenAI's Lean file proves a weaker bound, 2^O(n (log log n)^2 / log n), which still refutes ETH (Wikipedia) [fetch]. https://en.wikipedia.org/wiki/Exponential_time_hypothesis
- **Status.** Not through academic review. The reviewers wrote, "Our involvement should not be taken as certification of the claim" [secondary]. Fortnow (28 October 2026): "it is safe to assume now that the exponential-time hypothesis is toast" and "the OpenAI algorithm applies to k-SAT but not to NP problems in general" [fetch]. https://blog.computationalcomplexity.org/2026/
- **Scope.** Wikipedia: if ETH fails, "it would have no implication for the P versus NP problem" [fetch]. Anthropic says the result does not refute the Orthogonal Vectors Hypothesis [secondary, Dataconomy].
- **Practicality.** Galactic (see 2(c)). OpenAI: "turning theoretical advances into practical improvements, will require significant further research" [secondary, Decrypt]. https://decrypt.co/381956/opena-eth-false-crypto-twitter-has-questions?amp=1
- **Reaction in the field** [secondary, Dataconomy]. Lokshtanov called it "a giant bomb dropped into the middle of the field". Claude's own literature search found more than 800 papers that rely on ETH or something stronger. Williams has called OpenAI's earlier bulk releases a "DDOS attack on mathematicians" [secondary, TechCrunch].

### 5.3 AI and cryptanalysis

- **CryptanalysisBench** (arXiv:2607.18538; Schneier blog, 28 July 2026) [fetch]. It has 191 tasks. The models tested broke about 65–86% of tier-1 schemes, those with known practical breaks. They also produced novel results the authors call "to the best of our knowledge not previously known": a key-recovery attack on the SpoC AEAD and an error in KINDI's CCA proof. Schneier: "Still early results, but this is definitely something to watch." https://www.schneier.com/blog/archives/2026/07/measuring-llms-ability-to-perform-cryptanalysis.html
- **Anthropic, "Discovering cryptographic weaknesses" (28 July 2026)** [fetch]. Mythos Preview found:
  - the HAWK key-size-halving attack;
  - a 7-round AES-128 attack 200–800 times faster than prior attacks, which "does not break the full cipher".

  Each cost about $100,000 in compute. Anthropic writes that "we should not assume that language model capabilities will plateau at this level" and that "it would be prudent to consider how researchers should react if a language model were to discover vulnerabilities in cryptosystems where attacks do have an immediate real-world impact." https://www.anthropic.com/research/discovering-cryptographic-weaknesses

### 5.4 Earlier milestones

- **IMO 2024:** DeepMind's AlphaProof and AlphaGeometry 2 reached silver-medal level [memory]. https://deepmind.google/discover/blog/ai-solves-imo-problems-at-silver-medal-level/
- **IMO 2025 (July):** Gemini Deep Think scored 35/42, gold standard, certified by IMO graders. OpenAI's experimental model also scored 35, graded by former medallists rather than officially. https://deepmind.google/discover/blog/advanced-version-of-gemini-with-deep-think-officially-achieves-gold-medal-standard-at-the-international-mathematical-olympiad/ ; https://www.axios.com/2025/07/21/openai-deepmind-math-olympiad-ai
- **AlphaEvolve in complexity theory (September 2025):** AI-found gadgets gave improved NP-hardness-of-approximation bounds for MAX-3-CUT and MAX-4-CUT (Nagda, Raghavan, Thakurta; arXiv:2509.18057). https://arxiv.org/abs/2509.18057v4
- **August 2026:** an "unreleased research version of Claude" raised the proven fraction of zeta zeros on the critical line from 41.6% to 67.2%, with a Lean formalisation. It was prompted by a non-mathematician to "take a real stab" at RH. Anthropic wrote: "We don't expect that the techniques Claude used will lead to proving the Riemann hypothesis" [fetch]. https://www.anthropic.com/research/riemann-zeta
- **4 September 2026:** Anthropic formalised Fermat's Last Theorem in Lean, about 13 million lines in 11 days [secondary]. https://www.anthropic.com/research/formalizing-fermats-last-theorem ; https://siliconangle.com/2026/09/04/anthropic-uses-claude-to-formalize-proof-of-fermats-last-theorem/
- **6 October 2026:** OpenAI released 377 results, including two proofs of a "quasi-Riemann hypothesis" [fetch, Quanta]. https://www.quantamagazine.org/update/168664/

### 5.5 Have labs said anything about pointing models at open problems, or about cryptanalysis as a risk?

- **Pointing models at open problems: yes, explicitly.** Anthropic's zeta post and its Jacobian-conjecture footnote, the OpenAI SETH prompt, and OpenAI's academic-collaboration programme. OpenAI cites $5 million to a Simons Foundation initiative on AI-produced results. Links are in 5.2 and 5.4.
- **Cryptanalysis as a risk.**
  - Anthropic's July 2026 post (5.3) is the clearest public statement.
  - Lab frontier frameworks define cyber thresholds mainly as zero-day discovery and exploitation, and end-to-end cyberattacks. The Frontier Model Forum's report (13 February 2026) lists CTF-style tests of "ability to break encryption algorithms" but sets no threshold specific to cryptanalysis or mathematics [primary text]. https://www.frontiermodelforum.org/uploads/2026/02/FMF-Technical-Report_-Managing-Advanced-Cyber-Risks-in-Frontier-AI-Frameworks.pdf
  - OpenAI (7 August 2026) said of an upcoming model, Astra, that it "cannot rule out critical cyber capabilities under our Preparedness Framework". That threshold is defined by zero-day exploits, and the post does not mention cryptography [fetch]. https://openai.com/index/responding-next-frontier-critical-cyber-capabilities/
  - I found **no** lab framework that names mathematical results (P vs NP, ETH, factoring) as a gated capability.
  - The *only* documented security check on the ETH result is the informal one OpenAI's Roberts described (4.3).

---

## 6. Has anyone already argued for restraint or a disclosure norm?

- **The NSA and academic cryptography, 1978–1981.** NSA director Bobby Inman wrote to NSF about grant proposals from Adleman and Rivest in July and August 1980. The American Council on Education's Public Cryptography Study Group (report dated 7 February 1981), formed at NSA's request, recommended a voluntary, two-year experiment in which cryptography papers would be submitted to NSA for review before publication. Sources disagree on whether this meant approval or only notification. https://www.nationalacademies.org/read/253/chapter/14 ; https://csmonitor.com/1981/0624/062435.html ; https://uwnxt.nationalacademies.org/read/5131/chapter/19 . The academic community resisted *mandatory* review. Whether the voluntary experiment ran is unverified (Section 7).
- **Fortnow, "Should you reveal a P = NP algorithm?" (17 April 2014)** [fetch]:
  - "I would first warn the Internet companies (like was done for heartbleed) so they can modify their systems."
  - "Once the genie is out of the bottle everyone can use it and the government wouldn't be able to hide it."
  - "If you can find an algorithm so can others so you should just take the credit or someone else will discover it."

  https://blog.computationalcomplexity.org/2014/04/should-you-reveal-p-np-algorithm.html
- **Gasarch, 13 January 2020**, on what to do with a P = NP algorithm [fetch]. He points to the novel *Factor Man*, questions "how much damage would be done in the transition period", and notes Fortnow thinks the benefits outweigh the loss of crypto. https://blog.computationalcomplexity.org/2020/01/what-would-you-do-if-you-showed-pnp-i.html
- **Lipton, 2009:** a plan for reacting if cryptography is destroyed, and the remark that a discoverer "might choose not to tell anyone" (4.1).
- **Taranovsky (2019 poll comment)** [primary text]: a fully effective P = NP "if held secret by a power-seeking group, world government in 2 years." This is the secrecy hazard, which cuts *against* restraint by honest researchers. https://www.cs.umd.edu/users/gasarch/papers/poll3.pdf
- **Anthropic, July 2026:** it is "prudent to consider how researchers should react" to an AI-found, immediately impactful cryptographic break (5.3).
- **Restraining research on P vs NP or SAT itself:** I found *no* published expert argument for this, before or after the October 2026 ETH result. A search turned up only explainer blogs saying the near-term risk is a targeted attack on one scheme, not P = NP (e.g. https://ransomnews.com/p-vs-np-encryption-ai-claims-2026/ , low reliability).
- **Expert positions on restraint:** the ones found are Fortnow (warn, then publish; secrecy is futile), Lipton (plan for failure), and the cryptanalysis norm (notify designers, then publish, as with SIKE and HAWK). None argues for leaving a problem unstudied.

**Bearing on the proposal:** the documented expert norm is coordinated disclosure, not abstention. The historical attempt at prior restraint (NSA, 1980–81) is remembered by academics as a threat to open research. A proposal framed as "don't work on P vs NP" would be arguing against both.

---

## 7. Not checked, and where sources disagree

- **Quote reliability.** Quotes marked [fetch] went through a web-fetch tool. Quotes marked [secondary] (Dataconomy, TechCrunch, Quanta, The Conversation) are reporters' renderings. Lokshtanov, Husfeldt, Jonsson and Williams were quoted to me only through Dataconomy and TechCrunch, and I did not find the original interview (possibly *Science* or *New Scientist*).
- **RH claim, model status.** Alpöge's Remark says "Claude" without a version. "Unreleased research version" is Wikipedia's wording. I found no official Anthropic announcement as of 23 November.
- **RH claim, claimed theorem.** Sources disagree between RH and GRH. The Remark claims both. Sutherland's page scopes the formal result to Dirichlet L-functions.
- **RH claim, size.** "17 million lines" comes from The Conversation and Wikipedia. Sutherland gives module counts, not lines.
- **RH claim, pending checks.** Sutherland's `lake comparator` run under Lean v4.36.0 was still pending at 23:45 UTC on 23 November.
- **RH claim, other coverage.** I did not open the Nature article (login wall), Rubinstein's independent check (https://mrubinst.github.io/grh-lean-verification/), The Guardian or USA Today.
- **Masullo manuscript.** I could not find Vakil's post or the manuscript. Details come only from Quanta and The Conversation. "Problems found within hours" is The Conversation's claim alone.
- **ETH.** The reviewers' open letter is a Google Doc I did not open. The Bochum/MPI-SP elliptic-curve preprint is reported by Dataconomy only; I could not locate it on ePrint or arXiv. The 10^10,000 crossover figure is Dataconomy's report of Anthropic's paper. Majdoddin's preprint gives different, also astronomical, figures. Sources say ETH is "27 years old" (from 1999); some say 1998.
- **The 1999 dating.** Impagliazzo and Paturi's ETH paper is usually cited as CCC 1999 / JCSS 2001 [memory].
- **NIST IR 8547 final (27 October 2026).** I confirmed it exists, but did not read the 2030 and 2035 dates in the final text; the dates come from the draft and from secondary reports. FIPS 206 final status is unconfirmed.
- **Harvest now, decrypt later.** The NSA press release returned 403. The phrase is attributed to the August 2023 CISA/NSA/NIST factsheet through secondary pages.
- **SIKE disclosure dates.** The 22 July (designers informed) and 30 July (posted) dates come from a CACM quote reached through search; the CACM page itself returned 403. The ePrint page confirms 30 July 2022 as the received date.
- **Gasarch 2019 headline figure.** The blog says "about 80%" and the paper's table says 88% (109 of 124). The 80% may come from the 3 a.m. question. Wikipedia gives 151 rather than 152 for the 2012 respondent count; the 2019 paper says 152.
- **Knuth.** A widely quoted line, "It's probably true that P equals NP, but we will never know why", appeared in search snippets. I did not verify its source, so it is not used above.
- **NSA prior review, 1981.** Whether the PCSG's voluntary two-year experiment was implemented is unverified. Sources disagree on whether it meant NSA *approval* or *notification*.
- **From memory, not re-checked today:**
  - the NP ∩ coNP collapse argument;
  - the inference that cryptographic lattice approximation factors are not NP-hard;
  - hashes and proof of work being NP search problems;
  - Merkle puzzles surviving P = NP;
  - AlphaProof's 2024 silver;
  - the venue of Aaronson's survey;
  - the venue of Impagliazzo's paper (Structure in Complexity Theory, 1995).
- **Lab frameworks.** I did not read Anthropic's Responsible Scaling Policy or DeepMind's Frontier Safety Framework in full for any mention of cryptanalysis. I found none in the search results or the FMF report.
