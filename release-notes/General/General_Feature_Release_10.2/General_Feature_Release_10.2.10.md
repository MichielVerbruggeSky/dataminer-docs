---
uid: General_Feature_Release_10.2.10
---

# General Feature Release 10.2.10 – Preview

> [!IMPORTANT]
> We are still working on this release. Some release notes may still be modified or moved to a later release. Check back soon for updates!

> [!TIP]
> For release notes related to DataMiner Cube, see [DataMiner Cube 10.2.10](xref:Cube_Feature_Release_10.2.10).

## Highlights

#### Clearing an incident now clears any clearable base alarms it contains [ID_34112]

<!-- MR 10.3.0 - FR 10.2.10 -->

If an incident (also known as an alarm group) is cleared manually, any clearable base alarms of that incident will now also be cleared. This way, this behavior is consistent with the standard behavior for Correlation alarms.

#### Dashboards / Low-Code Apps: Parameter table component brought in line with Table component [ID_34132]

<!-- MR 10.3.0 - FR 10.2.10 -->

The *Parameter table* component of dashboards and low-code apps has now been adjusted to be more like that generic *Table* component. In addition to improving consistency between these components, this also makes the *Parameter table* component more user-friendly:

- The horizontal scrollbar is now permanently displayed, while previously you had to scroll all the way to the bottom of the table to see it.
- The table will load more easily, improving performance of the dashboard or app especially with large tables.

Moreover, the additional features of the *Table* component will now also be available for the *Parameter table* component:

- Grouping on one or multiple columns.
- Sorting based on multiple columns.
- Filtering on multiple columns via the column header context menu.
- Filtering using the search box below the table.
- Resizing columns.
- Dragging and dropping columns to change the column order.

> [!NOTE]
> This change does not affect the *Parameter table* component as viewed on mobile devices.

## Other features

#### Dashboards / Low-Code Apps: Checkboxes to select discrete values in column filter Table component [ID_34234]

<!-- MR 10.3.0 - FR 10.2.9 -->

When you configure a column filter for a Table component in a dashboard or low-code app, you can now select checkboxes to filter on discrete values.

## Changes

### Enhancements

#### DataMiner Taskbar Utility: Enhanced installation of app packages [ID_33969]

<!-- MR 10.1.0 [CU19]/10.2.0 [CU7] - FR 10.2.10 -->

Using the DataMiner Taskbar Utility, it is now possible to install all possible types of app packages. To install an app, you can either double-click the .dmapp file or right-click the Taskbar Utility icon, click *Update* and select the app from the list.

Also, the *SLAppPackageInstaller.txt* log file will now keep track of all actions performed and issues encountered during the installation of an app.

#### Enhanced performance when an SNMP element using multi-threaded timers is polling multiple sources simultaneously [ID_34143]

<!-- MR 10.1.0 [CU19]/10.2.0 [CU7] - FR 10.2.10 -->

Because of a number of enhancements, overall performance has increased when an SNMP element using multi-threaded timers is polling multiple sources simultaneously.

#### Edge WebView2 now preferred when SAML authentication is used [ID_34162]

<!-- MR 10.2.0 [CU7] - FR 10.2.10 -->

When SAML authentication is used, Cube will now try to use the Edge WebView2 browser engine instead of CefSharp. It will only fall back to using CefSharp if WebView2 is not available.

This will prevent the following possible issues:

- The CefSharp browser engine version used by Cube is not updated frequently and therefore not always trusted by certain SAML identity provider websites, such as Microsoft Azure. This can cause a lengthy authentication procedure, even if the browser cache is enabled.
- The CefSharp browser engine needs to be downloaded from the DMA before a first authentication (on a new device). However, this is currently not supported for HTTPS-only setups.

#### Dashboards app / Low-Code apps: Conditional coloring layout configuration now uses numeric filter instead of numeric slider [ID_34174]

<!-- MR 10.3.0 - FR 10.2.10 -->
<!-- Part of this RN is still in soft launch and consequently has not been documented yet -->

