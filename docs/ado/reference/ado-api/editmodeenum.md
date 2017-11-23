---
title: EditModeEnum | Documenti Microsoft
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
f1_keywords: EditModeEnum
helpviewer_keywords: EditModeEnum enumeration [ADO]
ms.assetid: 45d54b6e-db2c-4553-9fd0-528147d6da2f
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b9d1a7543dd09644bbda76a7b3f787479deb6a3e
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="editmodeenum"></a>EditModeEnum
Specifica lo stato di modifica di un record.  
  
|Costante|Valore|Description|  
|--------------|-----------|-----------------|  
|**adEditNone**|0|Indica che nessuna operazione di modifica è in corso.|  
|**adEditInProgress**|1|Indica che i dati del record corrente sono stati modificati ma non salvati.|  
|**adEditAdd**|2|Indica che il [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md) metodo è stato chiamato e il record corrente nel buffer di copia è un nuovo record che non è stato salvato nel database.|  
|**adEditDelete**|4|Indica che il record corrente è stato eliminato.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC equivalente  
 Pacchetto: **com.ms. wfc.**  
  
|Costante|  
|--------------|  
|AdoEnums.EditMode.NONE|  
|AdoEnums.EditMode.INPROGRESS|  
|AdoEnums.EditMode.ADD|  
|AdoEnums.EditMode.DELETE|  
  
## <a name="applies-to"></a>Si applica a  
 [Proprietà EditMode](../../../ado/reference/ado-api/editmode-property.md)
