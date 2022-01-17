# Planet Express

You are managing logistics for an intergalactic delivery service. Your current task is to calculate the amount of time needed to deliver a set of packages. In the best case, the time needed to deliver a package is the difference between the package "pickup" and package "dropoff" events. Unfortunately, it's a dangerous universe out there, and sometimes the courier gets eaten (an "eaten" event). It's really a good news/bad news sort of situation. The good news is that your delivery service has access to a limited form of time travel, so you can send out multiple couriers at the same time (you should see the looks on their faces when two leave at the same time, though). The bad news is that you have to count the time for all the couriers, no matter how many it takes to make a delivery.

Your input data is given in a list of data formatted like the following:

`(delivery id, timestamp, event)`

The timestamp is a [Unix Timestamp](https://www.unixtimestamp.com/). Your function should calculate the total time for all deliveries, including 'mishaps'. For example, if the input is the following:

```
(1, 1570320047, 'pickup')
(1, 1570320725, 'dropoff')
(2, 1570321092, 'pickup')
(3, 1570321212, 'pickup')
(3, 1570322352, 'dropoff')
(2, 1570323012, 'dropoff')
(2, 1570322092, 'eaten')
```

The total active time would be 4738 seconds by the following schedule:

```
(1, 1570320047, 'pickup') -> (1, 1570320725, 'dropoff') => 678 seconds
(2, 1570321092, 'pickup') -> (2, 1570322092, 'eaten')   => 1000 seconds, first attempt
(2, 1570321092, 'pickup') -> (2, 1570323012, 'dropoff') => 1920 seconds, second attempt
(3, 1570321212, 'pickup') -> (3, 1570322352, 'dropoff') => 1140 seconds
```

## Business Rules/Errata

- You may assume that each delivery is being carried by a different courier, time travel aside.
- The result of your calculation should be the total number of seconds of all attempts, added together.
- Every delivery ID will have one 'pickup' and one 'dropoff' event.
- It is possible, though most unfortunate, for more than one courier to be eaten in the course of making a particular delivery.
- If no delivery data is passed to your function, return 0 seconds.

## Examples

See above.
