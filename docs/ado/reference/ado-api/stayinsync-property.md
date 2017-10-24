---
title: "Proprietà StayInSync | Documenti Microsoft"
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
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 3951725cd3463af5cc4348cdb7803fe760345854
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="stayinsync-property"></a>Proprietà StayInSync
Indica, in una gerarchia [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetto, se il riferimento a record figlio sottostanti (vale a dire il *capitolo*) le modifiche quando la riga padre posiziona le modifiche.  
  
## <a name="settings-and-return-values"></a>Le impostazioni e valori restituiti  
 Restituisce o imposta un **booleano** valore. Il valore predefinito è **True**. Se **True**, il capitolo verrà aggiornato se l'elemento padre **Recordset** modifiche all'oggetto la posizione riga; se **False**, il capitolo continueranno a fare riferimento ai dati nel capitolo precedente anche se l'elemento padre **Recordset** oggetto è stata modificata la posizione riga.  
  
## <a name="remarks"></a>Osservazioni  
 Questa proprietà si applica agli oggetti Recordset gerarchici, ad esempio quelli supportati per il [Microsoft Data shaping per OLE DB](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md)e deve essere impostato sull'oggetto padre **Recordset** prima l'elemento figlio ** Recordset** viene recuperato. Questa proprietà semplifica lo spostamento nei recordset gerarchici.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Recordset ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di proprietà StayInSync (VB)](../../../ado/reference/ado-api/stayinsync-property-example-vb.md)   
 [Microsoft servizio Data Shaping per OLE DB (ADO Service Provider)](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md)

