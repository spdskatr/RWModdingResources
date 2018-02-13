# RimWorld Saving For Dummies

## Introduction
Saving is mainly done through overriding a virtual `ExposeData` method. In various classes, this method is called `CompExposeData` or `PostExposeData`. Most classes have this method, including `Thing`, `ThingComp`, `HediffComp`, `LordJob`, `JobDriver` and its derivatives.

```cs
public override void ExposeData()
{
}
```

In this method, we use various `Scribe` methods to save individual values.

The first parameter to most `Scribe` methods is a reference to the item you want to save. You pass the first parameter by reference, i.e. `ref myItem`

The second parameter to most `Scribe` methods, often called `label`, is the save key that you want to use to save the item. It must be unique and will appear in the save file.

## Saving Simple Values
Most simple values are saved using Scribe_Values. This class allows you to save a variety of primitives including:
- .NET Primitive Types (int, float, ushort, double, bool, char)
- Enum Types (AltitudeLayer, BindingFlags, PawnHealthState)
- Strings
- System.Type
- Vector Types (IntVec3, IntVec2, Vector3, Vector2)
- Rect, Color, ColorInt, Rot4, CellRect, CurvePoint
- FloatRange, IntRange, QualityRange
- PublishedFileId_t (Why would you want to use this?)

Use of this method: 
```cs
int foo;
string bar;
PublishedFileId_t baz;
Scribe_Values.Look(ref foo, "foo", 10); // When loading, if there is no entry of the value of foo, set it to 10
Scribe_Values.Look(ref bar, "bar"); // Simple example
Scribe_Values.Look(ref baz, "baz", new PublishedFileId_t(987654321)， true); // When loading, if there is no entry of the value of foo, set it to new PublishedFileId_t(987654321). Also force save the value
```

## Saving References to Defs
You can save references to Defs! Simply specify the field your def is in, and the save label.

```cs
Scribe_Defs.Look(ref myDef, "myDef");
```

## Saving Things
`Thing` is the base class of many important types, such as `Pawn`, `Building`, `Mote` and `Plant`. Things can be saved in two ways:
- By saving them as ILoadReferenceable (If they are spawned, or they are saved somewhere else)
- By saving them as IExposable (If they are not spawned or saved anywhere else)

## Saving IExposable
Classes that implement `IExposable` have multiple saveable parts that all need saved. If the item implements IExposable (and it isn't saved anywhere else), it can be saved with `Scribe_Deep`. There is also an optional `saveDestroyedThings` argument.

When IExposable items are instantiated, some need parameters in their constructor. You can specify the constructor arguments in the `ctorArgs` argument.
```cs
Scribe_Deep.Look(ref myExposable, "myExposable");
Scribe_Deep.Look(ref myOtherExposable, true, "myOtherExposable", this); // Saves myOtherExposable even if destroyed, and passes `this` to the constructor.
```

## Saving ILoadReferenceables
You can save references to classes that implement `ILoadReferenceable`. However, the object has to be saved somewhere else as well for this to work. This is useful for preserving references to items, pawns and buildings that are already spawned.

```cs
Scribe_References.Look(ref myReference, "myReference"); // Save the reference, unless destroyed.
Scribe_References.Look(ref myReference, "myReference", true); // Save the reference, even if destroyed.
```

## Saving TargetInfo
TargetInfo, LocalTargetInfo and GlobalTargetInfo are special types that point to a thing, location or world object. They can be saved with `Scribe_TargetInfo`. There are two optional parameters you can pass that allow you to specify whether you want to save destroyed things or have a default value.

```cs
Scribe_TargetInfo.Look(ref myLocation, "target");
```

## Saving Collections
Some collections, like List, Dictionary and HashSet can be saved as well. Their basic signature is similar, but you have to make sure the individual elements of the collection are also saveable, and specify which mode they can be saved in.

For dictionaries, if one of the elements (not both) has look mode `Reference`, then you must also provide two lists along with the dictionary to save. 

```cs
List<string> list1;
Dictionary<string, LocalTargetInfo> dict1;
Dictionary<Faction, int> dict2;
List<Faction> list2;
List<int> list3;
Stack<Thing> stack1;

Scribe_Collections.Look(ref list1, "list1", LookMode.Value);
Scribe_Collections.Look(ref dict1, "dict1", LookMode.Value, LookMode.TargetInfo);
Scribe_Collections.Look(ref dict2, "dict2", LookMode.Reference, LookMode.Value, ref list2, ref list3);
Scribe_Collections.Look(ref stack1, "stack1", LookMode.Reference);
```