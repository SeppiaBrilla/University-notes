![[Pasted image 20231021190414.png]]

The DMA engine is a dedicated engine optimized for integration of processors.
![[Pasted image 20231021190601.png]]

How the whole process work:
1) a core initiate the DMA transfer
2) the DMA copies data from memory to the processor memory
3) the core get notified from the DMA
4) the cores works on the data
5) the data get copied back from the DMA

Usually, all of this is done concurrently.


To analyse how much is the speed-up when we increase the number of parallel threads, we can use the following formula:
$$
\frac{N_{cycles-sequential}}{N_{cycles-parallel}} = \frac{N_{cycles-parallalelizable} + N_{cycle-nonpar}}{\max(\frac{N_{chuncks}}{processors}) \times \frac{N_{cycles}}{chunk} + c_{fork} + c_{join} + N_{cycle-nonpar}}
$$

In the formula we denote:
- with $c_{fork}$ the cost payed for forking the main process into smaller ones
- with $c_{join}$ the cost payed for joining the forked threads into one
- with $N_{cycle-nonpar}$ the number of operation that can't be parallelized 
- with $N_{cycle-parallelizable}$ the number of cycle that can be parallelized
- with $N_{chunks}$ the number of chunks in which the parallelizable code has been divided