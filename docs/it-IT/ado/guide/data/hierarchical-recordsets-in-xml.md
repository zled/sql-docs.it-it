---
title: Oggetti Recordset gerarchici in XML | Documenti Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- hierarchical Recordsets [ADO], in XML
ms.assetid: 5d4b11c4-c94f-4910-b99b-5b9abc50d791
caps.latest.revision: 4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 177a2255dfaffb62ea8dbedd2123c8eadbcc177b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="hierarchical-recordsets-in-xml"></a>Oggetti Recordset gerarchici in XML
ADO consente la persistenza degli oggetti Recordset gerarchici in XML. Con gli oggetti Recordset gerarchici, il valore di un campo nell'oggetto Recordset padre è un altro oggetto Recordset. Tali campi sono rappresentati come elementi figlio nel flusso XML anziché un attributo.  
  
## <a name="remarks"></a>Osservazioni  
 Nell'esempio seguente viene illustrato in questo caso:  
  
```  
Rs.Open "SHAPE {select stor_id, stor_name, state from stores} APPEND ({select stor_id, ord_num, ord_date, qty from sales} AS rsSales RELATE stor_id TO stor_id)", "Provider=MSDataShape;DSN=pubs;Integrated Security=SSPI;"  
```  
  
 Di seguito è il formato XML dell'oggetto Recordset permanente:  
  
```  
<xml xmlns:s="uuid:BDC6E3F0-6DA3-11d1-A2A3-00AA00C14882"     xmlns:dt="uuid:C2F41010-65B3-11d1-A29F-00AA00C14882"     xmlns:rs="urn:schemas-microsoft-com:rowset"   
    xmlns:z="#RowsetSchema">   
  <s:Schema id="RowsetSchema">   
    <s:ElementType name="row" content="eltOnly" rs:updatable="true">   
      <s:AttributeType name="stor_id" rs:number="1"   
        rs:writeunknown="true">   
        <s:datatype dt:type="string" dt:maxLength="4"   
          rs:fixedlength="true" rs:maybenull="false"/>   
      </s:AttributeType>   
      <s:AttributeType name="stor_name" rs:number="2" rs:nullable="true"   
        rs:writeunknown="true">   
          <s:datatype dt:type="string" dt:maxLength="40"/>   
      </s:AttributeType>   
      <s:AttributeType name="state" rs:number="3" rs:nullable="true"   
        rs:writeunknown="true">   
        <s:datatype dt:type="string" dt:maxLength="2"   
          rs:fixedlength="true"/>   
      </s:AttributeType>   
      <s:ElementType name="rsSales" content="eltOnly"   
        rs:updatable="true" rs:relation="010000000100000000000000">   
        <s:AttributeType name="stor_id" rs:number="1"   
          rs:writeunknown="true">   
          <s:datatype dt:type="string" dt:maxLength="4"   
            rs:fixedlength="true" rs:maybenull="false"/>   
        </s:AttributeType>   
        <s:AttributeType name="ord_num" rs:number="2"   
          rs:writeunknown="true">   
          <s:datatype dt:type="string" dt:maxLength="20"   
            rs:maybenull="false"/>   
        </s:AttributeType>   
        <s:AttributeType name="ord_date" rs:number="3"   
          rs:writeunknown="true">   
            <s:datatype dt:type="dateTime" dt:maxLength="16"   
              rs:scale="3" rs:precision="23" rs:fixedlength="true"   
              rs:maybenull="false"/>   
        </s:AttributeType>   
        <s:AttributeType name="qty" rs:number="4" rs:writeunknown="true">   
          <s:datatype dt:type="i2" dt:maxLength="2" rs:precision="5"   
            rs:fixedlength="true" rs:maybenull="false"/>   
        </s:AttributeType>   
        <s:extends type="rs:rowbase"/>   
      </s:ElementType>   
      <s:extends type="rs:rowbase"/>   
    </s:ElementType>   
  </s:Schema>   
  <rs:data>   
    <z:row stor_id="6380" stor_name="Eric the Read Books" state="WA">   
      <rsSales stor_id="6380" ord_num="6871"   
        ord_date="1994-09-14T00:00:00" qty="5"/>   
      <rsSales stor_id="6380" ord_num="722a"   
        ord_date="1994-09-13T00:00:00" qty="3"/>   
    </z:row>   
    <z:row stor_id="7066" stor_name="Barnum's" state="CA">   
      <rsSales stor_id="7066" ord_num="A2976"   
        ord_date="1993-05-24T00:00:00" qty="50"/>   
      <rsSales stor_id="7066" ord_num="QA7442.3"   
        ord_date="1994-09-13T00:00:00" qty="75"/>   
    </z:row>   
    <z:row stor_id="7067" stor_name="News & Brews" state="CA">   
      <rsSales stor_id="7067" ord_num="D4482"   
        ord_date="1994-09-14T00:00:00" qty="10"/>   
      <rsSales stor_id="7067" ord_num="P2121"   
        ord_date="1992-06-15T00:00:00" qty="40"/>   
      <rsSales stor_id="7067" ord_num="P2121"   
        ord_date="1992-06-15T00:00:00" qty="20"/>   
      <rsSales stor_id="7067" ord_num="P2121"   
        ord_date="1992-06-15T00:00:00" qty="20"/>   
    </z:row>   
  </rs:data>   
</xml>   
```  
  
 Quando viene resa persistente in questo modo, l'ordine esatto delle colonne nell'oggetto Recordset padre non è scontato. Qualsiasi campo nell'elemento padre può contenere un Recordset figlio. Il Provider di persistenza persiste out tutte le colonne scalari prima come attributi e quindi le colonne"tutti figlio Recordset" come elementi figlio della riga padre. La posizione ordinale del campo dell'elemento padre in Recordset può essere ottenuto esaminando la definizione dello schema dell'oggetto Recordset. Ogni campo ha una proprietà OLE DB rs: number, definita nello spazio dei nomi di schema Recordset che contiene il numero ordinale del campo.  
  
 I nomi di tutti i campi nel Recordset figlio sono concatenati con il nome del campo del Recordset che contiene l'elemento figlio del padre. Questo modo si garantisce che vi sono conflitti di nomi nei casi in cui entrambi Recordset padre e figlio contiene un campo che viene ottenuto da due tabelle diverse ma avente.  
  
 Durante il salvataggio recordset gerarchiche in XML, è necessario tenere presente le restrizioni seguenti in ADO:  
  
