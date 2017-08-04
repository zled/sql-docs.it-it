---
title: Editor trasformazione Ricerca termini (scheda Ricerca termini) | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.termlookup.termlookup.f1
helpviewer_keywords:
- Term Lookup Transformation Editor
ms.assetid: 245d3466-d51f-4073-978a-694a8d9dfaec
caps.latest.revision: 26
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 79e7f405e9418b47985efd7bcc8bb13b14f20ec6
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="term-lookup-transformation-editor-term-lookup-tab"></a>Editor trasformazione Ricerca termini (scheda Ricerca termini)
  Utilizzare la scheda **Ricerca termini** della finestra di dialogo **Editor trasformazione Ricerca termini** per eseguire il mapping tra una colonna di input e una colonna di ricerca in una tabella di riferimento e per specificare un alias per ogni colonna di output.  
  
 Per ulteriori informazioni sulla trasformazione Ricerca termini, vedere [Term Lookup Transformation](../../../integration-services/data-flow/transformations/term-lookup-transformation.md).  
  
## <a name="options"></a>Opzioni  
 **Colonne di input disponibili**  
 Utilizzare le caselle di controllo per selezionare le colonne di input da passare all'output senza modifiche. Trascinare una colonna di input nell'elenco **Colonne di riferimento disponibili** per eseguirne il mapping a una colonna di ricerca nella tabella di riferimento. Le colonne di input e di output devono avere tipi di dati corrispondenti e supportati, ovvero DT_NTEXT o DT_WSTR. Selezionare una riga di mapping e fare clic con il pulsante destro del mouse per modificare i mapping nella finestra di dialogo [Crea relazioni](../../../integration-services/data-flow/transformations/create-relationships.md) .  
  
 **Colonne di riferimento disponibili**  
 Consente di visualizzare le colonne disponibili nella tabella di riferimento. Selezionare la colonna contenente l'elenco dei termini per i quali si desidera trovare una corrispondenza.  
  
 **Colonna pass-through**  
 Consente di selezionare una colonna di input nell'elenco delle colonne di input disponibili. Le selezioni effettuate vengono riflesse nelle selezioni delle caselle di controllo nella tabella **Colonne di input disponibili** .  
  
 **Alias colonna di output**  
 Consente di digitare un alias per ogni colonna di output. Per impostazione predefinita, viene suggerito il nome della colonna. È comunque possibile scegliere qualsiasi nome descrittivo univoco.  
  
 **Configura output errori**  
 Usare la finestra di dialogo [Configura output errori](http://msdn.microsoft.com/library/5f8da390-fab5-44f8-b268-d8fa313ce4b9) per specificare le opzioni di gestione degli errori per le righe che causano errori.  
  
## <a name="see-also"></a>Vedere anche  
 [Errori di Integration Services e riferimento ai messaggi](../../../integration-services/integration-services-error-and-message-reference.md)   
 [Editor trasformazione Ricerca termini &#40; Scheda tabella di riferimento &#41;](../../../integration-services/data-flow/transformations/term-lookup-transformation-editor-reference-table-tab.md)   
 [Editor trasformazione Ricerca termini &#40; Scheda Avanzate &#41;](../../../integration-services/data-flow/transformations/term-lookup-transformation-editor-advanced-tab.md)   
 [Trasformazione estrazione termini](../../../integration-services/data-flow/transformations/term-extraction-transformation.md)  
  
  
