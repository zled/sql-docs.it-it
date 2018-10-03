---
title: Set di righe DISCOVER_CSDL_METADATA | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: a2d3cffd-a2c4-411c-b244-9e41ebe30939
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 27e3a36850dcf0d314398e994485d5e7410f9a8a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48051392"
---
# <a name="discovercsdlmetadata-rowset"></a>Set di righe DISCOVER_CSDL_METADATA
  Restituisce informazioni su un modello di dati di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] (tabulare o multidimensionale), fornendo la definizione del modello nel formato CSDLBI (Conceptual Schema Definition Language) con annotazioni Business Intelligence. CSDLBI si basa su CSDL, un XML Schema utilizzato da Entity Data Framework per la comunicazione tra un server [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] e il client [!INCLUDE[ssCrescent](../../../includes/sscrescent-md.md)]. Le annotazioni Business Intelligence forniscono metadati aggiuntivi sui modelli tabulari e sugli oggetti in essi contenuti. Per altre informazioni sui modelli di dati tabulari, vedere [Annotazioni CSDL per Business Intelligence &#40;CSDLBI&#41;](../../tabular-model-programming-compatibility-levels-1050-1103/csdl-annotations-for-business-intelligence-csdlbi.md).  
  
 Il contesto di sicurezza del comando influisce sul set di righe restituito. Le autorizzazioni di lettura nell'istanza di Analysis Services sono necessarie per ottenere la definizione CSDL dal server.  
  
 L'identificatore di lingua del client, tramite cui viene inviata la richiesta del set di righe, è incluso nella stringa di connessione per il comando e influisce sulla lingua visualizzata nelle varie proprietà restituite come parte del set di righe.  Per informazioni sulle proprietà e sulla descrizione che l'identificatore di lingua può influenzare, vedere la sezione relativa alle osservazioni.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il `DISCOVER_CSDL_METADATA` set di righe contiene le colonne seguenti.  
  
|**Nome colonna**|**Indicatore del tipo**|**Restrizione**|**Descrizione**|  
|---------------------|------------------------|---------------------|---------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|Sì|Specifica il nome del database per il quale viene richiesta la descrizione CSDLBI. Se omesso, viene utilizzato il database corrente.<br /><br /> Questa restrizione è necessaria per tutti i tipi di modello.|  
|`PERSPECTIVE_ID`|`DBTYPE_WSTR`|Sì|Specifica l'ID di una prospettiva che è stata definita nel modello specificato da CATALOG_NAME.<br /><br /> Restrizione facoltativa. Si applica a tutti i tipi di modello.|  
|`PERSPECTIVE_NAME`|`DBTYPE_WSTR`|Sì|Viene specificato il nome di una prospettiva che è stata definita nel modello specificato da CATALOG_NAME.<br /><br /> Questa restrizione è necessaria quando il modello tabulare include le prospettive o quando una soluzione multidimensionale include più cubi o prospettive.|  
|`METADATA`|`DBTYPE_WSTR`|no|Stringa contenente la definizione XML di un'origine dati e delle relative proprietà, in base allo schema CSDLBI.|  
|`CUBE_ID`|`DBTYPE_WSTR`|Sì|Identificatore di stringa.<br /><br /> Questa restrizione è facoltativa per i database multidimensionali. Se sono disponibili più cubi e la restrizione viene omessa, viene restituito il cubo predefinito.|  
  
## <a name="remarks"></a>Note  
 DISCOVER_CSDL_METADATA dispone dei requisiti seguenti:  
  
-   La richiesta DISCOVER non verrà completata se un database non viene specificato tramite la restrizione CATALOG_NAME.  
  
-   Per un modello tabulare, l'ID prospettiva è obbligatorio se è presente più di una prospettiva nel modello.  
  
-   Per i modelli multidimensionali, il nome del catalogo e il nome sia del cubo (prospettiva) sono obbligatori.  
  
-   Se una prospettiva viene fornita come restrizione, lo stesso set di righe CSDL viene restituito come per il modello. Tuttavia, tutti gli oggetti che sono nel modello ma non inclusi nella prospettiva specificata sono contrassegnati come `Hidden` = True.  
  
-   Per tabelle e colonne, tramite la richiesta DISCOVER viene restituito sempre un valore dalla dimensione del cubo. Se la proprietà della dimensione del cubo non è impostata, tramite la richiesta viene restituito il valore dalla dimensione.  
  
-   Tramite la richiesta DISCOVER non può essere restituita alcuna misura né colonne calcolate contenenti un errore semantico.  
  
-   Tramite la richiesta DISCOVER non verrà restituita alcuna informazione per oggetti che non dispongono di valori di proprietà. Tramite la richiesta DISCOVER non verranno restituiti neanche i valori degli attributi in cui viene utilizzato il valore predefinito.  
  
 È possibile che nella stringa XML restituita nel set di righe siano incluse le proprietà o i valori specifici della lingua. Se si invia ad esempio la richiesta del set di righe da un client con LCID 0403 (spagnolo catalano), tramite la proprietà verranno restituiti i valori seguenti in modo appropriato per lo spagnolo catalano. Se nel server non sono disponibili traduzioni, viene restituita la stringa per la lingua predefinita del server.  
  
-   Didascalia  
  
-   Qualifier  
  
-   SortDirection  
  
-   IsRightToLeft  
  
## <a name="example"></a>Esempio  
 **Tabella**  
  
 La query XMLA seguente restituisce la rappresentazione CSDL del modello tabulare di esempio di AdventureWorks 2012. Ogni soluzione tabulare può contenere un solo modello, pertanto la restrizione PERSPECTIVE_NAME può essere lasciata vuota. Tuttavia, questo modello contiene diverse prospettive.  
  
```  
  
<Discover  xmlns="urn:schemas-microsoft-com:xml-analysis">  
     <RequestType>DISCOVER_CSDL_METADATA</RequestType>  
         <Restrictions>  
            <RestrictionList>  
                <CATALOG_NAME>AdventureWorks2012Tabular</CATALOG_NAME>  
                <PERSPECTIVE_NAME>EMPLOYEE</PERSPECTIVE_NAME>  
                <VERSION>2.0</VERSION>  
            </RestrictionList>  
         </Restrictions>  
         <Properties>  
                <PropertyList>  
                </PropertyList>  
         </Properties>  
</Discover>  
  
```  
  
## <a name="example"></a>Esempio  
 **Multidimensionale**  
  
 La query XMLA seguente restituisce le rappresentazioni CSDLBI del cubo Operations di Contoso. La restrizione VERSION è necessaria per eseguire una query su un database multidimensionale. Il database Contoso Retail contiene due cubi, quindi al cubo Operations si fa riferimento utilizzando la restrizione PERSPECTIVE_NAME.  
  
```  
  
<Discover  xmlns="urn:schemas-microsoft-com:xml-analysis">  
     <RequestType>DISCOVER_CSDL_METADATA</RequestType>  
         <Restrictions>  
            <RestrictionList>  
                <CATALOG_NAME>Contoso_Retail</CATALOG_NAME>  
                <PERSPECTIVE_NAME>Operation</PERSPECTIVE_NAME>  
                <VERSION>2.0</VERSION>  
            </RestrictionList>  
         </Restrictions>  
         <Properties>  
                <PropertyList>  
                </PropertyList>  
         </Properties>  
 </Discover>  
  
```  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Utilizzo di ADOMD.NET per restituire il set di righe  
 Quando si utilizzano ADOMD.NET e il set di righe dello schema per recuperare metadati, è possibile utilizzare il GUID o la stringa per fare riferimento a un oggetto set di righe dello schema nel metodo GetSchemaDataSet. Per altre informazioni, vedere [Working with Schema Rowsets in ADOMD.NET](../../../relational-databases/native-client-ole-db-rowsets/rowsets.md).  
  
 Nella tabella seguente vengono forniti i GUID e i valori stringa che identificano questo set di righe.  
  
|Argomento|valore|  
|--------------|-----------|  
|GUID|3444B255-171E-4cb9-AD98-19E57888A75F|  
|ADOMDNAME|Csdl|  
  
## <a name="see-also"></a>Vedere anche  
 [I set di righe dello Schema di Analysis Services](../analysis-services-schema-rowsets.md)   
 [Annotazioni CSDL per Business Intelligence &#40;CSDLBI&#41;](../../tabular-model-programming-compatibility-levels-1050-1103/csdl-annotations-for-business-intelligence-csdlbi.md)  
  
  
