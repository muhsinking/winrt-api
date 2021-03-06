---
-api-id: T:Windows.Perception.Spatial.Surfaces.SpatialSurfaceInfo
-api-type: winrt class
---

<!-- Class syntax.
public class SpatialSurfaceInfo : Windows.Perception.Spatial.Surfaces.ISpatialSurfaceInfo
-->

# Windows.Perception.Spatial.Surfaces.SpatialSurfaceInfo

## -description
Represents a snapshot of metadata for a surface observed in the user's surroundings.

## -remarks
Mesh objects contain large vertex and index buffers, and so they're heavy to hold onto if you don't have good reason. For efficient use in rendering or physics, an app is expected to cache the mesh and buffer objects it's interested in, and to throw out mesh for areas where the user is no longer operating.

You can use the set of SpatialSurfaceInfo instances given to you by SpatialSurfaceObserver, representing what mesh is present in the targeted bounding volume, in order to manage your cache.

Correlating the Id and UpdateTime properties across multiple observations lets you identify new mesh, updated mesh and removed mesh:

If you see a SpatialSurfaceInfo with an Id you haven't seen before, treat it as new mesh.

If you see a SpatialSurfaceInfo with a known Id, but with a new UpdateTime, treat it as updated mesh.

If you no longer see a SpatialSurfaceInfo with a known Id, treat it as removed mesh.

Because this is a snapshot, the UpdateTime property will not change over time. To see if this surface's mesh has updated, or whether a surface has been removed or moved out of the bounding volume, return to the SpatialSurfaceObserver and either call GetObservedSurfaces each frame or handle the ObservedSurfacesChanged event.

## -examples

## -see-also
