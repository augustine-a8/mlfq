# Multi Level Feedback Queue (MLFQ)

The multi level feedback queue is a scheduler designed to improve turnaround time as well as response time. It acheives this without knowing a priori the characteristics of the jobs it is growing to run (like how long the job will run for, whether or not the job will be performing io, if the job is a short running one or long running one). MLFQ achieves this balance between turnaround time and response time by learning the job characteristics as they run and using the learnt characteristics to schedule them accordingly.

## Project Description

This project is an implementation of multi-level feedback queue in cpp. This particular implementation is in accordance with the mlfq described in [**Operating Systems 3 Easy Pieces** under the **Virtualization Section** chapter 8 titled **Multi-level Feedback**](https://pages.cs.wisc.edu/~remzi/OSTEP/cpu-sched-mlfq.pdf).

The set of mlfq rules described in the material are as follows:

- If priority(A) > priority(B) run A.
- If priority(A) = priority(B) run A and B in round robin fashion.
- If a job first enters a system, place it in the highest queue.
- If a job utilizes its time allotment in a given queue reduce its priority by moving it down one queue.
- After some time period, S, move all jobs back to the highest queue.

### MLFQ Parameters/Variables

These are some of the variables or constants that differ accross various implementations of mlfq.

- Number of queues
- Time slice per queue
- Time allotment per queue
- How long S should be (i.e. the time period after which all jobs are moved to the highest queue)

> **Difference between time slice and time allotment:** Time slice is the length of a quota in round robin. That is how long a process should run before being switched out for the next one. Time allotment refers to how long a process lasts on a particular queue before having its priority reduced.
