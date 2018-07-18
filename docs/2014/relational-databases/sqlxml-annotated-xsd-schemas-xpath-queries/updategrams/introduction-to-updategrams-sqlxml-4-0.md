---
title: Introduzione agli updategram (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- explicit schema mapping [SQLXML]
- updategrams [SQLXML], mapping schema specifying
- namespaces [SQLXML]
- updategrams [SQLXML], about updategrams
- attribute-centric mapping
- invalid characters [SQLXML]
- element-centric mapping [SQLXML]
- mapping schema [SQLXML], updategrams
- namespaces [SQLXML], updategrams
- executing updategrams [SQLXML]
- implicit schema mapping
ms.assetid: cfe24e82-a645-4f93-ab16-39c21f90cce6
caps.latest.revision: 12
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 9ad5fb71e83ed96c520980452748bfc268020ed1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37221001"
---
# <a name="introduction-to-updategrams-sqlxml-40"></a>Introduzione sugli updategram (SQLXML 4.0)
  È possibile modificare (inserire, aggiornare o eliminare) un database in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] da esistenti documento XML mediante un updategram o l'istruzione OPENXML [!INCLUDE[tsql](../../../includes/tsql-md.md)] (funzione).  
  
 La funzione OPENXML modifica un database suddividendo il documento XML esistente e fornendo un set di righe che può essere passato a un'istruzione INSERT, UPDATE o DELETE. Con OPENXML, le operazioni vengono eseguite direttamente sulle tabelle del database. OPENXML rappresenta pertanto la scelta più appropriata ogni volte che un provider di set di righe, ad esempio una tabella, può essere visualizzato come origine.  
  
 Analogamente a OPENXML, un updategram consente di inserire, aggiornare o eliminare dati nel database. Un updategram, tuttavia, agisce sulle viste XML fornite dallo schema XSD (o XDR) con annotazioni, applicando, ad esempio, gli aggiornamenti alla vista XML fornita dallo schema di mapping. Lo schema di mapping, a sua volta, dispone delle informazioni necessarie per eseguire il mapping di elementi e attributi XML alle tabelle e alle colonne di database corrispondenti. L'updategram utilizza queste informazioni di mapping per aggiornare le tabelle e le colonne di database.  
  
> [!NOTE]  
>  In questa documentazione si presuppone che l'utente disponga di una certa familiarità con i modelli e il supporto dello schema di mapping in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Per altre informazioni, vedere [Introduzione agli schemi XSD con annotazioni &#40;SQLXML 4.0&#41;](../../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md). Per le applicazioni legacy che utilizzano XDR, vedere [schemi XDR con annotazioni &#40;deprecato in SQLXML 4.0&#41;](../../sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md).  
  
## <a name="required-namespaces-in-the-updategram"></a>Spazi dei nomi necessari nell'updategram  
 Le parole chiave in un updategram, ad esempio  **\<sincronizzazione >**,  **\<prima >**, e  **\<dopo >**, esiste la `urn:schemas-microsoft-com:xml-updategram`dello spazio dei nomi. Il prefisso dello spazio dei nomi utilizzato è arbitrario. In questa documentazione il prefisso `updg` indica lo spazio dei nomi `updategram`.  
  
## <a name="reviewing-syntax"></a>Esame della sintassi  
 Un updategram è un modello con  **\<sync >**,  **\<prima >**, e  **\<dopo >** blocchi che formano la sintassi del Updategram. Tale sintassi, nella sua forma più semplice, viene illustrata nel codice seguente:  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync [mapping-schema= "AnnotatedSchemaFile.xml"] >  
    <updg:before>  
        ...  
    </updg:before>  
    <updg:after>  
        ...  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 Nelle definizioni seguenti viene descritto il ruolo di ogni blocco:  
  
 **\<prima >**  
 Identifica lo stato esistente, denominato anche "stato before", dell'istanza del record.  
  
 **\<after>**  
 Identifica il nuovo stato in cui devono essere modificati i dati.  
  
 **\<sync>**  
 Contiene il  **\<prima di >** e  **\<dopo >** blocchi. Oggetto  **\<sync >** blocco può contenere più di un set di  **\<prima >** e  **\<dopo >** blocchi. Se è presente più di un set di  **\<prima di >** e  **\<dopo >** blocchi, questi blocchi (anche se sono vuote) deve essere specificato sotto forma di coppie. Inoltre, un updategram può avere più di uno  **\<sync >** blocco. Ogni  **\<sincronizzazione >** blocco è un'unità di transazione (vale a dire che entrambi tutti gli elementi di  **\<sincronizzazione >** blocco viene eseguito o non viene eseguita alcuna operazione). Se si specificano più  **\<sync >** blocchi in un updategram, l'errore di uno  **\<sincronizzazione >** blocco influisce l'altro  **\<sincronizzazione >** blocchi.  
  
 Indica se un updategram Elimina, inserisce o aggiorna l'istanza di un record dipende dal contenuto del  **\<prima di >** e  **\<dopo >** blocchi:  
  
