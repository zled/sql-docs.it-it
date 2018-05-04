---
title: SaveOptionsEnum | Documenti Microsoft
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
- SaveOptionsEnum
helpviewer_keywords:
- SaveOptionsEnum enumeration [ADO]
ms.assetid: 59339100-6e29-48d1-aea3-6873796d186b
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ebd08388e2b658c6a4b5d85000d48dd4fe77c671
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="saveoptionsenum"></a>SaveOptionsEnum
Specifica se un file deve essere creato o sovrascritto durante il salvataggio da un [flusso](../../../ado/reference/ado-api/stream-object-ado.md) oggetto. I valori possono essere **adSaveCreateNotExist** o **adSaveCreateOverWrite**...  
  
|Costante|Value|Description|  
|--------------|-----------|-----------------|  
|**adSaveCreateNotExist**|1|Valore predefinito. Crea un nuovo file se il file specificato da di *FileName* parametro non esiste già.|  
|**adSaveCreateOverWrite**|2|Sovrascrive il file con i dati attualmente aperti **flusso** oggetto, se il file specificato da di *Filename* parametro esiste già. Se il file specificato da di *Filename* parametro non esiste, viene creato un nuovo file.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC equivalente  
 Queste costanti non dispongono di equivalenti ADO/WFC.  
  
## <a name="applies-to"></a>Si applica a  
 [Metodo SaveToFile](../../../ado/reference/ado-api/savetofile-method.md)
