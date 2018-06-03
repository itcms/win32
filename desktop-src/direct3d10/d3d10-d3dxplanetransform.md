---
Description: Transforms a plane by a matrix. The input matrix is the inverse transpose of the actual transformation.
ms.assetid: ded06eac-4086-47e8-bc55-c37959afc22d
title: D3DXPlaneTransform function
ms.technology: desktop
ms.prod: windows
ms.author: windowssdkdev
ms.topic: article
ms.date: 05/31/2018
---

# D3DXPlaneTransform function

Transforms a plane by a matrix. The input matrix is the inverse transpose of the actual transformation.

## Syntax


```C++
D3DXPLANE* D3DXPlaneTransform(
  _Inout_       D3DXPLANE  *pOut,
  _In_    const D3DXPLANE  *pP,
  _In_    const D3DXMATRIX *pM
);
```



## Parameters

<dl> <dt>

*pOut* \[in, out\]
</dt> <dd>

Type: **[**D3DXPLANE**](https://msdn.microsoft.com/windows/desktop/ffca4650-9788-4559-8f6b-a4e5db29ce55)\***

Pointer to the [**D3DXPLANE**](d3d10-d3dxplane.md) that contains the resulting transformed plane. See example.

</dd> <dt>

*pP* \[in\]
</dt> <dd>

Type: **const [**D3DXPLANE**](https://msdn.microsoft.com/windows/desktop/ffca4650-9788-4559-8f6b-a4e5db29ce55)\***

Pointer to the input D3DXPLANE structure, which contains the plane that will be transformed. The vector (a,b,c) that describes the plane must be normalized before this function is called. See example.

</dd> <dt>

*pM* \[in\]
</dt> <dd>

Type: **const [**D3DXMATRIX**](https://msdn.microsoft.com/windows/desktop/0911088b-50cf-4c4a-996e-351386fc359b)\***

Pointer to the source [**D3DXMATRIX**](d3d10-d3dxmatrix.md) structure, which contains the transformation values. This matrix must contain the inverse transpose of the transformation values.

</dd> </dl>

## Return value

Type: **[**D3DXPLANE**](https://msdn.microsoft.com/windows/desktop/ffca4650-9788-4559-8f6b-a4e5db29ce55)\***

Pointer to a D3DXPLANE structure, representing the transformed plane. This is the same value returned in the pOut parameter so that this function can be used as a parameter for another function.

## Remarks

### Examples

This example transforms a plane by applying a non-uniform scale.


```
D3DXPLANE   planeNew;
D3DXPLANE   plane(0,1,1,0);
D3DXPlaneNormalize(&amp;plane, &amp;plane);

D3DXMATRIX  matrix;
D3DXMatrixScaling(&amp;matrix, 1.0f,2.0f,3.0f); 
D3DXMatrixInverse(&amp;matrix, NULL, &amp;matrix);
D3DXMatrixTranspose(&amp;matrix, &amp;matrix);
D3DXPlaneTransform(&amp;planeNew, &amp;plane, &amp;matrix);
```



A plane is described by ax + by + cz + dw = 0. The first plane is created with (a,b,c,d) = (0,1,1,0), which is a plane described by y + z = 0. After scaling, the new plane contains (a,b,c,d) = (0, 0.353f, 0.235f, 0), which shows the new plane to be described by 0.353y + 0.235z = 0.

The parameter pM contains the inverse transpose of the transformation matrix. The inverse transpose is required by this method so that the normal vector of the transformed plane can be correctly transformed as well.

## Requirements



|                    |                                                                                         |
|--------------------|-----------------------------------------------------------------------------------------|
| Header<br/>  | <dl> <dt>D3DX10Math.h</dt> </dl> |
| Library<br/> | <dl> <dt>D3DX10.lib</dt> </dl>   |



## See also

<dl> <dt>

[Math Functions](d3d10-graphics-reference-d3dx10-functions-math.md)
</dt> </dl>

 

 



