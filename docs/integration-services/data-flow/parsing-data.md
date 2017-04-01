---
title: "Analisi dei dati | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "analisi [Integration Services]"
  - "analisi di dati [Integration Services]"
ms.assetid: 8893ea9d-634c-4309-b52c-6337222dcb39
caps.latest.revision: 39
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 38
---
# Analisi dei dati
  I flussi di dati nei pacchetti consentono di estrarre e caricare dati da archivi dati eterogenei, in cui possono venire utilizzati numerosi diversi tipi di dati standard e personalizzati. In un flusso di dati le origini di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sono responsabili dell'estrazione dei dati, dell'analisi dei dati stringa e della conversione dei dati in un tipo di dati di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Le trasformazioni successive possono analizzare dati per convertirli in un tipo di dati diverso oppure creare copie delle colonne con tipi di dati diversi. Anche le espressioni utilizzate nei componenti possono eseguire il cast di argomenti e operandi a tipi di dati diversi. Quando infine i dati vengono caricati in un archivio dati, la destinazione può analizzare i dati per convertirli in un tipo di dati utilizzato dalla destinazione. Per altre informazioni, vedere [Tipi di dati di Integration Services](../../integration-services/data-flow/integration-services-data-types.md).  
  
## Tipi di analisi  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] offre due tipi di analisi per la conversione dei dati: l'analisi veloce e l'analisi standard.  
  
-   L'analisi veloce è un semplice set di routine di analisi veloci, che non supportano conversioni di tipi di dati specifiche delle impostazioni locali e supportano solo i formati di data e ora utilizzati più di frequente. Per altre informazioni, vedere [Analisi veloce](../Topic/Fast%20Parse.md).  
  
-   L'analisi standard è un set completo di routine di analisi che supportano tutte le conversioni dei tipi di dati offerte dalle API per la conversione dei tipi di dati di automazione disponibili in Oleaut32.dll e Ole2dsip.dll. Per altre informazioni, vedere [Analisi standard](../Topic/Standard%20Parse.md).  
  
  