# Basics: 
- We begin by defining what Transaction ("Tx"), such that: 
	- A transaction is a **sequence** of **reads** and **writes** on database objects
	- Bath of work that must **commit** or **abort** as an atomic unit 
- A **transaction must end** in one of **two ways**: 
	- **COMMIT**ing a change after completing the transaction's operations 
	- **ABORT**ing a change after executing some operations 
		- Can be caused by the DBMS or a system crash 
# ACID Properties: 
- Atomicity: 
	 - Either all actions in the transaction happen, or none happen
- Consistency: 
	- Transactions preserve DB consistency
		- Given a consistent DB state, the transaction produces another consistent DB state
	- DB consistency expressed as a set of declarative integrity constraints 
		- CREATE TABLE/ASSERTION statements 
	- Transactions that violate integrity are aborted 
		- That's all the DBMS can automatically check 
	- DBMS connects the actions of many transactions, ensuring that 2 or more transactions do not interfere with each other
	- Each transactions executes as if it were executed by itself:
		- Concurrent accesses have no effects on transaction's behavior 
		- Net effect must be identical to executing all transactions in some serial order 
- Isolation:  
	- Execution of each transaction is isolated form that of all others
	- We can achieve isolation by running one transaction at a time. This is undesirable because of the time overhead, and so, we use "**locks**" to coordinate the serial order of execution. 
- Durability:
	- If a transaction commits, its effects persist across the entire DB
	- The effect of a committed transaction must survive failure 
	- The log ensures durability 
- DMBS are able to accomplish the above, by **logging** all transactions' operations. 
	- **UNDO**: 
		- Undoes the actions of ABORTed/failed transactions
	- **REDO**: 
		- Redoes the actions of committed transactions not yet propagated to disk when system crashes 
# Concurrency Control: 
- We can naively attempt to use serial order execution of our transaction, although this will cause: 
	- One transaction to run at time 
	- Safe but slow 
- To solve this, we can interleave execution for better performance. But, with concurrent executions, how do we define the order and ensure the correctness of our transactions?
# Transaction Schedule: 
- A schedule is a sequence of actions on data from one or more transactions. To denote this, we can either recognize the transactions in tabular, which is a table of transaction sources and their according actions, or string notation, which is the action subscript the transaction source in order of the request. 
	- Actions include: 
		1) Begin
		2) Read
		3) Write
		4) Commit
		5) Abort
# Serial Equivalence: 
## Serial Schedule: 
- A schedule that **does not interleave** the actions of different transactions. 
- Each transaction runs from **start to finish** without any **intervening actions from other transactions** 
- We recognize two schedules as **equivalent** when: 
	1) They involve the same transactions
	2) Each individual transaction's are ordered the same
	3) Both schedules leave the DB in the same state 
# Serializability: 
- A schedule $S$ is **serializable** if: 
	- $S$ is equivalent to some serial schedule 
# Conflict Serializable Schedules: 
- It becomes difficult to check whether the DB is consistently entering and leaving in the same final state. 
- To ensure the consistency of the DB after we commit, we can use an equivalence test: 
	- Settle for a "conservative" test: always true positives, but some false negatives
	- Sacrifice some concurrency for easier correct 
- We use notion of "*conflicting*" operations (read/write) when:
	- Two operations are in conflict if they: 
		- Are by different transaction sources
		- Are on the same DB object
		- At least one operation is "write"
- Thus, we consider two serializable schedules to be *conflict equivalent* if and only if: 
	- They involve the same actions of the same transaction sources and every pair of conflicting actions is ordered identically 
- We consider a schedule $S$ to be *conflict serializable* if $S$ is conflict equivalent to some other serial schedule, such that: 
	- You can transform an interleaved schedule $S$ into a serial schedule by swapping consecutive non-conflicting operations of different transaction sources
	- NOTE: Some serializable schedules are NOT conflict serializable 
# Conflict Dependency Graph: 
## Dependency Graphs: 
- We allocate one node per transaction 
- The edge connecting $T_{i}$ to $T_{j}$ is defined when: 
	- An operation, $O_{i}$, of $T_{i}$ conflicts with an operation, $O_{j}$, of $T_{j}$
	- The operation $O_{i}$ appears earlier in the schedule than the conflicting operation $O_{j}$
