# Circuit breaker
created:: 2024-07-17 06:22
status:: #zettel/fleeting
tags:: #solution-architecture 

## What is it?
Circuit breaker is a pattern used to handle mitigate failure and maintain stability, most likely when using microsservices. The circuit breaker interaction handler between systems, it will use states to request handler:
- Closed: normal use, allow massive requests.
- Open: requests blocked, will run a fallback.
- Half open: Send some requests to test the service, if something fails, will switch to open.
### Impact mitigation strategies
- Deadletters - Event Messages queues.
- [[Retry and exponential backoff]] - Wait a certain amount of time to before repeating the requests.
- Fallbacks and elegant degradation - Use oldest caches.
- Notifications - notify the user about the downtime.

