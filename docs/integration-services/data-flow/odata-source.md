---
title: Origine OData | Documenti Microsoft
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.DTS.DESIGNER.ODATASOURCE.F1
ms.assetid: cc9003c9-638e-432b-867e-e949d50cec90
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: c52506dcfa582cc3e0992fe4fda772489d544247
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="odata-source"></a>Origine OData
  Usare il componente di origine OData in un pacchetto SSIS per utilizzare i dati da un servizio Protocollo OData (Open Data). Il componente supporta i protocolli OData v3 e v4.  
  
-   Per il protocollo OData V3, il componente supporta i formati di dati ATOM e JSON.  
  
-   Per il protocollo OData V4, il componente supporta il formato dati JSON.  
  
> [!NOTE]  
>  È anche possibile usare l'origine OData per eseguire letture da elenchi SharePoint. Per visualizzare tutti gli elenchi in un server SharePoint, utilizzare il seguente URL: http://\<server > / _vti_bin/ListData.svc. Per ulteriori informazioni sulle convenzioni per l'URL di SharePoint, vedere la pagina relativa all' [interfaccia REST di SharePoint Foundation](http://msdn.microsoft.com/library/ff521587.aspx).  Origine OData adesso supporta i prodotti Microsoft Dynamics AX Online e Microsoft Dynamics CRM Online.
  
## <a name="odata-format"></a>Formato OData  
 I risultati restituiti dalla maggior parte dei servizi OData sono in più formati. È possibile specificare il formato del set di risultati utilizzando l'opzione query $format. I formati quali JSON e JSON Light sono più efficienti di ATOM o XML e possono garantire prestazioni migliori quando si trasferiscono grandi quantità di dati. Nella tabella seguente vengono forniti i risultati dei test di esempio. Come si può notare, si verifica un miglioramento delle prestazioni del 30-53% quando si passa dal formato ATOM a JSON e un miglioramento del 67% quando si passa da ATOM al nuovo formato JSON Light, disponibile in WCF Data Services 5.1.  
  
|||||  
|-|-|-|-|  
|Righe|ATOM|JSON|JSON (Light)|  
|10000|113 secondi|74 secondi|68 secondi|  
|1000000|1110 secondi|853 secondi|665 secondi|  
  
> [!NOTE]  
>  L'origine OData SSIS usa 5.6.1 per analizzare i feed OData V3 e ODataLib 6.12.0 per analizzare i feed OData V4.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
-   [Esercitazione: uso dell'origine OData](../../integration-services/data-flow/tutorial-using-the-odata-source.md)  
  
-   [Modificare la query di origine OData in fase di esecuzione](../../integration-services/data-flow/modify-odata-source-query-at-runtime.md)  
  
-   [Editor origine OData &#40;pagina Connessione &#41;](../../integration-services/data-flow/odata-source-editor-connection-page.md)  
  
-   [Editor origine OData &#40;pagina Colonne&#41;](../../integration-services/data-flow/odata-source-editor-columns-page.md)  
  
-   [Editor origine OData &#40;pagina Output degli errori&#41;](../../integration-services/data-flow/odata-source-editor-error-output-page.md)  
  
-   [Proprietà dell'origine OData](../../integration-services/data-flow/odata-source-properties.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione connessione OData](../../integration-services/connection-manager/odata-connection-manager.md)  
  
  
