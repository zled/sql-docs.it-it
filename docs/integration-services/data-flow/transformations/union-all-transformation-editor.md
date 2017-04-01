---
title: "Editor trasformazione Unione input multipli | Microsoft Docs"
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
  - "sql13.dts.designer.unionalltransformation.f1"
helpviewer_keywords: 
  - "Editor trasformazione Unione input multipli"
ms.assetid: 32fbc1c1-da83-4684-9479-31fc3e2df98c
caps.latest.revision: 26
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 26
---
# Editor trasformazione Unione input multipli
  Utilizzare la finestra di dialogo **Editor trasformazione Unione input multipli** per unire diversi set di righe di input in un unico set di righe di output. Includendo la trasformazione Unione input multipli in un flusso di dati è possibile unire dati tratti da più flussi di dati, creare set di dati complessi nidificando più trasformazioni Unione input multipli e unire nuovamente le righe dopo la correzione degli errori nei dati.  
  
 Per ulteriori informazioni sulla trasformazione Unione input multipli, vedere [Union All Transformation](../../../integration-services/data-flow/transformations/union-all-transformation.md).  
  
## Opzioni  
 **Nome colonna di output**  
 Consente di digitare un alias per ogni colonna. Per impostazione predefinita, viene suggerito il nome della colonna del primo input, ovvero l'input di riferimento. È comunque possibile scegliere qualsiasi nome descrittivo univoco.  
  
 **Input unione input multipli 1**  
 Consente di selezionare nell'elenco di colonne di input disponibili nel primo input, ovvero l'input di riferimento. I metadati delle colonne mappate devono corrispondere.  
  
 **Input unione input multipli n**  
 Consente di selezionare nell'elenco di colonne di input disponibili nel secondo input e negli input aggiuntivi. I metadati delle colonne mappate devono corrispondere.  
  
## Vedere anche  
 [Guida di riferimento ai messaggi e agli errori di Integration Services](../../../integration-services/integration-services-error-and-message-reference.md)   
 [Unione di dati tramite la trasformazione Unione input multipli](../../../integration-services/data-flow/transformations/merge-data-by-using-the-union-all-transformation.md)   
 [Trasformazione Unione](../../../integration-services/data-flow/transformations/merge-transformation.md)   
 [Trasformazione Merge join](../../../integration-services/data-flow/transformations/merge-join-transformation.md)  
  
  