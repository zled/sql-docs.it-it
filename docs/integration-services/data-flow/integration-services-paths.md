---
title: "Percorsi in Integration Services | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.patheditor.general.f1"
  - "sql13.dts.designer.patheditor.metadata.f1"
  - "sql13.dts.designer.patheditor.visualizers.f1"
helpviewer_keywords: 
  - "percorsi [Integration Services], informazioni"
  - "flusso di dati [Integration Services], percorsi"
  - "percorsi [Integration Services]"
  - "destinazioni [Integration Services], percorsi"
  - "origini [Integration Services], percorsi"
ms.assetid: 6c4629a9-2ede-4011-9101-3b342249640e
caps.latest.revision: 41
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 40
---
# Percorsi in Integration Services
  Un percorso collega due componenti in un flusso di dati connettendo l'output di un componente all'input dell'altro. Un percorso ha un'origine e una destinazione. Se un percorso connette, ad esempio, un'origine OLE DB e una trasformazione Ordinamento, l'origine OLE DB costituirà l'origine del percorso e la trasformazione Ordinamento ne costituirà la destinazione. L'origine è il componente da cui inizia il percorso, mentre la destinazione è il componente in cui termina.  
  
 Se si esegue un pacchetto in Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)], è possibile visualizzare i dati in un flusso di dati collegando visualizzatori dati a un percorso. Un visualizzatore dati può essere configurato in modo da visualizzare i dati in una griglia. Si tratta di un utile strumento di debug. Per altre informazioni, vedere [Debug di un flusso di dati](../../integration-services/troubleshooting/debugging-data-flow.md).  
  
## Configurazione del percorso  
 In Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] è disponibile la finestra di dialogo **Editor percorso flusso di dati** che consente di impostare le proprietà di un percorso, visualizzare i metadati delle colonne di dati che passano attraverso il percorso e configurare i visualizzatori dati.  
  
 Le proprietà configurabili di un percorso includono nome, descrizione e annotazione. È possibile configurare i percorsi anche a livello di codice. Per altre informazioni, vedere [Connessione dei componenti del flusso di dati a livello di programmazione](../../integration-services/building-packages-programmatically/connecting-data-flow-components-programmatically.md).  
  
 L'annotazione di un percorso visualizza il nome dell'origine del percorso o il nome del percorso sull'area di progettazione della scheda **Flusso di dati** in Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)]. Le annotazioni dei percorsi sono simili a quelle che è possibile aggiungere a flussi di dati, flussi di controllo e gestori di eventi. L'unica differenza è costituita dal fatto che sono collegate a un percorso, mentre le altre annotazioni vengono visualizzate nelle schede **Flusso di dati**, **Flusso di controllo** e **Gestore evento** di Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)].  
  
 I metadati indicano il nome, il tipo di dati, la precisione, la scala, la lunghezza, la tabella codici e il componente di origine di ogni colonna nell'output del componente precedente. Il componente di origine è il componente del flusso di dati che ha creato la colonna e può anche non essere il primo componente nel flusso di dati. Le trasformazioni Unione input multipli e Ordinamento, ad esempio, creano proprie colonne e costituiscono pertanto l'origine delle relative colonne di output. La trasformazione Copia colonna, invece, può passare colonne senza modificarle oppure creare nuove colonne copiando le colonne di input. La trasformazione Copia colonna costituisce il componente di origine solo per le nuove colonne.  
  
 È possibile impostare le proprietà tramite Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] o a livello di codice.  
  
 Per altre informazioni sulle proprietà che è possibile impostare nella finestra di dialogo **Editor percorso flusso di dati**, fare clic su uno degli argomenti seguenti:  
  
-   [Editor percorso flusso di dati &#40;pagina Generale&#41;](../Topic/Data%20Flow%20Path%20Editor%20\(General%20Page\).md)  
  
-   [Editor percorso flusso di dati &#40pagina Metadati&#41;](../Topic/Data%20Flow%20Path%20Editor%20\(Metadata%20Page\).md)  
  
-   [Editor percorso flusso di dati &#40;pagina Visualizzatori dati&#41;](../Topic/Data%20Flow%20Path%20Editor%20\(Data%20Viewers%20Page\).md)  
  
 Per altre informazioni sulle proprietà che è possibile impostare a livello di programmazione, vedere [Proprietà del percorso](../Topic/Path%20Properties.md).  
  
## Attività correlate  
  
-   [Visualizzazione dei metadati dei percorsi nell'Editor percorso flusso di dati](../Topic/View%20Path%20Metadata%20in%20the%20Data%20Flow%20Path%20Editor.md)  
  
-   [Connessione di componenti in un flusso di dati](../../integration-services/data-flow/connect-components-in-a-data-flow.md)  
  
## Vedere anche  
 [Flusso di dati](../../integration-services/data-flow/data-flow.md)  
  
  