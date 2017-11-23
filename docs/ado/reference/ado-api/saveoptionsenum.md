---
title: SaveOptionsEnum | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords: SaveOptionsEnum
helpviewer_keywords: SaveOptionsEnum enumeration [ADO]
ms.assetid: 59339100-6e29-48d1-aea3-6873796d186b
caps.latest.revision: "13"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f3d5a20bf9fbee275d55b01a8738b3b18a093cdb
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="saveoptionsenum"></a>SaveOptionsEnum
Specifica se un file deve essere creato o sovrascritto durante il salvataggio da un [flusso](../../../ado/reference/ado-api/stream-object-ado.md) oggetto. I valori possono essere **adSaveCreateNotExist** o **adSaveCreateOverWrite**...  
  
|Costante|Valore|Description|  
|--------------|-----------|-----------------|  
|**adSaveCreateNotExist**|1|Valore predefinito. Crea un nuovo file se il file specificato da di *FileName* parametro non esiste già.|  
|**adSaveCreateOverWrite**|2|Sovrascrive il file con i dati attualmente aperti **flusso** oggetto, se il file specificato da di *Filename* parametro esiste già. Se il file specificato da di *Filename* parametro non esiste, viene creato un nuovo file.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC equivalente  
 Queste costanti non dispongono di equivalenti ADO/WFC.  
  
## <a name="applies-to"></a>Si applica a  
 [Metodo SaveToFile](../../../ado/reference/ado-api/savetofile-method.md)
