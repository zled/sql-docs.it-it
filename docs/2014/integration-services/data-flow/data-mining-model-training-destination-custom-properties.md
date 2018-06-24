---
title: Proprietà personalizzate della destinazione Training modello di data mining | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f0a70216-fdac-44ae-af29-35f65626217c
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 17b2b721a5c90009fabca15864b62e71e0677251
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36065408"
---
# <a name="data-mining-model-training-destination-custom-properties"></a>Proprietà personalizzate della destinazione Training modello di data mining
  La destinazione Training modello di data mining include sia proprietà personalizzate che le proprietà comuni a tutti i componenti del flusso di dati.  
  
 Nella tabella seguente vengono descritte le proprietà personalizzate della destinazione Training modello di data mining. Tutte le proprietà sono di lettura/scrittura.  
  
|Proprietà|Tipo di dati|Description|  
|--------------|---------------|-----------------|  
|ASConnectionId|String|Identificatore univoco della gestione connessione.|  
|ASConnectionString|String|Stringa di connessione a un'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] o a un progetto [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .|  
|ObjectRef|String|Tag XML che identifica la struttura di data mining utilizzata dalla trasformazione.|  
  
 L'input e le colonne di input della destinazione Training modelli di data mining non includono proprietà personalizzate.  
  
 Per altre informazioni, vedere [Destinazione Training modello di data mining](data-mining-model-training-destination.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà comuni](../common-properties.md)  
  
  