### Conflict Serializability Existence Theorem: 
- Then we conclude that the schedule is conflict serializable iff its dependency graph is acyclic 
- Conflicting operations prevent us from swapping operations into a serial schedule 
- Visually in our graph, this appears as some transaction, $T_{i}$, depending on another transaction, $T_{j}$, and vice versa 
# View Serializability: 
- We can recognize an alternative, weaker notion of serializability, such that schedules, $S_{1}$ and $S_{2}$, are *view equivalent* based on the cases, such that: 
	1) When the initial reads are the same: 
		 - If $T_{i}$ reads the initial value of $A$ in $S_{1}$, then $T_{i}$ also reads the initial value of $A$ in $S_{2}$
	2) When there are the same dependent reads:
		- If $T_{i}$ reads value of $A$ written by $T_{j}$ in $S_{1}$, then $T_{i}$ also reads value of $A$ written by $T_{j}$ in $S_{2}$
	3) When there are the same "winning" writes: 
		- If $T_{i}$ writes final value of $A$ in $S_{1}$, then $T_{i}$ also writes final value of $A$ in $S_{2}$
- Thus, we conclude that allows all conflict serializable schedules + "blind writes"
# Notes on Conflict Serializability
- Conflict Serializability does not allow all schedules that you would consider correct
	- This is because it is strictly syntactic - it doesn't consider the meanings of the operations or the data 
- In practice, Conflict Serializability is what gets used, because it can be done efficiently: 
	- In order to allow more concurrency, some special cases do get implemented, such as for travel reservations, etc. 
## Two-Phase Locking:
- Two-phase locking (2PL) is how we address conflict serializability, such that: 
	- We use "**locks**" to control access to items, including: 
	- Shared Locks (S):
		- Multiple transactions can hold these on a particular item at the same time
	- Exclusive Locks (E):
		- Only one of these and no other locks, can be held on a particular item at a time
- Then, the locking protocol itself follows, such that: 
	- Each transaction must obtain a shared lock on an object before reading AND an exclusive lock on an object before writing 
	- NOTE: A transaction can not request additional locks once it releases any locks 
	- We recognize the systematicness of 2PL, by its phases, such that: 
		1) Growing Phase: 
			- The initial phase, where we are placing locks on operations of transactions
		2) Shrinking Phase: 
			- The secondary phase, which is caused by the release of the first lock. This cascades down and releases all consequent locks. While in the shrinking phase, we CANNOT go back to the growing phase. 
- 2PL on its own is sufficient to guarantee conflict serializability, since it doesn't allow cycles in the dependency graph 
- The main DISADVANTAGE of 2PL is that it is susceptible to "cascading aborts", where one abort disrupts the current phase. 
## Strict 2PL: 
- Strict 2PL follows the same locking protocol as the standard 2PL, except: 
	- All locks held by a transaction are released only when the transaction completes 
- Allows only schedules who precedence graph is acyclic, but it is actually stronger than needed for that purpose
- In effect,  the "shrinking phase" is then delayed until one of the following conditions is met: 
	- Transaction has committed (commit log record on disk)
	- Decision has been made to abort the transaction (then locks can be released after rollback)
# Lock Management: 
- Lock and unlock requests are handled by the Lock Manager (LM)
- The LM **contains** **an entry** **for each currently held lock**, such that: 
	- A pointer to a list of transactions currently holding the lock 
	- Type of lock held (shared or exclusive)
	- Pointer to queue of lock requests 
- When a lock request arrives, we check to see if there is any conflict lock and proceed such that: 
	- If not, create an entry and grant the lock
	- Else, put the requestor on the wait queue
- Locking and unlocking both must be atomic operations 
- Lock Upgrades:
	- When a transaction that holds a shared lock can be upgraded to hold an exclusive lock 
	- Can cause deadlock problems 
### Deadlocks: 
- We begin by defining a deadlock to be a cycle of transactions waiting for locks to be released by each other
- We have two ways of dealing with deadlocks: 
	- Deadlock prevention 
	- Deadlock detection 
- Many systems just punt use Timeouts 
	- What are the dangers with this approach?
- Assign priorities based on timestamps. Assume $T_{i}$ wants a lock that $T_{j}$ holds. Then two policies are possible, such that: 
	- Wait-Die: If $T_{i}$ has higher priority, $T_{i}$ waits for $T_{j}$; otherwise $T_{i}$ aborts 
	- Wound-Wait: If $T_{i}$ has higher priority, $T_{j}$ aborts; otherwise $T_{i}$ waits 
	- We also enforce that if a transaction restarts, make sure it gets its original timestamp 
### Detection: 
- Alternative is to allow deadlocks to happen but to check for them and resolve them. To accomplish this, we can create a waits-for graph, where: 
	- Nodes are transactions 
	- There is an edge from $T_{i}$ and $T_{j}$, if $T_{i}$ is waiting for $T_{j}$ to release a lock 
	- We periodically check for cycles in the waits-for graph