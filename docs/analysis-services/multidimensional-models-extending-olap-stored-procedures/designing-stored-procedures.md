---
title: Progettazione di Stored procedure | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- stored procedures [Analysis Services], designing
- dependent assemblies [Analysis Services]
- assemblies [Analysis Services]
ms.assetid: af4e7bd5-041b-4a40-9942-0ef6a3af46c6
caps.latest.revision: "28"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 4b8b145a22f7d309fbaf69c1da3f6f4bb068fad5
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="designing-stored-procedures"></a>Progettazione di stored procedure
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Sia l'oggetto di amministrazione del modello a oggetti AMO (Analysis Management) e il modello a oggetti orientato client [!INCLUDE[msCoName](../../includes/msconame-md.md)] ActiveX® Data Objects (ADO MD) (multidimensionale) sono disponibili nelle stored procedure.  
  
 Le stored procedure devono essere in un determinato ambito (il server o il database) per essere visibili nel livello MDX (Multidimensional Expressions) e quindi essere chiamate. Tuttavia, dopo che una stored procedure viene chiamata, il suo ambito non viene limitato alle azioni consentite dal relativo padre. Una stored procedure può infatti apportare cambiamenti o modifiche in qualsiasi punto del server ed è soggetta solo a limitazioni di sicurezza del processo utente che l'ha richiamata o a limitazioni alla transazione nella quale è in esecuzione.  
  
 Le procedure nell'ambito del server sono disponibili in tutti i contesti del server. Le stored procedure nell'ambito del database sono visibili solo nel contesto del database nel quale sono state definite.  
  
 Come qualsiasi altra funzione MDX, una stored procedure deve essere risolta prima che possa proseguire una sessione MDX. Le stored procedure bloccano le sessioni MDX durante l'esecuzione. A meno che non esista una ragione specifica per interrompere una sessione MDX con una interazione con l'utente in corso, è consigliabile evitare interazioni con l'utente, quali ad esempio le finestre di dialogo.  
  
## <a name="dependent-assemblies"></a>Assembly dipendenti  
 Affinché il CLR (Common Language Runtime) trovi tutti gli assembly dipendenti, questi devono essere caricati in un'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] archivia gli assembly dipendenti nella stessa cartella dell'assembly principale, pertanto CLR risolve automaticamente ogni riferimento alla funzione in tali assembly.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione di assembly di modelli multidimensionali](../../analysis-services/multidimensional-models/multidimensional-model-assemblies-management.md)   
 [Definizione delle stored procedure](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
  
