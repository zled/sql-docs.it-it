---
title: Sezione schema | Documenti Microsoft
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
- Schema section [ADO]
ms.assetid: 4ac6e524-2c92-48e8-b871-0a4b5c8fda18
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 86231be99be321361310dfcbd7fb2669a002a418
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="schema-section"></a>Sezione dello schema
La sezione dello schema è necessaria. Come illustrato nell'esempio precedente, ADO scrive metadati dettagliati su ogni colonna per mantenere la semantica dei valori dei dati il più possibile per l'aggiornamento. Tuttavia, per caricare il file XML, ADO richiede solo i nomi delle colonne e il set di righe a cui appartengono. Di seguito è riportato un esempio di uno schema minimo:  
  
```  
<xml xmlns:s="uuid:BDC6E3F0-6DA3-11d1-A2A3-00AA00C14882"  
    xmlns:rs="urn:schemas-microsoft-com:rowset"  
    xmlns:z="#RowsetSchema">  
  <s:Schema id="RowsetSchema">  
    <s:ElementType name="row" content="eltOnly">  
      <s:AttributeType name="ShipperID"/>  
      <s:AttributeType name="CompanyName"/>  
      <s:AttributeType name="Phone"/>  
      <s:Extends type="rs:rowbase"/>  
    </s:ElementType>  
  </s:Schema>  
  <rs:data>  
...  
  </rs:data>  
</xml>  
```  
  
 Nell'esempio precedente, ADO tratterà i dati sotto forma di stringhe di lunghezza variabile perché informazioni sul tipo non è inclusa nello schema.  
  
## <a name="creating-aliases-for-column-names"></a>Creazione di alias per i nomi di colonna  
 L'attributo rs: nome consente di creare un alias per un nome di colonna in modo che le informazioni di colonna esposte dal set di righe potrebbe visualizzare un nome descrittivo e un nome più breve può essere utilizzato nella sezione dei dati. Ad esempio, lo schema precedente può essere modificato per associare ShipperID s1, CompanyName e s2 e numero di telefono per s3 come indicato di seguito:  
  
```  
<s:Schema id="RowsetSchema">   
<s:ElementType name="row" content="eltOnly" rs:updatable="true">   
<s:AttributeType name="s1" rs:name="ShipperID" rs:number="1" ...>   
...  
</s:AttributeType>   
<s:AttributeType name="s2" rs:name="CompanyName" rs:number="2" ...>   
...  
</s:AttributeType>   
<s:AttributeType name="s3" rs:name="Phone" rs:number="3" ...>   
...  
</s:AttributeType>   
...  
</s:ElementType>   
</s:Schema>  
```  
  
 Quindi, nella sezione dati, la riga utilizzerà l'attributo name (non rs: name) per fare riferimento alla colonna:  
  
```  
"<row s1="1" s2="Speedy Express" s3="(503) 555-9831"/>  
```  
  
 È necessario creare alias per i nomi di colonna, ogni volta che un nome di colonna non è un attributo valido o un nome di tag XML. Ad esempio, "Cognome" deve avere un alias perché i nomi contenenti spazi incorporati sono attributi non validi. La riga seguente non verrà gestita correttamente dal parser XML, pertanto è necessario creare un alias per un altro nome che non dispone di uno spazio incorporato.  
  
```  
<row last name="Jones"/>  
```  
  
 Il valore è utilizzato per l'attributo del nome deve essere usato in modo coerente in ogni punto che fanno riferimento alla colonna nelle sezioni di schema e dati del documento XML. Nell'esempio seguente viene illustrato l'utilizzo coerenza di s1:  
  
```  
<s:Schema id="RowsetSchema">  
  <s:ElementType name="row" content="eltOnly">  
    <s:attribute type="s1"/>  
    <s:attribute type="CompanyName"/>  
    <s:attribute type="s3"/>  
    <s:extends type="rs:rowbase"/>  
  </s:ElementType>  
  <s:AttributeType name="s1" rs:name="ShipperID" rs:number="1"   
    rs:maydefer="true" rs:writeunknown="true">  
    <s:datatype dt:type="i4" dt:maxLength="4" rs:precision="10"   
      rs:fixedlength="true" rs:maybenull="true"/>  
  </s:AttributeType>  
</s:Schema>  
<rs:data>  
  <z:row s1="1" CompanyName="Speedy Express" s3="(503) 555-9831"/>  
</rs:data>  
```  
  
 Analogamente, in quanto è definito alcun alias per `CompanyName` nell'esempio precedente, `CompanyName` deve essere usata in modo coerente in tutto il documento.  
  