-   Un oggetto Recordset gerarchico con gli aggiornamenti in sospeso non può essere persistente in XML.  
  
-   Un oggetto Recordset gerarchico creato con un comando shape con parametri non può essere persistente (in formato XML o ADTG).  
  
-   ADO attualmente Salva la relazione tra padre e figlio (recordset) come un oggetto binario di grandi dimensioni (BLOB). Tag XML per descrivere la relazione non sono ancora state definite nello spazio dei nomi dello schema del set di righe.  
  
-   Quando viene salvato un Recordset gerarchico, figlio di tutti i recordset vengono salvati insieme a e. Se il Recordset corrente è un figlio di un altro oggetto Recordset, il relativo elemento padre non viene salvato. Figlio tutti i recordset che formare il sottoalbero del Recordset corrente vengono salvate.  
  
 Quando un oggetto Recordset gerarchico viene riaperto dal formato XML persistente, è necessario considerare le limitazioni seguenti:  
  
-   Se il record figlio contiene record per cui non esistono record padre corrispondente, tali righe non vengono scritte nella rappresentazione XML dell'oggetto Recordset gerarchico. Pertanto, queste righe andranno persi quando il Recordset viene riaperto dalla posizione persistente.  
  
-   Se un record figlio include riferimenti a più di un record padre, quindi su riaprire il Recordset, il Recordset figlio potrebbe contenere record duplicati. Tuttavia, i duplicati saranno visibili solo se l'utente interagisce direttamente con il set di righe figlio sottostante. Se viene utilizzato un capitolo per passare l'elemento figlio di Recordset (che è l'unico modo per passare tramite ADO), i duplicati non sono visibili.  
  
## <a name="see-also"></a>Vedere anche  
 [Persistenza di record in formato XML](../../../ado/guide/data/persisting-records-in-xml-format.md)
