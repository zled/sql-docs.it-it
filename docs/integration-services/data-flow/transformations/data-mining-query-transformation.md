---
title: "Trasformazione Query di data mining | Microsoft Docs"
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
  - "sql13.dts.designer.dataminingquerytrans.f1"
helpviewer_keywords: 
  - "Query di data mining - trasformazione"
  - "query di stima [Integration Services]"
ms.assetid: 7960133b-a3e1-48af-ba43-55ed78c38e71
caps.latest.revision: 43
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 43
---
# Trasformazione Query di data mining
  La trasformazione Query di data mining esegue query di stima basate su modelli di data mining. Questa trasformazione contiene un generatore di query per la creazione di query DMX (Data Mining Extensions). Il generatore di query consente di creare istruzioni personalizzate per la valutazione dei dati di input della trasformazione in base a un modello di data mining esistente, utilizzando il linguaggio DMX. Per altre informazioni, vedere [Guida di riferimento a DMX &#40;Data Mining Extensions&#41;](../../../dmx/data-mining-extensions-dmx-reference.md).  
  
 Una singola trasformazione può eseguire più query di stima, se i modelli sono compilati in base alla stessa struttura di data mining. Per altre informazioni, vedere [Data Mining Query Tools](../../../analysis-services/data-mining/data-mining-query-tools.md) (Strumenti query di data mining).  
  
## Configurazione della trasformazione Query di data mining  
 La trasformazione Query di data mining usa una gestione connessione [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] per connettersi al progetto di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] o all'istanza di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] che contiene la struttura e i modelli di data mining. Per altre informazioni, vedere [Gestione connessione Analysis Services](../../../integration-services/connection-manager/analysis-services-connection-manager.md).  
  
 Questa trasformazione include un input e un output. Non supporta un output degli errori.  
  
 È possibile impostare le proprietà tramite Progettazione [!INCLUDE[ssIS](../../../includes/ssis-md.md)] o a livello di codice.  
  
 Per altre informazioni sulle proprietà che è possibile impostare nella finestra di dialogo **Editor trasformazione Query di data mining** o a livello di codice, fare clic su uno degli argomenti seguenti:  
  
-   [Editor trasformazione Query di data mining &#40;scheda Modello di data mining&#41;](../../../integration-services/data-flow/transformations/data-mining-query-transformation-editor-mining-model-tab.md)  
  
-   [Editor trasformazione Query di data mining &#40;scheda Modello di data mining&#41;](../../../integration-services/data-flow/transformations/data-mining-query-transformation-editor-mining-model-tab.md)  
  
 Nella finestra di dialogo **Editor avanzato** sono disponibili le proprietà che è possibile impostare a livello di codice. Per ulteriori informazioni sulle proprietà che è possibile impostare nella finestra di dialogo **Editor avanzato** o a livello di codice, fare clic su uno degli argomenti seguenti:  
  
-   [Proprietà comuni](../Topic/Common%20Properties.md)  
  
-   [Proprietà personalizzate delle trasformazioni](../../../integration-services/data-flow/transformations/transformation-custom-properties.md)  
  
 Per altre informazioni su come impostare le proprietà, vedere [Impostazione delle proprietà di un componente del flusso di dati](../../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md).  
  
  