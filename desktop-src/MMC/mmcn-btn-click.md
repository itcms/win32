---
title: MMCN\_BTN\_CLICK message
description: Sent to the snap-in's IComponent, IComponentData, or IExtendControlbar implementation when a user clicks a toolbar button.
audience: developer
author: REDMOND\\markl
manager: REDMOND\\markl
ms.assetid: 166488ab-942f-4e25-9007-b9b79aac5995
ms.prod: windows-server-dev
ms.technology: microsoft-management-console
ms.tgt_platform: multiple
keywords:
- MMCN_BTN_CLICK message MMC
topic_type:
- apiref
api_name:
- MMCN_BTN_CLICK
api_location:
- Mmc.h
api_type:
- HeaderDef
ms.author: windowssdkdev
ms.topic: article
ms.date: 05/31/2018
---

# MMCN\_BTN\_CLICK message

The **MMCN\_BTN\_CLICK** notification message is sent to the snap-in's [**IComponent**](/windows/desktop/api/Mmc/nn-mmc-icomponent), [**IComponentData**](/windows/desktop/api/Mmc/nn-mmc-icomponentdata), or [**IExtendControlbar**](/windows/desktop/api/Mmc/nn-mmc-iextendcontrolbar) implementation when a user clicks a toolbar button.

## Parameters

<dl> <dt>

*lpDataObject* \[in\]
</dt> <dd>

For [**IComponent::Notify**](/windows/desktop/api/Mmc/nf-mmc-icomponent-notify) or [**IComponentData::Notify**](/windows/desktop/api/Mmc/nf-mmc-icomponentdata-notify), the pointer to the data object of the currently selected scope or result item. Not used by [**IExtendControlBar::ControlbarNotify**](/windows/desktop/api/Mmc/nf-mmc-iextendcontrolbar-controlbarnotify).

</dd> <dt>

*arg* 
</dt> <dd>

For [**IComponent::Notify**](/windows/desktop/api/Mmc/nf-mmc-icomponent-notify) or [**IComponentData::Notify**](/windows/desktop/api/Mmc/nf-mmc-icomponentdata-notify), this parameter must be 0 (zero). For [**IExtendControlBar::ControlbarNotify**](/windows/desktop/api/Mmc/nf-mmc-iextendcontrolbar-controlbarnotify), this parameter is the data object of the currently selected scope or result item.

</dd> <dt>

*param* \[in\]
</dt> <dd>

For [**IComponent::Notify**](/windows/desktop/api/Mmc/nf-mmc-icomponent-notify) or [**IComponentData::Notify**](/windows/desktop/api/Mmc/nf-mmc-icomponentdata-notify), this parameter is the verb that was selected (one of the [**MMC\_CONSOLE\_VERB**](/windows/desktop/api/Mmc/ne-mmc-_mmc_console_verb) enumerations). For [**IExtendControlBar::ControlbarNotify**](/windows/desktop/api/Mmc/nf-mmc-iextendcontrolbar-controlbarnotify), this parameter is the snap-in-defined command ID of the selected toolbar button.

</dd> </dl>

## Return value

<dl> <dt>

**S\_OK**
</dt> <dd>

The snap-in successfully handled the notification.

</dd> <dt>

**S\_FALSE**
</dt> <dd>

The snap-in does not handle the notification. MMC then performs a default operation for the notification.

</dd> </dl>

## Remarks

For a custom view (custom OCX or webpage) for which the MMC\_VERB\_PROPERTIES verb is enabled, when the user clicks the Properties button on the console toolbar, MMC sends the snap-in an **MMCN\_BTN\_CLICK** notification message. The notification's *param* argument contains the MMC\_VERB\_PROPERTIES enumerator value, and its *lpDataObject* argument contains DOBJ\_CUSTOMOCX or DOBJ\_CUSTOMWEB.

## Requirements



|                                     |                                                                                  |
|-------------------------------------|----------------------------------------------------------------------------------|
| Minimum supported client<br/> | Windows Vista<br/>                                                         |
| Minimum supported server<br/> | Windows Server 2008<br/>                                                   |
| Header<br/>                   | <dl> <dt>Mmc.h</dt> </dl> |



## See also

<dl> <dt>

[**IComponent::Notify**](/windows/desktop/api/Mmc/nf-mmc-icomponent-notify)
</dt> <dt>

[**IComponentData::Notify**](/windows/desktop/api/Mmc/nf-mmc-icomponentdata-notify)
</dt> <dt>

[**IExtendControlbar::ControlbarNotify**](/windows/desktop/api/Mmc/nf-mmc-iextendcontrolbar-controlbarnotify)
</dt> </dl>

 

 




