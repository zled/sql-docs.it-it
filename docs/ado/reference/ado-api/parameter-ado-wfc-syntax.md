---
title: Parametro (ADO - sintassi WFC) | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 02/15/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
helpviewer_keywords:
- Parameter collection [ADO], ADO/WFC syntax
ms.assetid: d00d1e1e-14b1-41a2-a00f-2a3cb7396f15
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 05f3e2f6f6b3985c1c68604e6e9829c1b1f3eef1
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="parameter-ado---wfc-syntax"></a>Parametro (ADO - sintassi WFC)
## <a name="package-commswfcdata"></a>package com.ms.wfc.data  
  
### <a name="constructor"></a>Costruttore  
  
```  
public Parameter()  
public Parameter(String name)  
public Parameter(String name, int type)  
public Parameter(String name, int type, int dir)  
public Parameter(String name, int type, int dir, int size)  
public Parameter(String name, int type, int dir, int size, Object value)  
```  
  
### <a name="methods"></a>Metodi  
  
```  
public void appendChunk(byte[] bytes)  
public void appendChunk(char[] chars)  
public void appendChunk(String chars)  
```  
  
### <a name="properties"></a>Proprietà  
  
```  
public int getAttributes()  
public void setAttributes(int attr)  
public int getDirection()  
public void setDirection(int dir)  
public String getName()  
public void setName(String name)  
public int getNumericScale()  
public void setNumericScale(int scale)  
public int getPrecision()  
public void setPrecision(int prec)  
public int getSize()  
public void setSize(int size)  
public int getType()  
public void setType(int type)  
public com.ms.com.Variant getValue()  
public void setValue(Object v)  
public AdoProperties getProperties()  
```  
  
## <a name="parameter-accessor-methods"></a>Metodi di accesso parametro  
 Il [valore](../../../ado/reference/ado-api/value-property-ado.md) proprietà di un [parametro](../../../ado/reference/ado-api/parameter-object.md) oggetto Ottiene o imposta il contenuto di tale oggetto. Il contenuto è rappresentato come un tipo di oggetto che può essere assegnato un valore e i diversi tipi di dati VARIANT.  
  
 ADO/WFC implementa il **valore** proprietà con il **getValue** metodo, che restituisce un oggetto VARIANT; e **setValue** metodo, che accetta una variante come argomento. Le varianti sono altamente efficiente in alcuni linguaggi, ad esempio Microsoft Visual Basic.  
  
 Oltre al **valore** proprietà ADO/WFC include *della funzione di accesso* metodi che utilizzano tipi di dati Java per ottenere e impostare il contenuto di **parametro** oggetti. La maggior parte di questi metodi ha il formato dei nomi **ottenere * * * il tipo di dati* o **impostare * * * il tipo di dati*.  
  
 Vi è un'eccezione degno di nota: è presente alcun **importante** proprietà; viene invece un **isNull** proprietà che restituisce un valore booleano che indica se il campo è null.  
  
```  
public boolean getBoolean()  
public void setBoolean(boolean v)  
public byte getByte()  
public void setByte(byte v)  
public double getDouble()  
public void setDouble(double v)  
public float getFloat()  
public void setFloat(float v)  
public int getInt()  
public void setInt(int v)  
public long getLong()  
public void setLong(long v)  
public short getShort()  
public void setShort(short v)  
public String getString()  
public void setString(String v)  
public boolean isNull()  
public void setNull()  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Parameter](../../../ado/reference/ado-api/parameter-object.md)
