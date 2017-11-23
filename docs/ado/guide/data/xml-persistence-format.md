---
title: Formato di persistenza XML | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: XML persistence [ADO], persistence format
ms.assetid: 6e146738-ac4d-47bb-b6cd-d87b2260aead
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4ef8f1495b6c790abe7b3b616e2d37908c42517b
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="xml-persistence-format"></a>Formato di persistenza XML
ADO utilizza la codifica UTF-8 per il flusso XML che persiste.  
  
 Il formato XML ADO viene suddiviso in due sezioni, una sezione schema seguita da una sezione dati. Di seguito è riportato un file XML di esempio per la tabella Shippers dal database Northwind. Vengono descritte varie parti del codice XML di esempio seguente.  
  
## <a name="remarks"></a>Osservazioni  
  
```  
<xml xmlns:s="uuid:BDC6E3F0-6DA3-11d1-A2A3-00AA00C14882"   
xmlns:dt="uuid:C2F41010-65B3-11d1-A29F-00AA00C14882"   
xmlns:rs="urn:schemas-microsoft-com:rowset"   
xmlns:z="#RowsetSchema">   
  <s:Schema id="RowsetSchema">   
    <s:ElementType name="row" content="eltOnly" rs:updatable="true">   
      <s:AttributeType name="ShipperID" rs:number="1"   
        rs:basetable="shippers" rs:basecolumn="ShipperID"  
        rs:keycolumn="true">   
        <s:datatype dt:type="int" dt:maxLength="4" rs:precision="10"   
          rs:fixedlength="true" rs:maybenull="false"/>   
      </s:AttributeType>   
      <s:AttributeType name="CompanyName" rs:number="2"   
        rs:nullable="true" rs:write="true" rs:basetable="shippers"   
        rs:basecolumn="CompanyName">   
        <s:datatype dt:type="string" dt:maxLength="40" />   
      </s:AttributeType>   
      <s:AttributeType name="Phone" rs:number="3" rs:nullable="true"   
        rs:write="true" rs:basetable="shippers"   
        rs:basecolumn="Phone">   
        <s:datatype dt:type="string" dt:maxLength="24"/>   
      </s:AttributeType>   
      <s:extends type="rs:rowbase"/>   
    </s:ElementType>   
  </s:Schema>   
  
  <rs:data>   
    <z:row ShipperID="1" CompanyName="Speedy Express"   
      Phone="(503) 555-9831"/>   
    <z:row ShipperID="2" CompanyName="United Package"   
      Phone="(503) 555-3199"/>   
    <z:row ShipperID="3" CompanyName="Federal Shipping"   
      Phone="(503) 555-9931"/>   
  </rs:data>   
</xml>  
```  
  
 Lo schema sono illustrate le dichiarazioni di spazi dei nomi, la sezione dello schema e la sezione di dati. La sezione dello schema contiene le definizioni per riga, ShipperID, CompanyName e telefono.  
  
 Definizioni dello schema conformi al [specifica W3C XML-Data](http://www.w3.org/TR/1998/NOTE-XML-data/) e può essere completamente convalidato (ma non verrà eseguita la convalida in Internet Explorer 5). Dati XML sono attualmente il formato di schemi supportati solo per la persistenza del Recordset.  
  
 La sezione di dati include tre righe che contengono informazioni degli spedizionieri. Per un set di righe vuoto, la sezione di dati può essere vuota, ma la \<: dati di Reporting Services > tag devono essere presenti. Senza dati, è possibile scrivere la sintassi abbreviata tag semplicemente come \<: dati rs / >. Qualsiasi tag preceduti dal prefisso "rs" indica che si tratta dello spazio dei nomi definito dall'urn: schemas-microsoft-com: rowset.  
  
## <a name="see-also"></a>Vedere anche  
 [Persistenza di record in formato XML](../../../ado/guide/data/persisting-records-in-xml-format.md)
