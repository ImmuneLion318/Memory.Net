# 📦 Memory.Net
> **Memory.Net** - .Net C# Memory Manipulation & Exploitation Library, With Features Such As Pattern Scanning, Memory Basic Manipulation, Disassembly, Thread & Module Manipulation And Much More.

**Memory.Net** - Documentation
--
```cs
using Memory.Net;
using Memory.Net.Type; /* For Premade Type Target, Module, Thread. */

/* Note : Memory.Net Implements IDisposable. */

/* Memory.Net Implements Multiple Directives To Creating An Instance And Using It 
You Can Pass Parameters To The Constructor Or Set The Target In The Object Initializer 
Both Of These Are Shown As Example Below. */

/* #1. Constructor */
MemoryFactory Memory = new MemoryFactory("Application"); 
/* Keep In Mind MemoryFactor's Constructor Has Multiple Overloads For Process, 
Process Id, Process Name, And The Target Premade Type. */

/* #2 Object Initializer */
Target Victim = new Target(000).Open(); /* 000 = Process Id */

MemoryFactory Memory = new MemoryFactory
{
	Target = Victim
};

/* At The End Of Operations Ensure The Disposal Of MemoryFactory. */
```
Using The Instance Created You Can Proceed To Call And Use Memory.Net's Functions To The Fullest Extent Some Examples Are Shown Below
```cs
Target Victim = new Target(000).Open(); /* 000 = Process Id */

MemoryFactory Memory = new MemoryFactory
{
	Target = Victim
};

IntPtr Allocation = Memory.Allocate(1024) /* Allocate 1 Megabyte */

bool Out = Memory.Write(Allocation, "Hello World, From Memory.Net");
if (Out != true)
	throw new Exception("Failed To Write To Memory");

string Data = Memory.Read<string>(Allocation, 1024);
/* Should Contain "Hello World, From Memory.Net" */
```