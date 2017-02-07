---
-api-id: T:Windows.Foundation.Collections.IPropertySet
-api-type: winrt interface
---

<!-- Interface syntax.
public interface IPropertySet : Windows.Foundation.Collections.IIterable<Windows.Foundation.Collections.IKeyValuePair<System.String, System.Object>>, Windows.Foundation.Collections.IMap<System.String, System.Object>, Windows.Foundation.Collections.IObservableMap<System.String, System.Object>
-->

# Windows.Foundation.Collections.IPropertySet

## -description
Represents a collection of key-value pairs, correlating several other collection interfaces.

## -remarks
This interface is unusual in that it doesn't define any new members. Instead, it correlates three other collection interfaces such that they share the same type parameter constraints:
+ [IIterable](iiterable_1.md) (constraint [IKeyValuePair](ikeyvaluepair_2.md), with inner constraint of **String**, **Object**)
+ [IMap](imap_2.md) (constraint **String**, **Object**)
+ [IObservableMap](iobservablemap_2.md) (constraint **String**, **Object**)


If you cast an object to [IPropertySet](ipropertyset.md) (which isn't a generic) you can then use the combined methods of these three interfaces based on using **String** for key, **Object** for value. For a practical implementation, Windows Runtime uses the [PropertySet](propertyset.md) class. See the documentation for various members of [PropertySet](propertyset.md) to learn how to use those methods once you cast as [IPropertySet](ipropertyset.md).

In many cases where a Windows Runtime API uses a [PropertySet](propertyset.md) as a value, it's actually shown as [IPropertySet](ipropertyset.md) in the signatures. [PropertySet](propertyset.md) can be considered the practical implementation of [IPropertySet](ipropertyset.md) that's ready for use by app code. JavaScript code can treat any [IPropertySet](ipropertyset.md) value as if it implemented the [PropertySet](propertyset.md) prototypes. Usage by type is the main scenario for [IPropertySet](ipropertyset.md); actually implementing the interface in your app code is less common.

[IPropertySet](ipropertyset.md) is also implemented by the [ValueSet](valueset.md) class. [ValueSet](valueset.md) is the value type of several **ContinuationData** properties, which enable restoring state when apps resume after calling an **AndContinue** method that might deactivate the app. [ValueSet](valueset.md) and all the **ContinuationData** properties and **AndContinue** methods are Windows Phone only APIs because it's only Windows Phone that has this behavior. For more info, see [How to continue your  after calling an AndContinue method](http://msdn.microsoft.com/library/3398d631-ff80-4336-be45-8ee3ea96fbdb). The difference between [ValueSet](valueset.md) and [PropertySet](propertyset.md) is that the [ValueSet](valueset.md) implementation of methods like [Insert](valueset_insert.md)/[Add](valueset_add_1.md) enforces that its property values are value types.

## -examples
This example shows how to check for an item within the [IPropertySet](ipropertyset.md) object returned by a Windows Runtime property. Specifically, this is from the [CoreApplication.Properties](../windows.applicationmodel.core/coreapplication_properties.md) property. This code snippet comes from the [ControlChannelT​rigger HTTP client sample](http://go.microsoft.com/fwlink/p/?linkid=258323). Note how the C# version casts to [IDictionary&lt;string,object&gt;](XREF:TODO:T:System.Collections.Generic.IDictionary`2) so that it can use the indexer, whereas the Visual C++ component extensions (C++/CX) version uses [HasKey](propertyset_haskey.md) and [Lookup](propertyset_lookup.md). Typically this is all you do with an [IPropertySet](ipropertyset.md) object that you get from the various Windows Runtime properties that return the type: look for specific keys in the property set, and then set some app property to the corresponding value if it exists.

```csharp
            // In this example, the channel name has been hardcoded to lookup the property bag 
            // for any previous contexts. The channel name may be used in more sophisticated ways 
            // in case an app has multiple ControlChannelTrigger objects. 
            string channelId = "channelOne"; 
            if (((IDictionary<string, object>)CoreApplication.Properties).ContainsKey(channelId)) 
            { 
                try 
                { 
                    AppContext appContext = null; 
                    lock (CoreApplication.Properties) 
                    { 
                        appContext = ((IDictionary<string, object>)CoreApplication.Properties)[channelId] as AppContext; 
                    } 
                    if (appContext != null && appContext.CommunicationInstance != null) 
                    { 
                        CommunicationModule communicationInstance = appContext.CommunicationInstance; 
 
                        // Clear any existing channels, sockets etc. 
                        communicationInstance.Reset(); 
 
                        // Create CCT enabled transport. 
                        communicationInstance.SetUpTransport(communicationInstance.serverUri, GetType().Name); 
                    } 
                } 
                catch (Exception ex) 
                { 
                    Diag.DebugPrint("Registering with CCT failed with: " + ex.ToString()); 
                } 
            } 
            else 
            { 
                Diag.DebugPrint("Cannot find AppContext key channelOne"); 
            } 

```

```cpp
    // In this example, the channel name has been hardcoded to look up the property bag 
    // for any previous contexts. The channel name may be used in more sophisticated ways 
    // in case an app has multiple ControlChannelTrigger objects. 
    String^ channelId = "channelOne"; 
    if (CoreApplication::Properties->HasKey(channelId)) 
    { 
        try 
        { 
            auto appContext = dynamic_cast<AppContext^>(CoreApplication::Properties->Lookup(channelId)); 
            if (appContext != nullptr && appContext->CommunicationInstance != nullptr) 
            { 
                CommunicationModule^ communicationInstance = appContext->CommunicationInstance; 
                 
                // Clear any existing channels, sockets etc. 
                communicationInstance->Reset(); 
                 
                // Create CCT enabled transport 
                communicationInstance->SetUpTransport("NetworkChangeTask"); 
            } 
        } 
        catch (Exception^ ex) 
        { 
            Diag::DebugPrint("Registering with CCT failed with: " + ex->Message); 
        } 
    } 
    else 
    { 
        Diag::DebugPrint("Cannot find AppContext key channelOne"); 
    } 

```



## -see-also
[PropertySet](propertyset.md)