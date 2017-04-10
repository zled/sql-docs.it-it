---
title: "Editor trasformazione Raggruppamento fuzzy (scheda Avanzate) | Microsoft Docs"
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
  - "sql13.dts.designer.fuzzygroupingtransformation.advanced.f1"
helpviewer_keywords: 
  - "Editor trasformazione Raggruppamento fuzzy"
ms.assetid: dd820d75-b8a7-4515-aea4-3553ba5b442e
caps.latest.revision: 28
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 28
---
# Editor trasformazione Raggruppamento fuzzy (scheda Avanzate)
  La scheda **Avanzate** della finestra di dialogo **Editor trasformazione Raggruppamento fuzzy** consente di specificare le colonne di input e output, impostare le soglie di somiglianza e definire i delimitatori.  
  
> [!NOTE]  
>  Le proprietà **Exhaustive** e **MaxMemoryUsage** della trasformazione Raggruppamento fuzzy non sono disponibili nell' **Editor trasformazione Raggruppamento fuzzy**, tuttavia possono essere impostate utilizzando l' **Editor avanzato**. Per ulteriori informazioni su queste proprietà, vedere la sezione relativa alla trasformazione Raggruppamento fuzzy in [Transformation Custom Properties](../../../integration-services/data-flow/transformations/transformation-custom-properties.md).  
  
 Per ulteriori informazioni sulla trasformazione Raggruppamento fuzzy, vedere [Fuzzy Grouping Transformation](../../../integration-services/data-flow/transformations/fuzzy-grouping-transformation.md).  
  
## Opzioni  
 **Nome colonna chiave di input**  
 Consente di specificare il nome di una colonna di output contenente l'identificatore univoco per ogni riga di input. La colonna **_key_in** contiene un valore che identifica in modo univoco ogni riga.  
  
 **Nome colonna chiave di output**  
 Consente di specificare il nome di una colonna di output contenente l'identificatore univoco per la riga canonica di un gruppo di righe duplicate. La colonna **_key_out** corrisponde al valore **_key_in** della riga di dati canonica.  
  
 **Nome colonna punteggio somiglianza**  
 Consente di specificare un nome per la colonna contenente il punteggio di somiglianza. Il punteggio di somiglianza è un valore compreso tra 0 e 1 che indica la somiglianza della riga di input alla riga canonica. I punteggi più prossimi a 1 indicano una corrispondenza maggiore.  
  
 **Soglia di somiglianza**  
 Consente di impostare la soglia di somiglianza mediante il dispositivo di scorrimento. Le soglie vicine a 1 indicano che le righe devono avere una somiglianza maggiore per poter essere considerate duplicati. L'aumento della soglia può incrementare la velocità di ricerca della corrispondenza in quanto viene considerato un minor numero di record candidati.  
  
 **Delimitatori token**  
 La trasformazione genera un set predefinito di delimitatori per la suddivisione in token dei dati. È tuttavia possibile aggiungere o rimuovere i delimitatori in base alle esigenze modificando l'elenco.  
  
## Vedere anche  
 [Guida di riferimento ai messaggi e agli errori di Integration Services](../../../integration-services/integration-services-error-and-message-reference.md)   
 [Identificazione di righe di dati simili tramite la trasformazione Raggruppamento fuzzy](../../../integration-services/data-flow/transformations/identify-similar-data-rows-by-using-the-fuzzy-grouping-transformation.md)  
  
  