2024/02/14 11:09
Status: #idea
Tags:

# Compensating for Uncertainty

The main comparison is adversarial vs. uncertainty. This is because with an adversary you can assume that the opponent is playing optimally which means you know which move they should make next in order to win. With uncertainty in mind you have to assume the player will be taking chances so the node that represented an adversary becomes a chance node.
### Adversarial

![[Pasted image 20240214112133.png]]

pointy arrow
### Uncertainty

![[Pasted image 20240214111954.png]]

circle

## Worst-Case vs. Average Case

Instead of calculating worst case like in adversarial,
Calculate the average of both chance nodes. Average Case will be 54.5. When you compute the average expect to receive some values that you will never see in the game. Like once you move to the chance node on the right you will find the value 100 and never 54.5.

![[Pasted image 20240214112652.png]]

## Expectimax Search Attributes

- Unpredictability: result of an action is unknown. Why? 
	- Explicit randomness (Dice roll)
	- Unpredictable opponents (the ghosts respond randomly)
	- Actions can fail (when moving a robot, wheels might slip)
- Values should now reflect average-case *(expectimax)* outcomes, not worst-case *(minimax)* outcomes
- Compute the average score under optimal play
	- Max nodes similar to *minimax* search
	- Chance nodes have uncertain outcomes
	- Calculate chance node's expected utility: Take their weighted average (expectation) of children

### Psuedocode

Assume the fra

![[Pasted image 20240214113923.png]]


---
# References