In the conditional coloring layout setting for Table and Node edge components, the numeric slider control has been replaced with a numeric filter. This has the following advantages:

- Full control over the boundaries. You can indicate whether the start and end should be in- or excluded.
- Possibility to not have a start or end boundary.
- More consistent with the free text filter.
- Easier to define a precise filter.

#### Dashboards app / Low-Code apps: Conditional coloring layout filter configuration now shows discrete column values [ID_34182]

<!-- MR 10.3.0 - FR 10.2.10 -->
<!-- Part of this RN is still in soft launch and consequently has not been documented yet -->

In the conditional coloring layout setting for Table and Node edge components, discrete column values will now be displayed to make it easier to configure a filter.

#### Cassandra: Alarms indicating that the cluster is down will no longer be repeated as long as the status of the cluster remains the same [ID_34209]

<!-- MR 10.1.0 [CU19]/10.2.0 [CU7] - FR 10.2.10 -->

When the Cassandra database was down, up to now, the alarms indicating that the cluster is not in a healthy state would be repeated every 40 seconds. From now on, those alarms will no longer be repeated as long as the status of the cluster remains the same.

#### Enhanced logging of issues occurring when parsing a compliance cache file entry [ID_34212]

<!-- MR 10.0.0 [CU22]/10.1.0 [CU19]/10.2.0 [CU7] - FR 10.2.10 -->

When an issue occurred when parsing a compliance cache file entry, up to now, a log entry of type "error" would be added to the SLDataMiner.txt log file.

From now on, when an issue occurs when parsing a compliance cache file entry, the following log entry of type "info" will be added to the SLDataMiner.txt log file instead:

```txt
Warning: <function> is unable to parse compliance cache file entry at line <line number>. <line content>
```

#### DataMiner Upgrade: Obsolete 'SNMP Simulation Generator' files removed from upgrade packages [ID_34250]

<!-- MR 10.1.0 [CU19]/10.2.0 [CU7] - FR 10.2.10 -->

All files related to the obsolete *SNMP Simulation Generator* tool have been removed from the DataMiner upgrade packages. This tool was replaced by the *QA Device Simulator* tool.

> [!NOTE]
> When you run an upgrade package on a system that contains this obsolete tool, it will automatically be removed.

#### Dashboards app: Configuring themes in user settings now requires dashboard edit permission [ID_34260]

<!-- MR 10.2.0 [CU7] - FR 10.2.10 -->

In the user settings (*user icon > Settings*), from now on, you will only be able to configure themes when you have permission to edit dashboards.s

#### Low-code apps: Header bar enhancements [ID_34264]

<!-- MR 10.2.0 [CU7] - FR 10.2.10 -->

A number of small enhancements have been made to the header bar of low-code apps:

- Button text now supports both upper case and lower case.

- Buttons no longer have lines between them.

### Fixes

#### Service & Resource Management: Files in C:\Skyline DataMiner\ResourceManager would not be locked properly when being read or updated during a midnight synchronization [ID_34104]

<!-- MR 10.1.0 [CU19]/10.2.0 [CU7] - FR 10.2.10 -->

Up to now, the files stored in the `C:\Skyline DataMiner\ResourceManager` folder would not be locked properly when being read or updated during a midnight synchronization. File locking has now been improved.

#### Web apps - DOM: Sections inheriting from a parent behavior definition would not be taken into account when displaying a form [ID_34125]

<!-- MR 10.2.0 [CU7] - FR 10.2.10 -->

When, a DOM definition containing a behavior definition with inheritance enabled was used in a web app form, any sections inheriting from that parent behavior definition would not be taken into account when displaying that form.

#### SLNet could throw an OutOfMemoryException due to a memory leak [ID_34126]

<!-- MR 10.1.0 [CU19]/10.2.0 [CU7] - FR 10.2.10 -->

In some cases, SLNet could throw an OutOfMemoryException due to a memory leak.

#### Dashboards app: Incorrect user validation in 'User access' section of 'Settings' tab [ID_34138]

