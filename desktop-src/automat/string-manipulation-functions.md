---
title: String Manipulation Functions
description: To handle strings that are allocated by one component and freed by another, Automation defines a special set of functions.
ms.assetid: 323cefbf-836c-4c9d-bcbe-f2663a57d2b5
ms.technology: desktop
ms.prod: windows
ms.author: windowssdkdev
ms.topic: article
ms.date: 05/31/2018
---

# String Manipulation Functions

To handle strings that are allocated by one component and freed by another, Automation defines a special set of functions. These functions use the following data type:


```C++
typedef OLECHAR * BSTR;
```



These strings are zero-terminated, and in most cases they can be treated just like OLECHAR\* strings. However, you can query a [BSTR](https://msdn.microsoft.com/windows/desktop/1B2D7D2C-47AF-4389-A6B6-B01B7E915228) for its length rather than scan it, so it can contain embedded null characters. The length is stored as a 32-bit integer at the memory location preceding the data in the string. Instead of reading this location directly, applications should use the string manipulation functions to access the length of a BSTR.

Automation may cache the space allocated for BSTRs. This speeds up the [SysAllocString](https://msdn.microsoft.com/windows/desktop/9E0437A2-9B4A-4576-88B0-5CB9D08CA29B)/[SysFreeString](https://msdn.microsoft.com/windows/desktop/8F230EE3-5F6E-4CB9-A910-9C90B754DCD3) sequence. However, this may also cause **IMallocSpy** to assign leaks to the wrong memory user because it is not aware of the caching done by Automation.

For example, if the application allocates a BSTR and frees it, the free block of memory is put into the BSTR cache by Automation. If the application then allocates another BSTR, it can get the free block from the cache. If the second BSTR allocation is not freed, **IMallocSpy** will attribute the leak to the first allocation of the BSTR. You can determine the correct source of the leak (the second allocation) by disabling the BSTR caching using the debug version of Oleaut32.dll, and by setting the environment variable OANOCACHE=1 before running the application.

## In this section



| Topic                                                             | Description                                                                                                                                                                                                                                                                                                    |
|-------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [**SysAddRefString**](/previous-versions/windows/desktop/api/Oleauto/nf-oleauto-sysaddrefstring)<br/>             | Increases the pinning reference count for the specified string by one.<br/>                                                                                                                                                                                                                              |
| [**SysAllocString**](/previous-versions/windows/desktop/api/OleAuto/nf-oleauto-sysallocstring)<br/>               | Allocates a new string and copies the passed string into it.<br/>                                                                                                                                                                                                                                        |
| [**SysAllocStringByteLen**](/previous-versions/windows/desktop/api/OleAuto/nf-oleauto-sysallocstringbytelen)<br/> | Takes an ANSI string as input, and returns a BSTR that contains an ANSI string. Does not perform any ANSI-to-Unicode translation.<br/>                                                                                                                                                                   |
| [**SysAllocStringLen**](/previous-versions/windows/desktop/api/OleAuto/nf-oleauto-sysallocstringlen)<br/>         | Allocates a new string, copies the specified number of characters from the passed string, and appends a null-terminating character.<br/>                                                                                                                                                                 |
| [**SysFreeString**](/previous-versions/windows/desktop/api/OleAuto/nf-oleauto-sysfreestring)<br/>                 | Deallocates a string allocated previously by [**SysAllocString**](/previous-versions/windows/desktop/api/OleAuto/nf-oleauto-sysallocstring), [**SysAllocStringByteLen**](/previous-versions/windows/desktop/api/OleAuto/nf-oleauto-sysallocstringbytelen), [**SysReAllocString**](/previous-versions/windows/desktop/api/OleAuto/nf-oleauto-sysreallocstring), [**SysAllocStringLen**](/previous-versions/windows/desktop/api/OleAuto/nf-oleauto-sysallocstringlen), or [**SysReAllocStringLen**](/previous-versions/windows/desktop/api/OleAuto/nf-oleauto-sysreallocstringlen).<br/> |
| [**SysReAllocString**](/previous-versions/windows/desktop/api/OleAuto/nf-oleauto-sysreallocstring)<br/>           | Reallocates a previously allocated string to be the size of a second string and copies the second string into the reallocated memory.<br/>                                                                                                                                                               |
| [**SysReAllocStringLen**](/previous-versions/windows/desktop/api/OleAuto/nf-oleauto-sysreallocstringlen)<br/>     | Creates a new BSTR containing a specified number of characters from an old BSTR, and frees the old BSTR.<br/>                                                                                                                                                                                            |
| [**SysReleaseString**](/previous-versions/windows/desktop/api/Oleauto/nf-oleauto-sysreleasestring)<br/>           | Decreases the pinning reference count for the specified string by one. When that count reaches 0, the memory for that string is no longer prevented from being freed.<br/>                                                                                                                               |
| [**SysStringByteLen**](/previous-versions/windows/desktop/api/OleAuto/nf-oleauto-sysstringbytelen)<br/>           | Returns the length (in bytes) of a BSTR.<br/>                                                                                                                                                                                                                                                            |
| [**SysStringLen**](/previous-versions/windows/desktop/api/OleAuto/nf-oleauto-sysstringlen)<br/>                   | Returns the length of a BSTR.<br/>                                                                                                                                                                                                                                                                       |



 

> [!Note]  
> A null pointer is a valid value for a BSTR variable. By convention, it is always treated the same as a pointer to a BSTR that contains zero characters. Also by convention, calls to functions that take a BSTR reference parameter must pass either a null pointer, or a pointer to an allocated BSTR. If the implementation of a function that takes a BSTR reference parameter assigns a new BSTR to the parameter, it must free the previously referenced BSTR.

 

## Related topics

<dl> <dt>

[Conversion and Manipulation Functions](conversion-and-manipulation-functions.md)
</dt> </dl>

 

 




