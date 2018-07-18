---
title: Blocco e sblocco di database (XMLA) | Microsoft Docs
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
- locking [XML for Analysis]
- XML for Analysis, locking
- XMLA, locking
- unlocking objects
ms.assetid: 451afa58-ce03-4ecc-8dd3-9e7e8559b5f1
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fa6eab7a4d0ebe15e87ee83b60020b7a1f809ae8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37278358"
---
# <a name="locking-and-unlocking-databases-xmla"></a>Blocco e sblocco di database (XMLA)
  È possibile bloccare e sbloccare database utilizzando, rispettivamente, il [Lock](../xmla/xml-elements-commands/lock-element-xmla.md) e [Unlock](../xmla/xml-elements-commands/unlock-element-xmla.md) comandi XML for Analysis (XMLA). In genere, gli altri comandi XMLA bloccano e sbloccano automaticamente gli oggetti in base alle esigenze per completare il comando durante l'esecuzione. In modo esplicito è possibile bloccare o sbloccare un database per eseguire più comandi all'interno di una singola transazione, ad esempio un [Batch](../xmla/xml-elements-commands/batch-element-xmla.md) comando, impedendo ad altre applicazioni dal commit di una transazione di scrittura al database.  
  
## <a name="locking-databases"></a>Blocco di database  
 Il comando `Lock` blocca un oggetto, per utilizzo condiviso o esclusivo, all'interno del contesto della transazione attualmente attiva. Un blocco su un oggetto impedisce alle transazioni di eseguire il commit finché non viene rimosso. [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] supporta due tipi di blocchi, blocchi condivisi e blocchi esclusivi. Per altre informazioni sui tipi di blocco supportati da [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], vedere [modalità elemento &#40;XMLA&#41;](../xmla/xml-elements-properties/mode-element-xmla.md).  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] consente solo che i database vengano bloccati. Il [oggetti](../xmla/xml-elements-properties/object-element-xmla.md) elemento deve contenere un riferimento a un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database. Se l'elemento `Object` non viene specificato oppure fa riferimento a un oggetto diverso da un database `Object`, si verifica un errore.  
  
> [!IMPORTANT]  
>  Solo amministratori del database o amministratori del server possono eseguire in modo esplicito un comando `Lock`.  
  
 Gli altri comandi eseguono implicitamente un comando `Lock` su un database [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Qualsiasi operazione che legge dati o metadati da un database, ad esempio qualsiasi [Discover](../xmla/xml-elements-methods-discover.md) metodo o un' [Execute](../xmla/xml-elements-methods-execute.md) metodo in esecuzione un [istruzione](../xmla/xml-elements-commands/statement-element-xmla.md) comando, applica implicitamente un condiviso bloccare il database. Qualsiasi transazione che esegue il commit delle modifiche nei dati o metadati per un oggetto in un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database, ad esempio un `Execute` metodo in esecuzione un' [Alter](../xmla/xml-elements-commands/alter-element-xmla.md) comando, applica implicitamente un blocco esclusivo sul database.  
  
## <a name="unlocking-objects"></a>Sblocco di oggetti  
 Il comando `Unlock` rimuove un blocco applicato all'interno del contesto della transazione attualmente attiva.  
  
> [!IMPORTANT]  
>  Solo gli amministratori del database o gli amministratori del server possono eseguire in modo esplicito un comando `Unlock`.  
  
 Tutti i blocchi sono contenuti nel contesto della transazione corrente. Quando viene eseguito il commit oppure il rollback della transazione corrente, tutti i blocchi definiti all'interno della transazione vengono rilasciati automaticamente.  
  
## <a name="see-also"></a>Vedere anche  
 [Bloccare l'elemento &#40;XMLA&#41;](../xmla/xml-elements-commands/lock-element-xmla.md)   
 [Elemento Unlock &#40;XMLA&#41;](../xmla/xml-elements-commands/unlock-element-xmla.md)   
 [Sviluppo con XMLA in Analysis Services](developing-with-xmla-in-analysis-services.md)  
  
  
