---
title: Editor trasformazione Ricerca termini (scheda Ricerca termini) | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.termlookup.termlookup.f1
helpviewer_keywords:
- Term Lookup Transformation Editor
ms.assetid: 245d3466-d51f-4073-978a-694a8d9dfaec
caps.latest.revision: 25
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 0f00dba7a6b5c634c284161cd8c0af3e0e471375
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36066472"
---
# <a name="term-lookup-transformation-editor-term-lookup-tab"></a>Editor trasformazione Ricerca termini (scheda Ricerca termini)
  Utilizzare la scheda **Ricerca termini** della finestra di dialogo **Editor trasformazione Ricerca termini** per eseguire il mapping tra una colonna di input e una colonna di ricerca in una tabella di riferimento e per specificare un alias per ogni colonna di output.  
  
 Per ulteriori informazioni sulla trasformazione Ricerca termini, vedere [Term Lookup Transformation](data-flow/transformations/lookup-transformation.md).  
  
## <a name="options"></a>Opzioni  
 **Colonne di input disponibili**  
 Utilizzare le caselle di controllo per selezionare le colonne di input da passare all'output senza modifiche. Trascinare una colonna di input nell'elenco **Colonne di riferimento disponibili** per eseguirne il mapping a una colonna di ricerca nella tabella di riferimento. Le colonne di input e di output devono avere tipi di dati corrispondenti e supportati, ovvero DT_NTEXT o DT_WSTR. Selezionare una riga di mapping e fare clic con il pulsante destro del mouse per modificare i mapping nella finestra di dialogo [Crea relazioni](data-flow/transformations/create-relationships.md) .  
  
 **Colonne di riferimento disponibili**  
 Consente di visualizzare le colonne disponibili nella tabella di riferimento. Selezionare la colonna contenente l'elenco dei termini per i quali si desidera trovare una corrispondenza.  
  
 **Colonna pass-through**  
 Consente di selezionare una colonna di input nell'elenco delle colonne di input disponibili. Le selezioni effettuate vengono riflesse nelle selezioni delle caselle di controllo nella tabella **Colonne di input disponibili** .  
  
 **Alias colonna di output**  
 Consente di digitare un alias per ogni colonna di output. Per impostazione predefinita, viene suggerito il nome della colonna. È comunque possibile scegliere qualsiasi nome descrittivo univoco.  
  
 **Configura output errori**  
 Usare la finestra di dialogo [Configura output errori](../../2014/integration-services/configure-error-output.md) per specificare le opzioni di gestione degli errori per le righe che causano errori.  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti per i messaggi e agli errori di Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Editor trasformazione Ricerca termini &#40;scheda tabella di riferimento&#41;](../../2014/integration-services/term-lookup-transformation-editor-reference-table-tab.md)   
 [Editor trasformazione Ricerca termini &#40;scheda Avanzate&#41;](../../2014/integration-services/term-lookup-transformation-editor-advanced-tab.md)   
 [Trasformazione Estrazione termini](data-flow/transformations/term-extraction-transformation.md)  
  
  