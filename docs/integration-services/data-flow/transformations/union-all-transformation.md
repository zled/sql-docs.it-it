---
title: "Trasformazione Unione input multipli | Microsoft Docs"
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
  - "sql13.dts.designer.unionalltrans.f1"
helpviewer_keywords: 
  - "unione di set di dati [Integration Services]"
  - "combinazione di set di dati"
  - "Unione input multipli - trasformazione"
  - "set di dati [Integration Services], unione"
ms.assetid: 942e4b90-9c41-4e9c-a6f3-80b3afe57f2f
caps.latest.revision: 39
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 39
---
# Trasformazione Unione input multipli
  La trasformazione Unione input multipli consente di combinare più input in un unico output. È ad esempio possibile utilizzare gli output di cinque diverse origini file flat come input per la trasformazione Unione input multipli e combinarli in un singolo output.  
  
## Input e output  
 Gli input della trasformazione vengono aggiunti all'output della trasformazione uno dopo l'altro, senza riordinare le righe. Se il pacchetto richiede un output ordinato, sarà necessario utilizzare la trasformazione Unione anziché la trasformazione Unione input multipli.  
  
 L'output della trasformazione Unione input multipli viene creato a partire dal primo input connesso alla trasformazione. Sulle colonne negli input connessi successivamente alla trasformazione viene eseguito il mapping a quelle dell'output della trasformazione.  
  
 Per unire gli input è necessario eseguire il mapping delle relative colonne alle colonne nell'output. È necessario eseguire il mapping di almeno una colonna di input a ogni colonna di output. Il mapping tra due colonne può essere eseguito solo se i relativi metadati corrispondono. Le colonne sulle quali viene eseguito il mapping devono ad esempio avere lo stesso tipo di dati.  
  
 Se le colonne sulle quali viene eseguito il mapping contengono dati stringa e la lunghezza della colonna di output è inferiore a quella della colonna di input, la lunghezza della colonna di output verrà aumentata automaticamente in modo che possa contenere la colonna di input. Le colonne di input sulle quali non viene eseguito il mapping a colonne di output vengono impostate su valori Null nelle colonne di output.  
  
 Questa trasformazione include più input e un output. Non supporta un output degli errori.  
  
## Configurazione della trasformazione Unione input multipli  
 È possibile impostare le proprietà tramite Progettazione [!INCLUDE[ssIS](../../../includes/ssis-md.md)] o a livello di codice.  
  
 Per altre informazioni sulle proprietà che è possibile impostare nella finestra di dialogo **Editor trasformazione Unione**, vedere [Editor trasformazione Unione input multipli](../../../integration-services/data-flow/transformations/union-all-transformation-editor.md).  
  
 Per altre informazioni sulle proprietà che è possibile impostare a livello di codice, vedere [Proprietà comuni](../Topic/Common%20Properties.md).  
  
 Per ulteriori informazioni sulle procedure per l'impostazione delle proprietà, fare clic su uno degli argomenti seguenti:  
  
-   [Impostazione delle proprietà di un componente del flusso di dati](../../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md)  
  
## Attività correlate  
 [Unione di dati tramite la trasformazione Unione input multipli](../../../integration-services/data-flow/transformations/merge-data-by-using-the-union-all-transformation.md)  
  
  