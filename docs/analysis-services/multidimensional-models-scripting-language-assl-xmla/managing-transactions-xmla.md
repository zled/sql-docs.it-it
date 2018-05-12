---
title: La gestione delle transazioni (XMLA) | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1f2884d49f03d8557d72d8d6d48cdba432a8c37f
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="managing-transactions-xmla"></a>Gestione di transazioni (XMLA)
  Ogni comando XML for Analysis (XMLA) inviato a un'istanza di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] viene eseguito all'interno del contesto di una transazione nella sessione implicita o esplicita corrente. Per gestire ognuna di queste transazioni, si utilizza il [BeginTransaction](../../analysis-services/xmla/xml-elements-commands/begintransaction-element-xmla.md), [CommitTransaction](../../analysis-services/xmla/xml-elements-commands/committransaction-element-xmla.md), e [RollbackTransaction](../../analysis-services/xmla/xml-elements-commands/rollbacktransaction-element-xmla.md) comandi. che consentono di creare transazioni implicite o esplicite, modificare il conteggio dei riferimenti alla transazione nonché di avviare le transazioni ed eseguirne il commit e il rollback.  
  
## <a name="implicit-and-explicit-transactions"></a>Transazioni implicite ed esplicite  
 Una transazione può essere implicita o esplicita, come descritto di seguito.  
  
 **Transazione implicita**  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Crea un' *implicita* transazione per un XMLA comando se il **BeginTransaction** comando non specifica l'inizio di una transazione. [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] esegue sempre il commit di una transazione implicita se il comando riesce e ne esegue il rollback se il comando non riesce.  
  
 **Transazione esplicita**  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Crea un' *esplicita* transazione se il **BeginTransaction** comando avvia una transazione. Tuttavia, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] esegue solo il commit di una transazione esplicita se un **CommitTransaction** comando viene inviato e rollback di una transazione esplicita se un **RollbackTransaction** comando viene inviato.  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] inoltre esegue il rollback sia di transazioni implicite che di transazioni esplicite se la sessione corrente termina prima del completamento della transazione attiva.  
  
## <a name="transactions-and-reference-counts"></a>Transazioni e conteggi dei riferimenti  
 In [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] viene gestito un conteggio dei riferimenti alla transazione per ogni sessione. [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] non supporta tuttavia transazioni nidificate poiché per ogni sessione viene gestita una sola transazione attiva. Se nella sessione corrente non è presente una transazione attiva, il conteggio dei riferimenti alla transazione è impostato su zero.  
  
 In altre parole, ogni **BeginTransaction** comando incrementa il conteggio dei riferimenti di uno, mentre ogni **CommitTransaction** comando decrementa il conteggio riferimenti di uno. Se un **CommitTransaction** comando imposta il numero di transazioni a zero, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] il commit della transazione.  
  
 Tuttavia, il **RollbackTransaction** comando esegue il rollback della transazione attiva indipendentemente dal valore corrente del conteggio dei riferimenti delle transazioni. In altre parole, un singolo **RollbackTransaction** comando esegue il rollback della transazione attiva, indipendentemente dal numero **BeginTransaction** comandi o **CommitTransaction** i comandi inviati e imposta il conteggio dei riferimenti delle transazioni su zero.  
  
## <a name="beginning-a-transaction"></a>Avvio di una transazione.  
 Il **BeginTransaction** comando avvia una transazione esplicita nella sessione corrente e incrementa il conteggio dei riferimenti delle transazioni per la sessione corrente di uno. Tutti i comandi successivi vengono considerati all'interno della transazione attiva, fino a quando non è sufficiente **CommitTransaction** vengono inviati i comandi per eseguire il commit della transazione attiva o un singolo **RollbackTransaction**comando viene inviato per eseguire il rollback della transazione attiva.  
  
## <a name="committing-a-transaction"></a>Esecuzione del commit di una transazione  
 Il **CommitTransaction** comando esegue il commit dei risultati di comandi che vengono eseguiti dopo il **BeginTransaction** comando è stato eseguito nella sessione corrente. Ogni **CommitTransaction** comando decrementa il conteggio dei riferimenti per le transazioni attive in una sessione. Se un **CommitTransaction** comando imposta il conteggio dei riferimenti su zero, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] esegue il commit della transazione attiva. Se non è presente alcuna transazione attiva (in altre parole, il conteggio dei riferimenti delle transazioni per la sessione corrente è già impostato su zero), un **CommitTransaction** comando genera un errore.  
  
## <a name="rolling-back-a-transaction"></a>Esecuzione del rollback di una transazione  
 Il **RollbackTransaction** comando consente di ripristinare i risultati dei comandi che vengono eseguiti dopo il **BeginTransaction** comando è stato eseguito nella sessione corrente. Il **RollbackTransaction** comando esegue il rollback della transazione attiva, indipendentemente dal conteggio dei riferimenti delle transazioni corrente e imposta il conteggio dei riferimenti delle transazioni su zero. Se non è presente alcuna transazione attiva (in altre parole, il conteggio dei riferimenti delle transazioni per la sessione corrente è già impostato su zero), un **RollbackTransaction** comando genera un errore.  
  
## <a name="see-also"></a>Vedere anche  
 [Sviluppo con XMLA in Analysis Services](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
