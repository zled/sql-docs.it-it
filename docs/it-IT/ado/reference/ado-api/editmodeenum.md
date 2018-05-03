---
title: EditModeEnum | Documenti Microsoft
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
- EditModeEnum
helpviewer_keywords:
- EditModeEnum enumeration [ADO]
ms.assetid: 45d54b6e-db2c-4553-9fd0-528147d6da2f
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3702e111333194804f3c0bd7335e4403f4bfddd0
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="editmodeenum"></a>EditModeEnum
Specifica lo stato di modifica di un record.  
  
|Costante|Value|Description|  
|--------------|-----------|-----------------|  
|**adEditNone**|0|Indica che nessuna operazione di modifica è in corso.|  
|**adEditInProgress**|1|Indica che i dati del record corrente sono stati modificati ma non salvati.|  
|**adEditAdd**|2|Indica che il [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md) metodo è stato chiamato e il record corrente nel buffer di copia è un nuovo record che non è stato salvato nel database.|  
|**adEditDelete**|4|Indica che il record corrente è stato eliminato.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC equivalente  
 Package: **com.ms.wfc.data**  
  
|Costante|  
|--------------|  
|AdoEnums.EditMode.NONE|  
|AdoEnums.EditMode.INPROGRESS|  
|AdoEnums.EditMode.ADD|  
|AdoEnums.EditMode.DELETE|  
  
## <a name="applies-to"></a>Si applica a  
 [Proprietà EditMode](../../../ado/reference/ado-api/editmode-property.md)
