---
title: Set di righe DISCOVER_CALC_DEPENDENCY | Documenti Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: schema-rowsets
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DISCOVER_CALC_DEPENDENCIES rowset
ms.assetid: f39dde72-fa5c-4c82-8b4e-88358aa2e422
caps.latest.revision: 22
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 86f0ed45ced35aba884f05284f886334d250694d
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="discovercalcdependency-rowset"></a>Set di righe DISCOVER_CALC_DEPENDENCY
  Crea report sulle dipendenze tra i calcoli e sugli oggetti a cui si fa riferimento in tali calcoli. Tali informazioni possono essere utilizzate in un'applicazione client per segnalare problemi con formule complesse o per visualizzare avvisi quando gli oggetti correlati vengono eliminati o modificati. È inoltre possibile utilizzare il set di righe per estrarre le espressioni DAX utilizzate nelle misure o nelle colonne calcolate.  
  
 **Si applica a:** i modelli tabulari  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il set di righe **DISCOVER_CALC_DEPENDENCY** contiene le colonne seguenti. Nella tabella viene inoltre specificato il tipo di dati, viene indicato se la colonna può essere limitata per ridurre le righe restituite e viene fornita una descrizione di ogni colonna.  
  
|Nome colonna|Indicatore del tipo|Restrizione|Description|  
|-----------------|--------------------|-----------------|-----------------|  
|**DATABASE_NAME**|**DBTYPE_WSTR**|Sì|Viene specificato il nome del database contenente l'oggetto per il quale viene richiesta l'analisi delle dipendenze. Se omesso, viene utilizzato il database corrente.<br /><br /> Il set di righe **DISCOVER_DEPENDENCY_CALC** può essere limitato tramite questa colonna.|  
|**OBJECT_TYPE**|**DBTYPE_WSTR**|Sì|Viene indicato il tipo di oggetto per il quale viene richiesta l'analisi delle dipendenze. L'oggetto deve essere uno dei tipi seguenti:<br /><br /> **ACTIVE_RELATIONSHIP**: una relazione attiva<br /><br /> **CALC_COLUMN**: colonna calcolata<br /><br /> **HIERARCHY**: una gerarchia<br /><br /> **MEASURE**: una misura<br /><br /> **RELATIONSHIP**: una relazione<br /><br /> **KPI**: un indicatore di prestazioni chiave<br /><br /> <br /><br /> Si noti che il **DISCOVER_DEPENDENCY_CALC** righe può essere limitato tramite questa colonna.|  
|**QUERY**|**DBTYPE_WSTR**|Sì|Per i modelli tabulari creati in [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)], è possibile includere una query o un'espressione DAX per visualizzare il grafico delle dipendenze per questa query o espressione. Tramite la restrizione QUERY viene fornita alle applicazioni client una modalità per determinare gli oggetti utilizzati da una query DAX.<br /><br /> La restrizione **QUERY** può essere specificata in XMLA o nella clausola WHERE di una query DMV. Per ulteriori informazioni, vedere la sezione degli esempi.|  
|**TAVOLO**|**DBTYPE_WSTR**||Nome della tabella contenente l'oggetto per il quale vengono generate le informazioni sulle dipendenze.|  
|**OGGETTO**|**DBTYPE_WSTR**||Nome dell'oggetto per il quale vengono generate le informazioni sulle dipendenze. Se l'oggetto è una misura o una colonna calcolata, utilizzare il nome della misura. Se l'oggetto è una relazione, il nome della tabella (o dimensione del cubo) contenente la colonna che fa parte della relazione.|  
|**ESPRESSIONE**|**DBTYPE_WSTR**||Formula contenente l'oggetto per il quale vengono richieste le dipendenze.|  
|**REFERENCED_OBJECT_TYPE**|**DBTYPE_WSTR**||Viene restituito il tipo di oggetto che presenta una dipendenza dall'oggetto a cui si fa riferimento. Gli oggetti restituiti possono essere del tipo seguente:<br /><br /> **CALC_COLUMN**: una colonna calcolata<br /><br /> **COLUMN**: una colonna di dati<br /><br /> **MEASURE**: una misura<br /><br /> **RELATIONSHIP**: una relazione<br /><br /> **KPI**: un indicatore di prestazioni chiave|  
|**REFERENCED_TABLE**|**DBTYPE WSTR**||Nome della tabella contenente l'oggetto dipendente.|  
|**REFERENCED_OBJECT**|**DBTYPE WSTR**||Nome dell'oggetto che presenta una dipendenza dall'oggetto a cui si fa riferimento. Per misure e colonne calcolate, il nome della misura o della colonna. Per le relazioni, il nome completo della tabella (o dimensione del cubo) contenente l'oggetto dipendente.|  
|**REFERENCED_EXPRESSION**|**DBTYPE_WSTR**||Formula, in una colonna calcolata o in una misura, che dipende dall'oggetto a cui si fa riferimento.|  
  
