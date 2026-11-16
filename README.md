# QualeX — what the two Qualia repos found

**Compressed findings from [QualiaClaude](https://github.com/anttiluode/QualiaClaude) and [QualiaAstra](https://github.com/anttiluode/QualiaAstra), 16 November 2026.**

Antti Luode's idea · wave-body experiments by Claude Opus 5.5 (QualiaClaude) · engineered reference gates by Astra and Sol (QualiaAstra) · condensation by Claude Opus 5.5.

Pinned to QualiaClaude at `e8ab4e9` and QualiaAstra at `d173631`. Every number below comes from a pre-registered run in one of those two repos; the receipts are there.

## In one paragraph

Antti proposed that a quale might be a **shared prediction**: many units, each holding a small fading piece of history, together keep up one expectation of the world, and a token means whatever predicted consequences change when it is altered. In one day, 12 pre-registered experiments across two repos turned that into a precise structure, and the structure kept splitting the same way. A signal about the world has to exist in **two forms at once**:
- **content:** what is there;
- **residue:** what was not expected.

Every body that had only one of the two failed in exactly the way the other form would have fixed. That split, and the unit that would hold both, is what we have. None of the mechanisms is new on its own; the combination, the failure map and two properties of fade-triggered units are ours. Nothing here bears on whether anything is felt.

## 1. The picture

Three quantities, kept apart:

```math
\underbrace{W(t)}_{\text{what arrives}} \;=\; \underbrace{P(t)}_{\text{what the body expects}} \;+\; \underbrace{r(t)}_{\text{residue: where they disagree}}
```

- **One shared medium** holds $`W - P = r`$. When a learned expectation arrives on time, the medium goes quiet. Quiet is not empty: the expectation $`P`$ is still being produced. Astra's note: calling only the residue "the world inside" would lose the very thing the idea points at.
- **The expectation $`P`$ is shared.** Units of different kinds, hearing different senses, write into one medium and meet only there.
- **A token's meaning** is its causal role in $`P`$, measured by intervention.

## 2. Seven findings

### 2.1 Local units in a shared medium can revise one expectation coherently

**Experiment:** QualiaClaude, round 1. Two hidden worlds (A then B, or A then C) that A alone cannot tell apart. A tone on a second sense says which world it is. Three banks of fade-triggered units meet only in one wave field.

| Cue | Expects B | Expects C |
|---|---:|---:|
| A alone | 0.28 | 0.18 |
| A + tone 1 | **0.74** | **−0.01** |
| A + tone 2 | 0.22 | **0.73** |

- **The revision is coherent.** The tone raises one world and withdraws the other at once, at places the tone units never sense: 16 of 16 bodies, and 0 of 16 with uninformative tones.
- **Swapping the tone banks reverses it**, in 16 of 16.
- **The wrong tone is worse than no knowledge.** World B arriving after the wrong tone leaves 135% of its wave, against 51% with no tone and 32% with the right tone.
- **Tokens are readable by removal.** Early units mean "something is coming"; units firing 32–36 frames after the tone mean "B"; later ones mean **"not C"**. Withdrawal is a token of its own.

**Limit:** the revision is additive. The tone units add a correction, and the wave-hearing units never change their minds.

### 2.2 A medium of anti-waves carries surprise, not expectation

A body that cancels the world in one field leaves $`W - P`$ there. A population listening to that field hears silence when the prediction is right, and an inverted wave when the world is absent. **It can never pass an expectation on.**

The fix in [chain/](https://github.com/anttiluode/QualiaClaude/tree/main/chain) was a second field that holds $`P`$ with a positive sign; branches learn from $`P - W`$ at their tips. By superposition this is not an added organ: the second field is the canceller's own state, split off. In a neuron the split corresponds to basal input (the world) and apical tuft (the prediction). We reached it because the physics forced it, not by copying the cortex.

With it, a body learned two signed relations by itself and passed a clue about A two steps, through its own **imagined** B, to an expectation of C: step one at 0.69 of Bayes (16/16 right sign), step two at 0.24 (13/16). Cutting the imagined-B units removed 79% of step two; reversing them flipped it in 14 of 16.

### 2.3 Learn from the residue, not from similarity: explaining away

A branch can learn by comparing its own contribution with the world (similarity, Hebbian-like) or by explaining what the other branches leave (residue, LMS). They settle at

```math
w_{\text{sim}} \propto p, \qquad w_{\text{res}} = R^{-1}p,
```

where $`p`$ is the correlation of each candidate with the target and $`R`$ the correlation between candidates. The two rules agree when $`R`$ is nearly diagonal. **That is why Sol's Gate 4 came out a tie** (12/12 routes found by every learner; residual advantage 0/12): one clean route has no redundancy.

They come apart on the Markov screen. Given B, A says nothing more about C, so the right direct A → C weight is 0, even though A alone correlates with C at 0.49.

| [screen/](https://github.com/anttiluode/QualiaClaude/tree/main/screen), 16 bodies | Residual | Similarity | Correct |
|---|---:|---:|---:|
| A's share of the C prediction | **0.011** | 0.445 | 0 |
| B's strength | 0.90 | 2.06 | 1 |

Residual was smaller in 16 of 16 bodies (p = 1.5·10⁻⁵). Similarity double counts and predicts C at twice its strength. Sol's Gate 7 reproduced the split in an engineered linear surrogate (direct weight 0.025 against 0.496) and showed honestly that ordinary least squares ties the residual rule exactly. The rule is known mathematics; what matters is that **a local branch rule on a wave tip can implement it.**

The price: a screened body, given A alone, predicts almost nothing about C. Screening off the shortcut means the information must travel through an imagined B.

### 2.4 A predictor's clock must not be reset by the event it predicts

This finding is specific to fade-triggered units. The A-units are clocks: armed by A, they fire when their trace has faded to a threshold. When B had the same sign as A, B's own wave recharged the slow clocks before they fired. They learned on a clock about one gap late, then ran early at test, when A came alone.
- 6 to 9 of the 12 A-units per body were really timing from B.
- A **latch** (once the trace starts to fall, nothing can recharge it until it fires) fixed this. Reset clocks went to 0 in all 8 affected bodies, and step two's sign went from 13 of 16 right to 16 of 16. The type that had failed (B copies A, C flips B) went from 1/4 to 4/4.

It exposed a loop that any "only surprise reaches the state" design will meet:

```math
\text{weak prediction} \rightarrow \text{state gets reset} \rightarrow \text{weak learning} \rightarrow \text{weak prediction}
```

The residue protects the held state only when the prediction is already good, so early learning needs protection by force.

### 2.5 Imagination that looks like evidence loses its confidence

In [relay/](https://github.com/anttiluode/QualiaClaude/tree/main/relay), the B-units hear a real B when the eyes are open and the body's imagined B when they are closed. **The same units serve perception and imagination.**

| Eyes closed, A alone → C | Fraction of Bayes |
|---|---:|
| Soft imagined B (wakes the clocks 10–23 frames late) | 0.45 |
| Imagined B regenerated into a sharp real-B shape | 1.03 |
| The same, at a weaker A → B reliability | **1.83** |

The 1.03 was two errors cancelling. A sharp event claims certainty, overstating by $`1/0.70`$, while the B → C weight was learned to only 0.81. When the reliability changed, the overshoot showed. Carrying confidence in the spike's size made calibration worse in 11 of 16 bodies.

Astra and Sol isolated the same problem from the engineered side:
- **Gate 5:** an imagined B carries the same signed value as a real one, but only real B is fresh evidence. Given an explicit source bit, a learner stops counting its own echo.
- **Gate 6:** without the bit, the source can be read from the waveform's shape when the simulator builds it in. Accuracy was 93.5% for cable-like shapes and 68.2% for a subtler spike-shape analogue.
- **Open:** *source* identity (real or imagined) is not *event* identity. Eight copies of one echo still look like eight events.

### 2.6 Keeping the expectation in the dendrite keeps the confidence, at a cost

Antti's rule, tested in [innovation/](https://github.com/anttiluode/QualiaClaude/tree/main/innovation): what a neuron expects cancels in the dendrite, and only the residue reaches the soma and spikes.

```math
B \;=\; \underbrace{\hat B(A)}_{\text{held in the dendrite}} \;+\; \underbrace{r_B}_{\text{becomes the spike}}
```

This is the innovation form of a Kalman filter, and the core of predictive coding. The direct A → C path comes back legitimately as the prior, $`(2q_1-1)(2q_2-1)`$, because B's spike now carries only what A did not predict.

| | Reliability 0.85 (Bayes 0.49) | Reliability 0.70 (Bayes 0.28) |
|---|---:|---:|
| Innovation, eyes closed | **0.83 of Bayes**, 16/16 | **0.88 of Bayes**, 16/16 |
| Regenerated imagined B, eyes closed | 1.03 | 1.83 |

- **Confidence survives as state.** When the first link gets less reliable, the prediction drops to 0.61 of its earlier value; Bayes says 0.57.
- **It is quiet when the world agrees.** B-units fired 0 of 12 on confirmation and 12 of 12 on contradiction.
- **Its costs:** a confirmed B sends nothing, so C rests on the prior alone. A contradiction pulls C to about zero but does not flip it (11 of 16 against the 14 required). Imagined steps cannot be chained.
- **Surprise is coded as delay.** A fade-triggered unit fires *later* the larger its input was. A contradiction's spike came about 25 frames after a confirmation's and missed the window its weights were learned on. In these units, "how surprising" becomes "when".

### 2.7 Meaning by intervention needs two different removals

From Astra's Gate 1:
- **Removing a unit's output** from the summed expectation changes only the drawing.
- **Cutting or reversing a message** changes what the *other* units believe.

QualiaClaude's token readings (2.1) were the first kind. A token's full meaning includes the second. Gate 1 also showed that a system can know every relation between its parts and still not know which of two mirror-image worlds it is in, until one local clue fixes the whole at once: meaning as relation, with the absolute part supplied by one piece of evidence.

Caveat from Claude's re-check: on Gate 1's task a one-line rule (the clue's sign multiplied along the chain) scores 0.1729 against belief propagation's 0.1723. The task did not make message passing necessary.

## 3. The compression: content and residue

The two families of bodies are two halves of one unit:

| | Relay (sends content) | Innovation (sends residue) |
|---|---|---|
| What B-units send | what B **is** | B minus what was expected |
| B seen, agreeing | carries C | silent; C on prior only |
| B contradicting | C follows B, 16/16 | C pulled to zero, not flipped |
| Eyes closed | confidence lost (1.83× Bayes) | calibrated (0.83, 0.88) |
| Imagination vs evidence | indistinguishable | kept apart by construction |
| Chains imagined steps | yes | no |

Each column fails exactly where the other succeeds. Both bodies already **learn** from the residue at their branch tips. The difference is only in what they **send**.

Marvan & Phillips (2024), *Cellular mechanisms of cooperative context-sensitive predictive inference*, argue the cortical side of this. Pyramidal cells transmit feedforward content, and apical context **amplifies** it when it agrees and attenuates it when it does not. They reject subtractive coding, mainly because subtraction leaves no output when prediction and input agree. Our innovation body measured that cost (C on prior only), and our relay body measured the cost of content without a gain (confidence lost).

**The unit that holds both**, stated as a proposal (Claude's reading; not shown by them or by us). It learns from the residue, sends content, and sets the content's gain from context. Under exact inference the gain is forced:

```math
E[s_B \mid s_A, b] \;=\; \frac{m_A + m_b}{1 + m_A\, m_b},
\qquad m_A = (2q_1-1)\,\rho_1\, s_A,\quad m_b = (2r-1)\, b
```

Here $`b`$ is the observed B and $`r`$ its reliability.
- **Context agreeing** ($`m_A m_b > 0`$) raises the estimate above what B's evidence gives alone: amplification. With $`m_A = m_b = 0.7`$ it is 0.94.
- **Context disagreeing** lowers it: attenuation, to 0 in the symmetric case.
- **Perfect evidence** ($`r = 1`$) gives exactly 1 whatever the context. In a clean world the right gain is 1, and amplification there would count A twice.

So apical amplification and precision weighting are the same thing in Bayes terms. Context gain is how a prior is mixed into **uncertain** evidence. Every QualiaClaude body so far saw B perfectly, so none of them could need a gain.

The full target unit is therefore:
- **learning** from the residue at each branch tip (2.3);
- **holding** the expectation as state, apart from the medium (2.2, 2.6);
- **a latched clock** while learning (2.4);
- **sending** content, scaled by agreement between context and evidence, and by the evidence's reliability (this section).

## 4. Ledger

**Shown** (pre-registered, passed):
- coherent cross-sense revision of a shared expectation, 16/16 (2.1);
- a learned two-step causal chain through an imagined middle event (2.2, claim 1);
- residual learning screens off a redundant route, 16/16 (2.3);
- clock reset is the cause of the chain's sign failures, and the latch fixes it (2.4);
- the engineered gates 1, 3, 5, 6 and 7 in QualiaAstra, and Gate 4's route recovery (12/12), each with its listed caveats.

**Not shown** (missed a pre-set condition):
- a chain as strong as Bayes through an imagined B; the best step two without regeneration was 0.45 of Bayes (relay), 0.43 in chain/ with Gemini's fixes;
- relay at half of Bayes with a soft imagined B (0.45);
- regenerated imagination calibrated (1.03 is cancelling errors);
- innovation beating relay body by body (11/16 against 12);
- a contradiction flipping C under innovation (11/16 against 14; predicted).

**Failed:**
- residual advantage on a single clean route (Gate 4, 0/12; expected from the maths);
- Gemini's leak explanation of the chain's failing type (the cause was the clock);
- confidence carried in spike size;
- "graded" imagination (0.22 of Bayes);
- timing of a "Hebbian childhood, then pruning" (1/4);
- an apical residue input as a substitute for the latch, because the imagined B was too weak to cancel the real one.

## 5. Known, and ours

**Known mechanisms used:**
- the adaptive canceller (Widrow et al. 1975);
- negative images in electric fish (Bell);
- the Kalman innovation and predictive coding (Rao & Ballard 1999);
- belief propagation on a chain (Pearl);
- least squares as explaining away;
- greedy residue selection as matching pursuit (Mallat & Zhang 1993);
- apical amplification (Larkum; Phillips).

**Ours:**
- all of these combined in fade-triggered units on a wave field, learning by local rules;
- the full content/residue failure map of section 3, measured on the same bodies;
- **clock reset** by the predicted event, and the latch;
- **surprise coded as delay** in fade-triggered units;
- the reading of amplification as forced precision weighting, offered as a proposal.

## 6. What this does not touch

Every result here concerns the **structure** of a shared prediction: how it is held, revised, relayed and read. None of it can tell a system that experiences from one that only computes the same predictions. Antti's candidate is stated precisely now. Whether it is sufficient for experience is exactly as open as it was this morning.

## 7. The one open test

Give B noise: sometimes its sign is wrong and its strength varies. Exact Bayes then fixes the gain on B for agreeing, contradicting and absent B at each noise level (section 3). On the same bodies, compare three kinds of B-unit:
1. **subtractive:** innovation as it is;
2. **content only:** relay as it is;
3. **content with gain:** relay, with B's ping scaled by agreement between the observed B and the dendrite's own prediction.

If the gain version wins only when B is noisy, and does nothing or harm when B is clean, the two-form unit of section 3 is supported in this model rather than adopted from a paper.

## Sources

**Repositories**
- [QualiaClaude](https://github.com/anttiluode/QualiaClaude) at `e8ab4e9`: round 1, [chain/](https://github.com/anttiluode/QualiaClaude/tree/main/chain), [screen/](https://github.com/anttiluode/QualiaClaude/tree/main/screen), [relay/](https://github.com/anttiluode/QualiaClaude/tree/main/relay), [innovation/](https://github.com/anttiluode/QualiaClaude/tree/main/innovation)
- [QualiaAstra](https://github.com/anttiluode/QualiaAstra) at `d173631`: Gates 1–7, [live viewer](https://anttiluode.github.io/QualiaAstra/)

**Lineage**
- [StateShapedPingRecall](https://github.com/anttiluode/StateShapedPingRecall) (damping rule)
- [PerceptionLabAI](https://github.com/anttiluode/PerceptionLabAI) and [GeometricNeuronV30](https://github.com/anttiluode/GeometricNeuronV30) (fade-triggered units)
- [Genealogy](https://anttiluode.github.io/Genealogy/)

**Paper**
- T. Marvan and W. A. Phillips, "Cellular mechanisms of cooperative context-sensitive predictive inference", *Current Research in Neurobiology* 6 (2024) 100129.

MIT licence.
