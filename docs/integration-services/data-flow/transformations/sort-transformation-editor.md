---
title: "Editor trasformazione Ordinamento | Microsoft Docs"
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
  - "sql13.dts.designer.sorttransformation.f1"
helpviewer_keywords: 
  - "Editor trasformazione Ordinamento"
ms.assetid: 8ae23970-49a9-4d6d-9f15-c7074783347c
caps.latest.revision: 25
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 25
---
# Editor trasformazione Ordinamento
  Utilizzare la finestra di dialogo **Editor trasformazione Ordinamento** per selezionare le colonne da ordinare, impostare il tipo di ordinamento e specificare se rimuovere i duplicati.  
  
 Per ulteriori informazioni sulla trasformazione Ordinamento, vedere [Sort Transformation](../../../integration-services/data-flow/transformations/sort-transformation.md).  
  
## Opzioni  
 **Colonne di input disponibili**  
 Consente di specificare le colonne da ordinare utilizzando le caselle di controllo.  
  
 **Nome**  
 Consente di visualizzare il nome di ogni colonna di input disponibile.  
  
 **Pass-through**  
 Indica se includere la colonna nell'output ordinato.  
  
 **Colonna di input**  
 Consente di selezionare una colonna di input nell'elenco delle colonne di input disponibili per ogni riga. Le selezioni effettuate vengono riflesse nelle selezioni delle caselle di controllo nella tabella **Colonne di input disponibili** .  
  
 **Alias di output**  
 Consente di digitare un alias per ogni colonna di output. Per impostazione predefinita viene suggerito il nome della colonna di input. È comunque possibile scegliere qualsiasi nome descrittivo univoco.  
  
 **Tipo di ordinamento**  
 Indica se eseguire l'ordinamento in ordine crescente o decrescente.  
  
 **Ordinamento**  
 Indica l'ordine da utilizzare per l'ordinamento delle colonne. È possibile impostare questa opzione in modo manuale per ogni colonna.  
  
 **Flag di confronto**  
 Per altre informazioni sulle opzioni per il confronto di stringhe, vedere [Confronto di dati stringa](../../../integration-services/data-flow/comparing-string-data.md).  
  
 **Rimuovi righe con valori di ordinamento duplicati**  
 Indica se la trasformazione copia le righe duplicate nell'output della trasformazione o se invece crea un'unica voce per tutti i duplicati in base alla stringa specificata nelle opzioni di confronto.  
  
## Vedere anche  
 [Guida di riferimento ai messaggi e agli errori di Integration Services](../../../integration-services/integration-services-error-and-message-reference.md)  
  
  