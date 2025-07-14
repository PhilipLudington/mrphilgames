---
layout: custom-post
title: "Strategy Pattern"
date: 2005-01-25
categories: programming
---

The Strategy Pattern allows flexibility in object behavior for game development. Here's a C# example that demonstrates how to encapsulate different behaviors for game objects (specifically ships) using interfaces and runtime behavior modification.

The strategy pattern allows different attack and fly behaviors to be defined and swapped dynamically:

```csharp
// Behavior interfaces
public interface AttackBehavior 
{
    void Attack();
}

public interface FlyBehavior 
{
    void Fly();
}

// Concrete attack behaviors
public class AttackWithRedLaser : AttackBehavior
{
    public void Attack()
    {
        // Red laser attack implementation
        Console.WriteLine("Firing red laser!");
    }
}

// Concrete fly behaviors  
public class FlyWithIonEngines : FlyBehavior
{
    public void Fly()
    {
        // Ion engine flight implementation
        Console.WriteLine("Flying with ion engines!");
    }
}

// Ship base class
public abstract class Ship
{
    protected AttackBehavior attackBehavior;
    protected FlyBehavior flyBehavior;
    
    public void SetAttackBehavior(AttackBehavior ab)
    {
        attackBehavior = ab;
    }
    
    public void SetFlyBehavior(FlyBehavior fb)
    {
        flyBehavior = fb;
    }
    
    public void PerformAttack()
    {
        attackBehavior.Attack();
    }
    
    public void PerformFly()
    {
        flyBehavior.Fly();
    }
}

// Concrete ship classes
public class TerranMarkI : Ship
{
    public TerranMarkI()
    {
        attackBehavior = new AttackWithRedLaser();
        flyBehavior = new FlyWithIonEngines();
    }
}

public class NeiwckronMkI : Ship
{
    public NeiwckronMkI()
    {
        // Different default behaviors
        attackBehavior = new AttackWithRedLaser();
        flyBehavior = new FlyWithIonEngines();
    }
}
```

Ships can change their behavior at runtime using `SetFlyBehavior()` and `SetAttackBehavior()`.

When I am not writing about making games, procrastinating or watching movies I'm working on a science fiction strategy game.