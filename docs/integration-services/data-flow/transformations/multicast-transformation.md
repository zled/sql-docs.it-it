---
title: "Trasformazione Multicast | Microsoft Docs"
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
  - "sql13.dts.designer.multicasttrans.f1"
helpviewer_keywords: 
  - "più output"
  - "Multicast - trasformazione"
  - "set di dati [Integration Services], più output"
  - "più trasformazioni"
ms.assetid: 32194784-1684-40cd-9f91-1aba4d8360d3
caps.latest.revision: 45
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 45
---
# Trasformazione Multicast
  La trasformazione Multicast distribuisce il proprio input a uno o più output. Questa trasformazione è simile alla trasformazione Suddivisione condizionale. Entrambe le trasformazioni dirigono uno stesso input verso più output, ma la trasformazione Multicast dirige tutte le righe verso tutti gli output, mentre la trasformazione Suddivisione condizionale dirige una riga a un singolo output. Per altre informazioni, vedere [Trasformazione Suddivisione condizionale](../../../integration-services/data-flow/transformations/conditional-split-transformation.md).  
  
 Per configurare la trasformazione Multicast, è necessario aggiungere gli output.  
  
 Tramite la trasformazione Multicast un pacchetto può creare copie logiche dei dati. Questa funzionalità è utile quando il pacchetto deve applicare più set di trasformazioni agli stessi dati. È ad esempio possibile aggregare una copia dei dati e caricare nella relativa destinazione solo le informazioni di riepilogo, mentre un'altra copia dei dati viene estesa con valori di ricerca e colonne derivate prima di caricarla nella relativa destinazione.  
  
 Questa trasformazione include un input e più output. Non supporta un output degli errori.  
  
## Configurazione della trasformazione Multicast  
 È possibile impostare le proprietà tramite Progettazione [!INCLUDE[ssIS](../../../includes/ssis-md.md)] o a livello di codice.  
  
 Per altre informazioni sulle proprietà che è possibile impostare nella finestra di dialogo **Editor trasformazione Multicast**, vedere [Editor trasformazione Multicast](../../../integration-services/data-flow/transformations/multicast-transformation-editor.md).  
  
 Per informazioni sulle proprietà che è possibile impostare a livello di codice, vedere [Proprietà comuni](../Topic/Common%20Properties.md).  
  
## Attività correlate  
 Per informazioni su come impostare le proprietà del componente, vedere [Impostazione delle proprietà di un componente del flusso di dati](../../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md).  
  
## Vedere anche  
 [Flusso di dati](../../../integration-services/data-flow/data-flow.md)   
 [Trasformazioni di Integration Services](../../../integration-services/data-flow/transformations/integration-services-transformations.md)  
  
  