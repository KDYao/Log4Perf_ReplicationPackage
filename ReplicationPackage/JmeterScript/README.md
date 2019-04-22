The Jmeter load testing script using in our study. Each of the test runs for 5 hours (30min warm-up + 4hour running + 30min cool down.)

We use 150 threads (users) as the testing load for CloudStore, 30 threads (users) for OpenMRS. This number is flexible according to the resource usage on the server. We do not suggest to use too many threads in case the server is overloaded at all times, which could make the performance variance hard to detect.

Other data are pre-defined and already dumped from database. These data could be used by Jmeter scripts at runtime.