-   Se l'istanza di un record viene visualizzato solo nella  **\<prima di >** senza alcuna istanza corrispondente nel blocco la  **\<dopo >** blocco, l'updategram esegue un'operazione di eliminazione.  
  
-   Se l'istanza di un record viene visualizzato solo nella  **\<dopo >** senza alcuna istanza corrispondente nel blocco la  **\<prima >** blocco, è un'operazione di inserimento.  
  
-   Se un'istanza di record viene visualizzato nei  **\<prima di >** block e ha un'istanza corrispondente nel  **\<dopo >** blocco, è un'operazione di aggiornamento. In questo caso, l'updategram Aggiorna l'istanza del record ai valori specificati nel  **\<dopo >** blocco.  
  
## <a name="specifying-a-mapping-schema-in-the-updategram"></a>Definizione di uno schema di mapping nell'updategram  
 In un updategram l'astrazione XML fornita da uno schema di mapping (sono supportati gli schemi XSD e XDR) può essere implicita o esplicita, ovvero un updategram può essere utilizzato con o senza uno schema di mapping specificato. Se non si specifica uno schema di mapping, l'updategram presuppone un mapping implicito (il mapping predefinito), dove ogni elemento di  **\<prima di >** blocco o  **\<dopo >** blocco viene eseguito il mapping a una tabella e ogni del figlio dell'elemento elemento o attributo esegue il mapping a una colonna nel database. Se si specifica in modo esplicito uno schema di mapping, gli elementi e gli attributi nell'updategram deve corrispondere agli elementi e agli attributi nello schema di mapping.  
  
### <a name="implicit-default-mapping"></a>Mapping implicito (predefinito)  
 Nella maggior parte dei casi, un updategram che esegue aggiornamenti semplici può non richiedere uno schema di mapping. In questo caso, l'updategram si basa sullo schema di mapping predefinito.  
  
 Nell'updategram seguente viene illustrato il mapping implicito. In questo esempio l'updategram inserisce un nuovo cliente nella tabella Sales.Customer. Poiché questo updategram utilizza il mapping implicito, la \<Sales. Customer > elemento viene mappato alla tabella Sales. Customer e gli attributi CustomerID e salespersonid sono associati alle colonne corrispondenti nella tabella Sales. Customer.  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync >  
<updg:before>  
</updg:before>  
<updg:after>  
    <Sales.Customer CustomerID="1" SalesPersonID="277" />  
    </updg:after>  
</updg:sync>  
</ROOT>  
```  
  
### <a name="explicit-mapping"></a>Mapping esplicito  
 Se si specifica uno schema di mapping (XSD o XDR), l'updategram utilizza lo schema per determinare le tabelle e le colonne di database che devono essere aggiornate.  
  
 Se l'updategram esegue un aggiornamento complesso, ad esempio l'inserimento di record in più tabelle sulla base della relazione padre-figlio specificata nello schema di mapping, è necessario fornire in modo esplicito lo schema di mapping tramite l'attributo `mapping-schema` sui cui viene eseguito l'updategram.  
  
 Poiché un updategram è un modello, il percorso specificato per lo schema di mapping nell'updategram è relativo al percorso del file di modello (relativo alla posizione di archiviazione dell'updategram). Per altre informazioni, vedere [specifica uno Schema di Mapping con annotazioni in un Updategram &#40;SQLXML 4.0&#41;](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).  
  
## <a name="element-centric-and-attribute-centric-mapping-in-updategrams"></a>Mapping incentrato sugli elementi e mapping incentrato sugli attributi negli updategram  
 Utilizzando il mapping predefinito, quando lo schema di mapping non viene specificato nell'updategram, gli elementi dell'updategram vengono mappati a tabelle, mentre gli elementi figlio (nel caso di mapping incentrato sugli elementi) e gli attributi (nel caso di mapping incentrato sugli attributi) vengono mappati a colonne.  
  
### <a name="element-centric-mapping"></a>Mapping incentrato sugli elementi  
 In un updategram incentrato sugli elementi, un elemento contiene elementi figlio che indicano le proprietà dell'elemento. Si consideri, ad esempio, l'updategram seguente. Il  **\<Person. Contact >** elemento contiene il  **\<FirstName >** e  **\<LastName >** gli elementi figlio. Tali elementi figlio sono proprietà del  **\<Person. Contact >** elemento.  
  
 Poiché questo updategram non specifica uno schema di mapping, l'updategram utilizza il mapping implicito, in cui il  **\<Person. Contact >** elemento viene mappato alla tabella Person. Contact ed eseguire il mapping dei relativi elementi figlio per il FirstName e Colonne LastName.  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync >  
  <updg:after>  
    <Person.Contact>  
       <FirstName>Catherine</FirstName>  
       <LastName>Abel</LastName>  
    </Person.Contact>  
  </updg:after>  
</updg:sync>  
</ROOT>  
```  
  
