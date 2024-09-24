2024/09/17 12:57
Status: #idea
Tags:

# Route Summarization Example

![[Pasted image 20240917125801.png]]

*You have a network with two routers as shown. Router A currently has a single static route to network 10.0.155.80/28. You need to add another subnet to router B. This subnet should also use a 28-bit mask. You would like to replace the existing static route to network 10.0.155.80/28 with a single summarized static route that includes the old network and the new network. You want to minimize wasted addresses.*

To solve this problem, let's follow these steps:

1. Identify the existing network: 10.0.155.80/28
2. Determine the new network to be added:
   - It should use a 28-bit mask
   - It should be adjacent to 10.0.155.80/28 to allow summarization

3. Calculate the summarized route:

   10.0.155.80/28 covers 10.0.155.80 - 10.0.155.95
   The next available /28 network would be 10.0.155.96/28

4. Convert these to binary:
   10.0.155.80 = 00001010.00000000.10011011.0101 0000
   10.0.155.96 = 00001010.00000000.10011011.0110 0000

5. Find the common bits:
   The first 27 bits are common

6. The summarized route will be:
   10.0.155.80/27

This covers 10.0.155.80 - 10.0.155.111, including both /28 networks.

To configure this on Router A:

1. Remove the existing static route:
   ```
   no ip route 10.0.155.80 255.255.255.240 10.0.155.32
   ```

2. Add the new summarized route:
   ```
   ip route 10.0.155.80 255.255.255.224 10.0.155.32
   ```

This summarization minimizes wasted addresses while covering both the existing and new networks.



---
# References

- [[Route Summarization]]