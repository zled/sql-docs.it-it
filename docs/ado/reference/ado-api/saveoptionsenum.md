---
title: SaveOptionsEnum | Documenti Microsoft
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
- SaveOptionsEnum
helpviewer_keywords:
- SaveOptionsEnum enumeration [ADO]
ms.assetid: 59339100-6e29-48d1-aea3-6873796d186b
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 739e06a2038a61c821fd9acf779ec70df9621b16
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35281540"
---
# <a name="saveoptionsenum"></a>SaveOptionsEnum
Specifica se un file deve essere creato o sovrascritto durante il salvataggio da un [flusso](../../../ado/reference/ado-api/stream-object-ado.md) oggetto. I valori possono essere **adSaveCreateNotExist** o **adSaveCreateOverWrite**...  
  
|Costante|valore|Description|  
|--------------|-----------|-----------------|  
|**adSaveCreateNotExist**|1|Valore predefinito. Crea un nuovo file se il file specificato da di *FileName* parametro non esiste già.|  
|**adSaveCreateOverWrite**|2|Sovrascrive il file con i dati attualmente aperti **flusso** oggetto, se il file specificato da di *Filename* parametro esiste già. Se il file specificato da di *Filename* parametro non esiste, viene creato un nuovo file.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC equivalente  
 Queste costanti non dispongono di equivalenti ADO/WFC.  
  
## <a name="applies-to"></a>Si applica a  
 [Metodo SaveToFile](../../../ado/reference/ado-api/savetofile-method.md)
