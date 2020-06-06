##### Task states

**Ready**: not executed, wait for scheduling point

**Running**: get scheduled to a processor

**Blocked**: not running & cannot be scheduled at the next scheduling point (delay, wait for data/resources)

**Suspended**: user/system wants to completely remove the task from being scheduled (user press the “pause” button)

<img src="Chapter%202.assets/image-20200606214558997.png" alt="image-20200606214558997" style="zoom:50%;" />





##### Feasible schedule
- A  schedule that never misses any deadline is called **feasible** 
- A set of tasks is **schedulable** if there exists **at least a feasible schedule** 
- A scheduling algorithm is optimal if it always produces a feasible schedule in case a given set of tasks is schedulable

