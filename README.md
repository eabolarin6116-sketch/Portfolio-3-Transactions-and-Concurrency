 Portfolio 3: Transactions and Concurrency

 1. Objective

This portfolio demonstrates how database transactions protect the consistency of financial operations in the Bank/Fintech Platform database.

 2. Transaction Commit

A successful deposit, withdrawal, and transfer were performed using PostgreSQL. The operations changed account balances and created transaction records. These operations provide practical examples of committed database changes.

 3. Transaction Rollback

A test transaction temporarily increased Ada Okafor's account balance by ₦1,000. The transaction was rolled back, and a subsequent query confirmed that the balance returned to its previous value of ₦105,000.

 4. Concurrency Control

The transfer implementation used `SELECT ... FOR UPDATE` to lock the source and destination account rows before updating balances. This helps prevent conflicting transactions from modifying the same account rows simultaneously.

 5. Evidence

Screenshots and SQL examples will be added to document commit, rollback, isolation, and concurrency-control behaviour.

 6. Conclusion

This portfolio examines how transaction management and concurrency controls help preserve consistency during financial operations.



 Repeatable-Read Isolation Experiment

Objective

To demonstrate how PostgreSQL's `REPEATABLE READ` isolation level provides a consistent view of account data during concurrent transactions.

 Procedure

1. Session A began a transaction using `REPEATABLE READ` and read Ada's account balance as ₦105,000.00.
2. Session B updated the balance by ₦1,000 and committed the change. Its updated balance was ₦106,000.00.
3. Session A queried the balance again without ending its transaction.
4. Session A still returned ₦105,000.00 because it continued to use its original transaction snapshot.

 Result

The experiment demonstrated repeatable-read behaviour: Session A did not see Session B's committed update while Session A's transaction remained open.

 Conclusion

Transaction isolation helps control how concurrent database operations observe changes. PostgreSQL's `REPEATABLE READ` level maintained a consistent snapshot for Session A during this experiment.

Screenshots of both sessions provide supporting evidence.


## Supporting Documentation and Evidence

- `concurrency-control.md` — explains row-level locking using `SELECT ... FOR UPDATE`.
- Repeatable-read experiment screenshots — show the account balance observed in Session A before and after Session B commits an update.
- Rollback evidence — shows that an uncommitted balance change is undone.
- Transaction evidence — documents successful deposits, withdrawals, and transfers.

## Summary

The portfolio demonstrates transaction commit and rollback, repeatable-read isolation, and row-level locking in PostgreSQL. These mechanisms help maintain data consistency during financial operations.


