In general, when doing a matrix multiplication, the situation is:
![[Pasted image 20231021193845.png]]

The huge number of memory operations can slow down the computation by a lot wasting many cycles. If, instead of reading that way, we read just a block of memory (the one we need at a given moment) the amount of wasted time is much lower
![[Pasted image 20231021194310.png]]
![[Pasted image 20231021200814.png]]
![[Pasted image 20231021200829.png]]
![[Pasted image 20231021200846.png]]