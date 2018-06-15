---
title: Sezione di dati | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- data section [ADO]
ms.assetid: 43dc42a8-7057-48e6-93d6-880d5c5c51a4
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1b861ce91ec8b7007e168cbdb7d0dae3f0ce48e9
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35270100"
---
# <a name="data-section"></a>Sezione di dati
La sezione di dati definisce i dati del set di righe insieme a eventuali aggiornamenti, le operazioni di inserimento o eliminazione in sospeso. La sezione di dati può contenere zero o più righe. Può contenere solo i dati da un set di righe in cui la riga è definita dallo schema. Inoltre, come accennato prima, colonne senza dati possono essere omessa. Se viene utilizzato un attributo o un sottoelemento nella sezione dei dati e tale costrutto non è stato definito nella sezione dello schema, viene ignorata automaticamente.  
  
## <a name="string"></a>String  
 I caratteri XML riservati nei dati di testo devono essere sostituiti con entità carattere appropriato. Ad esempio, nel nome della società "Joe Garage", la virgoletta singola devono essere sostituita da un'entità. La riga effettiva sarà simile alla seguente:  
  
```  
<z:row CompanyName="Joe's Garage"/>  
```  
  
 I seguenti caratteri sono riservati in XML e devono essere sostituiti da entità carattere: {"," &,\<, >}.  
  
## <a name="binary"></a>Binario  
 Dati binari sono con codificata hex (ovvero, un byte viene mappato a due caratteri, un carattere per nibble).  
  
## <a name="datetime"></a>DateTime  
 Il formato VT_DATE variant non è supportato direttamente da tipi di dati XML. Il formato corretto per le date con il componente di data e ora è aaaa-mm-ggThh.  
  
 Per ulteriori informazioni su formati della data specificata da XML, vedere il [specifica W3C XML-Data](https://go.microsoft.com/fwlink/?LinkId=5692).  
  
 Quando la specifica di dati XML definisce due tipi di dati equivalente (ad esempio i4 = = int), ADO verrà scrivere il nome descrittivo, ma di lettura in entrambi.  
  
## <a name="managing-pending-changes"></a>La gestione delle modifiche in sospeso  
 Un Recordset può essere aperto in immediato o in modalità di aggiornamento batch. Quando vengono aperti in modalità di aggiornamento batch con cursori sul lato client, fino a quando non viene chiamato il metodo UpdateBatch tutte le modifiche apportate all'oggetto Recordset sono in uno stato in sospeso. Le modifiche in sospeso vengono resi persistenti anche quando viene salvato il Recordset. Nel codice XML, sono rappresentati dall'utilizzo di elementi "update" definiti in urn: schemas-microsoft-com: rowset. Inoltre, se è possibile aggiornare un set di righe, la proprietà aggiornabile deve essere impostata su true nella definizione della riga. Ad esempio, per definire che la tabella Shippers contiene modifiche in sospeso, la definizione di riga sarebbe Cerca somigliare seguenti.  
  
```  
<s:ElementType name="row" content="eltOnly" updatable="true">  
  <s:attribute type="ShipperID"/>  
  <s:attribute type="CompanyName"/>  
  <s:attribute type="Phone"/>  
  <s:extends type="rs:rowbase"/>  
</s:ElementType>  
```  
  
 Ciò indica al Provider di persistenza di area dati in modo che ADO è possibile costruire un oggetto Recordset aggiornabile.  
  
 I dati di esempio seguente mostrano l'aspetto di inserimenti, le modifiche ed eliminazioni in file persistente.  
  
```  
<rs:data>  
  <z:row ShipperID="2" CompanyName="United Package"   
    Phone="(503) 555-3199"/>  
<rs:update>  
  <rs:original>  
    <z:row ShipperID="3" CompanyName="Federal Shipping"   
      Phone="(503) 555-9931"/>  
  </rs:original>  
  <z:row Phone="(503) 552-7134"/>  
</rs:update>  
<rs:insert>  
  <z:row ShipperID="12" CompanyName="Lightning Shipping"   
    Phone="(505) 111-2222"/>  
  <z:row ShipperID="13" CompanyName="Thunder Overnight"   
    Phone="(505) 111-2222"/>  
  <z:row ShipperID="14" CompanyName="Blue Angel Air Delivery"   
    Phone="(505) 111-2222"/>  
</rs:insert>  
<rs:delete>  
  <z:row ShipperID="1" CompanyName="Speedy Express" Phone="(503) 555-9831"/>  
</rs:delete>  
</rs:data>  
```  
  
 Un aggiornamento contiene sempre i dati della riga originale intero seguiti da dati della riga modificata. La riga modificata può contenere tutte le colonne o solo le colonne effettivamente modificati. Nell'esempio precedente, non viene modificata la riga per 2 spedizioniere e solo la colonna telefono è stato modificato i valori per 3 spedizioniere e pertanto è l'unica colonna inclusa nella riga modificata. Le righe inserite per Shippers 12, 13 e 14 sono batch tag rs: inserimento in un insieme. Si noti che le righe eliminate possono anche essere raggruppate, anche se questa opzione non è mostrata nell'esempio precedente.  
  
## <a name="see-also"></a>Vedere anche  
 [Persistenza di record in formato XML](../../../ado/guide/data/persisting-records-in-xml-format.md)
