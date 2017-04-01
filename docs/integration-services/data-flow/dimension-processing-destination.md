---
title: "Destinazione elaborazione dimensione | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.dimensionprocessingdest.f1"
helpviewer_keywords: 
  - "destinazione elaborazione dimensione"
  - "caricamento di dimensioni"
  - "destinazioni [Integration Services], elaborazione di dimensioni"
  - "dimensioni [Analysis Services], elaborazione"
ms.assetid: 4c49bb95-7259-42f4-a785-bb6aaf5f8566
caps.latest.revision: 40
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 40
---
# Destinazione elaborazione dimensione
  La destinazione elaborazione dimensione consente di caricare ed elaborare una dimensione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Per altre informazioni sulle dimensioni, vedere [Dimensioni &#40;Analysis Services - Dati multidimensionali&#41;](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md).  
  
 La destinazione elaborazione dimensione include le caratteristiche seguenti:  
  
-   Opzioni per l'esecuzione di elaborazioni incrementali, complete o di aggiornamento.  
  
-   Configurazione degli errori, per specificare se l'elaborazione della dimensione deve ignorare gli errori o arrestarsi dopo un numero di errori specificato.  
  
-   Mapping di colonne di input a colonne nelle tabelle delle dimensioni.  
  
 Per altre informazioni sull'elaborazione degli oggetti [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], vedere [Opzioni e impostazioni di elaborazione &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/processing-options-and-settings-analysis-services.md).  
  
## Configurazione della destinazione Elaborazione dimensione  
 La destinazione Elaborazione dimensione utilizza una gestione connessione di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] per connettersi al progetto di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] o all'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] che contiene le dimensioni elaborate dalla destinazione. Per altre informazioni, vedere [Gestione connessione Analysis Services](../../integration-services/connection-manager/analysis-services-connection-manager.md).  
  
 Questa destinazione include un input. Non supporta un output degli errori.  
  
 È possibile impostare le proprietà tramite Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] o a livello di codice.  
  
 Per altre informazioni sulle proprietà che è possibile impostare nella finestra di dialogo **Editor destinazione elaborazione dimensione**, fare clic su uno degli argomenti seguenti:  
  
-   [Editor destinazione elaborazione dimensione &#40;pagina Gestione connessione&#41;](../../integration-services/data-flow/dimension-processing-destination-editor-connection-manager-page.md)  
  
-   [Editor destinazione elaborazione dimensione &#40;pagina Mapping&#41;](../../integration-services/data-flow/dimension-processing-destination-editor-mappings-page.md)  
  
-   [Editor destinazione elaborazione dimensione &#40;pagina Avanzate&#41;](../../integration-services/data-flow/dimension-processing-destination-editor-advanced-page.md)  
  
 Nella finestra di dialogo **Editor avanzato** sono disponibili le proprietà che è possibile impostare a livello di codice. Per altre informazioni sulle proprietà che è possibile impostare nella finestra di dialogo **Editor avanzato** o a livello di programmazione, fare clic su uno degli argomenti seguenti:  
  
-   [Proprietà comuni](../Topic/Common%20Properties.md)  
  
 Per altre informazioni su come impostare le proprietà, vedere [Impostazione delle proprietà di un componente del flusso di dati](../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md).  
  
## Vedere anche  
 [Flusso di dati](../../integration-services/data-flow/data-flow.md)   
 [Trasformazioni di Integration Services](../../integration-services/data-flow/transformations/integration-services-transformations.md)  
  
  