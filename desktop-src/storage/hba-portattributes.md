---
title: HBA\_PortAttributes structure
description: The structure is used by the HBA\_GetPortAttributesByWWN fibre channel HBA library routine to report the attributes for a specified remote fibre channel port.
ms.assetid: 7628c68b-b851-4b41-a86b-aa54e7cd6ddf
keywords:
- HBA_PortAttributes structure Storage Devices
- HBA_PORTATTRIBUTES structure Storage Devices
- PHBA_PORTATTRIBUTES structure pointer Storage Devices
topic_type:
- apiref
api_name:
- HBA_PORTATTRIBUTES
api_location:
- hbaapi.h
api_type:
- HeaderDef
ms.technology: desktop
ms.prod: windows
ms.author: windowssdkdev
ms.topic: structure
ms.date: 05/31/2018
---

# HBA\_PortAttributes structure

The structure is used by the [**HBA\_GetPortAttributesByWWN**](hba-getportattributesbywwn.md) fibre channel HBA library routine to report the attributes for a specified remote fibre channel port.

## Syntax


```C++
typedef struct HBA_PortAttributes {
  HBA_WWN       NodeWWN;
  HBA_WWN       PortWWN;
  HBA_UINT32    PortFcId;
  HBA_PORTTYPE  PortType;
  HBA_PORTSTATE PortState;
  HBA_COS       PortSupportedClassofService;
  HBA_FC4TYPES  PortSupportedFc4Types;
  HBA_FC4TYPES  PortActiveFc4Types;
  char          PortSymbolicName[256];
  char          OSDeviceName[256];
  HBA_PORTSPEED PortSupportedSpeed;
  HBA_PORTSPEED PortSpeed;
  HBA_UINT32    PortMaxFrameSize;
  HBA_WWN       FabricName;
  HBA_UINT32    NumberofDiscoveredPorts;
} HBA_PORTATTRIBUTES, *PHBA_PORTATTRIBUTES;
```



## Members

<dl> <dt>

**NodeWWN**
</dt> <dd>

Contains a 64 bit world-wide name (WWN) that uniquely identifies the fibre channel node associated with **PortWWN**. For a discussion of worldwide names, see the T11 committee's *Fibre Channel HBA API* specification.

</dd> <dt>

**PortWWN**
</dt> <dd>

Contains a 64 bit world-wide name (WWN) that uniquely identifies the fibre channel port. For a discussion of worldwide names, see the T11 committee's *Fibre Channel HBA API* specification.

</dd> <dt>

**PortFcId**
</dt> <dd>

Contains the current fibre channel address of **PortWWN**. The high order byte of this member contains the first byte of the address, and successively lower order bytes of this member contain successively lower bytes of the address. The lowest order byte of this member must be zero.

</dd> <dt>

**PortType**
</dt> <dd>

Indicates the port type. This member must have one of the following values:



| Value                                | Meaning                                    |
|--------------------------------------|--------------------------------------------|
| HBA\_PORTTYPE\_UNKNOWN<br/>    | Unknown port type. <br/>             |
| HBA\_PORTTYPE\_OTHER<br/>      | Value that is not a port type. <br/> |
| HBA\_PORTTYPE\_NOTPRESENT<br/> | Port not present.<br/>               |
| HBA\_PORTTYPE\_NPORT<br/>      | Fabric. <br/>                        |
| HBA\_PORTTYPE\_NLPORT<br/>     | Public loop.<br/>                    |
| HBA\_PORTTYPE\_FLPORT<br/>     | Fabric on a loop. <br/>              |
| HBA\_PORTTYPE\_FPORT<br/>      | Fabric port. <br/>                   |
| HBA\_PORTTYPE\_EPORT<br/>      | Fabric expansion port. <br/>         |
| HBA\_PORTTYPE\_GPORT<br/>      | Generic Fabric. <br/>                |
| HBA\_PORTTYPE\_LPORT<br/>      | Private loop port. <br/>             |
| HBA\_PORTTYPE\_PTP<br/>        | Point to point. <br/>                |



 

</dd> <dt>

**PortState**
</dt> <dd>

Contains the state of the port indicated by **PortWWN**. This member must have one of the following values:



