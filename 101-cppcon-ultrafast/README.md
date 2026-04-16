𝗨𝗹𝘁𝗿𝗮𝗳𝗮𝘀𝘁 𝗧𝗿𝗮𝗱𝗶𝗻𝗴 𝗦𝘆𝘀𝘁𝗲𝗺𝘀 𝗯𝘆 𝗗𝗮𝘃𝗶𝗱 𝗚𝗿𝗼𝘀𝘀

At CppCon 2024, David Gross gave one of the most practical talks at the conference. He gave a deep dive into building low-latency trading systems from scratch.

From the start, his core message was clear: low latency is a design constraint, not an afterthought optimization.


𝗨𝗻𝗱𝗲𝗿𝘀𝘁𝗮𝗻𝗱 𝘆𝗼𝘂𝗿 𝗱𝗮𝘁𝗮 𝗯𝗲𝗳𝗼𝗿𝗲 𝗰𝗵𝗼𝗼𝘀𝗶𝗻𝗴 𝘆𝗼𝘂𝗿 𝗱𝗮𝘁𝗮 𝘀𝘁𝗿𝘂𝗰𝘁𝘂𝗿𝗲.
While optimizing an order book, David demonstrated that the std::map data structure exhibits poor cache locality when dealing with realistic workloads. Switching to a sorted std::vector with lower_bound dramatically improved performance.


𝗔𝘃𝗼𝗶𝗱 𝗻𝗼𝗱𝗲-𝗯𝗮𝘀𝗲𝗱 𝗰𝗼𝗻𝘁𝗮𝗶𝗻𝗲𝗿𝘀 𝗯𝘆 𝗱𝗲𝗳𝗮𝘂𝗹𝘁.
Avoid std::map, std::set, and std::list unless they are strictly necessary. Contiguous memory is not just a micro-optimization; it is a prerequisite for predictable, low-latency behavior.


𝗕𝗿𝗮𝗻𝗰𝗵𝗹𝗲𝘀𝘀 𝗯𝗶𝗻𝗮𝗿𝘆 𝘀𝗲𝗮𝗿𝗰𝗵 𝗵𝗮𝘀 𝗿𝗲𝗮𝗹 𝘁𝗿𝗮𝗱𝗲𝗼𝗳𝗳𝘀.
Eliminating branch mispredictions improved IPC. Branch mispredictions were measured at 25% bad speculation via Intel's Top-Down Analysis. However, branchless searches touch more memory due to the absence of an early exit. The ultimate winner? Linear search: simple, cache-friendly, and mechanically compatible with modern hardware.


𝗕𝘆𝗽𝗮𝘀𝘀 𝘁𝗵𝗲 𝗸𝗲𝗿𝗻𝗲𝗹 𝘄𝗵𝗲𝗿𝗲 𝗽𝗼𝘀𝘀𝗶𝗯𝗹𝗲.
In terms of networking, user-space solutions (e.g., Solarflare's Onload/EFVI) can reduce latency from ~3 µs to ~700 ns. For local communication, shared memory over sockets is best.


𝗗𝗲𝘀𝗶𝗴𝗻 𝘆𝗼𝘂𝗿 𝗰𝗼𝗻𝗰𝘂𝗿𝗿𝗲𝗻𝘁 𝗾𝘂𝗲𝘂𝗲𝘀 𝗰𝗮𝗿𝗲𝗳𝘂𝗹𝗹𝘆.
David's shared-memory SPMC queue achieved strong performance through three targeted optimizations: batching writes to reduce atomic contention, avoiding unnecessary cache-line alignment, and caching the read counter locally. The result outperformed well-known IPC libraries.


𝗦𝘁𝗮𝘆𝗶𝗻𝗴 𝗳𝗮𝘀𝘁 𝗶𝘀 𝗵𝗮𝗿𝗱𝗲𝗿 𝘁𝗵𝗮𝗻 𝗴𝗲𝘁𝘁𝗶𝗻𝗴 𝗳𝗮𝘀𝘁.
Essential profiling tools include perf, hardware counters, and Clang's XRay, which is runtime-patchable instrumentation with near-zero overhead. These tools are important not only for initial tuning but also for maintaining performance in production.


𝗬𝗼𝘂 𝗮𝗿𝗲 𝗻𝗼𝘁 𝗮𝗹𝗼𝗻𝗲 𝗼𝗻 𝘁𝗵𝗮𝘁 𝘀𝗲𝗿𝘃𝗲𝗿.
Perhaps the most underappreciated insight is that when multiple processes share an L3 cache, their memory access patterns interact. Even a single well-optimized process can be undermined by poorly designed neighbors. System-level thinking is essential.



💡 Simplicity and performance reinforce each other; they are not in tension. The fastest solution (linear search) was also the simplest. 



𝗥𝗲𝗳𝗲𝗿𝗲𝗻𝗰𝗲𝘀
🎥 David Gross, "When Nanoseconds Matter: Ultrafast Trading Systems in C++", CppCon 2024, 28 Feb 2025, https://www.youtube.com/watch?v=sX2nF1fW7kI



#CppCon
#LockFree
#HighPerformance
#HighFrequencyTrading
#LowLatency



