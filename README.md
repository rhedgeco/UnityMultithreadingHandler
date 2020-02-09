﻿# Unity Multithreading Handler
A simple script setup to inherit and quickly start multithreading in Unity Engine.

## Installation
Either clone this repo into your unity project or use the provided [UnityMultithreadingHandler.unitypackage](https://example.com)

## How to use
Create a class that inherits from ThreadWorker
```c#
using UnityMultithreading;

public class ExampleThreadWorker : ThreadWorker
{
    public ExampleThreadWorker()
    {
        // Add methods as listeners to have information update
        // These listeners will be called on the main thread
        OnStartWorker.AddListener(ExampleStartProcess);
        OnUpdateWorker.AddListener(ExampleUpdateProcess);
        OnCloseWorker.AddListener(ExampleCloseProcess);
        OnErrorWorker.AddListener(ExampleErrorProcess);
    }

    // Only work done in here will be run on seperate thread
    protected override void WorkBody()
    {
        // work to be done
    }

    private void ExampleStartProcess()
    {
    }

    private void ExampleUpdateProcess()
    {
    }

    private void ExampleCloseProcess()
    {
    }

    private void ExampleErrorProcess()
    {
    }
}
```

The work body is where all your off main thread processing will go.

Use the provided callbacks to make updates happen on the main thread.