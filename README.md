# Nice to have

- [ ] Differentiate better between safety training methods and post-processing attacks
    - Both could be trained to work with context, but with post-processing this would be faster to achieve, more transparent, and easier to update.

> (10) so much rests on figure 1, it'd be great to have a more detailed figure describing how you want to embed risk tiering into models in the appendix. 

- [ ] Maybe add a diagram: x-axis apparent harmfulness, y-axis actual harmfulness (binary). Dots=requests are a diagonal continuous cluster. Ideal safety method: cuts horizontally. Non-contextual safety methods: cut vertically. Access controls: not ideal, but at least diagonal. Can show gray zone, can show dark-gray. Decomposition attacks move one dot from the right to many dots on the left of some vertical content-based safety method. Context-faking attacks move the dot down; 

# Intro

- [ ] Make it clear what a grey zone question is: a question that could be both good or bad, depending on who is asking and why. 
    - Keeping everything else fixed and improving jailbreaking resilience or resilience to prompt injections won't help us, because if we reject the question, SOMETIMES that will be right, but SOMETIMES that will be wrong. We NEED the context.
    - Decomposition attacks are only there to illustrate the severity of the problem. If grey-zone questions are always let through, attackers will exploit this to decompose their black-zone questions to multiple grey-zone ones.
    - Dilemma: when faced with a grey-zone question, do we reject it or do we answer it?
- [ ] Talk more about government and industry incentives: both want more granularity to enable both more capabilities and more safety at the same time!
- [ ] Explain what kinds of models we are targeting (LLMs, not small specialized models)

# Reviewer Notes

> (8) Would developers actually go along with granting verified users deeper access? Many have refused to do this in the past.

- [X] Add developer incentives analysis addressing historical reluctance, regulatory pressure, and competitive advantages of surgical vs. blanket restrictions (~0.2 pages)

> More could be said about potential solutions to legal/ethical challenges arising from access controls. The use of a credential-based access control system opens many questions that, although mentioned in some places, ought to be further explored: How can we prevent such a system from further entrenching disparities in knowledge access? And so on.

> (11) leaving tradeoffs to the conclusion is not best, would address at least e.g. privacy earlier.

Expand discussion in Section 5 (System Limitations and Tradeoffs):

- [X] Add privacy discussion covering data retention, anonymization, and surveillance concerns (~0.2 pages)
- [X] Add governance and equity discussion addressing institutional bias, alternative credentialing pathways, and oversight mechanisms (~0.3 pages)



> As mentioned in the paper, the primary technical approach of gradient routing for addressing the capabilities gap has not been empirically validated, and this is an important consideration for feasibility.

> I think the paper would be better served by either focusing exclusively on access controls (and perhaps just a brief discussion of gradient routing as a possible means of implementation). As it stands, the scope seems too broad for a short paper, and some doubts are left unanswered on both fronts.

Make this less about gradient routing:

- [X] Restructure Section 4 (Technical Implementation Options) to briefly present gradient routing as one implementation option among several (post-processing, hybrid approaches), emphasizing other good implementation paths exist (~0.2 pages)

> The authors do mention that avoiding false positives and false negatives may nonetheless be a problem for gradient routing, but that "regularization techniques and adjusted detection thresholds, respectively, could mitigate these issues" - expanding on this further could be valuable.

Improve the presentation of gradient routing in Section 4:

- [X] Add mention of UNDO as one way to enable good separation of things.
- [X] Detail how the main problem is the one of classification and point to an existing body of work that says classification is possible.

> What counts as basic identity confirmation? Uploading an ID photo? 

> What possible governance structures could most effectively oversee credentialing?

> is institutional affiliation a sufficient indicator of responsible use?

- [X] Expand verification levels with specific examples of identity confirmation methods and institutional verification processes (~0.2 pages)
- [X] Add details about how the credentialing would work to 3.2.
- [X] Add defense information to 3.3 about the feasibility of the proposed credentialling setup.
- [X] Add defense of institutional affiliation to 3.3.

> If the authors were to instead place the central focus on gradient routing as a means to achieve access controls, it would be especially interesting to show some kind of validation or provide arguments that such techniques could effectively modularize the relevant level of technical sophistication in a domain - e.g., achieve routing of only advanced virology, but not basic virology. 

> While some problems such as verification/risk categories are intentionally written out of scope, which is reasonable, more could be said on feasibility of this as it is pertinent to the feasibility of the overall proposal of stratified access controls.

> Leaving false positives as an exercise for the reader is not ideal -- this seems like a central issue with the proposal. 

> Second, the dual use dilemma is dual - it is not just about preventing misuse, but also about enabling positive use. It does not seem true that "In practice, harmless content would require no verification, preserving frictionless experience for everyday queries" because identity verification and KYC introduce friction, so there would be fewer users who would go through with those checks. Raising how this can help models not overrefuse in more depth is a necessary part of the paper.

- [X] Expand false positives discussion with theoretical analysis of precision-recall tradeoffs, comparison to other safety systems, and graduated response strategies (~0.3 pages)
- [X] Address in Section 3.3 that 1) only a small portion of users actually use the models in ways that are risky (point to Anthropic's studies), and 2) the false positive rates would likely be quite small, which means only a small portion of a small portion of users would be hit.

> Many if not most GPAI system providers base responses not only on a user's immediate prompt, but also on their chat history. This provides plenty of additional context that could be used for a refusal (e.g. of a grey zone request). OpenAI's instruction hierarchy is another framework (though maybe this is grouped in with postprocessing in your eyes), as is Anthropic's constitutional classifiers; model specs are another. Enhanced logging is brought up at the end of section 3 but seems like a major area; e.g. background logging introduces surveillance risks.

> (4) Is it true that model providers can't refuse grey zone requests? OpenAI and Google make use of chat history by default. 

- [X] Expand Section 2 to explicitly address (and Explain why none of them fully address the trustworthy context problem):
    - [X] chat history
    - [X] model specs
    - [X] instruction hierarchies
    - [X] constitutional classifiers
- [X] Maybe show an actual example, at least in the appendix?

> "address address" - typo on p1 

- [X] Fix the typo.

> (5) For unlearning I would also take a look at Cooper et al. https://arxiv.org/abs/2412.06966 which also do a good job on this 

- [X] Cite Cooper in Section 2.1.

