ISA extension are some extension that can be added to any processor in order to make it faster at computing matrix multiplications.

## HW loops and post increment

Let's suppose to have a loop of this type:
``` c
for(int i = 0; i < X; i ++){
	var[i] = var[i] * 2
}
```
In this case, the processor will need to: 
1) load in memory the variable needed to perform the computation
2) perform the computation 
3) update the memory address to load the next variable

With post increment instruction, we can perform step 1 and 3 at the same time, making way faster the computation. To do so, we need some extra hardware, however the increment in the processor size (8-12%) does not make it consume more than what we save performing such operation.

Hardware loops can be implemented whenever we need beforehand how many times we need to perform a loop (for instruction). In this cases, we can design a special piece of hardware that can notify the main processor when to stop performing the loop. This way, the processor can avoid checking each time what to do next and, with a 5% increase in the processor size, we can have a 2x speed-up.

## Multiply accumulate

We can let the processor do just the multiply part and do the accumulate directly on the register.
Pro: 
- Faster access to mac 
- single cycle mac
Cons:
- additional read port on the register file
- used for pre/post increment with register

## Packed-SIMD

SIMD stands for "Same Instruction Multiple Data", basically, we can load either 4 8bit or 2 16bit numbers on a 32bit register and perform the same instruction for all the numbers at the same time.