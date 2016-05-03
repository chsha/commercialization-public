---
author: joshbax-msft
title: HybridPowerManagement\_AppIdle
description: HybridPowerManagement\_AppIdle
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 46885bbe-313a-43ca-81cf-72c776fc7fd6
---

# HybridPowerManagement\_AppIdle


Power management tests run on dGPU while analyzing Power-Management ETW events that are generated by DXGKrnl. For this test, an application is running on DGPU, but it is idle and nothing has been rendered for some time. The test performs following validations:

-   Validation of Power components – the test validates that all required power components are declared by the driver.

-   Validation of latency – the driver reports latency (time for a component to transition to another F-state). The test checks that this number matches the actual latency.

-   Validate Active/Idle state of the component – checks that power components are in expected Active/Idle state (based on the test scenario).

-   Validate DState – checks that DGPU is in expected D state (based on the test scenario).

-   Validate DGPU process – checks which processes have devices on DGPU. Anything other than the test itself will result in failure.

## Test details


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Associated requirements</strong></p></td>
<td><p>System.Fundamentals.Graphics.HybridGraphics.MultiGPU</p>
<p>[See the system hardware requirements.](http://go.microsoft.com/fwlink/p/?linkid=254482)</p></td>
</tr>
<tr class="even">
<td><p><strong>Platforms</strong></p></td>
<td><p>Windows RT 8.1 Windows 8.1 x64 Windows 8.1 x86 Windows Server 2012 R2</p></td>
</tr>
<tr class="odd">
<td><p><strong>Expected run time</strong></p></td>
<td><p>~30 minutes</p></td>
</tr>
<tr class="even">
<td><p><strong>Categories</strong></p></td>
<td><p>Certification Functional</p></td>
</tr>
<tr class="odd">
<td><p><strong>Type</strong></p></td>
<td><p>Automated</p></td>
</tr>
</tbody>
</table>

 

## Running the test


Before you run the test, complete the test setup as described in the test requirements: [WDTF System Fundamentals Testing Prerequisites](wdtf-system-fundamentals-testing-prerequisites.md).

## Troubleshooting


For troubleshooting information, see [Troubleshooting System Fundamentals Testing](troubleshooting-system-fundamentals-testing.md).

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Error</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Conformance issues</p></td>
<td><p>When the test detects a conformance issue, it saves an image in the test directory if the <strong>-saveBMP</strong> parameter is specified. You can view this image to help diagnose the issue.</p></td>
</tr>
<tr class="even">
<td><p>Validation failures</p></td>
<td><p>To get more information about the failure, run the test under User Mode Debugger. The test will output the information that it gets from ETW events, to help diagnose the failure.</p></td>
</tr>
</tbody>
</table>

 

## More information


### Command syntax

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Parameter</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>-saveBMP</strong></p></td>
<td><p>By using this parameter, the test saves presented images in BMP format to the test directory in case of conformance failure. This is useful for diagnosing conformance failures.</p></td>
</tr>
<tr class="even">
<td><p><strong>-whql | -featurelevel:&lt;fl&gt;</strong></p></td>
<td><p><strong>-whql</strong> results in device creation with highest support on a given adapter. <strong>–featurelevel:&lt;fl&gt;</strong> creates a device of requested feature level</p>
<p>Default value: <strong>-wqhl</strong> for DX10+ drivers; <strong>-featurelevel</strong>:9.1 for DX9 drivers</p></td>
</tr>
<tr class="odd">
<td><p><strong>-hybrid</strong></p></td>
<td><p>This value forces application execution on dGPU as if it was on the DList.</p></td>
</tr>
</tbody>
</table>

 

 

 

[Send comments about this topic to Microsoft](mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bp_hck\p_hck%5D:%20HybridPowerManagement_AppIdle%20%20RELEASE:%20%284/27/2016%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "Send comments about this topic to Microsoft")