<!-- MR 10.2.0 [CU7] - FR 10.2.10 -->

When editing a dashboard, you can go to *Settings > User access* and specify the users and/or user groups that are allowed to view or edit the dashboard in question. When you did not have permission to change security settings, the users and user groups you entered would not be validated correctly.

#### Cassandra cluster: No trending information shown for parameters of which the value had not changed for 10 days or more [ID_34149]

<!-- MR 10.2.0 [CU7] - FR 10.2.10 -->

On a system with a Cassandra cluster, no trending information would be shown for parameters of which the value had not changed for 10 days or more.

#### Automation: Invalid script changes would incorrectly be saved [ID_34150]

<!-- MR 10.2.0 [CU7] - FR 10.2.10 -->

When, in the *Automation* app, you made an invalid change in a script, closed the app and clicked *Yes* to confirm the changes, up to now, the invalid changes you made would incorrectly be saved. If the invalid change was an invalid script name change, then the script would even be deleted. From now on, it will only be possible to save valid changes.

#### Scheduled alarm templates would incorrectly not be updated when the system time changed [ID_34154]

<!-- MR 10.1.0 [CU19]/10.2.0 [CU7] - FR 10.2.10 -->

When the system time changed because of e.g. a clock resynchronization or a switch to or from daylight-saving time, up to now, the start time and end time of scheduled alarm templates would incorrectly not get updated.

#### GQI: 'Bookings' data source incorrectly contained two 'Last modified at' columns [ID_34170]

<!-- MR 10.2.0 [CU7] - FR 10.2.10 -->

The GQI data source "Bookings" did not contain a *Last modified by* column and contained two different *Last modified at* columns (one with timestamps adjusted to the timezone and another with unadjusted timestamps). The *Last modified at* column containing unadjusted timestamps has now been replaced by a *Last modified by* column.

Also, the *Created at* and *Last modified at* columns will no longer be selected by default.

#### Dashboards app: Problem when trying to access a shared dashboard created in a previous version [ID_34210]

<!-- MR 10.2.0 [CU7] - FR 10.2.10 -->

When you tried to access a shared dashboard created in a previous version, the migration of the dashboard could get stuck because the Web API was unable to write the current Dashboards app version to the `C:\Skyline DataMiner\WebPages\dashboard\appversion.json` file.

#### Web apps: App would incorrectly log in again after the user had logged out [ID_34227]

<!-- MR 10.1.0 [CU19]/10.2.0 [CU7] - FR 10.2.10 -->

After a user had logged out of a web app, in some cases, that app would incorrectly continue to send out network requests and try to automatically log itself in again.

#### Run-time error in SLProtocol when a group was launched while a poll group with option 'PartialSNMP' was waiting for incoming SNMP data [ID_34233]

<!-- MR 10.1.0 [CU19]/10.2.0 [CU7] - FR 10.2.10 -->

When, on one thread, a group other than a poll group was launched while, on another thread, a poll group with option "partialSNMP" was waiting for incoming SNMP data, in some cases, a run-time error could occur in SLProtocol.

#### Low-code apps: Header bar font color would incorrectly not be aligned with the theme color of the app [ID_34267]

<!-- MR 10.2.0 [CU7] - FR 10.2.10 -->

In some cases, the header bar font color would incorrectly not be aligned with the theme color of the app.

#### Web apps - Query builder: Hovering over an arrow to change the column order in the select node would select an incorrect arrow [ID_34268]

<!-- MR 10.2.0 [CU7] - FR 10.2.10 -->

In the select node of the query builder, you can change the column order by clicking up and down arrows. Up to now, when you hovered over one of those arrows, in some cases, the incorrect arrow would be selected.

#### Dashboards app - Time range feed: Delete icons of custom quick pick buttons would incorrectly be displayed on top of the time range feed overlay [ID_34278]

<!-- MR 10.1.0 [CU19]/10.2.0 [CU7] - FR 10.2.10 -->

In some cases, the delete icons of custom quick pick buttons would incorrectly be displayed on top of the time range feed overlay.