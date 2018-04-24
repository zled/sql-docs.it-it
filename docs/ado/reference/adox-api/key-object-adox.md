---
title: Chiave di oggetto (ADOX) | Documenti Microsoft
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
- Key
helpviewer_keywords:
- Key object [ADOX]
ms.assetid: 55f116fe-4d56-4892-bffe-0cdd6fc727c9
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 07e5798db39b07af2adac55f39770a9a6e33b091
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="key-object-adox"></a>Oggetto chiave (ADOX)
Rappresenta un campo di chiave primario, esterno o univoco di una tabella di database.  
  
## <a name="remarks"></a>Osservazioni  
 Il codice seguente crea un nuovo **chiave**:  
  
```  
Dim obj As New Key  
```  
  
 Con le proprietà e raccolte di un **chiave** dell'oggetto, è possibile:  
  
-   Identificare la chiave con il [nome](../../../ado/reference/adox-api/name-property-adox.md) proprietà.  
  
-   Determinare se la chiave è primaria, esterna o univoco con il [tipo](../../../ado/reference/adox-api/type-property-key-adox.md) proprietà.  
  
-   Accedere alle colonne di database della chiave con il [colonne](../../../ado/reference/adox-api/columns-collection-adox.md) insieme.  
  
-   Specificare il nome della tabella correlata con il [RelatedTable](../../../ado/reference/adox-api/relatedtable-property-adox.md) proprietà.  
  
-   Determinare l'azione eseguita su eliminazione o l'aggiornamento di una chiave primaria con la [DeleteRule](../../../ado/reference/adox-api/deleterule-property-adox.md) e [UpdateRule](../../../ado/reference/adox-api/updaterule-property-adox.md) proprietà.  
  
 In questa sezione contiene l'argomento seguente.  
  
-   [Proprietà, metodi ed eventi dell'oggetto Key](../../../ado/reference/adox-api/key-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Chiavi Aggiungi metodo, tipo di chiave, RelatedColumn, RelatedTable e UpdateRule proprietà esempio (VB)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Raccolta di colonne (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)   
 [Raccolta di oggetti Key (ADOX)](../../../ado/reference/adox-api/keys-collection-adox.md)
