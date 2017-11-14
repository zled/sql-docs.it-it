---
title: Metodo GetDataProviderDSO | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GetDataProviderDSO Method [ADO]
ms.assetid: 5a4c6bd5-0c79-4f81-a977-0561392d8d50
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 40b23b500c50100b5a50f06566eeadd44e7f519c
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="getdataproviderdso-method"></a>Metodo GetDataProviderDSO
Recupera l'oggetto origine dati OLE DB sottostante dal provider di forma.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
HRESULT GetDataProviderDSO(  
      IUnknown **ppDataProviderDSOIUnknown  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 *ppDataProviderDSOIUnknown*  
 [out]  Un puntatore a un puntatore che restituisce l'interfaccia IUnknown dell'oggetto origine dati OLE DB sottostante.  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo non non addref il puntatore di interfaccia. Se il chiamante prevede di posizionare il puntatore, il chiamante deve eseguire le necessarie addref e release.  
  
## <a name="applies-to"></a>Applicabile a  
 [Interfaccia IDSOShapeExtensions](../../../ado/reference/ado-api/idsoshapeextensions-interface.md)

