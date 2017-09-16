---
title: Delete (metodo) (insiemi ADOX) | Documenti Microsoft
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
- Views::Delete
- Groups::Delete
- Indexes::raw_Delete
- Columns::raw_Delete
- Tables::Delete
- Keys::Delete
- Users::Delete
- Users::raw_Delete
- Keys::raw_Delete
- Procedures::raw_Delete
- Views::raw_Delete
- Indexes::Delete
- Procedures::Delete
- Groups::raw_Delete
- Tables::raw_Delete
- Columns::Delete
helpviewer_keywords:
- delete method [ADOX]
ms.assetid: e6b6e3a4-8952-4d79-81f4-51019c338374
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 72dd3f6d514b20bb28f9daee6fc16c5c7c346095
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="delete-method-adox-collections"></a>Delete (metodo) (ADOX raccolte)
Rimuove un oggetto da una raccolta.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Collection.Delete Name  
```  
  
#### <a name="parameters"></a>Parametri  
 *Nome*  
 Oggetto **Variant** che specifica il nome o la posizione ordinale (indice) dell'oggetto da eliminare.  
  
## <a name="remarks"></a>Osservazioni  
 Si verifica un errore se il *nome* non esiste nella raccolta.  
  
 Per [tabelle](../../../ado/reference/adox-api/tables-collection-adox.md) e [utenti](../../../ado/reference/adox-api/users-collection-adox.md) raccolte, si verifica un errore se il provider non supporta l'eliminazione di tabelle o gli utenti, rispettivamente. Per [procedure](../../../ado/reference/adox-api/procedures-collection-adox.md) e [viste](../../../ado/reference/adox-api/views-collection-adox.md) raccolte, **eliminare** avrà esito negativo se il provider non supporta i comandi di persistenza.  
  
## <a name="applies-to"></a>Si applica a  
  
||||  
|-|-|-|  
|[Raccolta di colonne (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)|[Raccolta di gruppi (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)|[Raccolta di indici (ADOX)](../../../ado/reference/adox-api/indexes-collection-adox.md)|  
|[Raccolta di chiavi (ADOX)](../../../ado/reference/adox-api/keys-collection-adox.md)|[Raccolta di procedure (ADOX)](../../../ado/reference/adox-api/procedures-collection-adox.md)|[Raccolta di tabelle (ADOX)](../../../ado/reference/adox-api/tables-collection-adox.md)|  
|[Raccolta di utenti (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)|[Raccolta di visualizzazioni (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)||  
  
## <a name="see-also"></a>Vedere anche  
 [Procedure di esempio del metodo Delete (VB)](../../../ado/reference/adox-api/procedures-delete-method-example-vb.md)   
 [Viste di esempio del metodo Delete (VB)](../../../ado/reference/adox-api/views-delete-method-example-vb.md)
