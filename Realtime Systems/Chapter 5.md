# Chapter 5: Resource access control protocols
In previous chapters, we ignores resources for scheduling processors. From this chapter, along with processors, additional **resources are required for jobs to be executed**.  
**Resources:** hardware devices, disk, memory, software resources (mutexes, locks, queues...)  
**Aims of this chapter:**
- How **resource contention** **affects** the **execution** behavior and **schedulability** of jobs 
- How **various resource access-control protocols** work to **reduce the undesirable effect** of resource contention 
- **How well these protocols succeed** in achieving this goal

## Definitions & Notations 
*Slide 4 - 14*
### Locks
### Critical sections
### Conflict & Blocking
### Resource access control
- Priority inversion
- Time anomalies
- Deadlock

### Resource access control protocols
- Non-preemptable Critical Sections - NPCS 
- Priority inheritance protocol
  - **The priority-ceiling protocol** extends the **priority-inheritance protocol** to **prevent deadlocks** and to **further reduce the blocking time**
- Basic priority ceiling protocol 
  - This has led to **two modifications** to the protocol:
    - The **stack-based priority ceiling protocol**
    - The **ceiling priority protocol**
- Stack-based priority ceiling protocol
- The ceiling priority protocol (in dynamic priority systems)




(Bên dưới chưa phân loại)
## Đề bài :
![](chapter5.assets/2020-06-03-10-09-49.png)

## Uncontrolled - Priority inversion

## Non-preemptive critical sections

## Basic priority inheritance protocol
### Rule
![](chapter5.assets/2020-05-27-11-16-31.png)

### Steps to schedule
- Schedule with algorithm
- Whenever resources needed, use the protocol to grant the resources: use rule 2
  - If there is any job blocked: use rule 3
- Whenever resource released, use rule 3 to return priorities

### Complex example
...
- t = 6:
  - J2 needs R2, but J5 holds R2. J2 is blocked by J5. Use rule 3, pi_5(6) = 2,  J5's priority now (t = 6) is J2's priority. J5 is executed with inherited priority (ignore blocked J2)
- t = 7: J5 continues to execute with its R2 resource.
- t = 8: J1 is released, it is highest priority. J1 is executed (J2 is stopped).   
...
- t = 11, J2 and J4 are both available, but we take J4 because at this time J4's priority is 1, J2 is 2.
- t = 12.5, J4 releases R2 resource, but J4 is not blocked with R2 resource => no return priority (still hold that priority).
- t = 13, ...

## Basic priority ceiling protocol

##### Two additional terms:

- **Priority ceiling** of resource $R_k$ = highest priority of all the jobs that require $R_k$. Denoted by: $Π(R_k)$
- Vào thời điểm t bất kỳ, **current priority ceiling** $Π(t)$ of the system = **highest priority ceiling** of *in-use* resources at time t.
- If all resources are free, $Π(R_k)$ = Ω (a nonexistent priority level that is lower than the lowest priority level of all jobs)

### Rules:

#### Rule 1 – Scheduling rule:

- Vào lúc job được release, current priority of this job = assigned priority. Job **thay đổi** **priority** khi **thoả mãn các điều kiện ở rule 3**.
- Every ready job J is scheduled preemptively and in a priority-driven manner at its current priority $π(t)$.

#### Rule 2 - Allocation rule:

When a job **J** requests resource **R** at time **t,** có 2 trường hợp sau xảy ra:

- R is **busy**. J's request **fails**, J is **blocked**.

- R is **free**:

  - If **J's priority > current priority ceiling $Π(t)$**. R is allocated to J.
  - If **J's priority ≤ current priority ceiling $Π(t)$**. R is allocated to J **only if this job J holding resource(s) có priority ceiling =  $Π(t)$**. Otherwise, J's request is denied and J becomes blocked.

  *=> Unlike priority inheritance: priority ceiling can deny access to an available resource*

#### Rule 3 - Priority-inheritance rule:

- The job $J_l$ blocks job $J$. Job $J_l$ **inherits current priority** $π(t)$ of $J$.
- $J_l$ vẫn giữ inherited priority cho tới lúc nó giải phóng hết mọi resource(s) có priority ceiling ≥ $π(t)$. Vào thời điểm đó, priority of $J_l$ returns to priority trước lúc mà nó được cấp các resource(s) bên trên.

### Enhancing the priority ceiling protocol

* Stack-based priority ceiling protocol



#### Stack-based priority ceiling protocol

##### Example

![image-20200605104333833](Chapter%205.assets/image-20200605104333833.png)

$π(R_1) = 1; π(R_2) = 2$ 

Note: nó cần resource, cần thì cấp, không được thì thôi, không xảy ra chuyện block => không có inherit. (need to think more)

#### Priority-ceiling protocol in dynamic priority systems

Dùng với "dynamic priority systems", nên có những thứ khác cần lưu ý:

- Mỗi lần một job mới được release, priority của các jobs sẽ thay đổi (hoặc giữ nguyên) => Cập nhật lại **priority của resources $π(R_k)$** và **current priority ceiling của system $π(t)$**.
- 

