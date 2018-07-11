---
title: Proprietà personalizzate della destinazione DataReader | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: f151c3e8-3811-457d-a3d3-6158ca65a646
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 6bda3a31cf3d498d59d4ec86c6c7b32bd2134385
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37158632"
---
# <a name="datareader-destination-custom-properties"></a>Proprietà personalizzate della destinazione DataReader
  La destinazione DataReader include sia proprietà personalizzate che le proprietà comuni a tutti i componenti del flusso di dati.  
  
 Nella tabella seguente vengono descritte le proprietà personalizzate della destinazione DataReader. Tutte le proprietà, ad eccezione di `DataReader` sono di lettura/scrittura.  
  
|Nome proprietà|Tipo di dati|Description|  
|-------------------|---------------|-----------------|  
|DataReader|String|Nome di classe della destinazione DataReader.|  
|FailOnTimeout|Boolean|Indica se generare un errore quando si verifica un `ReadTimeout`. Il valore predefinito di questa proprietà è **False**.|  
|ReadTimeout|Valore intero|Numero di millisecondi prima di un timeout. Il valore predefinito di questa proprietà è 30000 (30 secondi).|  
  
 L'input e le colonne di input della destinazione DataReader non includono proprietà personalizzate.  
  
 Per altre informazioni, vedere [Destinazione DataReader](datareader-destination.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà comuni](../common-properties.md)  
  
  
