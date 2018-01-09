---
title: Blocco e sblocco di database (XMLA) | Documenti Microsoft
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
- locking [XML for Analysis]
- XML for Analysis, locking
- XMLA, locking
- unlocking objects
ms.assetid: 451afa58-ce03-4ecc-8dd3-9e7e8559b5f1
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 0d4a50d1e4732a0b93f0fd536aa0ddfb950ca695
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="locking-and-unlocking-databases-xmla"></a>Blocco e sblocco di database (XMLA)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]È possibile bloccare e sbloccare database utilizzando, rispettivamente, il [blocco](../../analysis-services/xmla/xml-elements-commands/lock-element-xmla.md) e [Unlock](../../analysis-services/xmla/xml-elements-commands/unlock-element-xmla.md) comandi XML for Analysis (XMLA). In genere, gli altri comandi XMLA bloccano e sbloccano automaticamente gli oggetti in base alle esigenze per completare il comando durante l'esecuzione. È possibile in modo esplicito bloccare o sbloccare un database per eseguire più comandi all'interno di una singola transazione, ad esempio un [Batch](../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md) comando, impedendo l'esecuzione del commit di una transazione di scrittura al database di altre applicazioni.  
  
## <a name="locking-databases"></a>Blocco di database  
 Il **blocco** comando Blocca un oggetto, per utilizzo condiviso o esclusivo, all'interno del contesto della transazione attualmente attiva. Un blocco su un oggetto impedisce alle transazioni di eseguire il commit finché non viene rimosso. [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] supporta due tipi di blocchi, blocchi condivisi e blocchi esclusivi. Per ulteriori informazioni sui tipi di blocco supportati da [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], vedere [elemento Mode &#40; XMLA &#41; ](../../analysis-services/xmla/xml-elements-properties/mode-element-xmla.md).  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] consente solo che i database vengano bloccati. Il [oggetto](../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md) elemento deve contenere un riferimento a un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database. Se il **oggetto** elemento non è specificato o se il **oggetto** elemento fa riferimento a un oggetto diverso da un database, si verifica un errore.  
  
> [!IMPORTANT]  
>  Solo gli amministratori di database o gli amministratori del server possono eseguire in modo esplicito un **blocco** comando.  
  
 Altri comandi eseguono implicitamente un **blocco** comando un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database. Qualsiasi operazione che legge dati o metadati da un database, ad esempio [Discover](../../analysis-services/xmla/xml-elements-methods-discover.md) metodo o un [Execute](../../analysis-services/xmla/xml-elements-methods-execute.md) metodo in esecuzione un [istruzione](../../analysis-services/xmla/xml-elements-commands/statement-element-xmla.md) comando, applica implicitamente un oggetto condiviso blocco del database. Qualsiasi transazione che esegue il commit delle modifiche nei dati o metadati per un oggetto su un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database, ad esempio un **Execute** metodo in esecuzione un [Alter](../../analysis-services/xmla/xml-elements-commands/alter-element-xmla.md) comando, applica implicitamente un blocco esclusivo sul database.  
  
## <a name="unlocking-objects"></a>Sblocco di oggetti  
 Il comando **Unlock** rimuove un blocco applicato all'interno del contesto della transazione attualmente attiva.  
  
> [!IMPORTANT]  
>  Solo gli amministratori del database o gli amministratori del server possono eseguire in modo esplicito un comando **Unlock** .  
  
 Tutti i blocchi sono contenuti nel contesto della transazione corrente. Quando viene eseguito il commit oppure il rollback della transazione corrente, tutti i blocchi definiti all'interno della transazione vengono rilasciati automaticamente.  
  
## <a name="see-also"></a>Vedere anche  
 [Blocca elemento &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/lock-element-xmla.md)   
 [Sblocca elemento &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/unlock-element-xmla.md)   
 [Sviluppo con XMLA in Analysis Services](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
