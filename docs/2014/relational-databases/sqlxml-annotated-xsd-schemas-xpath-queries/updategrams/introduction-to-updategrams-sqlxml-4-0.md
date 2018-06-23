---
title: Introduzione sugli updategram (SQLXML 4.0) | Documenti Microsoft
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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2fce6a3a005df07f7c06f668809f7635aad55a27
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36054926"
---
# <a name="introduction-to-updategrams-sqlxml-40"></a>Introduzione sugli updategram (SQLXML 4.0)
  È possibile modificare (inserire, aggiornare o eliminare) un database in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] da esistente documento XML mediante un updategram o l'istruzione OPENXML [!INCLUDE[tsql](../../../includes/tsql-md.md)] (funzione).  
  
 La funzione OPENXML modifica un database suddividendo il documento XML esistente e fornendo un set di righe che può essere passato a un'istruzione INSERT, UPDATE o DELETE. Con OPENXML, le operazioni vengono eseguite direttamente sulle tabelle del database. OPENXML rappresenta pertanto la scelta più appropriata ogni volte che un provider di set di righe, ad esempio una tabella, può essere visualizzato come origine.  
  
 Analogamente a OPENXML, un updategram consente di inserire, aggiornare o eliminare dati nel database. Un updategram, tuttavia, agisce sulle viste XML fornite dallo schema XSD (o XDR) con annotazioni, applicando, ad esempio, gli aggiornamenti alla vista XML fornita dallo schema di mapping. Lo schema di mapping, a sua volta, dispone delle informazioni necessarie per eseguire il mapping di elementi e attributi XML alle tabelle e alle colonne di database corrispondenti. L'updategram utilizza queste informazioni di mapping per aggiornare le tabelle e le colonne di database.  
  
> [!NOTE]  
>  In questa documentazione si presuppone che l'utente disponga di una certa familiarità con i modelli e il supporto dello schema di mapping in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Per altre informazioni, vedere [Introduzione agli schemi XSD con annotazioni &#40;SQLXML 4.0&#41;](../../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md). Per le applicazioni legacy che utilizzano XDR, vedere [schemi XDR &#40;deprecato in SQLXML 4.0&#41;](../../sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md).  
  
## <a name="required-namespaces-in-the-updategram"></a>Spazi dei nomi necessari nell'updategram  
 Le parole chiave in un updategram, ad esempio  **\<sync >**,  **\<prima >**, e  **\<dopo >**, esiste il `urn:schemas-microsoft-com:xml-updategram`dello spazio dei nomi. Il prefisso dello spazio dei nomi utilizzato è arbitrario. In questa documentazione il prefisso `updg` indica lo spazio dei nomi `updategram`.  
  
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
  
 **\<prima di >**  
 Identifica lo stato esistente, denominato anche "stato before", dell'istanza del record.  
  
 **\<after>**  
 Identifica il nuovo stato in cui devono essere modificati i dati.  
  
 **\<sync>**  
 Contiene il  **\<prima di >** e  **\<dopo >** blocchi. Un  **\<sync >** blocco può contenere più di un set di  **\<prima >** e  **\<dopo >** blocchi. Se è presente più di un set di  **\<prima di >** e  **\<dopo >** blocchi, questi blocchi (anche se sono vuote) devono essere specificati come coppie. Inoltre, un updategram può avere più di uno  **\<sync >** blocco. Ogni  **\<sincronizzazione >** blocco è un'unità di transazione (vale a dire che l'intero contenuto di  **\<sync >** blocchi viene eseguita o viene eseguita alcuna operazione). Se si specificano più  **\<sync >** blocchi in un updategram, l'errore in uno  **\<sync >** blocco non influisce sull'altro  **\<sincronizzazione >** blocchi.  
  
 Indica se un updategram Elimina, inserisce o aggiorna un'istanza di record dipende dal contenuto del  **\<prima di >** e  **\<dopo >** blocchi:  
  
-   Se l'istanza di un record è presente solo nel  **\<prima di >** senza alcuna istanza corrispondente nel blocco di  **\<dopo >** blocco, l'updategram esegue un'operazione di eliminazione.  
  
-   Se l'istanza di un record è presente solo nel  **\<dopo >** senza alcuna istanza corrispondente nel blocco di  **\<prima >** blocco, è un'operazione di inserimento.  
  
-   Se un'istanza di record è presente il  **\<prima di >** blocca e dispone di un'istanza corrispondente nel  **\<dopo >** blocco, è un'operazione di aggiornamento. In questo caso, l'updategram Aggiorna l'istanza del record ai valori specificati nel  **\<dopo >** blocco.  
  
## <a name="specifying-a-mapping-schema-in-the-updategram"></a>Definizione di uno schema di mapping nell'updategram  
 In un updategram l'astrazione XML fornita da uno schema di mapping (sono supportati gli schemi XSD e XDR) può essere implicita o esplicita, ovvero un updategram può essere utilizzato con o senza uno schema di mapping specificato. Se non si specifica uno schema di mapping, l'updategram presuppone un mapping implicito (il mapping predefinito), dove ogni elemento di  **\<prima di >** blocco o  **\<dopo >** blocco esegue il mapping a una tabella e l'elemento figlio di ogni elemento o attributo viene mappato a una colonna nel database. Se si specifica in modo esplicito uno schema di mapping, gli elementi e gli attributi nell'updategram deve corrispondere agli elementi e agli attributi nello schema di mapping.  
  
