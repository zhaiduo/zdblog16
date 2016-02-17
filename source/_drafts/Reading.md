---
title: Reading
id: 2276
comment: false
categories:
  - Uncategorized
tags:
---

About Pass-by-Value
http://javadude.com/articles/passbyvalue.htm

http://www.roguelazer.com/2015/02/beating-the-compiler/
On a Haswell processor, which has two "Vector Int ALU"s, you can theoretically be doing two AVX2 operations in parallel, each of which can be operating on eight 32-bit integers at once. According to the Intel 64 and IA32 Architectures Optimization Reference Manual, each of these instructions has a latency of 1 cycle, giving us a maximum theoretical PPC of 16.0, which is quite a lot. In fact, it's impossibly much. Transferring 16 32-bit words to the CPU per cycle would require 64 bytes/cycle of memory throughput, which translates on my CPU to 147GB/s of memory throughput. The PC3-12800 RAM in my system can do a maximum of 12.8GB/s per stick (25.6GBps total), which is only 11 bytes per cycle. That gives us a maximum throughput from memory of slightly above 2.75 PPC. Anything above that is probably an artifact of the lovely 128MB of eDRAM L4 cache on my CPU.

http://karpathy.github.io/neuralnets/

https://babeljs.io/docs/learn-es6/