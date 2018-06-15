---
title: StreamWriteEnum | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
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
ms.openlocfilehash: 62b5718d87d9c5117d10ad4ba55cdc783948778a
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35282712"
---
# <a name="streamwriteenum"></a>StreamWriteEnum
Specifica se un separatore di riga viene aggiunto alla stringa di scrivere un [flusso](../../../ado/reference/ado-api/stream-object-ado.md) oggetto.  
  
|Costante|valore|Description|  
|--------------|-----------|-----------------|  
|**adWriteChar**|0|Valore predefinito. Scrive la stringa di testo specificato (specificato da di *dati* parametro) per il **flusso** oggetto.|  
|**adWriteLine**|1|Scrive una stringa di testo e un carattere separatore di riga per un **flusso** oggetto. Se il [LineSeparator](../../../ado/reference/ado-api/lineseparator-property-ado.md) proprietà non è definita, quindi viene restituito un errore di run-time.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC equivalente  
 Queste costanti non dispongono di equivalenti ADO/WFC.  
  
## <a name="applies-to"></a>Si applica a  
 [Metodo WriteText](../../../ado/reference/ado-api/writetext-method.md)
