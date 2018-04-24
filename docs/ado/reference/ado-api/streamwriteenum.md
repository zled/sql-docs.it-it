---
title: StreamWriteEnum | Documenti Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- StreamWriteEnum
helpviewer_keywords:
- StreamWriteEnum enumeration [ADO]
ms.assetid: bdbf3405-a0bd-4f02-85d4-e3fe8da3f3f7
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 37435758716d914b868e785eaaf72243de8ebbc6
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="streamwriteenum"></a>StreamWriteEnum
Specifica se un separatore di riga viene aggiunto alla stringa di scrivere un [flusso](../../../ado/reference/ado-api/stream-object-ado.md) oggetto.  
  
|Costante|Value|Description|  
|--------------|-----------|-----------------|  
|**adWriteChar**|0|Valore predefinito. Scrive la stringa di testo specificato (specificato da di *dati* parametro) per il **flusso** oggetto.|  
|**adWriteLine**|1|Scrive una stringa di testo e un carattere separatore di riga per un **flusso** oggetto. Se il [LineSeparator](../../../ado/reference/ado-api/lineseparator-property-ado.md) proprietà non è definita, quindi viene restituito un errore di run-time.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC equivalente  
 Queste costanti non dispongono di equivalenti ADO/WFC.  
  
## <a name="applies-to"></a>Si applica a  
 [Metodo WriteText](../../../ado/reference/ado-api/writetext-method.md)
