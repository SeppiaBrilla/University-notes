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
