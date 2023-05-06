---
category: laravel
sub_category_1: queue
sub_category_2: worker
language: en
tags:
- laravel
- forge
- queue
- worker
---

# Laravel Forge queue worker

Here are a few tips and tricks for the Laravel Forge que worker.

## Maximum Seconds Per Job

The Maximum Seconds Per Job option is a setting available when configuring a worker in Forge. It specifies the maximum amount of time a worker can spend executing a single task (job).

In many cases, it is important that tasks are executed quickly and reliably to maximize application performance and ensure that users have a good experience. At the same time, however, some tasks can be very time-consuming and block the worker, preventing other tasks from running. The Maximum Seconds Per Job option helps solve this problem by ensuring that a single task does not take too long.

The "Maximum Seconds Per Job" setting specifies the maximum amount of time the worker can spend executing a single task. If the task is completed within this time, the worker will return the results and wait for the next task. However, if the task takes longer than the specified time, the worker will abort the task and wait for the next task.

This setting is useful to ensure that the worker works efficiently and does not get blocked. However, if tasks vary greatly in duration, it may be difficult to choose an appropriate "Maximum Seconds Per Job" setting. In this case, it may be necessary to adjust the setting or use multiple workers to ensure that all tasks are executed quickly and reliably.

## Rest Seconds When Empty

The Rest Seconds When Empty option refers to a setting available when configuring a worker in Forge. This setting specifies how long a worker should pause when it has no tasks to perform.

When a worker has no tasks, it can unnecessarily consume resources by using CPU cycles and memory to look for new tasks. To avoid this, the "Rest Seconds When Empty" parameter can be used to instruct the worker to pause for a specified time before searching again for new tasks.

The "Rest Seconds When Empty" setting is usually specified in seconds and can be adjusted depending on the use case. For example, if the worker has tasks that arrive very frequently, it might make sense to set a relatively short idle time to ensure that the worker can respond quickly to new tasks. On the other hand, if the worker receives tasks only occasionally, it might make sense to set a longer idle time to save resources and reduce costs.

## Graceful Shutdown Seconds

The Graceful Shutdown Seconds option is a setting available when configuring a worker in Forge. It specifies how much time the worker has to complete running tasks before it is shut down.

In some cases, it may be necessary to shut down a worker, such as when a new version of the application is deployed or when the worker is no longer needed. However, if the worker is shut down while a task is running, this can lead to unexpected errors or data loss. To avoid this, there is an option called "Graceful Shutdown Seconds".

This setting specifies how much time the worker should have to complete running tasks before shutting down. The Worker initiates the "Shutdown" process by rejecting new tasks and then waiting for the running tasks to finish. When the time specified in the Graceful Shutdown Seconds setting expires, the worker completes all tasks still in progress and then shuts down.

The Graceful Shutdown Seconds setting is optional because in some cases it may not be necessary for the worker to complete tasks before shutting down. However, when such a setting is required, it can help ensure that the worker shuts down without causing errors or data loss.

## The interplay between Graceful Shutdown Seconds and Maximum Seconds Per Job.

The interaction between "Graceful Shutdown Seconds" and "Maximum Seconds Per Job" can be important, as they can both help to ensure that a worker is working reliably and performing tasks quickly and efficiently.

If the "Graceful Shutdown Seconds" value is too low, there is a risk that the worker will not have enough time to properly complete ongoing tasks before shutting down. On the other hand, if the "Maximum Seconds Per Job" value is too high, there is a risk that the worker will work on a single task for too long, blocking other tasks and reducing throughput.

A good practice is to set the "Maximum Seconds Per Job" setting so that most tasks can usually be completed within this time. However, if a task takes longer than this time, the "Graceful Shutdown Seconds" value should be set so that the worker has enough time to complete the ongoing task before shutting down.

However, it is also important to note that in some cases it may be appropriate to select a higher "Maximum Seconds Per Job" setting when dealing with complex or resource intensive tasks. In this case, the "Graceful Shutdown Seconds" value should be adjusted accordingly to ensure that the worker has enough time to complete these tasks.

---

Official documentation of Forge:

- Creating A Queue Worker: [Forge - creating-a-queue-worker](https://forge.laravel.com/docs/1.0/sites/queues.html#creating-a-queue-worker)
- Forge ddocumentation: [Forge introduction](https://forge.laravel.com/docs/1.0/introduction.html)
