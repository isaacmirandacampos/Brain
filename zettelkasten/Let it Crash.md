# Let it crash
created:: 2024-04-14 09:30
status:: #zettel/permanent 
tags:: #cloud #docker
## What is it?
A strategy of handle your containers. You control the errors of applications recreating other container after a internal error. A example is the database error off connections. Instead control the error flows to retry connections, you can create a new container, the new request will send of the new container, and the request that the oldest container already processing, is waiting finish for we killer them.
## Benefits
With it strategy, we can handler better the errors without consume more of our application. It is more easy to maintain our application resilience. 
# References
-  [Sistemas feitos em JavaScript não são confiáveis?! Error Handling - Let it Crash - Graceful Shutdown - YouTube](https://youtu.be/iC_tKAyLeag?si=KwEkxJdD6w5V3ag9&t=1855)