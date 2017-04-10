---
title: "Informazioni sullo script di distribuzione di Analysis Services | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Distribuzione guidata Analysis Services, script"
  - "distribuzione [Analysis Services], script"
  - "distribuzioni Analysis Services, script"
  - "script [Analysis Services], distribuzione"
ms.assetid: a63ebee9-9848-48f1-82ad-64ecf2e47019
caps.latest.revision: 31
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 31
---
# Informazioni sullo script di distribuzione di Analysis Services
  Lo script di distribuzione XMLA generato dalla Distribuzione guidata [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] include due sezioni:  
  
-   La prima parte dello script di distribuzione contiene i comandi necessari per creare, modificare o eliminare gli oggetti di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] appropriati nel database di destinazione. Per impostazione predefinita, i file di input generati dal progetto [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] sono basati su una distribuzione incrementale. Lo script di distribuzione di XMLA avrà pertanto effetto solo sugli oggetti modificati o eliminati.  
  
-   La seconda parte dello script di distribuzione contiene i comandi necessari per elaborare soltanto gli oggetti creati o modificati nel server di destinazione (opzione Elaborazione predefinita) o per elaborare completamente il database di destinazione. Si può inoltre scegliere di non includere alcun comando di elaborazione nello script di distribuzione.  
  
 L'intero script di distribuzione può essere eseguito in una singola transazione o in più transazioni. Se lo script viene eseguito in più transazioni, la prima parte dello script viene eseguita come singola transazione e ogni oggetto viene elaborato nella relativa transazione.  
  
> [!IMPORTANT]  
>  Tramite la Distribuzione guidata [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] è possibile distribuire oggetti solo in un singolo database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Non è possibile distribuire alcun oggetto o dato a livello del server.  
  
## Vedere anche  
 [Esecuzione della Distribuzione guidata Analysis Services](../../analysis-services/multidimensional-models/running-the-analysis-services-deployment-wizard.md)   
 [Informazioni sui file di input utilizzati per creare uno script di distribuzione](../../analysis-services/multidimensional-models/understanding-the-input-files-used-to-create-the-deployment-script.md)  
  
  