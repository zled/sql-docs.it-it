---
title: "Contenitore Host delle attivit&#224; | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.taskhostcontainer.f1"
helpviewer_keywords: 
  - "contenitori [Integration Services], host attività"
  - "Host delle attività - contenitore"
ms.assetid: 7394a2c2-1b07-427d-b94a-9792e7783d35
caps.latest.revision: 45
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 45
---
# Contenitore Host delle attivit&#224;
  Il contenitore host delle attività incapsula una singola attività. In Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] il contenitore host delle attività non viene configurato separatamente, ma viene configurato quando si impostano le proprietà dell'attività incapsulata. Per altre informazioni sulle attività incapsulate nel contenitore Host delle attività, vedere [Attività di Integration Services](../../integration-services/control-flow/integration-services-tasks.md).  
  
 Questo contenitore estende al livello delle attività l'utilizzo di gestori di eventi e variabili. Per altre informazioni, vedere [Gestori eventi di Integration Services &#40;SSIS&#41;](../../integration-services/integration-services-ssis-event-handlers.md) e [Variabili di Integration Services &#40;SSIS&#41;](../../integration-services/integration-services-ssis-variables.md).  
  
## Configurazione dell'Host attività  
 È possibile impostare le proprietà a livello di codice o nella finestra **Proprietà** di [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] .  
  
 Per informazioni sull'impostazione di queste proprietà in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], vedere [Impostazione delle proprietà di un'attività o di un contenitore](../Topic/Set%20the%20Properties%20of%20a%20Task%20or%20Container.md).  
  
 Per informazioni sull'impostazione di queste proprietà a livello di codice, vedere <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>.  
  
## Attività correlate  
  
-   [Impostazione delle proprietà di un'attività o di un contenitore](../Topic/Set%20the%20Properties%20of%20a%20Task%20or%20Container.md)  
  
## Vedere anche  
 [Contenitori in Integration Services](../../integration-services/control-flow/integration-services-containers.md)  
  
  