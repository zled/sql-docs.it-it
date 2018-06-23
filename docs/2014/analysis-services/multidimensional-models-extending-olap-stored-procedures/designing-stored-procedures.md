---
title: Progettazione di Stored procedure | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- stored procedures [Analysis Services], designing
- dependent assemblies [Analysis Services]
- assemblies [Analysis Services]
ms.assetid: af4e7bd5-041b-4a40-9942-0ef6a3af46c6
caps.latest.revision: 27
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 245d02d18fdaf9fdce5d1b63b965525642bebcc4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36064133"
---
# <a name="designing-stored-procedures"></a>Progettazione di stored procedure
  Sia il modello a oggetti amministrativo AMO (Analysis Management Objects) sia il modello a oggetti orientato al client [!INCLUDE[msCoName](../../includes/msconame-md.md)] ADO MD (ActiveX® Data Objects Multidimensional) sono disponibili nelle stored procedure.  
  
 Le stored procedure devono essere in un determinato ambito (il server o il database) per essere visibili nel livello MDX (Multidimensional Expressions) e quindi essere chiamate. Tuttavia, dopo che una stored procedure viene chiamata, il suo ambito non viene limitato alle azioni consentite dal relativo padre. Una stored procedure può infatti apportare cambiamenti o modifiche in qualsiasi punto del server ed è soggetta solo a limitazioni di sicurezza del processo utente che l'ha richiamata o a limitazioni alla transazione nella quale è in esecuzione.  
  
 Le procedure nell'ambito del server sono disponibili in tutti i contesti del server. Le stored procedure nell'ambito del database sono visibili solo nel contesto del database nel quale sono state definite.  
  
 Come qualsiasi altra funzione MDX, una stored procedure deve essere risolta prima che possa proseguire una sessione MDX. Le stored procedure bloccano le sessioni MDX durante l'esecuzione. A meno che non esista una ragione specifica per interrompere una sessione MDX con una interazione con l'utente in corso, è consigliabile evitare interazioni con l'utente, quali ad esempio le finestre di dialogo.  
  
## <a name="dependent-assemblies"></a>Assembly dipendenti  
 Affinché il CLR (Common Language Runtime) trovi tutti gli assembly dipendenti, questi devono essere caricati in un'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] archivia gli assembly dipendenti nella stessa cartella dell'assembly principale, pertanto CLR risolve automaticamente ogni riferimento alla funzione in tali assembly.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione di assembly di modello multidimensionale](../multidimensional-models/multidimensional-model-assemblies-management.md)   
 [Definizione delle stored procedure](../multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
  