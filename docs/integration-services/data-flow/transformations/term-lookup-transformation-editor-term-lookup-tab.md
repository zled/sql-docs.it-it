---
title: "Editor trasformazione Ricerca termini (scheda Ricerca termini) | Microsoft Docs"
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
  - "sql13.dts.designer.termlookup.termlookup.f1"
helpviewer_keywords: 
  - "Editor trasformazione Ricerca termini"
ms.assetid: 245d3466-d51f-4073-978a-694a8d9dfaec
caps.latest.revision: 26
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 26
---
# Editor trasformazione Ricerca termini (scheda Ricerca termini)
  Utilizzare la scheda **Ricerca termini** della finestra di dialogo **Editor trasformazione Ricerca termini** per eseguire il mapping tra una colonna di input e una colonna di ricerca in una tabella di riferimento e per specificare un alias per ogni colonna di output.  
  
 Per ulteriori informazioni sulla trasformazione Ricerca termini, vedere [Term Lookup Transformation](../../../integration-services/data-flow/transformations/term-lookup-transformation.md).  
  
## Opzioni  
 **Colonne di input disponibili**  
 Utilizzare le caselle di controllo per selezionare le colonne di input da passare all'output senza modifiche. Trascinare una colonna di input nell'elenco **Colonne di riferimento disponibili** per eseguirne il mapping a una colonna di ricerca nella tabella di riferimento. Le colonne di input e di output devono avere tipi di dati corrispondenti e supportati, ovvero DT_NTEXT o DT_WSTR. Selezionare una riga di mapping e fare clic con il pulsante destro del mouse per modificare i mapping nella finestra di dialogo [Crea relazioni](../../../integration-services/data-flow/transformations/create-relationships.md).  
  
 **Colonne di riferimento disponibili**  
 Consente di visualizzare le colonne disponibili nella tabella di riferimento. Selezionare la colonna contenente l'elenco dei termini per i quali si desidera trovare una corrispondenza.  
  
 **Colonna pass-through**  
 Consente di selezionare una colonna di input nell'elenco delle colonne di input disponibili. Le selezioni effettuate vengono riflesse nelle selezioni delle caselle di controllo nella tabella **Colonne di input disponibili** .  
  
 **Alias colonna di output**  
 Consente di digitare un alias per ogni colonna di output. Per impostazione predefinita, viene suggerito il nome della colonna. È comunque possibile scegliere qualsiasi nome descrittivo univoco.  
  
 **Configura output errori**  
 Usare la finestra di dialogo [Configura output errori](../Topic/Configure%20Error%20Output.md) per specificare le opzioni di gestione degli errori per le righe che causano errori.  
  
## Vedere anche  
 [Guida di riferimento ai messaggi e agli errori di Integration Services](../../../integration-services/integration-services-error-and-message-reference.md)   
 [Editor trasformazione Ricerca fuzzy &#40;scheda Tabella di riferimento&#41;](../../../integration-services/data-flow/transformations/term-lookup-transformation-editor-reference-table-tab.md)   
 [Editor trasformazione Ricerca termini &#40;scheda Avanzate&#41;](../../../integration-services/data-flow/transformations/term-lookup-transformation-editor-advanced-tab.md)   
 [Trasformazione Estrazione termini](../../../integration-services/data-flow/transformations/term-extraction-transformation.md)  
  
  