# Cost-sharing mechanism research for MEV-Boost relays.


### Introduction to MEV-Boost

MEV-Boost is an implementation of proposer-builder separation (PBS) built by Flashbots for proof of stake Ethereum. A summary of MEV-Boost is a protocol that allow validators maximize their staking reward by selling blockspace to an open market of builders.

MEV-Boost formalizes the separation of block construction from block proposal, a process that was previously unified in Ethereum's PoW mechanism. This separation is crucial for enhancing network decentralization and efficiency. There are three key identities in the MEV-Boost:

- **Builders (Buyers of Blockspace)**: Builders are responsible for constructing blocks. They collect transactions from the transaction pool, arrange them in a block, and then bid for their proposed blocks to be included in the blockchain. Builders can include strategies to maximize MEV (Maximal Extractable Value) opportunities, which involves reordering, inserting, or censoring transactions to profit from the differences in state that transactions create.
- **Validators (Sellers of Blockspace)**: In a PoS system, validators replace miners from the PoW system. Validators are responsible for choosing which block to add to the blockchain. With MEV-Boost, validators receive block proposals from relays and decide which one to include in the blockchain. 
- **Relays (Auctioneers)**: Relays act as intermediaries between builders and validators. More precisly, Relays are a doubly-trusted data-availability layer and communication interface between builders and validators. Relays are trusted by builders for fair payload routing, and trusted by proposers for block validity, accuracy, and data availability.

MEV-Boost allows validators selected to propose blocks (i.e., proposers) to access blocks from a builder marketplace through trusted intermediaries, known as relays, via MEV-Boost auctions. In MEV-Boost auctions, builders compete for the right to build blocks auctioned off by proposers by submitting valid, EVM-compatible blocks alongside bids to relays. Bid values represent block rewards, and include priority fees from user transactions pending in the public mempool, as well as searchers’ payments for bundle inclusion, indicative of the amount of MEV opportunities created by user transactions or by off-chain signals.

The builders have incentives to participate in the auction since they can capture the difference between the value that they extract from the block and the bid. The validators have incenties to participate in the auction since they at least obtain base reward per block, potentially increasing their revenue. However, currently there is no economic incentive to run the relay, incurring operating cost of more than $100.000 dollars per year.

Different solutions have been proposed to incentivize Relays, see:

- [The Pursuit of Relay Incentivization](https://mirror.xyz/0xE21b1e6f471EDeF18264e9BBe51b7fA7643EE6B5/0Sh7BDW7qgH_nadfqF8bpmnjxnfoYzPFvRdmoIoi9mg)
- [PBS-Guild](https://collective.flashbots.net/t/pbs-guild-proposal-v3-wip/2223)
- [Competitive & Sustainable Relay Market](https://docs.google.com/document/u/0/d/1hFVw1dIIfLqFyRM8qPZfRdAc7FCnyDLuKGRZZqFj3rs/mobilebasic?pli=1)


Notation

- $[n]=$ Set of builders
- $[m]=$ Set of relays
- $b^j_i(t)$ is the highest bid made at time $t\geq0$ by the builder $i$ to the relay $j$.
- $b^j(t)=\text{max}\{b^j_i(t): i\in[n]\}$.
- $t_{f}$ last time where the validator can accept a bid from MEV-Boost.
- $h(t)=$ all bids history
- $b^\star(t) = \text{max}\{b^j(t):j\in[m]\}$ and $j^\star = \text{argmax}\{b^j(t):j\in[m]\}$.
- $b'(t) = \text{max}\{b^j(t):j\in[m]\setminus\{j\}\}$

The solutions proposed can be summarized as follows:

- **Procurment auction**: Every relay $j$ posts a cost parameteter $c^j(t_f,h(t))$ asociated to relaying a block to the validator. This cost parameter $c^j(t_f,h(t))$ is choosen by the relay, taking into account the information it has about the bids observed by the validators, other relays, its costs, etc. The validator chooses the block with highest payment, that is, at the end of the auction, the validator pics $p^\star\in\text{argmax}\{b^j_i(t_f)-c^j:j\in[m]\}$. The validator gets paid $p^\star$ and the relay gets paid $c^j$.
- **Second-price latency auction**: Validator accepts the block with highest bid and gets paid $b'(t_f)$. The relay gets paid $b^\star(t_f)-b'(t_f)$.
- **Subscription fee for validators (builders)**: Relays post the cost of providing the service. They run a cost-sharing mechanism that determinates which validators (builders) have access to the relay and how much they have to pay. By default, all builders (validators) hace access to relay. 



### Subscription fee mechanisms





### Main objective

The objective of the mechanism should be to maximize social-welfare of builders, validators and users having as non-deficit relays as a constraint. Moreover, we would like to do so in a prior-free setting. 




### Open questions

- What is the worst-case welfare of a non-deficit mechanism for public excludable goods with private and public interdependent valuation?
- What if we add positive and negative externalities?
- How do we define false-name strategies when the valuations are interdependent? Can we lower bound the worst-case welfare of a non-deficit mechanism that is Sybil-proof, or at least, Sybil-proof invariant?
- Can we tokenize and use constant function market maker to mimic the cost-sharing mechanism?

### Partial answers

For public interdependent valuations, the worst-case social cost is $\mathcal H_n$, by considering the potential mechanism with interdependent valuations.
