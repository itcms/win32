---
title: AnalogTVTuningSpace Object
description: AnalogTVTuningSpace Object
ms.assetid: f256a003-147a-4b0b-abc9-af386dcbb3c3
ms.technology: desktop
ms.prod: windows
ms.author: windowssdkdev
ms.topic: article
ms.date: 05/31/2018
---

# AnalogTVTuningSpace Object

The **AnalogTVTuningSpace** object represents a tuning space for analog television.



|                           |                                                      |
|---------------------------|------------------------------------------------------|
| Interfaces                | [**IAnalogTVTuningSpace**](/previous-versions/windows/desktop/api/tuner/nn-tuner-ianalogtvtuningspace) |
| Outgoing Event Interfaces | None                                                 |
| CLSID                     | CLSID\_AnalogTVTuningSpace                           |



 

## Remarks

The Microsoft Unified Tuning Model supports analog tuning spaces, but there are no analog TV devices based on the Broadcast Driver Architecture (BDA). When the Video Control receives an analog TV tune request, it gets the channel number and creates a WDM analog TV filter graph.

Applications should get this object from the [SystemTuningSpaces](systemtuningspaces-object.md) collection; the CLSID is provided for clients that wish to create custom tuning spaces.

Tune request objects created by this tuning space support the [**ITuneRequest**](/previous-versions/windows/desktop/api/tuner/nn-tuner-itunerequest) and [**IChannelTuneRequest**](/previous-versions/windows/desktop/api/tuner/nn-tuner-ichanneltunerequest) interfaces.

## Related topics

<dl> <dt>

[Tuning Model Objects](tuning-model-objects.md)
</dt> <dt>

[Tuning Spaces](tuning-spaces.md)
</dt> </dl>

 

 



