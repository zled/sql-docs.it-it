---
title: Proprietà CursorLocation (ADO) | Documenti Microsoft
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
- Connection15::CursorLocation
- Recordset15::CursorLocation
helpviewer_keywords:
- CursorLocation property [ADO]
ms.assetid: 39c8d86e-7ee9-4182-be5e-aad5ce952f84
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a720586cc2ee6f866565fe9e43382395bcb44e65
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35277280"
---
# <a name="cursorlocation-property-ado"></a>Proprietà CursorLocation (ADO)
Indica la posizione del servizio di cursore.  
  
## <a name="settings-and-return-values"></a>Le impostazioni e valori restituiti  
 Restituisce o imposta un **lungo** valore che può essere impostato su uno del [CursorLocationEnum](../../../ado/reference/ado-api/cursorlocationenum.md) valori.  
  
## <a name="remarks"></a>Remarks  
 Questa proprietà consente di scegliere tra varie librerie di cursori accessibili al provider. In genere, è possibile scegliere tra l'utilizzo di una libreria di cursori sul lato client o che si trova nel server.  
  
 Impostazione di questa proprietà influisce sulle connessioni stabilite solo dopo aver impostata la proprietà. Modifica il **CursorLocation** proprietà ha effetto sulle connessioni esistenti.  
  
 I cursori restituiti dal [Execute](../../../ado/reference/ado-api/execute-method-ado-connection.md) metodo erediteranno questa impostazione. **Recordset** oggetti erediterà automaticamente questa impostazione dalle connessioni associate.  
  
 Questa proprietà è di lettura/scrittura in un [connessione](../../../ado/reference/ado-api/connection-object-ado.md) o un oggetto chiuso [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)e di sola lettura su un oggetto aperto **Recordset**.  
  
> [!NOTE]
>  **Utilizzo del servizio dati remoti** quando viene utilizzata su un lato client **Recordset** o **connessione** oggetto, il **CursorLocation** proprietà può essere impostata solo su **adUseClient**.  
  
## <a name="applies-to"></a>Si applica a  
  
|||  
|-|-|  
|[Oggetto Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)|[Oggetto Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Appendice A: Provider](../../../ado/guide/appendixes/appendix-a-providers.md)
