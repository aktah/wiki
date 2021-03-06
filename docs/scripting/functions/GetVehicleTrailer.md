---
id: GetVehicleTrailer
title: GetVehicleTrailer
description: Get the ID of the trailer attached to a vehicle.
tags: ["vehicle"]
---

## Description

Get the ID of the trailer attached to a vehicle.

| Name      | Description                                  |
| --------- | -------------------------------------------- |
| vehicleid | The ID of the vehicle to get the trailer of. |

## Returns

The vehicle ID of the trailer or 0 if no trailer is attached.

## Examples

```c
new trailerid = GetVehicleTrailer(vehicleid);
DetachTrailerFromVehicle(trailerid);
```

## Notes

:::warning

This function does not work for trains.

:::

## Related Functions

- [AttachTrailerToVehicle](AttachTrailerToVehicle.md): Attach a trailer to a vehicle.
- [DetachTrailerFromVehicle](DetachTrailerFromVehicle.md): Detach a trailer from a vehicle.
- [IsTrailerAttachedToVehicle](IsTrailerAttachedToVehicle.md): Check if a trailer is attached to a vehicle.
