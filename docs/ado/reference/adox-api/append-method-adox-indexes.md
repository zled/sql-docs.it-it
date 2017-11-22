---
title: Append (metodo) (ADOX indici) | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords: Indexes::Append
helpviewer_keywords: Append method [ADOX]
ms.assetid: 6695769f-275b-4b70-81bd-1a5f7d74926c
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 27ddeee201dba9d1381b31023039256d9e587a1f
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="append-method-adox-indexes"></a>Append (metodo) (ADOX indici)
Aggiunge un nuovo [indice](../../../ado/reference/adox-api/index-object-adox.md) dell'oggetto per il [indici](../../../ado/reference/adox-api/indexes-collection-adox.md) insieme.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Indexes.Append Index [,Columns]  
```  
  
#### <a name="parameters"></a>Parametri  
 *Index*  
 Il **indice** oggetto da accodare o il nome dell'indice per creare e aggiungere.  
  
 *Colonne*  
 Facoltativa. Oggetto **Variant** valore che specifica il nome di una o più colonne da indicizzare. Il *colonne* parametro corrisponde ai valori del [nome](../../../ado/reference/adox-api/name-property-adox.md) proprietà di un [colonna](../../../ado/reference/adox-api/column-object-adox.md) o più oggetti.  
  
## <a name="remarks"></a>Osservazioni  
 Il *colonne* parametro può accettare il nome di una colonna o una matrice di nomi di colonna.  
  
 Se il provider non supporta la creazione di indici, si verificherà un errore.  
  
## <a name="applies-to"></a>Si applica a  
 [Raccolta di oggetti Index (ADOX)](../../../ado/reference/adox-api/indexes-collection-adox.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Indici di esempio del metodo Append (VB)](../../../ado/reference/adox-api/indexes-append-method-example-vb.md)   
 [Append (metodo) (ADOX colonne)](../../../ado/reference/adox-api/append-method-adox-columns.md)   
 [Append (metodo) (ADOX gruppi)](../../../ado/reference/adox-api/append-method-adox-groups.md)   
 [Append (metodo) (ADOX chiavi)](../../../ado/reference/adox-api/append-method-adox-keys.md)   
 [Append (metodo) (ADOX procedure)](../../../ado/reference/adox-api/append-method-adox-procedures.md)   
 [Append (metodo) (ADOX tabelle)](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Append (metodo) (ADOX utenti)](../../../ado/reference/adox-api/append-method-adox-users.md)   
 [Metodo Append (oggetti View ADOX)](../../../ado/reference/adox-api/append-method-adox-views.md)