### <a name="implicit-default-mapping"></a>Mapping implicito (predefinito)  
 Nella maggior parte dei casi, un updategram che esegue aggiornamenti semplici può non richiedere uno schema di mapping. In questo caso, l'updategram si basa sullo schema di mapping predefinito.  
  
 Nell'updategram seguente viene illustrato il mapping implicito. In questo esempio l'updategram inserisce un nuovo cliente nella tabella Sales.Customer. Poiché questo updategram utilizza il mapping implicito, la \<Sales. Customer > elemento viene mappato alla tabella Sales. Customer e gli attributi CustomerID e SalesPersonID esegue il mapping alle colonne corrispondenti nella tabella Sales. Customer.  
  
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
  
 Poiché un updategram è un modello, il percorso specificato per lo schema di mapping nell'updategram è relativo al percorso del file di modello (relativo alla posizione di archiviazione dell'updategram). Per altre informazioni, vedere [specifica di uno Schema di Mapping con annotazioni in un Updategram &#40;SQLXML 4.0&#41;](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).  
  
## <a name="element-centric-and-attribute-centric-mapping-in-updategrams"></a>Mapping incentrato sugli elementi e mapping incentrato sugli attributi negli updategram  
 Utilizzando il mapping predefinito, quando lo schema di mapping non viene specificato nell'updategram, gli elementi dell'updategram vengono mappati a tabelle, mentre gli elementi figlio (nel caso di mapping incentrato sugli elementi) e gli attributi (nel caso di mapping incentrato sugli attributi) vengono mappati a colonne.  
  
### <a name="element-centric-mapping"></a>Mapping incentrato sugli elementi  
 In un updategram incentrato sugli elementi, un elemento contiene elementi figlio che indicano le proprietà dell'elemento. Si consideri, ad esempio, l'updategram seguente. Il  **\<Person. Contact >** elemento contiene il  **\<FirstName >** e  **\<LastName >** gli elementi figlio. Tali elementi figlio sono proprietà del  **\<Person. Contact >** elemento.  
  
 Poiché questo updategram non specifica uno schema di mapping, l'updategram utilizza il mapping implicito, in cui il  **\<Person. Contact >** elemento viene mappato alla tabella Person. Contact ed eseguire il mapping dei relativi elementi figlio per il nome e Colonne LastName.  
  
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
 In un mapping incentrato sugli attributi, gli elementi includono attributi. Nell'updategram seguente viene utilizzato il mapping incentrato sugli attributi. In questo esempio, il  **\<Person. Contact >** elemento è costituito il **FirstName** e **LastName** attributi. Questi attributi sono le proprietà del  **\<Person. Contact >** elemento. Come nell'esempio precedente, l'updategram specifica alcuno schema di mapping, pertanto si basa sul mapping implicito per eseguire il mapping di  **\<Person. Contact >** elemento alla tabella Person. Contact e degli attributi dell'elemento per il alle rispettive colonne nella tabella.  
  
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
 È possibile specificare una combinazione di mapping incentrato sugli elementi e mapping incentrato sugli attributi, come illustrato nell'updategram seguente. Si noti che il  **\<Person. Contact >** elemento contiene un attributo sia un elemento figlio. L'updategram si basa inoltre su un mapping implicito. Di conseguenza, il **FirstName** attributo e il  **\<LastName >** mapping dell'elemento figlio alle colonne corrispondenti nella tabella Person. Contact.  
  
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
  
 Per codificare i caratteri validi [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] identificatori ma che non sono identificatori XML validi, utilizzare ' __xHHHH\_\_' come valore di codifica, dove HHHH rappresenta il codice UCS-2 esadecimale a quattro cifre per il carattere in più ordine del primo bit significativo. Utilizzando questo schema di codifica, un carattere di spazio viene sostituito da x0020 (il formato a quattro cifre codice esadecimale per un carattere di spazio); di conseguenza, il nome della tabella [Dettagli ordine] in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] diventa _x005B_Order_x0020_Details_x005D\_ in XML.  
  
 Analogamente, potrebbe essere necessario specificare nomi di elemento di tre parti, ad esempio \<[database]. [ proprietario]. [tabella] >. Poiché le parentesi quadre ([e]) non sono validi in XML, è necessario specificare questo elemento come \<_x005B_database_x005D\_._x005B_owner_x005D\_._x005B_table_x005D\_>, dove _x005B\_ è la codifica per la parentesi quadra aperta ([) e _x005D\_ la codifica per la parentesi quadra chiusa (]).  
  
## <a name="executing-updategrams"></a>Esecuzione di updategram  
 Poiché un updategram è un modello, utilizza tutti i meccanismi di elaborazione di un modello. Per SQLXML 4.0, è possibile eseguire un updategram in una delle modalità seguenti:  
  
-   Inviandolo in un comando ADO.  
  
-   Inviandolo come comando OLE DB.  
  
## <a name="see-also"></a>Vedere anche  
 [Considerazioni sulla sicurezza di updategram &#40;SQLXML 4.0&#41;](../security/updategram-security-considerations-sqlxml-4-0.md)  
  
  