# Chapter 1
## System concepts
* Software = Systems programs + Application programs
* A system is a mapping of a set of inputs into a set of outputs

## Realtime systems
* Typical realtime control system
  - input: sensors + image device: analog => digital
  - output: control signals + display: digital => analog
* Classic representation of a realtime system
	- Sequence of jobs to be scheduled
	- Hidden hardware complexity
* A real-time system is a system that must satisfy explicit response-time constraints or risk severe consequences, including failure.
* Failure: inability of the system to perform according to system specification. *Eg: space shuttle, nuclear plant vs ATM.*
* Reactive systems: scheduling is driven by ongoing interaction with their environment. Eg: fire-control
* Embedded systems: inside a system (not ifself a computer). *Eg: embedded computers in an automobile: fuel injection, airbag deployment,...*
* Block diagram of a generic real-time control system
  ![](Chapter%201.assets/2020-06-03-16-02-51.png)

## Soft vs Hard
A **soft** real-time system is one in which performance is degraded but not destroyed by failure to meet response-time constraints  
A **hard** real-time system is one in which failure to meet a single deadline may lead to complete and catastrophic system failure  
A **firm** real-time system is one in which a few missed deadlines will not lead to total failure, but missing more than a few may lead to complete and catastrophic system failure  

## Deadlines come from

Underlying physical phenomena of the system under control  
– Images updated at approximately 30 frames/second
– Accelerations must be read at a rate based on the velocity of
the vehicle

## Response time & Punctuality
The time between the presentation of a set of inputs to a system and the realization of the required behavior, including the availability of all associated outputs, is called the response time of the system

## Common misconceptions
* Real-time systems are synonymous with “fast” systems
  * Many (but not all) hard real-time systems deal with deadlines in the tens of milliseconds; e.g. airline reservation system
* There are universal, widely accepted methodologies for real-time systems specification and design
  * There is still no methodology available that answers all of the challenges of real-time specification and design all the time and for all applications
* There is no more a need to build a real-time operating system, because many commercial products exist
  * Commercial solutions have certainly their place, but choosing when to use an off-the-shelf solution and choosing the right one are continuing challenges

## Realtime System Design Issue
![](Chapter%201.assets/2020-06-03-16-01-57.png)

<hr>

## Reference model is characterized by:  

* A workload model: describes the application supported by the system
* A resource model describes resources available to the applications
* Scheduling algorithms define how the application
system uses the resources at all times

## Jobs and Tasks
A **job** is a unit of work that is scheduled and executed by a
system  
A **task** is a set of related jobs which jointly provide some
function
## Execution time
A job $J_i$ will execute for time $e_i$  

- This is the amount of time required to complete the
  execution of when it executes alone and has all the resources it needs  
- Value of depends upon complexity of the job and speed of
  the processor on which it is scheduled; may change for a variety of reasons: 
  - *Conditional branches*
  - *Cache memories and/or pipelines*
  - *Compression*

## Release and Response time
**Release time:** the instant in time when a job becomes available for execution  
**Response time:** the length of time from the release time of the job to the time instant when it completes

![image-20200606220725529](Chapter%201.assets/image-20200606220725529.png)

## Deadlines and Timing constraints
* Completion time: the instant at which a job completes execution  
* Relative deadline (D_i): the maximum allowable job response time  
* Absolute deadline (d_i):  the instant of time by which a job is required to be completed (often called simply the deadline)  
`absolute deadline = release time + relative deadline`
![](Chapter%201.assets/2020-06-03-16-04-39.png)

## Task
* Unit of computation is a task
  * A task can be executed multiple times
  * An instance of task is a job
  * The functionality of the job is defined in the task
* A processor executes a task
* Types of task:
  * Periodic: set of jobs that are executed repeatedly at regular time intervals can be modelled as a periodic task
    * The most common type of task used in real-time systems
  * Aperiodic
  * Sporadic
* Different execution time patterns for the jobs in the task
* Must be modelled differently
  * Differing scheduling algorithms
  * Differing impact on system performance
  * Differing constraints on scheduling

## Periodic tasks: parameters
Periodic task $T_i$ has sequence of jobs $J_{i,1}, J_{i, 2}, ..., J_{i, n}$  
* The release time ($r_i$): time instant of first job J(i, 1) is ready for execution
* The period ($p_i$): the minimum time between release times of consecutive jobs
* The execution time ($e_i)$: the maximum execution time of all jobs in the periodic task
* The relative deadline ($D_i)$: the interval of time by which a job is required to be completed from released
  * In case no deadline specified $D_i$ = $p_i$
* The relative deadline is smaller than the time between jobs, allowing some **slack time** for other jobs. `Slacktime = Period - Relative deadline`

![](Chapter%201.assets/2020-06-03-16-05-23.png)

## Further terminology
* Feasibility interval between release time and deadline `(r, r + D]`  
* Phase of task = release time of the first job

