2024/02/05 13:31
Status: #MOC
Tags:

# Adversarial  Search

## Types of Games

![[Pasted image 20240212122037.png]]

Choices: 

- Deterministic 
- Stochastic

### Deterministic

There are many possible formalizations here is one:

- States: S (statrt at $S_0$)
- Players: P={1...N} (usually take turns)
- Actions: A (may depend on player/state)
- Transition Function: SxA -> S
- Terminal Test: S -> {t, f}
- Terminal Utilities: SxP -> R

## Multi-agent Games

- Zero-Sum Games
	- Agents have opposite utilities (values on outcomes)
	- Lets us think of a single value that one maximizes and the other minimizes
	- Adversarial, pure competition

## Value of a State

The best achievable outcome (utility) from that state.

- Non-Terminal States:

	$$V(s) = \max_{s' \in \text{children}(s)} V(s')
$$
- Terminal States: 

	$$V(s) = known$$
## Adversarial Game Trees

![[Pasted image 20240212124145.png]]

In an adversarial game you apply the max function for the pacman state (in blue) and min function for the ghost state (in red). The reason is that you have to assume the adversary is wishing the worst for you and is playing optimally.

## Mini-max Values

![[Pasted image 20240212124517.png]]

---