## <a name="data-types"></a>Tipi di dati  
 È possibile applicare un tipo di dati a una colonna con l'attributo dt: Type. Per la Guida definitiva a tipi XML consentiti, vedere la sezione tipi di dati di [specifica W3C XML-Data](http://www.w3.org/TR/1998/NOTE-XML-data/). È possibile specificare un tipo di dati in due modi: specificare l'attributo dt: Type direttamente nella definizione di colonna stessa oppure utilizzare il costrutto s:datatype come elemento nidificato della definizione della colonna. Ad esempio,  
  
```  
<s:AttributeType name="Phone" >  
  <s:datatype dt:type="string"/>  
</s:AttributeType>  
```  
  
 equivale a  
  
```  
<s:AttributeType name="Phone" dt:type="string"/>  
```  
  
 Se si omette l'attributo dt: Type completamente dalla definizione di riga, per impostazione predefinita, il tipo della colonna sarà una stringa di lunghezza variabile.  
  
 Se si dispone di più informazioni di tipo rispetto al nome del tipo (ad esempio, dt: maxLength), rende più leggibile, utilizzare l'elemento figlio s:datatype. Si tratta semplicemente di una convenzione, tuttavia, non è un requisito.  
  
 Negli esempi seguenti viene illustrano ulteriormente includere le informazioni sul tipo nello schema.  
  
```  
<!-- 1. String with no max length -->  
<s:AttributeType name="title_id"/>  
<!—or -->  
<s:AttributeType name="title_id" dt:type="string"/>  
  
<!—- 2. Fixed length string with max length of 6 -->  
<s:AttributeType name="title_id">  
    <s:datatype dt:type="string" dt:maxLength="6" rs:fixedlength="true" />  
</s:AttributeType>  
  
<!—- 3. Variable length string with max length of 6 -->  
<s:AttributeType name="title_id">  
    <s:datatype dt:type="string" dt:maxLength="6" />  
</s:AttributeType>  
  
<!—- 4. Integer -->  
<s:AttributeType name="title_id" dt:type="int"/>  
```  
  
 È un utilizzo dell'attributo rs: fixedlength nel secondo esempio. Una colonna con l'attributo rs: fixedlength è impostato su true indica che i dati devono avere la lunghezza definita nello schema. In questo caso, un valore valido per title_id è "123456", "123". Tuttavia, "123" non sarebbe valido perché la lunghezza è 3, non 6. Vedere il manuale di OLE DB Programmer per più descrizione della proprietà fixedlength completa.  
  
## <a name="handling-nulls"></a>Gestione dei valori null  
 I valori null vengono gestiti dall'attributo rs: maybenull. Se questo attributo è impostato su true, il contenuto della colonna può contenere un valore null. Inoltre, se la colonna non viene trovata in una riga di dati, l'utente che legge i dati dal set di righe otterrà uno stato null da IRowset. Prendere in considerazione le seguenti definizioni di colonna dalla tabella degli spedizionieri.  
  
```  
<s:AttributeType name="ShipperID">  
  <s:datatype dt:type="int" dt:maxLength="4"/>  
</s:AttributeType>  
<s:AttributeType name="CompanyName">  
  <s:datatype dt:type="string" dt:maxLength="40" rs:maybenull="true"/>  
</s:AttributeType>  
```  
  
 Consente la definizione `CompanyName` su null, ma `ShipperID` non può contenere un valore null. Se la sezione di dati contiene la riga seguente, il Provider di persistenza imposta lo stato dei dati per il `CompanyName` colonna con la costante di stato OLE DB DBSTATUS_S_ISNULL:  
  
```  
<z:row ShipperID="1"/>  
```  
  
 Se la riga è stata completamente vuota, come indicato di seguito, il Provider di persistenza restituirà uno stato di OLE DB di DBSTATUS_E_UNAVAILABLE per `ShipperID` e DBSTATUS_S_ISNULL per CompanyName.  
  
```  
<z:row/>   
```  
  
 Si noti che una stringa di lunghezza zero non è lo stesso come null.  
  
```  
<z:row ShipperID="1" CompanyName=""/>  
```  
  
 Per la riga precedente, il Provider di persistenza verrà restituito lo stato di OLE DB DBSTATUS_S_OK per entrambe le colonne. Il `CompanyName` in questo caso è semplicemente "" (una stringa di lunghezza zero).  
  
 Per ulteriori informazioni su OLE DB costrutti disponibili per l'utilizzo all'interno dello schema di un documento XML per OLE DB, vedere la definizione di "urn: schemas-microsoft-com: rowset" e Guida OLE DB Programmer.  
  
## <a name="see-also"></a>Vedere anche  
 [Persistenza di record in formato XML](../../../ado/guide/data/persisting-records-in-xml-format.md)
