---
title: Editor trasformazione Raggruppamento fuzzy (scheda Avanzate) | Documenti Microsoft
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
- sql12.dts.designer.fuzzygroupingtransformation.advanced.f1
helpviewer_keywords:
- Fuzzy Grouping Transformation Editor
ms.assetid: dd820d75-b8a7-4515-aea4-3553ba5b442e
caps.latest.revision: 28
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: b1696734810b1b3fd4ceccb624139358cea0dcaa
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36168841"
---
# <a name="fuzzy-grouping-transformation-editor-advanced-tab"></a>Editor trasformazione Raggruppamento fuzzy (scheda Avanzate)
  La scheda **Avanzate** della finestra di dialogo **Editor trasformazione Raggruppamento fuzzy** consente di specificare le colonne di input e output, impostare le soglie di somiglianza e definire i delimitatori.  
  
> [!NOTE]  
>  Il `Exhaustive` e il `MaxMemoryUsage` delle proprietà della trasformazione Raggruppamento Fuzzy non sono disponibili nel **Editor trasformazione Raggruppamento Fuzzy**, ma può essere impostata utilizzando il **Editor avanzato**. Per ulteriori informazioni su queste proprietà, vedere la sezione relativa alla trasformazione Raggruppamento fuzzy in [Transformation Custom Properties](data-flow/transformations/transformation-custom-properties.md).  
  
 Per ulteriori informazioni sulla trasformazione Raggruppamento fuzzy, vedere [Fuzzy Grouping Transformation](data-flow/transformations/fuzzy-grouping-transformation.md).  
  
## <a name="options"></a>Opzioni  
 **Nome colonna chiave di input**  
 Consente di specificare il nome di una colonna di output contenente l'identificatore univoco per ogni riga di input. Il `_key_in` colonna ha un valore che identifica in modo univoco ogni riga.  
  
 **Nome colonna chiave di output**  
 Consente di specificare il nome di una colonna di output contenente l'identificatore univoco per la riga canonica di un gruppo di righe duplicate. La colonna `_key_out` corrisponde al valore `_key_in` della riga di dati canonica.  
  
 **Nome colonna punteggio somiglianza**  
 Consente di specificare un nome per la colonna contenente il punteggio di somiglianza. Il punteggio di somiglianza è un valore compreso tra 0 e 1 che indica la somiglianza della riga di input alla riga canonica. I punteggi più prossimi a 1 indicano una corrispondenza maggiore.  
  
 **Soglia di somiglianza**  
 Consente di impostare la soglia di somiglianza mediante il dispositivo di scorrimento. Le soglie vicine a 1 indicano che le righe devono avere una somiglianza maggiore per poter essere considerate duplicati. L'aumento della soglia può incrementare la velocità di ricerca della corrispondenza in quanto viene considerato un minor numero di record candidati.  
  
 **Delimitatori token**  
 La trasformazione genera un set predefinito di delimitatori per la suddivisione in token dei dati. È tuttavia possibile aggiungere o rimuovere i delimitatori in base alle esigenze modificando l'elenco.  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti per i messaggi e agli errori di Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Identificare righe di dati simili tramite la trasformazione Raggruppamento fuzzy](data-flow/transformations/identify-similar-data-rows-by-using-the-fuzzy-grouping-transformation.md)  
  
  