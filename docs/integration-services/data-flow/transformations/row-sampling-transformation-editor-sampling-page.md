---
title: "Editor trasformazione Campionamento righe (pagina Campionamento) | Microsoft Docs"
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
  - "sql13.DTS.DESIGNER.ROWSAMPLINGTRANSFORMATION.COLUMNS.F1"
  - "sql13.dts.designer.rowsamplingtransformation.f1"
helpviewer_keywords: 
  - "Editor trasformazione Campionamento righe"
ms.assetid: 544c7709-6de0-4c08-bda3-759985be9a05
caps.latest.revision: 23
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 23
---
# Editor trasformazione Campionamento righe (pagina Campionamento)
  Utilizzare la finestra di dialogo **Editor trasformazione Campionamento righe** per dividere parte di un input in un campione utilizzando il numero di righe specificato. La trasformazione divide l'input in due output separati.  
  
 Per ulteriori informazioni sulla trasformazione Campionamento righe, vedere [Row Sampling Transformation](../../../integration-services/data-flow/transformations/row-sampling-transformation.md).  
  
## Opzioni  
 **Numero di righe**  
 Consente di specificare il numero di righe dell'input da utilizzare come campione.  
  
 È possibile specificare il valore di questa proprietà tramite un'espressione di proprietà.  
  
 **Nome output campione**  
 Consente di specificare un nome univoco per l'output che includerà le righe campionate. Il nome specificato verrà visualizzato in Progettazione SSIS.  
  
 **Nome output non selezionato**  
 Consente di specificare un nome univoco per l'output che conterrà le righe escluse dal campionamento. Il nome specificato verrà visualizzato in Progettazione SSIS.  
  
 **Usa il valore di inizializzazione casuale seguente**  
 Consente di specificare il valore di inizializzazione del campionamento per il generatore di numeri casuali utilizzato dalla trasformazione per creare un campione. È consigliato solo a scopo di sviluppo e test. Se non viene specificato alcun valore di inizializzazione casuale, la trasformazione utilizza il conteggio tick di Microsoft Windows come valore di inizializzazione.  
  
## Vedere anche  
 [Guida di riferimento ai messaggi e agli errori di Integration Services](../../../integration-services/integration-services-error-and-message-reference.md)   
 [Trasformazione Campionamento percentuale](../../../integration-services/data-flow/transformations/percentage-sampling-transformation.md)  
  
  