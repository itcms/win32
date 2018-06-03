---
title: CLUSCTL\_RESOURCE\_SET\_MAINTENANCE\_MODE control code
description: Enables or disables maintenance mode for the specified disk resource.
audience: developer
author: REDMOND\\markl
manager: REDMOND\\markl
ms.assetid: 211de9d9-7fcb-47b7-a6b3-ee1bc241f176
ms.prod: windows-server-dev
ms.technology: failover-clustering
ms.tgt_platform: multiple
keywords:
- CLUSCTL_RESOURCE_SET_MAINTENANCE_MODE control code Failover Cluster
topic_type:
- apiref
api_name:
- CLUSCTL_RESOURCE_SET_MAINTENANCE_MODE
api_location:
- ClusAPI.h
api_type:
- HeaderDef
ms.author: windowssdkdev
ms.topic: article
ms.date: 05/31/2018
---

# CLUSCTL\_RESOURCE\_SET\_MAINTENANCE\_MODE control code

Enables or disables [*maintenance mode*](https://www.bing.com/search?q=*maintenance mode*) for the specified disk resource. Applications use this [control code](about-control-codes.md) as a parameter to the [**ClusterResourceControl**](/previous-versions/windows/desktop/api/ClusAPI/nf-clusapi-clusterresourcecontrol) function.


```C++
ClusterResourceControl( hResource,                // resource handle
                        hHostNode,                // host node
                        CLUSCTL_RESOURCE_SET_MAINTENANCE_MODE, // control code
                        lpInBuffer,               // CLUS_MAINTENANCE_MODE_INFO
                        cbInBufferSize,           // allocated buffer size
                        NULL,                     // not used
                        0,                        // not used
                        NULL );                   // not used
```



## Parameters

The following control code function and DLL support parameters are specific to this control code. For complete parameter descriptions, see [**ClusterResourceControl**](/previous-versions/windows/desktop/api/ClusAPI/nf-clusapi-clusterresourcecontrol).

<dl> <dt>

*lpInBuffer* 
</dt> <dd>

Points to a [**CLUS\_MAINTENANCE\_MODE\_INFO**](/previous-versions/windows/desktop/api/ClusAPI/ns-clusapi-clus_maintenance_mode_info) structure containing the boolean flag used to enable or disable maintenance mode. Additional private data for the resource DLL may be included immediately after the **CLUS\_MAINTENANCE\_MODE\_INFO** structure, provided *cbInBufferSize* is adjusted appropriately.

</dd> </dl>

## Return value

[**ClusterResourceControl**](/previous-versions/windows/desktop/api/ClusAPI/nf-clusapi-clusterresourcecontrol) returns one of the following values:

<dl> <dt>

**ERROR\_SUCCESS**
</dt> <dd>

0

The property list is correctly formatted and contains valid data values.

</dd> <dt>

**ERROR\_INVALID\_FUNCTION**
</dt> <dd>

1

The disk resource DLL does not support maintenance mode.

</dd> <dt>

**ERROR\_INVALID\_PARAMETER**
</dt> <dd>

87 (0x57)

The [**CLUS\_MAINTENANCE\_MODE\_INFO**](/previous-versions/windows/desktop/api/ClusAPI/ns-clusapi-clus_maintenance_mode_info) structure pointed to by the *lpInBuffer* parameter is formatted incorrectly.

</dd> <dt>

**RPC\_X\_BAD\_STUB\_DATA**
</dt> <dd>

1783 (0x6F7)

The *lpInBuffer* parameter is **NULL**.

</dd> <dt>

**ERROR\_HOST\_NODE\_NOT\_RESOURCE\_OWNER**
</dt> <dd>

5015 (0x1397)

A disk resource not owned by the hosting node cannot be put into maintenance mode.

</dd> <dt>

**ERROR\_INVALID\_STATE**
</dt> <dd>

5023 (0x139F)

The disk resource is offline.

</dd> <dt>

**ERROR\_CLUSTER\_INVALID\_REQUEST**
</dt> <dd>

5048 (0x13B8)

A quorum resource cannot be put into maintenance mode.

</dd> <dt>

**[System error code](https://msdn.microsoft.com/library/windows/desktop/ms681381)**
</dt> <dd>

The operation failed.

</dd> </dl>

## Remarks

Only disk resources support maintenance mode.

A resource must be online and not identified as the quorum resource in order to be placed in maintenance mode.

The calling application must direct the maintenance mode resource control codes to the node hosting the resource.

ClusAPI.h defines the 32 bits of CLUSCTL\_RESOURCE\_SET\_MAINTENANCE\_MODE (0x014001e6) as follows:



| Component                 | Bit location     | Value                                                   |
|---------------------------|------------------|---------------------------------------------------------|
| Object code<br/>    | 24 31<br/> | **CLUS\_OBJECT\_RESOURCE** (0x1)<br/>             |
| Global bit<br/>     | 23<br/>    | **CLUS\_NOT\_GLOBAL** (0x0)<br/>                  |
| Modify bit<br/>     | 22<br/>    | **CLUS\_MODIFY** (0x1)<br/>                       |
| User bit<br/>       | 21<br/>    | **CLCTL\_CLUSTER\_BASE** (0x0)<br/>               |
| Type bit<br/>       | 20<br/>    | External (0x0)<br/>                               |
| Operation code<br/> | 0 23<br/>  | **CLCTL\_SET\_MAINTENANCE\_MODE** (0x4001e6)<br/> |
| Access code<br/>    | 0 1<br/>   | **CLUS\_ACCESS\_WRITE** (0x2)<br/>                |



 

For more information, see [Control Code Architecture](control-code-architecture.md).

## Requirements



|                                     |                                                                                             |
|-------------------------------------|---------------------------------------------------------------------------------------------|
| Minimum supported client<br/> | None supported<br/>                                                                   |
| Minimum supported server<br/> | Windows Server 2008 Datacenter with SP1, Windows Server 2008 Enterprise with SP1<br/> |
| Header<br/>                   | <dl> <dt>ClusAPI.h</dt> </dl>        |



## See also

<dl> <dt>

[External Resource Control Codes](external-resource-control-codes.md)
</dt> <dt>

[Maintaining Physical Disk Resources](maintaining-physical-disk-resources.md)
</dt> <dt>

[**CLUS\_MAINTENANCE\_MODE\_INFO**](/previous-versions/windows/desktop/api/ClusAPI/ns-clusapi-clus_maintenance_mode_info)
</dt> <dt>

[CLUSCTL\_RESOURCE\_QUERY\_MAINTENANCE\_MODE](clusctl-resource-query-maintenance-mode.md)
</dt> <dt>

[**ClusterResourceControl**](/previous-versions/windows/desktop/api/ClusAPI/nf-clusapi-clusterresourcecontrol)
</dt> </dl>

 

 




