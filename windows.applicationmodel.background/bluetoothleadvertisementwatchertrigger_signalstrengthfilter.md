---
-api-type: winrt property
---
 **InRangeThresholdInDBm**: The maximum value for RSSI for Bluetooth LE is +20. The minimum value for RSSI for Bluetooth LE is -127 (default when NULL is -127).
 **OutOfRangeThresholdInDBm**: The maximum value for RSSI for Bluetooth LE is +20. The maximim value for RSSI for Bluetooth LE is -127 (default when NULL is -127).
 **OutOfRangeTimeout**: Equal or greater than 1 second and less than or equal to 60 seconds (default when NULL is 60 seconds).
 **SamplingInterval**: Equal or greater than 1 second. Any sampling interval greater or equal to 25.5 seconds will disable sampling entirely. In that special case, the filtering is trigger-based. For more information about the behavior of the RSSI filtering, refer to [BluetoothSignalStrengthFilter](../windows.devices.bluetooth/bluetoothsignalstrengthfilter.md).