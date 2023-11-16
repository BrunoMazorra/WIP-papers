# Cost-sharing mechanism.


In light of the challenges posed by MEV-Boost relays, as detailed in the article on [The Pursuit of Relay Incentivization](https://mirror.xyz/0xE21b1e6f471EDeF18264e9BBe51b7fA7643EE6B5/0Sh7BDW7qgH_nadfqF8bpmnjxnfoYzPFvRdmoIoi9mg) and further explained in the context of cost-sharing mechanisms in [Interdependent Public Projects](https://epubs.siam.org/doi/epdf/10.1137/1.9781611977554.ch18), a deeper exploration into innovative funding solutions is warranted. The research highlights the complexity of cost-sharing mechanisms, especially under conditions where valuations are not privately independent but interdependent, as is the case with validators and builders in the MEV-Boost relay network. These interdependencies, along with potential externalities on validators, users, and builders, underscore the need for developing mechanisms that not only address the no-deficit goal but also account for public and private interdependent valuations and welfare maximization. This approach becomes crucial when considering the competitive nature of block auctions in the MEV ecosystem, where access to relay sets can significantly impact builders' and validators' profits. The predictive nature of agents regarding future MEV, which is a common asset like oil in auctions, further adds to the valuation interdependencies. Consequently, studying non-deficit cost-sharing mechanisms in this context is vital for addressing the unique challenges presented by the MEV-Boost relay network.

### Open questions

- What is the worst-case welfare of a non-deficit mechanism for public excludable goods with private and public interdependent valuation?
- What if we add positive and negative externalities?
- How do we define false-name strategies when the valuations are interdependent? Can we lower bound the worst-case welfare of a non-deficit mechanism that is Sybil-proof, or at least, Sybil-proof invariant?
- Can we tokenize and use constant function market maker to mimic the cost-sharing mechanism?

### Partial answers

For public interdependent valuations, the worst-case social cost is $\mathcal H_n$, by considering the potential mechanism with interdependent valuations.
