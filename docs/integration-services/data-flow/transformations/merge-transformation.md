---
title: "Trasformazione Unione | Microsoft Docs"
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
  - "sql13.dts.designer.mergetrans.f1"
helpviewer_keywords: 
  - "unione di set di dati [Integration Services]"
  - "unione di dati [Integration Services]"
  - "Unione - trasformazione"
  - "combinazione di set di dati"
  - "set di dati [Integration Services], unione"
ms.assetid: cff8690c-07ac-46a0-aab5-20bd4848c677
caps.latest.revision: 43
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 43
---
# Trasformazione Unione
  La trasformazione Unione consente di combinare due set di dati ordinati in un singolo set di dati. Le righe di ogni set di dati vengono inserite nell'output in base ai valori delle relative colonne chiave.  
  
 Includendo la trasformazione Unione in un flusso di dati, è possibile eseguire le attività seguenti:  
  
-   Unire dati da due origini dei dati, ad esempio tabelle e file.  
  
-   Creare set di dati complessi, nidificando più trasformazioni Unione.  
  
-   Unire di nuovo le righe dopo aver corretto gli errori nei dati.  
  
 La trasformazione Unione è simile alle trasformazioni Unione input multipli. Utilizzare la trasformazione Unione input multipli anziché la trasformazione Unione nelle situazioni seguenti:  
  
-   Gli input della trasformazione non sono ordinati.  
  
-   Non è necessario che l'output combinato sia ordinato.  
  
-   La trasformazione include più di due input.  
  
## Requisiti relativi all'input  
 Per eseguire la trasformazione Unione, è necessario che i relativi dati di input siano ordinati. Per altre informazioni su questo requisito importante, vedere [Ordinamento dei dati per le trasformazioni Unione e Merge Join](../../../integration-services/data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md).  
  
 La trasformazione Unione richiede inoltre che le colonne da unire nei relativi input abbiano metadati corrispondenti. Non è ad esempio possibile unire una colonna con tipo di dati numeric a una colonna con tipo di dati character. Se i dati sono di tipo string, la lunghezza della colonna nel secondo input dovrà essere minore o uguale a quella della colonna nel primo input, alla quale verrà unita.  
  
 In Progettazione [!INCLUDE[ssIS](../../../includes/ssis-md.md)] l'interfaccia utente della trasformazione Unione mappa automaticamente le colonne con gli stessi metadati. È quindi possibile eseguire il mapping manualmente altre colonne con tipi di dati compatibili.  
  
 Questa trasformazione include due input e un output. Non supporta un output degli errori.  
  
## Configurazione della trasformazione Unione  
 È possibile impostare le proprietà tramite Progettazione [!INCLUDE[ssIS](../../../includes/ssis-md.md)] o a livello di codice.  
  
 Per altre informazioni sulle proprietà che è possibile impostare nella finestra di dialogo **Editor trasformazione Unione** , vedere [Editor trasformazione Unione](../../../integration-services/data-flow/transformations/merge-transformation-editor.md).  
  
 Per ulteriori informazioni sulle proprietà che è possibile impostare a livello di codice, fare clic su uno degli argomenti seguenti:  
  
-   [Proprietà comuni](../Topic/Common%20Properties.md)  
  
-   [Proprietà personalizzate delle trasformazioni](../../../integration-services/data-flow/transformations/transformation-custom-properties.md)  
  
## Attività correlate  
 Per informazioni dettagliate sull'impostazione delle proprietà, vedere i seguenti argomenti:  
  
-   [Impostazione delle proprietà di un componente del flusso di dati](../../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md)  
  
-   [Ordinamento dei dati per le trasformazioni Unione e Merge Join](../../../integration-services/data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md)  
  
## Vedere anche  
 [Trasformazione Merge join](../../../integration-services/data-flow/transformations/merge-join-transformation.md)   
 [Trasformazione Unione input multipli](../../../integration-services/data-flow/transformations/union-all-transformation.md)   
 [Flusso di dati](../../../integration-services/data-flow/data-flow.md)   
 [Trasformazioni di Integration Services](../../../integration-services/data-flow/transformations/integration-services-transformations.md)  
  
  