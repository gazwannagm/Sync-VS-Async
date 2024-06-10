# **Synchronous and Asynchronous Programming**

# 1.What is it?

## Synchronous Programming

Synchronous programming works by handling tasks one at a time, in order.
Basically, we can\'t move on to the next task until the current one is
done. because the program stops at each
step and waits until that particular task is finished before moving on.

## Asynchronous Programming

Asynchronous programming let us do multiple things at once. we can start
a task and then move on to other things while waiting for it to finish.
This way, the program doesn\'t just sit there waiting and can keep
working on other tasks, making everything faster and more efficient.

# 2.Why Do We Need it?

## Synchronous Programming

There is many advantages to use sync and async programming but we will consider the
more important

1.  **Easier to Implement**: It\'s really easy to write and understand
    because everything happens in a straightforward, step-by-step
    manner.

2.  **Easier to Debug :** Since tasks run in a set order, it\'s easier
    to debug and figure out what\'s going on in our code .

### Asynchronous Programming

1.  **Efficiency:** we can handle multiple tasks at once. For example,
    if we're waiting for a file to download, we can do other tasks at
    the same time.

2.  **Responsiveness:** In applications, especially those with a user
    interface, the app remains responsive to user actions even while
    other tasks are being completed in the background.

3.  **Scalability:** If we're building something like a web server, it
    needs to handle many requests at the same time. Asynchronous
    programming makes this possible without slowing everything down.

# 3. How can we implement it?

#### Synchronous Example

#### Python 
```python
import time

def task1():

print(\"Task 1 started\")

time.sleep(2) \# Adding some Delay

print(\"Task 1 completed\")

def task2():

print(\"Task 2 started\")

time.sleep(1) \# Adding Some Dealy delay

print(\"Task 2 completed\")

task1()

task2()
```

Here, task1 finishes completely before task2 starts.

#### Asynchronous Example

#### Python 
```python

import asyncio

async def async_task1():

print(\"Async Task 1 started\")

await asyncio.sleep(2) \# Adding Some Delay

print(\"Async Task 1 completed\")

async def async_task2():

print(\"Async Task 2 started\")

await asyncio.sleep(1) \# Adding Some Delay

print(\"Async Task 2 completed\")

async def main():

await asyncio.gather(async_task1(), async_task2())

asyncio.run(main())
```

Here, both tasks can run at the same time, and we don\'t have to wait
for one to finish before starting the other.

#### Synchronous Example

#### Typescript
```typescript

function task1() {

console.log(\"Task 1 started\");

let start = Date.now();

while (Date.now() - start \< 2000) {} // adding Some Delay

console.log(\"Task 1 completed\");

}

function task2() {

console.log(\"Task 2 started\");

let start = Date.now();

while (Date.now() - start \< 1000) {} // Adding Some Delay

console.log(\"Task 2 completed\");

}

task1();

task2();
```

#### Asynchronous Example

#### Typescript
```typescript

function asyncTask1() {

return new Promise\<void\>((resolve) =\> {

console.log(\"Async Task 1 started\");

setTimeout(() =\> { // adding Some Delay

console.log(\"Async Task 1 completed\");

resolve();

}, 2000);

});

}

function asyncTask2() {

return new Promise\<void\>((resolve) =\> {

console.log(\"Async Task 2 started\");

setTimeout(() =\> { // adding Some Delay

console.log(\"Async Task 2 completed\");

resolve();

}, 1000);

});

}

async function main() {

await Promise.all(\[asyncTask1(), asyncTask2()\]);

}

main();
```

#### Synchronous Example

#### Dotnet
```C#

using System;

using System.Threading;

class Program

{

static void Task1()

{

Console.WriteLine(\"Task 1 started\");

Thread.Sleep(2000); // Adding some Delay

Console.WriteLine(\"Task 1 completed\");

}

static void Task2()

{

Console.WriteLine(\"Task 2 started\");

Thread.Sleep(1000); // Adding some Dealy

Console.WriteLine(\"Task 2 completed\");

}

static void Main(string\[\] args)

{

Task1();

Task2();

}

}
```

#### Asynchronous Example

#### Dotnet
```C#

using System;

using System.Threading.Tasks;

class Program

{

static async Task AsyncTask1()

{

Console.WriteLine(\"Async Task 1 started\");

await Task.Delay(2000); // Adding Some Delay

Console.WriteLine(\"Async Task 1 completed\");

}

static async Task AsyncTask2()

{

Console.WriteLine(\"Async Task 2 started\");

await Task.Delay(1000); // Adding Some Delay

Console.WriteLine(\"Async Task 2 completed\");

}

static async Task Main(string\[\] args)

{

await Task.WhenAll(AsyncTask1(), AsyncTask2());

}

}
```

# 4.where Does it need to be implemented?

### Synchronous Programming:

1.  **Image Processing Pipeline:** This is useful when processing steps
    must be completed in a specific order without overlap.

2.  **Daily Report Generation:** Ideal for batch jobs where each task
    depends on the successful completion of the previous one.

### Asynchronous Programming

1.  **Smart Home System:** Keeps the system responsive and can handle
    multiple sensor readings without delay.

2.  **Real-Time Collaboration Tool:** Ensures a smooth and responsive
    experience for all users simultaneously editing the document For
    Example ( Notion , Excel and Word Live Share ) Etc...

And many other examples

# Conclusion:

Understanding the difference between synchronous and asynchronous
programming is super important for writing software that\'s both
efficient and responsive. Synchronous programming is straightforward and
easy to grasp, but it can be pretty slow when We have tasks that take a
long time. On the other hand, asynchronous programming let us handle
multiple tasks at once, which is key for making apps that are quick and
scalable. By picking the right approach for what we're working on, we
can create software that\'s both powerful and efficient.
