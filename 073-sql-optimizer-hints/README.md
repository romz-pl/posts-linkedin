# Harnessing the power of Oracle Database optimizer hints

Have you ever added a hint to a SQL statement only to wonder why the optimizer seemed to ignore it? If so, you're not alone. Maria Colgan's session, "Harnessing the Power of Oracle Database Optimizer Hints," addresses this issue directly, offering invaluable insights for any serious Oracle DBA or developer.

**Hints are directives, not suggestions, but only when applicable.** A hint will always be followed if it is valid for the query. Asking for a hash join on a non-equality predicate won't work. The optimizer won't use it because it can't. It's not the optimizer ignoring you; it's protecting you.

**Common reasons hints go unused:**
- Typo in the hint or index name;
- Using the table name instead of the alias;
- Placing the hint in the wrong query block;
- Requesting an incompatible combination (e.g., a parallel index scan on a non-partitioned table);

**Use the hint report (Oracle 19c+).** Before 19c, diagnosing hint issues required digging through the trace file. Starting with version 19c, the hint report displays below the execution plan and tells you exactly what happened, including syntax errors, unresolved hints, and unused directives. It's a game-changer for troubleshooting!

**Hints should be a last resort.** Before using them, exhaust other options such as accurate statistics, the SQL Tune Advisor, and the SQL Plan Management (SPM) feature. For plan stability, SPM is far more maintainable than embedding a full outline of hints directly in your SQL.

**Upgrading to 19c?** Test your hinted queries with _OPTIMIZER_IGNORE_HINTS = TRUE. The optimizer may already deliver equal or better performance without them.

💡 Optimizer hints are powerful, but only when used precisely and purposefully.



## References
+ Harnessing the power of Oracle Database optimizer hints, [23th Nov 2022](https://www.youtube.com/watch?v=fVdFT8y-IX4)


```
#DatabaseOptimization
#SQLTuning
#Oracle
#SQLTutorial 
#SQL
```

![Harnessing the power of Oracle Database optimizer hints](./img.png)
