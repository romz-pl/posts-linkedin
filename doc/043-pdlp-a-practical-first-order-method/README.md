# PDLP: A Practical First-Order Method for Large-Scale Linear Programming

David Applegate, Mateo Díaz, Oliver Hinder, Haihao Lu, Miles Lubin, Brendan O'Donoghue, Warren Schudy

**arXiv:2501.07018 [math.OC], [Submitted on 13 Jan 2025]**



## ABSTRACT


We present PDLP, a practical first-order method for linear programming (LP) designed to solve large-scale LP problems. PDLP is based on the primal-dual hybrid gradient (PDHG) method applied
to the minimax formulation of LP. PDLP incorporates several enhancements to PDHG, including diagonal preconditioning, presolving, adaptive step sizes, adaptive restarting, and feasibility polishing. Our algorithm is implemented in C++, available in Google’s open-source OR-Tools library, and supports multithreading.

To evaluate our method, we introduce a new collection of eleven large-scale LP problems with sizes ranging from 125 million to 6.3 billion nonzeros. PDLP solves eight of these instances to optimality gaps of 1% (with primal and dual feasibility errors of less than 10−8) within six days on a single machine. We also compare PDLP with Gurobi barrier, primal simplex, and dual simplex implementations. Gurobi barrier solves only three instances, exceeding our 1TB RAM limit on the other eight. While primal and dual simplex are more memory-efficient than the barrier method, they are slower and solve only three instances within six days.

Compared with the conference version of this work (in: Advances in Neural Information Processing Systems 34 (NeurIPS 2021)), the key new contributions are: (i) feasibility polishing, a technique that quickly finds solutions that are approximately optimal but almost exactly feasible (without which only three of the eleven problems can be solved); (ii) a multithreaded C++ implementation available in Google OR-Tools; and (iii) a new collection of large-scale LP problems. Note that the conference version should be referred to for comparisons with SCS and ablation studies, which we do not repeat in this paper.




## References

+ 🔗 "PDLP: A Practical First-Order Method for Large-Scale Linear Programming" (Open Acces Article), [2025](https://arxiv.org/abs/2501.07018)
+ 🔗 Haihao (Sean) Lu, "New Developments of First Order Methods for Linear Programming", [2023](https://www.mccormick.northwestern.edu/research/optimization-machine-learning-center/documents/events/lu-us-mexico-2023.pdf)
+ 🔗 "Practical Large-Scale Linear Programming using Primal-Dual Hybrid Gradient" (Open Acces Article), [2021](https://arxiv.org/abs/2106.04756)
+ 🔗 HiGHS Newsletter 25.0, [May 2025](https://highs.dev/assets/HiGHS_Newsletter_25_0.pdf)
+ 🔗 The fractal image was created using the [JavaScript Fractal Explorer](https://jsdw.me/js-fractal-explorer/) program, which was written by James Wilson.


```
#OperationsResearch
#Optimization
#DataScience
#Analytics
#MathematicalProgramming
```

![PDLP: A Practical First-Order Method for Large-Scale Linear Programming](./img.png)
