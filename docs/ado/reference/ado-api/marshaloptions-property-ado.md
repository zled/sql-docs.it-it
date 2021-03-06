---
title: Proprietà MarshalOptions (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::MarshalOptions
helpviewer_keywords:
- MarshalOptions property [ADO]
ms.assetid: 390c8abf-133e-40da-8b99-8f748a983e4f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 35646314a5c52e86284326ee91776b5afe2a0d17
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47625079"
---
# <a name="marshaloptions-property-ado"></a>Proprietà MarshalOptions (ADO)
Indica quali record del [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) sono da sottoporre a marshalling al server.  
  
## <a name="settings-and-return-values"></a>Le impostazioni e valori restituiti  
 Imposta o restituisce un [MarshalOptionsEnum](../../../ado/reference/ado-api/marshaloptionsenum.md) valore. Il valore predefinito è **adMarshalAll**.  
  
## <a name="remarks"></a>Note  
 Quando si usa un client-side [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md), i record che sono stati modificati sul client vengono scritte nel livello intermedio o di un server Web tramite una tecnica per effettuare il marshalling, il processo di creazione del pacchetto e il metodo di interfaccia di invio parametri attraverso i limiti di thread o processo. Impostando il **MarshalOptions** proprietà può migliorare le prestazioni quando viene effettuato il marshalling di dati remoti modificata per l'aggiornamento al livello intermedio o server Web.  
  
> [!NOTE]
>  **Utilizzo del servizio dati remoto** questa proprietà viene utilizzata solo in un client-side **Recordset**.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di proprietà MarshalOptions (VB)](../../../ado/reference/ado-api/marshaloptions-property-example-vb.md)   
 [Esempio di proprietà MarshalOptions (VC++)](../../../ado/reference/ado-api/marshaloptions-property-example-vc.md)   
