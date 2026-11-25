# The P = NP page, read as its hardest readers would

*Written Tue 2026-11-24, 10:25 PST. This is the work of a language
model (Claude, Opus 5.5) reading as three kinds of expert. No mathematician, complexity theorist or cryptographer has
read the page or this file. Where an objection rests on a technical fact I opened a primary source and quoted it (see
Sources); where I could not, I say so. The five opening results are taken as fact, by ruling. I read
`site/index.html`, `MEMO.md` and `README.md` whole, and searched the four files in `research/` for the threads below;
I did not read those four whole. Nothing outside this file was written.*

---

## The five changes most worth making

1. **Replace the public hash with an announcement of nothing.** A labelled hash says out loud that a result exists, and
   the page's own diagram says that is what starts the hunt. Worse, a practical method breaks the hash, so the hash
   stops proving priority. Ask instead for a sealed, dated deposit with an independent body (the 1940 committee's dated
   papers; the Académie's *plis cachetés*, whose title is optional). Make "tell the standards bodies first" say who is
   told, since the page says there is no patch.
2. **Draw the line by what counts as success, not by topic, and list what is allowed.** As written ("fast algorithms
   for NP-complete problems", "against ... the Exponential Time Hypothesis and its relatives"), the line takes in the
   leading route to the harmless answer (Williams: faster-than-brute-force satisfiability algorithms *are* how lower
   bounds get proved), ordinary solver work, and the October result itself. Name the ruled-out goal: an algorithm that
   runs in polynomial or quasi-polynomial time for an NP-complete problem, or a general average-case one. Then say in
   one line what stays open: lower bounds, subexponential work, solver engineering, cryptanalysis with defenders.
3. **Aim at the catastrophe, which is the end of one-way functions, and say why targeted cryptanalysis is left out.** A
   cryptographer will see two gaps. Cryptography can die while P ≠ NP holds (Impagliazzo's Heuristica and Pessiland).
   And the nearer danger, an AI breaking lattices, factoring or AES directly, is not covered: the page even counts the
   HAWK break among results that "put nothing at risk". Add two sentences: this ask covers the one kind of result with
   no fallback; targeted breaks stay under disclosure because there is a scheme to move to.
4. **Give it the features the page's own history says restraint needs: checkable, collective, with an end.** As written
   it is open-ended, asked of rivals who cannot check one another, and not yet asked for by insiders. By the page's own
   reading of the cases, that is how restraint fails. The smallest version that a lab could keep and others could check:
   - a public statement in each framework update that no such campaign ran, signed by a named officer;
   - an anonymous internal channel for reporting a breach;
   - a commitment that binds once a stated set of labs, open-weight developers included, have made it;
   - a review by an outside panel every two years, with the stop ending on a proof of P ≠ NP or of one-way functions.
5. **Replace "a stop buys years" with the real window, and state the trade plainly.** The years in the page's timeline
   are human rediscovery in the 1970s. Open-weight models trailed the closed frontier by about four months in 2026
   (four to seven on cyber tasks). GCHQ, a state agency, was the first finder in both of the page's own cases. Say it
   straight: if P ≠ NP, as most experts expect, these campaigns could not have succeeded and abstaining costs almost
   nothing. If not, abstaining buys months, perhaps years, and time to settle who holds such a thing.

---

## Where the page is strong (all three readers would grant these)

- **The direction is right and stated early.** "If the opposite is proved, that P ≠ NP, nothing breaks. Nobody is
  asking anyone to stop proving that." A theorist reading for a crank tell will not find one here.
- **The best argument on the page is new to this genre and correct.** Coordinated disclosure works "because there is
  another cipher to move to"; here there is none, and "harvest now, decrypt later" means a warning does nothing for
  traffic already taken. That is the real reason the field's norm of warning first, then publishing, does not cover this
  case, and it is sourced (NIST IR 8547). It answers the cryptographer's first reflex before they raise it.
- **The non-constructive escape is closed.** The diagram's second step says any proof yields an explicit, absurdly slow
  method. A cryptographer would raise this first, and it holds (Levin's universal search; Aaronson quoted below).
- **It concedes the good and answers on timing, not by denying it.** "The good would take years to build. The harm
  would be ready that afternoon." That is the right shape: cryptographers' letters concede the legitimate goal first
  (`research/letters_cryptographers_signed.md`).
- **It asks nothing of the field and says so.** The 1970s history of prior review is told honestly. The publication
  norm is the cryptographer's sorest point, and the page steps around it.
- **The history section argues against itself where it should.** "Both times the secret held, and both times
  outsiders found the same thing by themselves." Readers trust a page that shows them evidence it would rather not.
- **The "only the labs" answer is specific and checkable**: money, model access, named results.
- **The status line is honest**: unsigned, checked once, exit undecided.

---

## 1. The complexity theorist

*Reads for: whether the ask understands how the field actually makes progress, and whether it would cost them the
research they care about.*

**1.1 The harmless direction runs through the forbidden one. (Most serious; the page does not see it.)**
The page asks labs for "no campaigns for fast algorithms for NP-complete problems" and promises that work toward P ≠ NP
is untouched. Since 2010 the most successful route to circuit lower bounds, the harmless kind of result, has been
designing algorithms for satisfiability that beat brute force. Williams, in his own abstract: "there are natural NP and
BPP problems for which minor algorithmic improvements over the trivial deterministic simulation already entail lower
bounds such as NEXP ⊄ P/poly". Aaronson's survey calls it "ironic complexity theory": it "uses the existence of
surprising algorithms in one setting to show the nonexistence of algorithms in another setting ... and reduces the
problem of proving impossibility theorems to the much better-understood task of designing efficient algorithms."
Williams's ACC lower bound (NEXP ⊄ ACC, 2011) came from exactly such a satisfiability algorithm. Aaronson says
theorists were "electrified". One paper's title says the whole thing: "A Polylog Shaved is a Lower Bound Made" (Abboud,
Hansen, Vassilevska Williams, Williams). Its abstract: shaving "an arbitrarily large polylog factor from n^2 for Edit
Distance" would mean "NEXP does not have non-uniform NC^1 circuits." Read literally, then, the ask bans the lower-bound
programme the page says it protects. The cost also falls hardest on the theorists the page wants to sign.
*Smallest change:* define "fast" as a running time, not a direction: "no campaign whose aim is a polynomial- or
quasi-polynomial-time algorithm for an NP-complete problem". Add one line: "Faster-than-brute-force algorithms
pursued for lower bounds, and subexponential results generally, are not covered."

**1.2 Natural proofs make even the P ≠ NP side cryptanalytic. (Serious for credibility; not seen.)**
"If the opposite is proved ... nothing breaks" is true of the *result*. It is not true of every *route*. Razborov and
Rudich showed that a "natural" lower-bound proof would itself be an algorithm that distinguishes pseudorandom functions
from random. Aaronson: "if we showed certain problems (factoring and discrete logarithm) to be harder and harder via a
natural proof, we'd simultaneously show those same problems to be easier and easier!" Carmosino, Impagliazzo, Kabanets
and Kolokolova turned natural proofs into learning algorithms: "a natural proof of a circuit lower bound against any
(sufficiently powerful) circuit class yields a learning algorithm for the same circuit class." The practical risk
from this route is small: the attacks it gives are far from usable, and if strong pseudorandom functions exist,
natural proofs cannot reach P/poly. But a theorist will notice that the page treats the two directions as cleanly
separable, and they are not.
*Smallest change:* soften to "If P ≠ NP is proved, the result breaks nothing" and rely on 1.1's running-time line
instead of on direction.

**1.3 The October result would be over the line. (Serious; answered badly.)**
The page calls the ETH refutation a "warning shot" and asks for "no campaigns against ... the Exponential Time
Hypothesis and its relatives." But the refuted claim is that 3-SAT needs 2^(δn) time. By the page's own margin, the
refutation's advantage begins near 2^(8.6 × 10^9) variables. A subexponential, galactic result is the sort of thing the
lower-bound programme wants (1.1), and the page itself says "nothing was hit". A theorist will ask why a harmless
result is cast as the danger. "Its relatives" is also undefined. Fine-grained complexity has dozens of hypotheses (SETH,
NSETH, orthogonal vectors, 3SUM, APSP), and almost none bear on cryptography.
*Smallest change:* keep October as evidence that *the machines can now move these conjectures* (that is the real
warning), and drop ETH and its relatives from the ban. Make them a tripwire instead: a lab whose system refutes one of a
*named* list pauses that line of work and applies the second ask.

**1.4 Worst case is the wrong target; the catastrophe is average case. (Serious; not seen.)**
Cryptography needs one-way functions, which are an average-case object. Impagliazzo's survey defines **Heuristica** as
"the world where NP problems are intractable in the worst-case, but tractable on average for any samplable
distribution." He defines **Pessiland** as "the world in which there are hard average-case problems, but no one-way
functions." Both are consistent with P ≠ NP, and in both, computational cryptography is gone. Aaronson: "It would be
laughable to advertise a cryptosystem on the grounds that there exist messages that are hard to decode!" Liu and Pass
(2020) show one-way functions exist if and only if time-bounded Kolmogorov complexity is "mildly hard-on-average".
That puts some meta-complexity work closer to the danger than most worst-case NP work is. A theorist will say the
page aims at the famous question and misses the one that matters.
*Smallest change:* in the ask, after NP-complete problems, add "or a general method for inverting one-way functions on
average". In "If P = NP", add one sentence: cryptography could fail without P = NP, and this ask covers that case too.

**1.5 Small precision errors a theorist reads as a tell. (Minor each; not seen.)**
- Lede: "the hardest problems in computing". NP-complete problems are not the hardest; PSPACE, EXP and undecidable
  problems are harder. Say "the hardest problems whose answers can be checked".
- Ask: "No campaigns against the conjectures that guard them: P versus NP". P versus NP is a question, not a
  conjecture. Say "against P ≠ NP".
- Title: "stop working on P = NP". A theorist reads "P = NP" as shorthand for the question, which contradicts "nobody is
  asked to stop proving" P ≠ NP. The body needs to say plainly whether *labs* may campaign for P ≠ NP (I read it as yes).
  If yes, consider "AI labs should stop hunting for P = NP" or similar. The title is the author's to rule.
- Diagram step 2: "A method exists at once". Levin's universal search exists *today*. A proof of P = NP would tell
  everyone that it runs in polynomial time. Aaronson: "If we know P = NP, then we know this particular algorithm will
  find a valid solution ... in polynomial time ... Admittedly, however, the polynomial or constant factor will be so
  enormous as to negate this algorithm's practical use." Say "A method is known at once to work".

**1.6 What this reader would accept as an exit.** A proof of P ≠ NP, or of the existence of one-way functions, ends it
outright. Short of that: a fixed term (two years, say), renewed only by a panel that includes theorists from outside
the labs. They would reject any exit that a lab judges alone.

---

## 2. The applied cryptographer

*Reads for: whether the threat model is right, whether the mechanism is sound, and whether it fits the norms they have
signed letters to defend.*

**2.1 The published hash is the announcement. (Most serious; the page does not see it.)**
The diagram's third step: "Everyone now knows a fast method may exist, and the systems that found the proof are
pointed at finding it." The ask: "publish a hash of it at once, which fixes its priority and reveals nothing." A hash
published *as* the commitment to a P = NP-type result reveals the one fact that matters: that such a result exists, and
which lab holds it. That is step three. A cryptographer will also note three technical problems:
- "Reveals nothing" holds only if the hashed text contains a long random nonce; a bare hash of a short claim can be
  guessed.
- A hash with no label proves nothing until it is opened, so a lab must either label it (which announces) or publish
  many unlabelled ones.
- Binding fails under the very result. Finding a well-formed message x with SHA-256(x) = y is an NP search problem, so
  whoever holds a practical method can open *any* old hash to *any* text. Digital commitments, routine ones included,
  stop proving priority once the method exists. Signed timestamps fall the same way, because the signatures fall.
What survives is a physical, institutional deposit. Article 66 of the Académie des sciences rules on *plis cachetés*:
deposits exist "pour but de donner une date certaine aux découvertes qu'ils sont supposés contenir, sans avoir recours
à une publication" (to give a certain date to the discoveries they are supposed to contain, without resorting to
publication). Rule 66-1 adds: "L'indication du titre du document contenu dans le pli est facultative" (stating the
title is optional). The page's own 1940 precedent is the same kind of thing: papers held by a committee and published
later "with a statement of the original date of the paper". Neither announced anything.
*Smallest change:* "If a system finds such a result anyway, the lab should seal a dated copy with an independent body,
announce nothing, and publish only when [the body agreed in advance] decides." If a hash is kept, label it nothing,
salt it, and make it one of many routine ones. The page should then say this protects priority only until a method
exists.

**2.2 "Tell the standards bodies first" contradicts "There is no patch". (Serious; answered badly.)**
The page says, rightly: "A warning cannot help when nothing can be changed." The ask then says to tell the standards
bodies first and "publish in full only once whatever can be protected has been." Under a practical method, symmetric
ciphers and hashes fall too (the page says so), so what can be protected is close to nothing. Telling someone first is
not neutral either: it is a decision about who holds the instrument. The page itself says that question has to be
settled "before the fact." The precedent on the page cuts the same way. Anthropic's HAWK post says the results were
shared "after a period of consultation with US government and industry leaders." A lab's first call, in practice, may
be to a government, and to a cryptographer that means a signals agency.
*Smallest change:* replace the clause with "and hand it to no one, government included, outside a process agreed in
advance". Then say plainly that agreeing that process is part of what the stop is for, as the page already half-says.

**2.3 The nearer danger is outside the ask, and the page calls it safe. (Serious; answered badly.)**
`MEMO.md` §2 has it right: "Encryption in use does not rest on P versus NP ... That is the nearer danger." Factoring,
discrete log and the lattice problems behind the new standards are not believed NP-hard. Aharonov and Regev show
approximating lattice problems "to within a factor of √n lie in NP intersect coNP", and a problem in NP ∩ coNP is not
NP-hard unless NP = coNP. So the ask ("fast algorithms for NP-complete problems") does not touch the attack class
already being demonstrated: HAWK in July, and a 7-round AES attack "between 200 and 800 times faster" than earlier
work (Anthropic's post, which also calls the AES attack "completely impractical"). Meanwhile the opening says HAWK
"put [nothing] at risk". A cryptographer will read that as missing the likely threat while aiming at the famous one.
*The honest answer is already on the page*: targeted breaks have somewhere to move (lattices to hash-based or code-based
signatures; factoring to lattices), so disclosure works there, as it did for HAWK (shared with the authors in June,
public with the results). Only the end of one-way functions leaves nowhere to go.
*Smallest change:* add after "That works because there is another cipher to move to": "That is why this ask leaves
targeted code-breaking to the field's disclosure norms. It covers only the one result that leaves nothing to move to."
Change "none of them put anything at risk" to "none of them left us without somewhere to go".

**2.4 The states problem. (Serious; answered badly.)**
"Today only the labs can do this." The page's own timeline shows that the closed group that found cryptographic
mathematics first was GCHQ, both times. A state has the money ($6–20M is nothing to it), the strongest motive to keep a
practical method secret, and, increasingly, access to frontier models through government deployments. The page should
not claim to reach states, but it has to say whether the line covers campaigns run *on a lab's models by customers*,
government customers included. If it does not, a lab can keep the letter of the line while a state runs the campaign
on its system.
*Smallest change:* one sentence in the ask: "This covers campaigns run on a lab's systems by anyone, its government
customers included." Or, if that is not wanted, say so and why.

**2.5 Fit with what cryptographers sign. (Mostly strong; one gap.)**
Per `research/letters_cryptographers_signed.md`, their letters are narrow, technical, concede the legitimate goal first,
and offer an alternative. The page does the first three. It offers no alternative path for the good it concedes (no
"labs may instead do X"). Listing what is allowed (change 2) is that alternative, and it costs one line.

**2.6 What this reader would accept as an exit.** There is no migration target that survives a practical method
(only one-time pads and quantum key distribution, as the page quotes Aaronson), so "after migration" is not an exit and
the page should not imply one. Real exits: a proof that one-way functions exist, or an agreed custody process for such
a result, with a named body, which would turn the stop into a protocol. Short of those, a fixed term with outside review.

---

## 3. The lab's policy lead

*Reads for: can this line be written into a published framework, kept at a cost the lab will bear, and checked by
someone outside the lab?*

**3.1 It cannot yet be written: no one could tell which side a project is on. (Most serious; answered badly.)**
"Campaign", "fast", "pointing their systems at this" and "relatives" are undefined. Labs use and improve SAT and
integer-programming solvers for verification and scheduling every day, and that is literally "fast algorithms for
NP-complete problems". `MEMO.md` §6 puts "everyday solver engineering" and "code-breaking done with defenders" outside
the line; the page says neither. A general mathematics agent that wanders into a satisfiability bound is not a
campaign by intent, but it may produce the result.
*Smallest change:* a three-part definition the framework can quote:
- *Out:* a directed project whose stated goal or success criterion is a polynomial- or quasi-polynomial-time algorithm
  for an NP-complete problem, a general average-case inversion of one-way functions, or a refutation of P ≠ NP.
- *In:* solver engineering on practical instances; lower bounds, including algorithms built for them; subexponential
  work; cryptanalysis of specific schemes done with their designers or a standards body.
- *Tripwire:* any system output that refutes a named conjecture on a short list goes to the second ask, whether or not
  anyone was aiming at it.

**3.2 It cannot be checked, and the page's history says that is how restraint fails. (Most serious; not seen.)**
The page: restraint that failed "was open-ended and asked of rivals who could not check one another." This ask is
both. Campaigns run on internal models; only successes are announced; failures and targets are invisible. What would
make it partly checkable:
- **A signed attestation in each framework update** ("no project of the excluded kind ran this period"), naming the
  officer who signed it. A false public statement carries risk.
- **An anonymous internal channel**: an employee who sees a breach can report it. California's SB 53, as summarised by
  the Future of Privacy Forum, already requires large frontier developers to "maintain anonymous reporting channels".
  It also says the published framework "must also assess catastrophic risk from internal use of models." I could not
  open the statute itself (the legislature's site refused the request), so whether a breach of this line would count as
  a reportable catastrophic risk is unverified.
- **Outside review of the list of campaign targets**, under confidentiality, by the panel in 1.6 and 2.6.
None of these proves a negative. The page should not claim more than "harder to break quietly". The MEMO already says
that ("a public line makes secret defection costlier").
*Smallest change:* one sentence in the ask naming the attestation and the reporting channel, and the history paragraph
saying which of its failure conditions this design answers.

**3.3 Unilateral abstention hands the prize to a rival. (Serious; not seen.)**
The page's opening is a list of the labs collecting famous problems, two of them Millennium Prize problems. P versus
NP is the most famous left. For one lab, the real cost of abstaining is not lost research. It is the prospect of a rival
announcing the result. No policy lead will write the line unless rivals write it too.
*Smallest change:* make the ask conditional and collective: "Each lab should commit, the commitment to bind once
[named labs] have made it." Say who "AI labs" means: at least the developers of frontier closed models *and* of
open-weight models, since an open release ends everyone's window (3.4).

**3.4 "Only the labs" has a short shelf life. (Serious; answered badly.)**
The money ($6–10M for the Navier–Stokes proof, $15–20M for the effort, by NPR's estimate) is within reach of any state
and many firms, so the barrier is the model. Epoch AI, 29 May 2026: "Since January 2026, the most capable open-weight
models have lagged frontier closed models by an average of four months". The UK AI Security Institute, 17 July 2026:
"recent open weight models lag frontier closed models' cyber capabilities by 4 to 7 months." Research mathematics at
the level of the opening results may lag by more. That is not measured, and the page should not guess. But "a stop
buys years" leans on the timeline of 1970s human rediscovery (4 to 16 years), which is not this setting.
*Smallest change:* "Right now the labs are the only ones who can find it. That will not last long, perhaps months
once open models catch up. Every month still counts, for the reasons above." Drop "buys years" or source it.

**3.5 The trade is never stated. (Moderate; not seen.)**
For a reader who thinks P ≠ NP (88% of the poll, 99% of those counted as experts), the strongest honest framing is one
the page never makes: *if you are right, the campaigns we ask labs not to run could never have succeeded at the
dangerous thing, so abstaining costs almost nothing you could have had; if you are wrong, it buys time and a chance to
settle custody.* It costs little exactly in the world most readers believe in. 1.1 is why "almost nothing" is honest
only once the line is drawn by running time; drawn by topic, the cost includes the lower-bound programme.
*Smallest change:* two sentences in "What we ask", or as a fourth reply ("Why should I sign if I think P ≠ NP?").

**3.6 What this reader needs as an exit.** A date and a decision-maker. Frameworks are already reviewed on a cadence
(annually under SB 53, per the FPF summary). The workable version: the line expires at the first framework review after
a fixed term unless the outside panel renews it, and it ends at once on a proof of P ≠ NP or of one-way functions. The
page's status line says the exit is undecided. Until it is decided, a policy lead will treat this as the 2023 pause
letter, as `MEMO.md` §6 warns.

---

## Leads from the brief: where each came out

- **The hash and the hunt**: right, and worse than the lead said (binding fails under the result). §2.1.
- **Is the harmless direction separable**: the memory was right (Williams, 2010 and 2011), with more besides
  (Abboud et al.; natural proofs). §1.1, §1.2.
- **Where the line is**: it cannot be told apart from solver work as written; a running-time criterion fixes most of it.
  §3.1.
- **Rivals who cannot check one another**: yes, this is that ask; partial remedies listed. §3.2, §3.3.
- **"Only the labs"**: the barrier is the model, and the window is months by current measurements. §3.4, §2.4.
- **The nearer danger**: yes, and the page already holds the answer (disclosure works where there is somewhere to move).
  §2.3; also the average-case point, §1.4.
- **The arithmetic**: the strongest honest framing, and the page lacks it. §3.5.
- **Exit conditions**: per reader, §1.6, §2.6, §3.6. They agree on one thing: a proof of P ≠ NP or of one-way functions
  ends it, and anything short of that needs a fixed term and an outside reviewer.

## Not checked

- I did not read the October ETH preprints, the published prompt, or the arXiv analysis of the crossover. I relied on
  the page and `research/` for those, by ruling.
- California SB 53: statute text refused (403); I quote the Future of Privacy Forum's summary only.
- Razborov–Rudich: I could not open the original (a certificate error on the author's site). Their result is quoted
  through Aaronson's survey, a primary source by a complexity theorist, and the CIKK abstract.
- Jahanjou, Miles and Viola tighten Williams's connection (arXiv abstract opened). I did not verify any claim that
  refuting SETH by itself yields lower bounds, and I make none.
- Whether research mathematics in open-weight models lags by the same four to seven months is unmeasured, as far as I
  found.
- The claim that frontier models are reaching state customers through government deployments is general knowledge;
  I opened no source for it.

## Sources (all opened for this file unless marked)

- R. Williams, "Improving Exhaustive Search Implies Superpolynomial Lower Bounds", preprint 4 May 2010 (STOC 2010; SIAM J.
  Comput. 2013). https://people.csail.mit.edu/rrw/improved-algs-lbs2.pdf (abstract quoted)
- R. Williams, "Non-uniform ACC circuit lower bounds", ECCC TR11-017. https://eccc.weizmann.ac.il/report/2011/017/
  (abstract: NEXP has a language not computed by quasi-polynomial-size ACC_m circuits). That it came from a satisfiability
  algorithm is as described in Aaronson §6.4.2.
- A. Abboud, T. D. Hansen, V. Vassilevska Williams, R. Williams, "Simulating Branching Programs with Edit Distance and
  Friends, or: A Polylog Shaved is a Lower Bound Made", arXiv 1511.06022. https://arxiv.org/abs/1511.06022
- S. Aaronson, "P =? NP" (survey, 2017). https://www.scottaaronson.com/papers/pnp.pdf: abstract ("a duality between
  impossibility proofs and algorithms"); §1.2 note 4 (Levin's universal search); §5.3 ("It would be laughable");
  §6.2 (natural proofs, "harder and harder ... easier and easier"); §6.4 ("Ironic Complexity Theory"); §6.4.2.
- M. Carmosino, R. Impagliazzo, V. Kabanets, A. Kolokolova, "Learning Algorithms from Natural Proofs", CCC 2016.
  https://www2.cs.sfu.ca/~kabanets/Research/natural-learning.html (abstract)
- R. Impagliazzo, "A Personal View of Average-Case Complexity", 1995. https://cseweb.ucsd.edu/~russell/average.ps
  (§2.2 Heuristica, §2.3 Pessiland, §2.4 Minicrypt)
- Y. Liu, R. Pass, "On One-way Functions and Kolmogorov Complexity", arXiv 2009.11514. https://arxiv.org/abs/2009.11514
- D. Aharonov, O. Regev, "Lattice Problems in NP ∩ coNP", 2005. https://cims.nyu.edu/~regev/papers/cvpconp.pdf
  (abstract). That NP ∩ coNP problems are not NP-hard unless NP = coNP is the standard consequence, my gloss.
- H. Jahanjou, E. Miles, E. Viola, "Local reductions", arXiv 1311.3171. https://arxiv.org/abs/1311.3171
- Anthropic, "Discovering cryptographic weaknesses", 28 July 2026.
  https://www.anthropic.com/research/discovering-cryptographic-weaknesses (consultation with "US government and industry
  leaders"; HAWK shared with authors "in June"; AES "between 200 and 800 times faster", "completely impractical";
  "it would be prudent to consider ...")
- L. Fortnow, "Should you reveal a P = NP algorithm?", 2014.
  https://blog.computationalcomplexity.org/2014/04/should-you-reveal-p-np-algorithm.html (his own plan: "I would first
  warn the Internet companies ... Then I would just publish the algorithm." It offers no priority mechanism.)
- Académie des sciences, "Règlement des plis cachetés", 6 July 2004, articles 66–68 and 66-1, 68-1, 68-4.
  https://www.academie-sciences.fr/pdf/archives/reglement_plis.pdf
- B. Laurie, A. Langley, E. Kasper, RFC 6962, "Certificate Transparency", 2013. https://www.rfc-editor.org/rfc/rfc6962
  ("publicly auditable, append-only, untrusted logs"; the model for routine, unlabelled commitments, which §2.1 says
  lose their value once a method exists)
- Epoch AI, data insight, 29 May 2026. https://epoch.ai/data-insights/open-closed-eci-gap
- UK AI Security Institute, blog, 17 July 2026.
  https://aisi.gov.uk/blog/how-far-behind-the-frontier-are-leading-open-weight-models-on-cyber
- Future of Privacy Forum, "California's SB 53: The First Frontier AI Law, Explained" (secondary; the statute at
  leginfo.legislature.ca.gov answered 403). https://fpf.org/blog/californias-sb-53-the-first-frontier-ai-law-explained/
- From the page's own sources, not re-opened here: Weart 1976 / Smyth (the 1940 dated papers), Ellis (GCHQ), NIST IR
  8547, NPR (cost), Gasarch (poll).

*Downloads were kept in the session scratch directory, one directory each, and read as data only.*
