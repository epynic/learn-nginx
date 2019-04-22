# worker_processes 

Changing the max number of worker processes that our nginx can use, by default they should be the number of core the host system has.

To view the number of CPU cores run in terminal `nproc` or `lscpu`
This is use to update the worker_processes

````
worker_processes 2;
````

# worker_connections
They are the simultaneous number of connection a host machine can process.

This would be best to set, the max number of files the host machine can access at a time. To find the max number of files that can be accessed simultaneous use ` ulimit -n ` 

````
events{
worker_connections 1024;
}
````