| Value                                  | Meaning                         |
|----------------------------------------|---------------------------------|
| HBA\_PORTSTATE\_UNKNOWN<br/>     | Unknown. <br/>            |
| HBA\_PORTSTATE\_ONLINE<br/>      | Operational. <br/>        |
| HBA\_PORTSTATE\_OFFLINE<br/>     | User Offline<br/>         |
| HBA\_PORTSTATE\_BYPASSED<br/>    | Bypassed. <br/>           |
| HBA\_PORTSTATE\_DIAGNOSTICS<br/> | In diagnostics mode.<br/> |
| HBA\_PORTSTATE\_LINKDOWN<br/>    | Link Down<br/>            |
| HBA\_PORTSTATE\_ERROR<br/>       | Port Error. <br/>         |
| HBA\_PORTSTATE\_LOOPBACK<br/>    | Loopback. <br/>           |



 

</dd> <dt>

**PortSupportedClassofService**
</dt> <dd>

Indicates the class of service that are supported by **PortWWN**. For a list of the differences classes of service and the values that must be assigned to this member for each class, see the ANSI standard for *Fibre Channel Generic Services 4th Generation* (FC-GS-4).

</dd> <dt>

**PortSupportedFc4Types**
</dt> <dd>

Contains a structure of type [**HBA\_fc4types**](hba-fc4types.md) that indicates the FC-4 types that are supported by **PortWWN**. For a discussion FC-4 types, see the ANSI standard for *Fibre Channel Generic Services 4th Generation* (FC-GS-4).

</dd> <dt>

**PortActiveFc4Types**
</dt> <dd>

Contains a structure of type [**HBA\_fc4types**](hba-fc4types.md) that indicates the FC-4 types that are currently available on **PortWWN**. For a discussion FC-4 types, see the ANSI standard for *Fibre Channel Generic Services 4th Generation* (FC-GS-4).

</dd> <dt>

**PortSymbolicName**
</dt> <dd>

Contains the symbolic name of the port.

</dd> <dt>

**OSDeviceName**
</dt> <dd></dd> <dt>

**PortSupportedSpeed**
</dt> <dd>

Indicates the signaling bit rates at which **PortWWN** can operate. For a list of the values that this member supports, see **PortSpeed**.

</dd> <dt>

**PortSpeed**
</dt> <dd>

Indicates the signaling bit rates at which **PortWWN** is currently operating. This member must have one of the following values:



| Value                                      | Meaning                                                                            |
|--------------------------------------------|------------------------------------------------------------------------------------|
| HBA\_PORTSPEED\_UNKNOWN<br/>         | Speed unknown. The transceiver is incapable of reporting the speed. <br/>    |
| HBA\_PORTSPEED\_1GBIT<br/>           | 1 gigabit per sec<br/>                                                       |
| HBA\_PORTSPEED\_2GBIT<br/>           | 2 gigabits per sec<br/>                                                      |
| HBA\_PORTSPEED\_10GBIT<br/>          | 10 gigabits per sec<br/>                                                     |
| HBA\_PORTSPEED\_4GBIT<br/>           | 4 gigabits per sec<br/>                                                      |
| HBA\_PORTSPEED\_NOT\_NEGOTIATED<br/> | The speed at which the port will operate has not yet been established. <br/> |



 

</dd> <dt>

**PortMaxFrameSize**
</dt> <dd>

Indicates the maximum frame size, in bytes, that is supported by **PortWWN**.

</dd> <dt>

**FabricName**
</dt> <dd>

Contains the name identifier for the fabric to which **PortWWN** is attached.

</dd> <dt>

**NumberofDiscoveredPorts**
</dt> <dd>

Indicates the number of ports that are visible to **PortWWN**. For a more detailed explanation of the sorts of ports that this number takes into consideration, see the T11 committee's specification for *Fibre Channel HBA API* (FC-HBA).

</dd> </dl>

## Remarks

The HBA\_PortAttributes structure serves a purpose very similar to the MSFC\_HBAPortAttributesResults structure that the [**GetDiscoveredPortAttributes**](https://msdn.microsoft.com/library/windows/hardware/ff553925) WMI method to report port attributes.

## Requirements



|                   |                                                                                                        |
|-------------------|--------------------------------------------------------------------------------------------------------|
| Header<br/> | <dl> <dt>Hbaapi.h (include Hbaapi.h)</dt> </dl> |



## See also

<dl> <dt>

[**GetDiscoveredPortAttributes**](https://msdn.microsoft.com/library/windows/hardware/ff553925)
</dt> <dt>

[**HBA\_GetPortAttributesByWWN**](hba-getportattributesbywwn.md)
</dt> </dl>

 

 

[Send comments about this topic to Microsoft](mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bstorage\storage%5D:%20HBA_PortAttributes%20structure%20%20RELEASE:%20%283/29/2018%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "Send comments about this topic to Microsoft")





