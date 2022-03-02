---
uid: GetActiveAlarmsV2
---

# GetActiveAlarmsV2

Use this method to retrieve all the active alarms along with the alarm cache status.

Available from DataMiner 10.0.7 onwards.

## Input

| Item       | Format | Description                                          |
|------------|--------|------------------------------------------------------|
| Connection | String | The connection ID. See [ConnectApp](xref:ConnectApp) . |

## Output

| Item                     | Format                                                                   | Description                                                   |
|--------------------------|--------------------------------------------------------------------------|---------------------------------------------------------------|
| GetActiveAlarmsV2­Result | Array of DMAAlarm (see [DMAAlarm](xref:DMAAlarm)) | The list of active alarms, as well as the alarm cache status. |
