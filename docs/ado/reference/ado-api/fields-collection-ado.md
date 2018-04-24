---
title: Campi insieme (ADO) | Documenti Microsoft
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
f1_keywords:
- Fields
- Recordset15::Fields
- _Record::Fields
helpviewer_keywords:
- Fields collection [ADO]
ms.assetid: 7c371474-b88f-4730-afa5-44163a0488d5
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 7a70341a6506ca585afca3adbff9f9e7ad7b2ff3
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="fields-collection-ado"></a>Raccolta di campi (ADO)
Contiene tutti i [campo](../../../ado/reference/ado-api/field-object.md) gli oggetti di un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) o [Record](../../../ado/reference/ado-api/record-object-ado.md) oggetto.  
  
## <a name="remarks"></a>Osservazioni  
 Oggetto **Recordset** oggetto ha un **campi** raccolta costituita da **campo** oggetti. Ogni **campo** oggetto corrisponde a una colonna di **Recordset**. È possibile popolare il **campi** raccolta prima dell'apertura di **Recordset** chiamando il [aggiornamento](../../../ado/reference/ado-api/refresh-method-ado.md) metodo per la raccolta.  
  
> [!NOTE]
>  Vedere il **campo** argomento di oggetto per una spiegazione più dettagliata di come utilizzare **campo** oggetti.  
  
 Il **campi** raccolta ha un [Append](../../../ado/reference/ado-api/append-method-ado.md) metodo, che è temporaneamente crea e aggiunge un **campo** oggetto alla raccolta e un **aggiornare**(metodo), che consente di finalizzare qualsiasi aggiunta o eliminazione.  
  
 Oggetto **Record** oggetto dispone di due campi speciale che possono essere indicizzati con [FieldEnum](../../../ado/reference/ado-api/fieldenum.md) costanti. Una costante accede a un campo contenente il flusso predefinito per il **Record**, e l'altro accede a un campo che contiene la stringa URL assoluta per il **Record**.  
  
 Alcuni provider (ad esempio, il [Provider Microsoft OLE DB per Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md)) possono popolare la **campi** insieme con un sottoinsieme dei campi disponibili per il **Record** o **Recordset**. Non possibile aggiungere altri campi a raccolta finché vengono innanzitutto a cui fa riferimento in base al nome o indicizzati tramite il codice.  
  
 Se si tenta di fare riferimento a un campo non esistente in base al nome, un nuovo **campo** verrà aggiunto all'oggetto di **campi** insieme con un [stato](../../../ado/reference/ado-api/status-property-ado-field.md) di  **adFieldPendingInsert**. Quando si chiama [aggiornamento](../../../ado/reference/ado-api/update-method.md), ADO creerà un nuovo campo nell'origine dati se consentito dal provider.  
  
 In questa sezione contiene l'argomento seguente.  
  
-   [Le proprietà della raccolta campi, metodi ed eventi](../../../ado/reference/ado-api/fields-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Field](../../../ado/reference/ado-api/field-object.md)
