# Reviewer Notes

> As mentioned in the paper, the primary technical approach of gradient routing for addressing the capabilities gap has not been empirically validated, and this is an important consideration for feasibility.

> I think the paper would be better served by either focusing exclusively on access controls (and perhaps just a brief discussion of gradient routing as a possible means of implementation). As it stands, the scope seems too broad for a short paper, and some doubts are left unanswered on both fronts.

Make this less about gradient routing:

- [ ] Restructure Section 5 (Technical Implementation Options) to briefly present gradient routing as one implementation option among several (post-processing, hybrid approaches), emphasizing other good implementation paths exist (~0.2 pages)

> If the authors were to instead place the central focus on gradient routing as a means to achieve access controls, it would be especially interesting to show some kind of validation or provide arguments that such techniques could effectively modularize the relevant level of technical sophistication in a domain - e.g., achieve routing of only advanced virology, but not basic virology. 

> The authors do mention that avoiding false positives and false negatives may nonetheless be a problem for gradient routing, but that "regularization techniques and adjusted detection thresholds, respectively, could mitigate these issues" - expanding on this further could be valuable.

Improve the presentation of gradient routing in Section 5:

- [ ] Add mention of UNDO as one way to enable good separation of things.
- [ ] Detail how the main problem is the one of classification and point to an existing body of work that says classification is possible.

> While some problems such as verification/risk categories are intentionally written out of scope, which is reasonable, more could be said on feasibility of this as it is pertinent to the feasibility of the overall proposal of stratified access controls.

> What counts as basic identity confirmation? Uploading an ID photo? 

> (8) Would developers actually go along with granting verified users deeper access? Many have refused to do this in the past. 

> Leaving false positives as an exercise for the reader is not ideal -- this seems like a central issue with the proposal. 

Expand discussion in Section 4.1 (Implementation Feasibility) — main goal is showing the approach is **feasible**:

- [ ] Expand verification levels with specific examples of identity confirmation methods and institutional verification processes (~0.2 pages)
- [ ] Add developer incentives analysis addressing historical reluctance, regulatory pressure, and competitive advantages of surgical vs. blanket restrictions (~0.2 pages)
- [ ] Expand false positives discussion with theoretical analysis of precision-recall tradeoffs, comparison to other safety systems, and graduated response strategies (~0.3 pages)

> More could be said about potential solutions to legal/ethical challenges arising from access controls. The use of a credential-based access control system opens many questions that, although mentioned in some places, ought to be further explored: is institutional affiliation a sufficient indicator of responsible use? What possible governance structures could most effectively oversee credentialing? How can we prevent such a system from further entrenching disparities in knowledge access? And so on.

> (11) leaving tradeoffs to the conclusion is not best, would address at least e.g. privacy earlier.

Expand discussion in Section 4.2 (System Limitations and Tradeoffs):

- [ ] Add governance and equity discussion addressing institutional bias, alternative credentialing pathways, and oversight mechanisms (~0.3 pages)
- [ ] Add privacy discussion covering data retention, anonymization, and surveillance concerns (~0.2 pages)

> Many if not most GPAI system providers base responses not only on a user's immediate prompt, but also on their chat history. This provides plenty of additional context that could be used for a refusal (e.g. of a grey zone request). OpenAI's instruction hierarchy is another framework (though maybe this is grouped in with postprocessing in your eyes), as is Anthropic's constitutional classifiers; model specs are another. Enhanced logging is brought up at the end of section 3 but seems like a major area; e.g. background logging introduces surveillance risks.

> (4) Is it true that model providers can't refuse grey zone requests? OpenAI and Google make use of chat history by default. 

- [ ] Expand Section 2 to explicitly address chat history (noting it can be disabled on the user side), instruction hierarchies, constitutional classifiers, and model specs as existing contextual approaches (~0.3 pages). Explain why none of them fully address the trustworthy context problem.
- [ ] Maybe show an actual example, at least in the appendix?

> Second, the dual use dilemma is dual - it is not just about preventing misuse, but also about enabling positive use. It does not seem true that "In practice, harmless content would require no verification, preserving frictionless experience for everyday queries" because identity verification and KYC introduce friction, so there would be fewer users who would go through with those checks. Raising how this can help models not overrefuse in more depth is a necessary part of the paper.

- [ ] Address in Section 4.1 that 1) only a small portion of users actually use the models in ways that are risky (point to Anthropic's studies), and 2) the false positive rates would likely be quite small, which means only a small portion of a small portion of users would be hit.

> "address address" - typo on p1 

- [X] Fix the typo.

> (5) For unlearning I would also take a look at Cooper et al. https://arxiv.org/abs/2412.06966 which also do a good job on this 

- [X] Cite Cooper in Section 2.1.

> (10) so much rests on figure 1, it'd be great to have a more detailed figure describing how you want to embed risk tiering into models in the appendix. 

- [ ] **Modify Figure 1** to show general access control framework rather than gradient routing specifics (since Section 5 will present multiple technical options)
