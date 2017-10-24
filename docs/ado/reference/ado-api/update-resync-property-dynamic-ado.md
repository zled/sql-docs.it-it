---
title: "Aggiornare risincronizzazione proprietà dinamica (ADO) | Documenti Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
helpviewer_keywords:
- Update Resync property [ADO]
ms.assetid: 8a3bb608-66d7-4128-a3ef-84cb0556de0d
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 7c43bd5b60fef002d4fad9cc6fc6842d602d5673
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="update-resync-property-dynamic-ado"></a>Aggiornamento risincronizzazione proprietà dinamica (ADO)
Specifica se il [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) metodo è seguito da implicita [Resync](../../../ado/reference/ado-api/resync-method.md) operazione del metodo e in tal caso, l'ambito dell'operazione.  
  
## <a name="settings-and-return-values"></a>Le impostazioni e valori restituiti  
 Imposta o restituisce uno o più di [ADCPROP_UPDATERESYNC_ENUM](../../../ado/reference/ado-api/adcprop-updateresync-enum.md) valori.  
  
## <a name="remarks"></a>Osservazioni  
 I valori di ADCPROP_UPDATERESYNC_ENUM possono essere combinati, ad eccezione di adResyncAll che già rappresenta una combinazione di altri valori.  
  
 La costante **adResyncConflicts** archivia i valori di risincronizzazione come valori sottostanti, ma non esegue l'override delle modifiche in sospeso.  
  
 **Aggiornare risincronizzazione** è una proprietà dinamica accodata la [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetto [proprietà](../../../ado/reference/ado-api/properties-collection-ado.md) raccolta quando il [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) proprietà è impostata su **adUseClient**.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Recordset ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)

