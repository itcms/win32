---
Description: WPD\_CONTENT\_TYPE\_NETWORK\_ASSOCIATION
ms.assetid: 5c17aba1-98f7-4d6c-a5d2-2b4623a65255
title: WPD\_CONTENT\_TYPE\_NETWORK\_ASSOCIATION
ms.technology: desktop
ms.prod: windows
ms.author: windowssdkdev
ms.topic: article
ms.date: 05/31/2018
---

# WPD\_CONTENT\_TYPE\_NETWORK\_ASSOCIATION

An object that describes its type as WPD\_CONTENT\_TYPE\_NETWORK\_ASSOCIATION represents an association between a host and a device.

This type of object supports the following properties.



|                                                                                                                                              |                                                                       |
|----------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------|
| **Property Name**                                                                                                                            | **Required or Optional**                                              |
| [WPD\_OBJECT\_ID](https://www.bing.com/search?q=WPD\_OBJECT\_ID)                                                                                       | Required.                                                             |
| [WPD\_OBJECT\_PARENT\_ID](https://www.bing.com/search?q=WPD\_OBJECT\_PARENT\_ID)                                                                        | Required.                                                             |
| [WPD\_OBJECT\_NAME](https://www.bing.com/search?q=WPD\_OBJECT\_NAME)                                                                                   | Required if the object represents a file.                             |
| [WPD\_OBJECT\_PERSISTENT\_UNIQUE\_ID](https://www.bing.com/search?q=WPD\_OBJECT\_PERSISTENT\_UNIQUE\_ID)                                                 | Required.                                                             |
| [WPD\_OBJECT\_FORMAT](https://www.bing.com/search?q=WPD\_OBJECT\_FORMAT)                                                                               | Required.                                                             |
| [WPD\_OBJECT\_CONTENT\_TYPE](https://www.bing.com/search?q=WPD\_OBJECT\_CONTENT\_TYPE)                                                                  | Required.                                                             |
| [WPD\_OBJECT\_ISHIDDEN](https://www.bing.com/search?q=WPD\_OBJECT\_ISHIDDEN)                                                                           | Required if the object is hidden.                                     |
| [WPD\_OBJECT\_ISSYSTEM](https://www.bing.com/search?q=WPD\_OBJECT\_ISSYSTEM)                                                                           | Required if the object is a system object (represents a system file). |
| [WPD\_OBJECT\_SIZE](https://www.bing.com/search?q=WPD\_OBJECT\_SIZE)                                                                                   | Required if the object has at least one resource.                     |
| [WPD\_OBJECT\_ORIGINAL\_FILE\_NAME](https://www.bing.com/search?q=WPD\_OBJECT\_ORIGINAL\_FILE\_NAME)                                                     | Required if the object represents a file.                             |
| [WPD\_OBJECT\_NON\_CONSUMABLE](https://www.bing.com/search?q=WPD\_OBJECT\_NON\_CONSUMABLE)                                                              | Recommended if the object is not meant for consumption by the device. |
| [WPD\_OBJECT\_REFERENCES](https://www.bing.com/search?q=WPD\_OBJECT\_REFERENCES)                                                                       | Required if the object has references to other objects.               |
| [WPD\_OBJECT\_KEYWORDS](https://www.bing.com/search?q=WPD\_OBJECT\_KEYWORDS)                                                                           | Optional.                                                             |
| [WPD\_OBJECT\_SYNC\_ID](https://www.bing.com/search?q=WPD\_OBJECT\_SYNC\_ID)                                                                            | Optional.                                                             |
| [WPD\_OBJECT\_IS\_DRM\_PROTECTED](https://www.bing.com/search?q=WPD\_OBJECT\_IS\_DRM\_PROTECTED)                                                         | Required if the object is protected by DRM technology.                |
| [WPD\_OBJECT\_DATE\_CREATED](https://www.bing.com/search?q=WPD\_OBJECT\_DATE\_CREATED)                                                                  | Optional.                                                             |
| [WPD\_OBJECT\_DATE\_MODIFIED](https://www.bing.com/search?q=WPD\_OBJECT\_DATE\_MODIFIED)                                                                | Recommended.                                                          |
| [WPD\_OBJECT\_DATE\_AUTHORED](https://www.bing.com/search?q=WPD\_OBJECT\_DATE\_AUTHORED)                                                                | Optional.                                                             |
| [WPD\_OBJECT\_BACK\_REFERENCES](object-properties.md)                                                                                       | Recommended if the object is referenced by another object.            |
| [WPD\_OBJECT\_CONTAINER\_FUNCTIONAL\_OBJECT\_ID](https://www.bing.com/search?q=WPD\_OBJECT\_CONTAINER\_FUNCTIONAL\_OBJECT\_ID)                            | Optional.                                                             |
| [WPD\_OBJECT\_GENERATE\_THUMBNAIL\_FROM\_RESOURCE](https://www.bing.com/search?q=WPD\_OBJECT\_GENERATE\_THUMBNAIL\_FROM\_RESOURCE)                        | Optional.                                                             |
| [WPD\_OBJECT\_CAN\_DELETE](https://www.bing.com/search?q=WPD\_OBJECT\_CAN\_DELETE)                                                                      | Required if the object cannot be deleted.                             |
| [WPD\_OBJECT\_LANGUAGE\_LOCAL](object-properties.md)                                                                                        | Optional.                                                             |
| [WPD\_NETWORK\_ASSOCIATION\_HOST\_NETWORK\_IDENTIFIERS](https://www.bing.com/search?q=WPD\_NETWORK\_ASSOCIATION\_HOST\_NETWORK\_IDENTIFIERS) | Required.                                                             |
| [WPD\_NETWORK\_ASSOCIATION\_X509V3SEQUENCE](https://www.bing.com/search?q=WPD\_NETWORK\_ASSOCIATION\_X509V3SEQUENCE)                       | Optional.                                                             |



 

## Typical Resources

These objects typically do not host resources.

## Related topics

<dl> <dt>

[**Requirements for Objects**](requirements-for-objects.md)
</dt> </dl>

 

 


