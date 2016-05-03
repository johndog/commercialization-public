---
author: joshbax-msft
title: SCSI Enclosure Services (SES) Device Testing Prerequisites
description: SCSI Enclosure Services (SES) Device Testing Prerequisites
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: ffb50e5b-9ff3-4fee-b102-1af160f87cc6
---

# SCSI Enclosure Services (SES) Device Testing Prerequisites


This topic describes the tasks that you must complete before you test a SES device by using the Windows Hardware Certification Kit (Windows HCK):

-   [Hardware Requirements](#bkmk-hardwarerequirements)

-   [Software Requirements](#bkmk-softwarerequirements)

-   [Configuring the Test Computer](#bkmk-configure)

## <a href="" id="bkmk-hardwarerequirements"></a>Hardware Requirements


To test a SES device, you need following hardware:

-   SES device with at least two ports that can be used to connected to servers

-   Two identical Host Bus Adapters (HBAs), each with at least one port

-   Two cables, each connected to one HBA port and to the SCSI Enclosure Storage target device

-   Must be fully loaded with hard disk drives in the SES device that can be accessed via the SES device

-   The CiB (Cluster in a Box) Continuously Available test requires a cluster configuration

## <a href="" id="bkmk-softwarerequirements"></a>Software Requirements


To test a SES device, you need the following software:

-   Drivers for hardware devices, if required

-   The latest Windows HCK filters or updates

## <a href="" id="bkmk-configure"></a>Configuring the Test Computer


To configure the test computer for your test device, follow these steps:

1.  Use an appropriate OS installation.

2.  Install HCK Controller and HCK Studio on the Test Server.

3.  Install HCK Client on computers where you intend to run the test.

4.  Select the SES device that you want to test.

5.  Select a disk device contained in the SES device.

6.  On the Test Computer, go to **Disk Management** to ensure that the disk you have selected in the HCK is online. You need a formatted volume on the disk you have selected to successfully pass all tests.

7.  Ensure that the test computer is in **Ready** state before you begin testing. If you do not change the machine status to **Ready**, the tests will not run. You cannot change the machine status to **Ready** while it is in the Default Pool. You need to move the machine to the new pool that you have created before you can do this.

 

 

[Send comments about this topic to Microsoft](mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bp_hck\p_hck%5D:%20SCSI%20Enclosure%20Services%20%28SES%29%20Device%20Testing%20Prerequisites%20%20RELEASE:%20%284/27/2016%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "Send comments about this topic to Microsoft")



