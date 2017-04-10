---
title: "Editor trasformazione Merge join | Microsoft Docs"
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
  - "sql13.dts.designer.mergejointransformation.f1"
helpviewer_keywords: 
  - "Editor trasformazione Merge join"
ms.assetid: ac06f419-30b3-42aa-8b34-42000bec4285
caps.latest.revision: 31
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 31
---
# Editor trasformazione Merge join
  Utilizzare la finestra di dialogo **Editor trasformazione Merge join** per specificare il tipo di join, le colonne di join e le colonne di output per l'unione di due input combinati tramite un join.  
  
> [!IMPORTANT]  
>  Per eseguire la trasformazione Merge join, è necessario che i relativi dati di input siano ordinati. Per altre informazioni su questo requisito importante, vedere [Ordinamento dei dati per le trasformazioni Unione e Merge Join](../../../integration-services/data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md).  
  
 Per ulteriori informazioni sulla trasformazione Merge Join, vedere [Merge Join Transformation](../../../integration-services/data-flow/transformations/merge-join-transformation.md).  
  
## Opzioni  
 **Tipo di join**  
 Consente di specificare se utilizzare un inner join, un outer join sinistro o un full join.  
  
 **Inverti ordine input**  
 Il pulsante **Inverti ordine input** consente di invertire l'ordine degli input. Questa selezione può risultare utile in caso si scelga di utilizzare un outer join sinistro.  
  
 **Input**  
 Per ogni colonna che si desidera includere nell'output unito, è innanzitutto necessario procedere a una selezione nell'elenco degli input disponibili.  
  
 Gli input vengono visualizzati in due tabelle separate. Selezionare le colonne da includere nell'output. Trascinare le colonne per creare un join tra le tabelle. Per eliminare un join, selezionarlo e quindi premere CANC.  
  
 **Colonna di input**  
 Selezionare una colonna da includere nell'output unito dall'elenco delle colonne disponibili nell'input selezionato.  
  
 **Alias di output**  
 Consente di digitare un alias per ogni colonna di output. Per impostazione predefinita viene suggerito il nome della colonna di input. È comunque possibile scegliere qualsiasi nome descrittivo univoco.  
  
## Vedere anche  
 [Guida di riferimento ai messaggi e agli errori di Integration Services](../../../integration-services/integration-services-error-and-message-reference.md)   
 [Ordinamento dei dati per le trasformazioni Unione e Merge Join](../../../integration-services/data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md)   
 [Estensione di un set di dati tramite la trasformazione Merge join](../../../integration-services/data-flow/transformations/extend-a-dataset-by-using-the-merge-join-transformation.md)   
 [Trasformazione Unione](../../../integration-services/data-flow/transformations/merge-transformation.md)   
 [Trasformazione Unione input multipli](../../../integration-services/data-flow/transformations/union-all-transformation.md)  
  
  