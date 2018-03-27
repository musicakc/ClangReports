# Analysis Report #

## General ##
**Warning Type:** RunTime: Const vs Logical   
**Warning Explanation:**```kernel/sched/fair.c:3927:14: warning: use of logical '&&' with
constant operand [-Wconstant-logical-operand]
        if (initial && sched_feat(START_DEBIT))
                    ^  ~~~~~~~~~~~~~~~~~~~~~~~
kernel/sched/fair.c:3927:14: note: use '&' for a bitwise operation
        if (initial && sched_feat(START_DEBIT))
                    ^~
                    &
kernel/sched/fair.c:3927:14: note: remove constant to silence this warning
        if (initial && sched_feat(START_DEBIT))
                   ~^~~~~~~~~~~~~~~~~~~~~~~~~~```  
**File Location:** kernel/sched/fair.c
## History ##
**Introduced By:** 94dfb5e75e ("sched: add tree based averages")  
**Reported Since:** TODO  
**Resolved By:** TODO

## Manuel Assesment ##
**Classification:** [Tool can detect during runtime](WarningTypeClassifications.md)
### Rationale ###
The warning generated is due to the following code:
static void
place_entity(struct cfs_rq *cfs_rq, struct sched_entity *se, int initial)
{
	u64 vruntime = cfs_rq->min_vruntime;

	/*
	 * The 'current' period is already promised to the current tasks,
	 * however the extra weight of the new task will slow them down a
	 * little, place the new task so that it fits in the slot that
	 * stays open at the end.
	 */
	if (initial && sched_feat(START_DEBIT))
		vruntime += sched_vslice(cfs_rq, se);
	//...
}

Specifically,
		if (initial && sched_feat(START_DEBIT))
creates the clang warning. The sched_feat() macro is used to test if a scheduler feature is enabled or not, a list of which is available in the same file i.e. *kernel/sched/fair.c*. So, the macro returns a constant, which is causing the warning.
As pointed out by clang, we can alternatively use the bitwise operator '&', the use of '&&' is deemed to be safer than '&'. The change to '&' will remove the warning, but does not make the code *safer*.
