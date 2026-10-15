# Concurrency Control in the Bank/Fintech Platform

 1. Objective

The objective is to explain how PostgreSQL row-level locking helps maintain consistent account balances when multiple financial transactions operate concurrently.

 2. Locking Mechanism

The transfer operation uses the following SQL statement:

```sql
SELECT account_id
FROM accounts
WHERE account_number IN ('FIN100001', 'FIN100002')
ORDER BY account_id
FOR UPDATE;
```

The `FOR UPDATE` clause locks the selected account rows until the transaction ends. Other transactions attempting to acquire conflicting row locks must wait until the locks are released.

 3. Application to Fund Transfers

Before transferring funds, the application locks the source and destination account rows. It then checks that both accounts are valid and that the source has sufficient funds before updating balances and recording the transfer.

Ordering the rows by `account_id` provides a consistent lock-acquisition order for this operation, which can help reduce the risk of deadlocks when transfers involve the same accounts in opposite directions.

 4. Benefits

- Helps prevent conflicting updates to the same account rows.
- Supports consistent balance changes during transfers.
- Works with transaction commit and rollback.
- Reduces the risk of race conditions when combined with appropriate validation and transaction boundaries.

 5. Limitations

Row-level locks do not eliminate every possible concurrency problem. Transactions must handle errors, maintain suitable isolation, and ensure that balance updates and transaction records are committed or rolled back together.

 6. Conclusion

PostgreSQL row-level locking provides a practical concurrency-control mechanism for the Bank/Fintech Platform. The transfer operation demonstrates how locks can protect account updates while funds are transferred between accounts.