### <a name="attribute-centric-mapping"></a>mapping incentrato sugli attributi  
 In un mapping incentrato sugli attributi, gli elementi includono attributi. Nell'updategram seguente viene utilizzato il mapping incentrato sugli attributi. In questo esempio, il  **\<Person. Contact >** elemento è costituito il **FirstName** e **LastName** attributi. Questi attributi sono le proprietà del  **\<Person. Contact >** elemento. Come nell'esempio precedente, l'updategram specifica alcuno schema di mapping, pertanto si basa sul mapping implicito per eseguire il mapping di  **\<Person. Contact >** elemento alla tabella Person. Contact e degli attributi dell'elemento per il rispettive colonne nella tabella.  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync >  
  <updg:before>  
  </updg:before>  
  <updg:after>  
    <Person.Contact FirstName="Catherine" LastName="Abel" />  
  </updg:after>  
</updg:sync>  
</ROOT>  
```  
  
### <a name="using-both-element-centric-and-attribute-centric-mapping"></a>Utilizzo di una combinazione di mapping incentrato sugli elementi e mapping incentrato sugli attributi  
 È possibile specificare una combinazione di mapping incentrato sugli elementi e mapping incentrato sugli attributi, come illustrato nell'updategram seguente. Si noti che il  **\<Person. Contact >** elemento contiene un attributo sia un elemento figlio. L'updategram si basa inoltre su un mapping implicito. Di conseguenza, il **FirstName** attributo e il  **\<LastName >** mappa degli elementi figlio alle colonne corrispondenti nella tabella Person. Contact.  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync >  
  <updg:before>  
  </updg:before>  
  <updg:after>  
    <Person.Contact FirstName="Catherine" >  
       <LastName>Abel</LastName>  
    </Person.Contact>  
  </updg:after>  
</updg:sync>  
</ROOT>  
```  
  
## <a name="working-with-characters-valid-in-sql-server-but-not-valid-in-xml"></a>Utilizzo di caratteri validi in SQL Server ma non validi in XML  
 In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] i nomi di tabella possono includere uno spazio. Questo tipo di nome di tabella, tuttavia, non è valido in XML.  
  
 Per codificare i caratteri validi [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] identificatori ma non sono identificatori XML validi, usare ' __xHHHH\_\_' come valore di codifica, dove HHHH rappresenta il codice UCS-2 esadecimale a quattro cifre per il carattere in più ordine del primo bit significativo. Utilizzando questa schema di codifica, un carattere di spazio viene sostituito da x0020 (il a quattro cifre esadecimale codice per il carattere spazio); di conseguenza, il nome della tabella [Dettagli ordine] in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] diventa _x005B_Order_x0020_Details_x005D\_ in XML.  
  
 Analogamente, potrebbe essere necessario specificare i nomi di elemento in tre parti, ad esempio \<[database]. [ proprietario]. [tabella] >. Poiché i caratteri parentesi quadra ([e]) non sono validi in XML, è necessario specificare questo elemento come \<_x005B_database_x005D\_._x005B_owner_x005D\_._x005B_table_x005D\_>, dove _x005B\_ è la codifica per la parentesi quadra aperta ([) e _x005D\_ la codifica per la parentesi quadra chiusa (]).  
  
## <a name="executing-updategrams"></a>Esecuzione di updategram  
 Poiché un updategram è un modello, utilizza tutti i meccanismi di elaborazione di un modello. Per SQLXML 4.0, è possibile eseguire un updategram in una delle modalità seguenti:  
  
-   Inviandolo in un comando ADO.  
  
-   Inviandolo come comando OLE DB.  
  
## <a name="see-also"></a>Vedere anche  
 [Considerazioni sulla sicurezza degli updategram &#40;SQLXML 4.0&#41;](../security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
