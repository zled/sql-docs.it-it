---
title: Metodo get_OLEDBCommand | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: get_OLEDBCommand method [ADO]
ms.assetid: 23d551f5-3d5b-434b-ade6-fef15f1710e7
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: bb9a2fc69b7919cc738c4050c410a167352d3801
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="getoledbcommand-method"></a>get_OLEDBCommand (metodo)
Restituisce il sottostante comando OLE DB, innanzitutto propaga qualsiasi informazione di parametro impostato sul comando ADO per comando OLE DB.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
HRESULT get_OLEDBCommand(  
      IUnknown **ppOLEDBCommand  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 *ppOLEDBCommand*  
 [out] Puntatore a una posizione del puntatore in cui verrà scritto il puntatore IUnknown per sottostante comando OLE DB.  
  
## <a name="applies-to"></a>Si applica a  
 [IADOCommandConstruction](http://msdn.microsoft.com/en-us/d8e54333-00eb-4b72-bf4a-ca92c7ca5f86)
