---
title: "Report di programmabilità della Web Part visualizzatore nell'integrazione con SharePoint | Documenti Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: 714017b7-1bd6-4950-a3c6-d0df8450a877
caps.latest.revision: 8
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: 9339b0f383efd757e9be49271f4a5bdd2d7a4d4f
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="report-viewer-web-part-programmability-in-sharepoint-integration"></a>Programmabilità della web part Visualizzatore report nell'integrazione con SharePoint
  La Web Part Visualizzatore Report è un controllo server, che contiene un set di pubblico application programming interface (API) che consente agli sviluppatori di creare applicazioni di SharePoint personalizzate. È possibile creare web part personalizzate che forniscono parametri e percorsi di report a web part Visualizzatore report tramite connessioni web part. È inoltre possibile incorporare la web part in una pagina web part di SharePoint personalizzata e personalizzarla usando l'API pubblica.  
  
## <a name="connecting-to-report-viewer-web-part-with-custom-web-parts"></a>Connessione a web part Visualizzatore report con web part personalizzate  
 La Web Part Visualizzatore Report è un consumer di connessione di Web part di SharePoint che implementano <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> o T:Microsoft.SharePoint.WebPartPages.IFilterValues. Un <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> Web Part, ad esempio il **documenti** può fornire il percorso di un report a una Web Part Visualizzatore Report quando viene inserita nella stessa pagina Web Part della Web Part Visualizzatore Report. Analogamente, un T:Microsoft.SharePoint.WebPartPages.IFilterValues Web Part, ad esempio il **testo filtro** o **filtro scelte**, può fornire un parametro di report a una Web Part Visualizzatore Report quando viene inserita nella stessa pagina Web Part della Web Part Visualizzatore Report.  
  
### <a name="implementing-a-report-path-provider-with-iwebpartrow"></a>Implementazione di un provider del percorso report con IWebPartRow  
 Per fornire il percorso di un report a una web part Visualizzatore report tramite connessioni web part, eseguire le operazioni seguenti:  
  
1.  Creare una web part che implementa l'interfaccia <xref:System.Web.UI.WebControls.WebParts.IWebPartRow>.  
  
2.  Aggiungere la web part alla stessa pagina web part della web part Visualizzatore report.  
  
3.  Connettere la web part alla web part Visualizzatore report nell'interfaccia utente di progettazione delle web part basata sul Web.  
  
    > [!NOTE]  
    >  È possibile connettere una sola <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> Web Part della Web Part Visualizzatore Report per una volta, è possibile connettere contemporaneamente un <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> Web e un T:Microsoft.SharePoint.WebPartPages.IFilterValues Web Part alla Web Part Visualizzatore Report nello stesso momento.  
  
 Per il <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> Web Part per funzionare correttamente con T:Microsoft.ReportingServices.SharePoint.UI.WebParts.ReportViewerWebPart, è necessario eseguire le operazioni seguenti <xref:System.Web.UI.WebControls.WebParts.IWebPartRow.GetRowData%2A> metodo:  
  
-   Richiamare il metodo di callback con un oggetto <xref:System.Data.DataRowView> come parametro di input.  
  
-   Verificare che l'oggetto <xref:System.Data.DataRowView> contenga una colonna denominata "DocUrl" contenente il percorso del report.  
  
    > [!NOTE]  
    >  La web part Visualizzatore report nel componente aggiuntivo per [!INCLUDE[offSPServ](../includes/offspserv-md.md)] supporta inoltre la ricezione del percorso del report tramite la colonna "FileRef".  
  
### <a name="implementing-a-report-parameter-provider-with-ifiltervalues"></a>Implementazione del provider di un parametro di report con IFilterValues  
 Una Web Part che implementa T:Microsoft.SharePoint.WebPartPages.IFilterValues può fornire un valore del parametro per la Web Part Visualizzatore Report. Il valore del parametro inviato alla web part Visualizzatore report è soggetto alle stesse restrizioni esistenti per il parametro del report come specificato nella definizione del report, ad esempio tipo di dati, valori validi e così via.  
  
 Per fornire un parametro di report a una web part Visualizzatore report, eseguire le operazioni seguenti:  
  
1.  Creare una Web Part che implementa l'interfaccia T:Microsoft.SharePoint.WebPartPages.IFilterValues.  
  
2.  Aggiungere la Web Part alla stessa pagina come il T:Microsoft.ReportingServices.SharePoint.UI.WebParts.ReportViewerWebPart.  
  
3.  Connettere la Web Part di T:Microsoft.SharePoint.WebPartPages.IFilterValues per la Web Part Visualizzatore Report nell'interfaccia utente di progettazione Web Part basata sul Web.  
  
    > [!NOTE]  
    >  È possibile connettersi più T:Microsoft.SharePoint.WebPartPages.IFilterValues Web part alla Web Part Visualizzatore Report alla volta. Tuttavia, è possibile connettere entrambi un <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> Web e un T:Microsoft.SharePoint.WebPartPages.IFilterValues Web Part alla Web Part Visualizzatore Report nello stesso momento.  
  
  
