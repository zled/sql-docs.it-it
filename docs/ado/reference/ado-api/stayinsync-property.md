---
title: Proprietà StayInSync | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset20::StayInSync
- Recordset20::put_StayInSync
- Recordset20::PutStayInSync
- Recordset20::get_StayInSync
- Recordset20::GetStayInSync
helpviewer_keywords:
- StayInSync property
ms.assetid: 502d69b5-dc9a-455d-b115-a03bd39a552b
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d4e5067036aaaf36c60a134f825012fdc5facf75
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="stayinsync-property"></a>Proprietà StayInSync
Indica, in una gerarchia [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetto, se il riferimento a record figlio sottostanti (vale a dire il *capitolo*) le modifiche quando la riga padre posiziona le modifiche.  
  
## <a name="settings-and-return-values"></a>Le impostazioni e valori restituiti  
 Restituisce o imposta un **booleano** valore. Il valore predefinito è **True**. Se **True**, il capitolo verrà aggiornato se l'elemento padre **Recordset** modifiche all'oggetto la posizione riga; se **False**, il capitolo continueranno a fare riferimento ai dati nel capitolo precedente anche se l'elemento padre **Recordset** oggetto è stata modificata la posizione riga.  
  
## <a name="remarks"></a>Osservazioni  
 Questa proprietà si applica agli oggetti Recordset gerarchici, ad esempio quelli supportati per il [Microsoft Data shaping per OLE DB](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md)e deve essere impostato sull'oggetto padre **Recordset** prima l'elemento figlio  **Recordset** viene recuperato. Questa proprietà semplifica lo spostamento nei recordset gerarchici.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di proprietà StayInSync (VB)](../../../ado/reference/ado-api/stayinsync-property-example-vb.md)   
 [Microsoft servizio Data Shaping per OLE DB (ADO Service Provider)](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md)
