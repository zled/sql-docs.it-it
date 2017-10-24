---
title: Definizione delle Stored procedure | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- stored procedures [Analysis Services]
- OLAP [Analysis Services], stored procedures
- external routines [Analysis Services]
- stored procedures [Analysis Services], about stored procedures
ms.assetid: f9c57d91-f60f-4f0e-8f7f-d87f4ba97b7c
caps.latest.revision: 24
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b70d20ea8ad3cc108076261b692129bf72ccb6ef
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="defining-stored-procedures"></a>Definizione delle stored procedure
  È possibile utilizzare le stored procedure per chiamare routine esterne da [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. È possibile scrivere una routine esterna chiamata da una stored procedure in ogni linguaggio di Common Runtime Language (CLR), ad esempio C, C++, C#, Visual Basic o Visual Basic .NET. Una stored procedure può essere creata una volta e chiamata da vari contesti, ad esempio da altre stored procedure, da misure calcolate o da applicazioni client. Consentendo di sviluppare il codice comune una sola volta e di archiviarlo in una singola posizione, le stored procedure semplificano le operazioni di sviluppo e di implementazione del database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Possono essere utilizzate per aggiungere alle applicazioni funzionalità business non presenti in quelle native di MDX.  
  
 In questa sezione vengono fornite le informazioni necessarie per comprendere, progettare e implementare stored procedure.  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Progettazione di Stored procedure](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/designing-stored-procedures.md)|Descrive la procedura per progettare assembly da utilizzare con [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|[Creazione di Stored procedure](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/creating-stored-procedures.md)|Descrive la procedura per creare assembly per [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|[Chiamata di Stored procedure](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/calling-stored-procedures.md)|Offre informazioni sull'utilizzo degli assembly in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|[Accesso al contesto di Query nelle Stored procedure](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/accessing-query-context-in-stored-procedures.md)|Descrive la procedura per accedere alle informazioni sul contesto e l'ambito con gli assembly.|  
|[Impostazione della protezione per le Stored procedure](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/setting-security-for-stored-procedures.md)|Descrive la procedura per configurare la sicurezza degli assembly in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|[Debug di Stored procedure](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/debugging-stored-procedures.md)|Descrive la procedura per eseguire il debug degli assembly in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione di assembly di modelli multidimensionali](../../analysis-services/multidimensional-models/multidimensional-model-assemblies-management.md)  
  
  

