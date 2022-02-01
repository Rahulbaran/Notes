- `PromiseJobs` is an internal queue (also called microtask Queue/Job Queue) which is used by javascript engine to put `.then/catch/finally` of a **promise** in the queue if it is ready (promise has settled).

- any asynchronous code runs in browser background before they are ready to get queued in

- While execution of asynchronous code in the **Function execution Stack(Call Stack) event loop** gives priority to **microtask Queue (queue for ready promises)** over **macrotask/Callback/Message/Task Queue(queue to handle other async codes)**.

- callback function passed in a **Promise** Constructor is also known as **executor** function.
