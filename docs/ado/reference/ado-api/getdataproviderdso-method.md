---
title: Metodo GetDataProviderDSO | Documenti Microsoft
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
helpviewer_keywords: GetDataProviderDSO Method [ADO]
ms.assetid: 5a4c6bd5-0c79-4f81-a977-0561392d8d50
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 51b64a4e9bb2ea1c600e9f1c04f345c18e486e0b
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
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
