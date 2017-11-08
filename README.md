# wait
An obsessively simple and performant library for protecting critical sections.

[![NuGet](https://img.shields.io/nuget/dt/wait.svg)](https://www.nuget.org/packages/wait/)


Let's look at some examples! Wait can be used using `Wait.On()` or `Wait.GetWaiter()`.

#### Wait.On()
```
Wait.On("critical section", () =>
{
	// Critical Section
	// Only one "critical section" will run at a time
});

new Thread(() =>
{
	Wait.On("critical section", () =>
	{
		// Critical Section
		// Only one "critical section" will run at a time
	});
}).Start();
```

#### Wait.GetWaiter()
```
Waiter waiter = Wait.GetWaiter();

new Thread(() =>
{
	// Downloading
	waiter.Done();
}).Start();

waiter.WaitUntilDone();
// Download is done
```