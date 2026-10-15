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
