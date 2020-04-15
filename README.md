# Monero lock times

By - Isthmus & TheCharlatan

Analysis and mitigation of information leaks through Monero's plaintext lock time

## Data

Lock time data retrieved by:
```
SELECT 
	block.height,
	encode(tx.hash,'hex'),
        tx.unlock_time
FROM 
	monero block,
	LATERAL UNNEST(block.transactions) tx(hash, version, unlock_time, vin, vout, extra, fee)
ORDER BY 
	height DESC
```

h/t Neptune for the Monero-SQL database
