# Caching Strategies
created:: 2024-07-15 20:50
status:: #zettel/fleeting
tags:: #solution-architecture #database #performance 

-  Time-based Invalidation - invalidation occur after a time.
- TTL-based Invalidation - Invalidation will expired by time too, but will occur per time.
- Least Recently Used (LRU) - The cache have a size limite, when will reach the limit, the most oldest will replaced.
- Most Recently Used (MRU) - It's similar to LRU, but the most recently will erase(CDN is a use cenary). 
- Least Frequently Used (LFU) - When the will reach the limit, the less frequent will replaced.
- Write-through Invalidation - After a new write in Database occur, already update the new data version in the caching.
- Write-back Invalidation - first time, the data is inserted in the caching, and in other moment, the database is updated. 