## <a name="example"></a>Esempio  
 **Sintassi di base**  
  
 Di seguito è riportata una query DMV semplice tramite cui vengono restituiti valori per tutte le colonne di questo set di righe, utilizzando il database predefinito nella connessione corrente. È possibile eseguire questa query in una finestra di query MDX e visualizzarne i risultati in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]. È anche possibile seguire le tecniche descritte in [query sulle DMV di Power Pivot di Excel](http://go.microsoft.com/fwlink/?LinkID=235146) per visualizzare i risultati della query DMV in Excel.  
  
```  
SELECT * FROM $System.DISCOVER_CALC_DEPENDENCY  
```  
  
## <a name="example"></a>Esempio  
 **Ordinare i risultati**  
  
 Aggiungere una clausola ORDER BY per ordinare il set di righe in base alla tabella o a un'altra colonna.  
  
```  
SELECT * FROM $System.DISCOVER_CALC_DEPENDENCY ORDER BY [TABLE] ASC  
```  
  
## <a name="example"></a>Esempio  
 **Applicare filtri tramite una clausola WHERE**  
  
 Nella query successiva viene illustrato come aggiungere una restrizione utilizzando la clausola WHERE. Le colonne seguenti possono essere utilizzate come filtri query in una clausola WHERE: **Database_Name**, **Object_Type**e **Query**.  
  
```  
SELECT * From $SYSTEM.DISCOVER_CALC_DEPENDENCY WHERE OBJECT_TYPE = 'RELATIONSHIP' OR OBJECT_TYPE = 'ACTIVE_RELATIONSHIP'  
```  
  
## <a name="example"></a>Esempio  
 **Filtrare le misure e colonne calcolate per visualizzare le espressioni DAX sottostanti**  
  
 In questa query è possibile selezionare solo la misura o la colonna calcolata e, successivamente, visualizzare l'espressione DAX utilizzata nel calcolo. Nella colonna EXPRESSION sono contenute le espressioni DAX. Se si utilizza DISCOVER_CALC_DEPENDENCY per estrarre l'espressione DAX utilizzata nel modello, questa query è sufficiente a tale scopo. Infatti vengono restituite tutte le espressioni utilizzate nel modello, in ordine crescente.  
  
```  
SELECT * From $SYSTEM.DISCOVER_CALC_DEPENDENCY WHERE OBJECT_TYPE = 'MEASURE' OR OBJECT_TYPE = 'CALC_COLUMN' ORDER BY [EXPRESSION] ASC  
```  
  
## <a name="example"></a>Esempio  
 **Applicare filtri tramite la QUERY**  
  
 Utilizzando la restrizione QUERY, è possibile specificare una query DAX per visualizzare tutti gli oggetti utilizzati nella query. Si consideri una query semplice come "Evaluate Customer". In base a quanto scritto, tramite questa query vengono restituite le righe dei dati dei clienti, in cui la composizione delle righe è basata sulle colonne della tabella Customer. Se ora si esegue DISCOVER_CALC_DEPENDENCY con una restrizione QUERY di "Evaluate Customer", si otterranno le colonne (o gli oggetti) utilizzate nella query. In questo caso, si tratta di un elenco di colonne della tabella Customer.  
  
 Nel set successivo di query viene illustrata la sintassi per la restrizione QUERY. È possibile eseguire queste query sul [modello tabulare di AdventureWorks per SQL Server 2012](http://msftdbprodsamples.codeplex.com/releases/view/55330) per visualizzare il set di risultati.  
  
 Nella prima query viene illustrato come specificare una restrizione QUERY per i nomi di oggetto contenenti spazi. Il secondo esempio, preso in prestito dalla pagina relativa all' [esecuzione di query DAX tramite OLE DB e ADOMD.NET](http://go.microsoft.com/fwlink/?LinkId=254329), è una query più complessa in cui sono inclusi oggetti di più tabelle.  
  
> [!NOTE]  
>  Anche se sembra che per le query vengano utilizzate le virgolette doppie, in realtà vengono utilizzate solo quelle singole. Una coppia di virgolette racchiude ' Evaluate \<Tablename >', e deve essere eseguito da raddoppiandole virgolette singole utilizzate attorno al nome della tabella. Le virgolette singole attorno a un nome di tabella sono necessarie solo per i nomi di tabelle contenenti uno spazio.  
  
```  
SELECT * From $SYSTEM.DISCOVER_CALC_DEPENDENCY WHERE QUERY = 'EVALUATE ''Reseller Sales'''  
```  
  
```  
SELECT * from $system.DISCOVER_CALC_DEPENDENCY WHERE QUERY = 'EVALUATE CALCULATETABLE(VALUES(''Product Subcategory''[Product Subcategory Name]), ''Product Category''[Product Category Name] = "Bikes")'  
```  
  
## <a name="example"></a>Esempio  
 **Esempio di XMLA restrizione QUERY**  
  
 È possibile utilizzare il comando di individuazione (Discover) di XMLA per restituire gli oggetti query in una tabella. Tramite XMLA i risultati vengono restituiti come XML non elaborato. È possibile utilizzare ADOMD.NET per analizzare i risultati in un formato più leggibile.  
  
```  
<Discover xmlns="urn:schemas-microsoft-com:xml-analysis">  
   <RequestType>DISCOVER_CALC_DEPENDENCY</RequestType>  
     <Restrictions>  
        <RestrictionList>  
            <QUERY>Evaluate 'Reseller Sales'</QUERY>  
        </RestrictionList>  
    </Restrictions>  
    <Properties />  
</Discover>  
```  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Utilizzo di ADOMD.NET per restituire il set di righe  
 Quando si utilizzano ADOMD.NET e il set di righe dello schema per recuperare metadati, è possibile utilizzare il GUID o la stringa per fare riferimento a un oggetto set di righe dello schema nel metodo GetSchemaDataSet. Per altre informazioni, vedere [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md).  
  
 Nella tabella seguente vengono forniti i GUID e i valori stringa che identificano questo set di righe.  
  
|Argomento|Valore|  
|--------------|-----------|  
|GUID|a07ccd46-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|DependencyGraph|  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe dello Schema di Analysis Services](../../../analysis-services/schema-rowsets/analysis-services-schema-rowsets.md)   
 [Usare dinamica viste a Gestione &#40; viste a gestione dinamica &#41; per monitorare Analysis Services](../../../analysis-services/instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services.md)  
  
  

