---
title: Sintassi di query XML per i dati del report XML (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- namespaces [Reporting Services]
- data processing extensions [Reporting Services], data sources
- xmldp [Reporting Services]
- XML [Reporting Services], data retrieval
ms.assetid: d203886f-faa1-4a02-88f5-dd4c217181ef
caps.latest.revision: 46
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 7697f6bf230b3d37b145e56f6827895b44daa5c0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37227001"
---
# <a name="xml-query-syntax-for-xml-report-data-ssrs"></a>Sintassi di query XML per i dati del report XML (SSRS)
  In [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]è possibile creare set di dati per origini dati XML. Dopo aver definito un'origine dati, è possibile creare una query per il set di dati. A seconda del tipo di dati XML a cui punta l'origine dati, si crea la query del set di dati includendo un file XML `Query` o un percorso di elemento. Un file XML `Query` inizia con un  **\<Query >** tag e include spazi dei nomi ed elementi XML che variano a seconda dell'origine dati. Un percorso di elemento è indipendente dallo spazio dei nomi e specifica i nodi e gli attributi dei nodi dei dati XML sottostanti da utilizzare tramite una sintassi di tipo XPath. Per altre informazioni sui percorsi di elementi, vedere [Sintassi del percorso di elemento per i dati del report XML &#40;SSRS&#41;](report-data-ssrs.md).  
  
 È possibile creare un'origine dei dati XML per i tipi di dati XML seguenti:  
  
-   Documenti XML a cui punta un URL tramite il protocollo HTTP  
  
-   Endpoint del servizio Web che restituiscono dati XML  
  
-   Dati XML incorporati  
  
 La modalità utilizzata per specificare un elemento `Query` XML o un percorso di elemento dipende dal tipo di dati XML.  
  
 Per un documento XML, il codice XML `Query` è facoltativo. Se viene incluso, può contenere un elemento `ElementPath` XML facoltativo. Per il valore dell'elemento `ElementPath` XML viene utilizzata la sintassi del percorso di elemento. Si include il codice XML `Query` e XML `ElementPath` per elaborare correttamente gli spazi dei nomi quando richiesto dai dati XML dall'origine dati.  
  
 Per un endpoint del servizio Web a cui punta un URL della stringa di connessione, l'elemento `Query` definisce l'azione SOAP o il metodo del servizio Web oppure entrambi. Tramite il provider di dati XML viene creata una richiesta del servizio Web per recuperare i dati XML da utilizzare per il report.  
  
> [!NOTE]  
>  Quando uno spazio dei nomi del servizio Web contiene una barra (`/)`, includere sia il metodo del servizio Web che l'azione SOAP, per consentire all'estensione per l'elaborazione dati XML di derivare lo spazio dei nomi in modo corretto.  
  
 Per un documento XML incorporato, il codice XML `Query` definisce i dati XML incorporati da utilizzare, include gli spazi dei nomi facoltativi e contiene un file XML facoltativo `ElementPath`...  
  
## <a name="specifying-query-parameters-for-xml-data"></a>Impostazione di parametri di query per dati XML  
 È possibile specificare parametri di query per documenti XML.  
  
-   Per le richieste di URL, i parametri di query vengono inclusi come parametri URL standard.  
  
-   Per le richieste del servizio Web, i parametri di query vengono passati al metodo del servizio Web. Per definire un parametro di query, usare la pagina **Parametri** della finestra di dialogo **Proprietà set di dati** . Per altre informazioni, vedere [finestra di dialogo Proprietà set di dati, parametri](dataset-properties-dialog-box-parameters.md).  
  
### <a name="example"></a>Esempio  
 Negli esempi della tabella seguente viene illustrato come recuperare i dati dal servizio Web ReportServer, da un documento XML e dai dati XML incorporati.  
  
|Origine dei dati XML|Esempio di query|  
|---------------------|-------------------|  
|Dati XML del servizio Web dal metodo ListChildren.|`<Query>`<br /><br /> `<Method Name="ListChildren" Namespace="http://schemas.microsoft.com/sqlserver/2005/06/30/reporting/reportingservices" />`<br /><br /> `</Query>`|  
|Dati XML del servizio Web tramite SoapAction.|`<Query xmlns=namespace>`<br /><br /> `<SoapAction>http://schemas/microsoft.com/sqlserver/2005/03/23/reporting/reportingservices/ListChildren</SoapAction>`<br /><br /> `</Query>`|  
|Documento XML o dati XML incorporati che utilizzano spazi dei nomi.<br /><br /> Elemento Query specificando gli spazi dei nomi per un percorso di elemento.|`<Query xmlns:es="http://schemas.microsoft.com/StandardSchemas/ExtendedSales">`<br /><br /> `<ElementPath>/Customers/Customer/Orders/Order/es:LineItems/es:LineItem</ElementPath>`<br /><br /> `</Query>`|  
|Documento XML incorporato.|`<Query>`<br /><br /> `<XmlData>`<br /><br /> `<Customers>`<br /><br /> `<Customer ID="1">Bobby</Customer>`<br /><br /> `</Customers>`<br /><br /> `</XmlData>`<br /><br /> `<ElementPath>Customer {@}</ElementPath>`<br /><br /> `</Query>`|  
|Documento XML che utilizza valori predefiniti.|*Nessuna query*.<br /><br /> Il percorso viene derivato dal documento XML stesso ed è indipendente dallo spazio dei nomi.|  
  
> [!NOTE]  
>  Nel primo esempio di servizio Web è riportato il contenuto del server di report che usa il metodo <xref:ReportService2006.ReportingService2006.ListChildren%2A> . Per eseguire questa query, è necessario creare una nuova origine dati e impostare la stringa di connessione su http://localhost/reportserver/reportservice2006.asmx. Il <xref:ReportService2006.ReportingService2006.ListChildren%2A> metodo accetta due parametri: `Item` e `Recursive`. Impostare il valore predefinito per `Item` al `/` e `Recursive` a `1`.  
  
## <a name="specifying-namespaces"></a>Definizione degli spazi dei nomi  
 Usare il codice XML `Query` elemento per specificare gli spazi dei nomi utilizzati nei dati XML dall'origine dati. Nella query XML seguente viene utilizzato lo spazio dei nomi `sales`. Nei nodi `ElementPath` XML per `sales:LineItems` e `sales:LineItem` viene utilizzato lo spazio dei nomi `sales`.  
  
```  
<Query xmlns:sales=  
"http://schemas.microsoft.com/StandardSchemas/ExtendedSales">  
   <SoapAction>  
      http://schemas.microsoft.com/SalesWebService/ListOrders   
   </SoapAction>  
   <ElementPath>  
      Customers/Customer/Orders/Order/sales:LineItems/sales:LineItem  
   </ElementPath>  
</Query>  
```  
  
 Per specificare lo spazio dei nomi del provider di dati in modo che lo spazio dei nomi predefinito rimanga vuoto, usare `xmldp`. come illustrato nell'esempio seguente.  
  
### <a name="example"></a>Esempio  
 Negli esempi seguenti viene utilizzato il documento XML DPNamespace.xml, illustrato dopo la tabella. Nella tabella sono illustrati due esempi di sintassi ElementPath XML che include i prefissi degli spazi dei nomi.  
  
|Elemento Query XML|Campi risultanti nel set di dati|  
|-----------------------|-------------------------------------|  
|\<Query/>|Valore a: http://schemas.microsoft.com/...<br /><br /> Valore b: http://schemas.microsoft.com/...<br /><br /> Valore di c: http://schemas.microsoft.com/...|  
|\<XmlDP:query xmlns:xmldp = "http://schemas.microsoft.com/sqlserver/2005/02/reporting/XmlDPQuery" xmlns:ns = "http://schemas.microsoft.com/..." ><br /><br /> \<XmlDP:ElementPath > radice {}/ns:Element2 / nodo\</xmldp:ElementPath ><br /><br /> \</XmlDP:query >|Value D<br /><br /> Value E<br /><br /> Value F|  
  
#### <a name="xml-document-dpnamespacexml"></a>Documento XML: DPNamespace.xml  
 È possibile copiare il codice XML seguente e salvarlo in un URL disponibile per Progettazione report, per l'uso come origine dati XML, ad esempio, http://localhost/DPNamespace.xml.  
  
```  
<Root xmlns:ns="http://schemas.microsoft.com/...">  
   <ns:Element1>  
      <Node>Value A</Node>  
      <Node>Value B</Node>  
      <Node>Value C</Node>  
   </ns:Element1>  
   <ns:Element2>  
      <Node>Value D</Node>  
      <Node>Value E</Node>  
      <Node>Value F</Node>  
   </ns:Element2>  
</Root>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Tipo di connessione XML &#40;SSRS&#41;](xml-connection-type-ssrs.md)   
 [Esercitazioni su Reporting Services &#40;SSRS&#41;](../reporting-services-tutorials-ssrs.md)  
  
  
