---
title: Modificare la forma di nome proprietà dinamica (ADO) | Documenti Microsoft
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
helpviewer_keywords:
- Reshape Name property [ADO]
ms.assetid: 690229d1-46cc-42e6-a57d-4438251fe248
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8a1d81e91edfcab8b6938f5898ae4fd46cc38b67
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="reshape-name-property-dynamic-ado"></a>Modificare la forma di nome proprietà dinamica (ADO)
Specifica un nome per il [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetto.  
  
## <a name="return-values"></a>Valori restituiti  
 Restituisce un **stringa** valore che rappresenta il nome del **Recordset**.  
  
## <a name="remarks"></a>Osservazioni  
 I nomi vengono mantenute per tutta la durata della connessione o fino a quando il **Recordset** viene chiuso.  
  
 Il **modificare la forma di nome** proprietà viene usata principalmente per l'utilizzo con la funzionalità di ripetizione del data shaping di [Microsoft Data shaping per OLE DB](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md) provider del servizio. I nomi devono essere univoci a partecipare di nuovo data shaping.  
  
 Questa proprietà è di sola lettura, ma può essere impostata indirettamente quando un **Recordset** viene creato. Ad esempio, se una clausola di un comando Shape crea un **Recordset** e assegna un nome di alias utilizzando il **AS** (parola chiave), a cui viene assegnato l'alias di **modificare la forma di nome** proprietà. Se non viene dichiarato alcun alias, il **modificare la forma di nome** proprietà viene assegnato un nome univoco generato dal servizio di data shaping. Se il nome di alias è lo stesso nome di un oggetto esistente **Recordset**, né **Recordset** può modificare la forma fino al rilascio di uno di essi. Il comportamento predefinito può essere modificato impostando un nome univoco [modificare la forma di nome](../../../ado/reference/ado-api/reshape-name-property-dynamic-ado.md) proprietà per la connessione ADO a **True**. Impostazione di questa proprietà fornisce i dati di data shaping di autorizzazione del servizio per modificare il nome utente assegnato, se necessario, per garantire l'univocità. Per ulteriori informazioni sulla modifica della forma, vedere [Microsoft Data shaping per OLE DB (ADO Service Provider)](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md).  
  
 Utilizzare il **modificare la forma di nome** proprietà quando si desidera fare riferimento a un **Recordset** in un comando Shape o quando non si conosce il nome perché è stato generato dal servizio di Data Shaping. In tal caso, è possibile generare un comando SHAPE concatenando il comando per la stringa restituita dal **modificare la forma di nome** proprietà.  
  
 **Modificare la forma di nome** viene aggiunta una proprietà dinamica per il **Recordset** dell'oggetto [proprietà](../../../ado/reference/ado-api/properties-collection-ado.md) raccolta quando il [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) è impostata su **adUseClient**.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Microsoft servizio Data Shaping per OLE DB (ADO Service Provider)](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md)   
 [Comandi Shape in generale](../../../ado/guide/data/shape-commands-in-general.md)   
 [Oggetto Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
