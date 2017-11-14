---
title: Campo (ADO - sintassi WFC) | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
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
- Field collection [ADO], ADO/WFC syntax
ms.assetid: 7e01cb24-2338-4f92-ad46-8d97248e1a4d
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 0ea83e9a9d928ebfbab416a6cf85b4adbc887f05
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="field-ado---wfc-syntax"></a>Campo (ADO - sintassi WFC)
## <a name="package-commswfcdata"></a>pacchetto com.ms. wfc.  
  
### <a name="methods"></a>Metodi  
  
```  
public void appendChunk(byte[] bytes)  
public void appendChunk(char[] chars)  
public void appendChunk(String chars)  
public byte[] getByteChunk(int len)  
public char[] getCharChunk(int len)  
public String getStringChunk(int len)  
```  
  
### <a name="properties"></a>Proprietà  
  
```  
public int getActualSize()  
public int getAttributes()  
public void setAttributes(int pl)  
public com.ms.com.IUnknown getDataFormat()  
public void setDataFormat(com.ms.com.IUnknown format)  
```  
  
 (Per ulteriori informazioni, vedere la documentazione per l'interfaccia IDataFormat).  
  
```  
public int getDefinedSize()  
public void setDefinedSize(int pl)  
public String getName()  
public int getNumericScale()  
public void setNumericScale(byte pbNumericScale)  
public Variant getOriginalValue()  
public int getPrecision()  
public void setPrecision(byte pbPrecision)  
public int getType()  
public void setType(int pDataType)  
public Variant getUnderlyingValue()  
public Variant getValue()  
public void setValue(Variant value)  
public AdoProperties getProperties()  
```  
  
### <a name="field-accessor-methods"></a>Metodi di accesso di campo  
 Il [valore](../../../ado/reference/ado-api/value-property-ado.md) proprietà di un [campo](../../../ado/reference/ado-api/field-object.md) oggetto Ottiene o imposta il contenuto di tale oggetto. Il contenuto è rappresentato come un tipo di oggetto che può essere assegnato un valore e i diversi tipi di dati VARIANT.  
  
 ADO/WFC implementa il **valore** proprietà con il **getValue** metodo, che restituisce un oggetto VARIANT; e **setValue** metodo, che accetta una variante come argomento. Le varianti sono altamente efficiente in alcuni linguaggi, ad esempio Microsoft Visual Basic.  
  
 Oltre al **valore** proprietà ADO/WFC include *della funzione di accesso* metodi che utilizzano tipi di dati Java per ottenere e impostare il contenuto di **campo** oggetti. La maggior parte di questi metodi ha il formato dei nomi **ottenere***DataType* o **impostare***DataType*.  
  
 Esistono due eccezioni degno di nota: una del **getObject** metodi restituisce un oggetto convertito in una classe specificata. Non esiste alcun **importante** proprietà; viene invece utilizzato un **isNull** proprietà che restituisce un valore booleano che indica se il campo è null.  
  
```  
public native boolean getBoolean();  
public void setBoolean(boolean v)  
public native byte getByte();  
public void setByte(byte v)  
public native byte[] getBytes();  
public void setBytes(byte[] v)  
public native double getDouble();  
public void setDouble(double v)  
public native float getFloat();  
public void setFloat(float v)  
public native int getInt();  
public void setInt(int v)  
public native long getLong();  
public void setLong(long v)  
public native short getShort();  
public void setShort(short v)  
public native String getString();  
public void setString(String v)  
public native boolean isNull();  
public void setNull()  
public Object getObject()  
public Object getObject(Class c)  
public void setObject(Object value)  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Field](../../../ado/reference/ado-api/field-object.md)

