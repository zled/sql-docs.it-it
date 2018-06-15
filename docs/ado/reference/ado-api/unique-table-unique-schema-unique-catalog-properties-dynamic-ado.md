---
title: Controllo le modifiche nella tabella di Base di Recordset (ADO) | Documenti Microsoft
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
helpviewer_keywords:
- Unique Table property [ADO]
- Unique Schema property [ADO]
- Unique Catalog property [ADO]
ms.assetid: d0e775d8-e353-46a1-ad10-ed4cc240dfaa
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8351eb10101219b09450055526f0cb6a47a95b5f
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35282700"
---
# <a name="unique-table-unique-schema-unique-catalog-properties-dynamic-ado"></a>Tabella univoca, Schema univoco, univoco catalogo proprietà dinamica (ADO)
Consente di controllare rigorosamente le modifiche a una tabella di base in un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) che valido da un'operazione di JOIN più tabelle di base.  
  
-   **Tabella univoca** specifica il nome della tabella di base su cui sono consentite gli aggiornamenti, inserimenti ed eliminazioni.  
  
-   **Schema univoco** specifica il *schema*, o il nome del proprietario della tabella.  
  
-   **Catalogo univoca** specifica il *catalogo*, o il nome del database contenente la tabella.  
  
## <a name="settings-and-return-values"></a>Le impostazioni e valori restituiti  
 Restituisce o imposta un **stringa** valore che rappresenta il nome di una tabella, schema o catalogo.  
  
## <a name="remarks"></a>Remarks  
 La tabella di base desiderata è identificata in modo univoco il catalogo, schema e i nomi di tabella. Quando il **tabella univoca** è impostata, i valori del **Schema univoco** o **catalogo univoca** proprietà vengono utilizzate per trovare la tabella di base. È consigliabile, ma non è obbligatorio, che una o entrambe le **Schema univoco** e **catalogo univoca** prima di impostare le proprietà di **tabella univoca** proprietà è impostata.  
  
 La chiave primaria del **tabella univoca** viene trattato come chiave primaria dell'intero **Recordset**. Si tratta della chiave utilizzata per qualsiasi metodo richiede una chiave primaria.  
  
 Mentre **tabella univoca** è impostata, il [eliminare](../../../ado/reference/ado-api/delete-method-ado-recordset.md) metodo interessa solo la tabella denominata. Il [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md), [Resync](../../../ado/reference/ado-api/resync-method.md), [aggiornamento](../../../ado/reference/ado-api/update-method.md), e [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) metodi hanno effetto su qualsiasi tabella di base sottostante del **Recordset**.  
  
 **Tabella univoca** deve essere specificato prima di eseguire qualsiasi risincronizzazione personalizzata. Se **tabella univoca** non è stato specificato il [Resync Command](../../../ado/reference/ado-api/resync-command-property-dynamic-ado.md) proprietà avrà alcun effetto.  
  
 Se una tabella di base univoca non viene trovata, verrà generato un errore in fase di esecuzione.  
  
 Queste proprietà dinamiche vengono aggiunte al **Recordset** oggetto [proprietà](../../../ado/reference/ado-api/properties-collection-ado.md) raccolta quando il [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) è impostata su  **adUseClient**.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
