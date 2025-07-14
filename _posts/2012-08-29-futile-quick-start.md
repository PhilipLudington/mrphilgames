---
layout: post
title: "Futile Quick Start"
date: 2012-08-29
author: MrPhil
categories: [news, unity, development]
---

[Futile](http://struct.ca/futile/) is a framework that allows you to control rendering within Unity programmatically. This is a boon to anyone interested in 2D games and finds, like myself, that Unity impedes 2D game development.

## Steps:

1. Get [Futile from Github](http://github.com/MattRix/Futile)
2. Import the Futile.unitypackage into Unity project
3. Create an Empty GameObject called "Futile Camera"
4. Drag Futile script to the "Futile Camera" object
5. Add an image (example below)
6. Configure image texture settings
7. Create a new script "FunWithFutile.cs"
8. Add the code below to the script
9. Press play

![OMG IT SPINS]({{ '/assets/images/futile-spinning-example.jpg' | relative_url }})

```csharp
using UnityEngine;
using System.Collections;

public class FunWithFutile : MonoBehaviour, FutileUpdateDelegate
{
    void Start()
    {
        FutileParams fparams = new FutileParams(true, true, true, true);
        fparams.AddResolutionLevel(480.0f, 1.0f, 1.0f, "");
        fparams.origin = new Vector2(0.5f, 0.5f);
        
        Futile.instance.Init(fparams);
        Futile.atlasManager.LoadAtlas("Atlases/MyAtlas");
        Futile.instance.UpdateDelegate = this;
        
        Go.to(this, 1.0f, new TweenConfig().floatProp("rotation", 360.0f).setIterations(-1));
    }
    
    public void HandleFutileUpdate()
    {
        // Update logic here
    }
}
```

*Note: This post was imported from mrphilgames.com*