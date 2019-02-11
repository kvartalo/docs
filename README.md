# kvartalo - docs
cryptocurrency system for neighbourhoods

## Disclamer
This document is an ongoing process, that will be improved through collective debates and consensus.

## Naming
- `eur` is euro
- `kvt` is the `kvartalo` token
- `entity` / `entities` are the organizations/associations that participate

## Economics
- value 1:1 with `eur`
	- tokenized `eur`s
	- with possibility to unlink the value from `eur` in the future, but for the moment is a fixed rate
- token creation
	- each entity that will participate in the experiment, says which quantity of `eur` will be able to block
	- each entity 'blocks' / 'frozes' that quantity of `eur`, and receives that quantity in `kvt`. That action is a trusted action, as the entity is a trusted entity by the ecosystem
		- in this way, all the `kvt` quantity of the ecosystem will be backed up with `eur`
	- to adquire `kvt` people can go to one of the entites that participate in the experiment, changing their `eur` for `kvt`
	- a person that have `kvt` will be always able to change them back to `eur`
- a multisig owned by the different entities manages the suply of `kvt`
	- when a new entity want to go in, will hold the `eur` and will receive the same quantity in `kvt` that are created (minted) by that multisig
- no money value is created in any moment. All the `kvt` are 'tokenized `eur`', in other words, the `kvt` are representations of real `eur`
	- all the inputs and outputs are always equal

## Tech
- deployed over a Ethereum PoA

More details in https://github.com/kvartalo/docs/blob/master/TechnicalDetails.md

### Components
- [token](https://github.com/kvartalo/token)
- [relay](https://github.com/kvartalo/relay)
- [web-wallet](https://github.com/kvartalo/web-wallet)

## Usability tradeoffs for the first version
- common addresses limited to maximum of 20`kvt`
	- it's a low amount for the first phase of the experiment
	- to avoid acumulation and risks
	- 20`eur` is a typical amount that people have in their pockets in a 20`eur` bill format
- shop addresses will be able to hold more `kvt`, as they will need to accumulate the transactions of the payments
- a proposal could be that the products selled in `kvt` will have some kind of % discount, to incentivize the use of `kvt` instead of `eur`

## Governance
- for each transaction, there is a 1% fee
- each month, the people using their wallet will be able to vote in which social cause will go the fees of that month
- in this first phase, to avoid cheating, only addresses with more than a threshold `kvt` amount during X window time, will be able to vote
- `kvt` from fees will go directly to the address decided in the votation

