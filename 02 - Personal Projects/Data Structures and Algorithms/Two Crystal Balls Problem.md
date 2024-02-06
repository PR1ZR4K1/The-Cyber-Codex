2024/02/05 20:22
Status: #idea
Tags:

# Two Crystal Balls Problem

Generalized version is we are on a 100 story building and need to find the most optimized way to determine where our crystal balls will break.

![[Pasted image 20240205202933.png]]

At some point the ball will break and from that point on the ball will still break. So we need to find the first story that will make our ball break.

The point of this problem is to be able to jump in such a way that isn't some portion of n so we do not walk by such portion of n. We need to jump by a fundamentally different unit:
## $\sqrt n$

![[Pasted image 20240205202655.png]]

The workflow is jump by the $\sqrt n$ until we find the point where it breaks. Now that we know it breaks at this point we have to go back to the last known good state which is

current state - $\sqrt n$

Now our worst case time complexity if we walk a maximum distance of $\sqrt n$ is:
$\sqrt n$

---
# References

- TwoCrystalBalls.ts