# Non-Uniform Memory Architecture (NUMA) by Fedor G Pikus


At C++Now 2023, Fedor G. Pikus delivered one of the most eye-opening systems programming talks I have ever encountered. 


NUMA systems are no longer exotic hardware. Nearly every mid-range server today has 32 to 40 cores and under 500 GB of RAM and is a NUMA machine. Yet most of us still write code as if memory access were uniform. It isn't.


## What is NUMA?

Modern CPUs have integrated memory controllers. Each processor socket has its own physical memory bank. Accessing local memory is fast. But crossing the interconnect to reach another socket's memory? That's where things get expensive, with roughly 40–60% bandwidth loss at saturation and even worse performance for random access patterns or shared atomic variables.



## The counterintuitive results are striking:

+ A scheduler running on 16 cores (one NUMA node) outperformed the same scheduler running unrestricted across 64 cores — because threads were constantly fighting across node boundaries.

+ A compute-intensive `parallel_for_each` with a tiny memory footprint reached a bottleneck at ~80% UPI link saturation, which was caused by a single shared atomic variable bouncing between nodes at 180 ns per round trip.

+ Binding all threads to one oversubscribed node, which causes OS time-slicing, still outperformed allowing the OS to freely schedule across nodes.



## How to debug NUMA issues:

The most valuable diagnostic step that Fedor demonstrates is deceptively simple. Run your program three times and compare the throughput.

1. Unbound (OS decides everything)

2. CPU and memory both pinned to one node

3. CPU on one node, memory on another


If the bound outperforms the unbound, then you have a NUMA problem. If cross-node performance is dramatically worse than in-node performance, the cause is memory locality, not just compute.


Although hardware profilers like VTune can provide NUMA remote access metrics, Fedor warns that they can also be severely misleading. 



## The fix: hierarchical synchronization.

For the parallel_for_each case, the solution was to switch to per-node task counters, or one atomic counter per NUMA node, with the main thread aggregating across all nodes. This approach eliminated cross-node cache line bouncing entirely, increasing throughput by 20x at 64 threads.



💡 NUMA isn't a niche concern. It's the default architecture of the machines on which your production code is currently running. Knowing how to understand, detect, profile, and fix NUMA-related regressions is becoming a core competency for any C++ systems programmer.


## References


+ 🎥 Fedor G Pikus, "Non-Uniform Memory Architecture (NUMA): A Nearly Unfathomable Morass of Arcana", C++Now 2023, [21 Jul 2023](https://www.youtube.com/watch?v=f0ZKBusa4CI)


```
#CPlusPlus
#SystemsProgramming
#HighPerformance
#NUMA
#LowLatency
```

![Non-Uniform Memory Architecture (NUMA) by Fedor G Pikus](./img.png)
