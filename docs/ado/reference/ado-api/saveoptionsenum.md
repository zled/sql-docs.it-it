---
title: SaveOptionsEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- SaveOptionsEnum
helpviewer_keywords:
- SaveOptionsEnum enumeration [ADO]
ms.assetid: 59339100-6e29-48d1-aea3-6873796d186b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 288168b2a4b47c8a73612bd89a6f1987e2808475
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47788762"
---
# <a name="saveoptionsenum"></a>SaveOptionsEnum
Specifica se un file deve essere creato o sovrascritto durante il salvataggio di un [Stream](../../../ado/reference/ado-api/stream-object-ado.md) oggetto. I valori possibili sono **adSaveCreateNotExist** oppure **adSaveCreateOverWrite**...  
  
|Costante|valore|Description|  
|--------------|-----------|-----------------|  
|**adSaveCreateNotExist**|1|Valore predefinito. Crea un nuovo file se il file specificato per il *FileName* parametro non esiste già.|  
|**adSaveCreateOverWrite**|2|Sovrascrive il file con i dati attualmente aperti **Stream** dell'oggetto, se il file specificato dalle *Filename* parametro già esistente. Se il file specificato per il *Filename* parametro non esiste, viene creato un nuovo file.|  
  
## <a name="adowfc-equivalent"></a>Equivalente di ADO o WFC  
 Queste costanti non dispongono di equivalenti di ADO o WFC.  
  
## <a name="applies-to"></a>Si applica a  
 [Metodo SaveToFile](../../../ado/reference/ado-api/savetofile-method.md)
