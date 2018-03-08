---
title: Indice di oggetto (ADOX) | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Index
helpviewer_keywords:
- Index object [ADOX]
ms.assetid: 6b9578c0-bc94-46b9-b801-c18e14b04b31
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: bb35b814dbd06136c9ce0a47a82e5956e98b6945
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="index-object-adox"></a>Oggetto Index (ADOX)
Rappresenta un indice di una tabella di database.  
  
## <a name="remarks"></a>Osservazioni  
 Il codice seguente crea un nuovo **indice**:  
  
```  
Dim obj As New Index  
```  
  
 Con le proprietà e raccolte di un **indice** dell'oggetto, è possibile:  
  
-   Identificare l'indice con il [nome](../../../ado/reference/adox-api/name-property-adox.md) proprietà.  
  
-   Accedere alle colonne di database dell'indice con il [colonne](../../../ado/reference/adox-api/columns-collection-adox.md) insieme.  
  
-   Specificare se le chiavi di indice devono essere univoche con la [Unique](../../../ado/reference/adox-api/unique-property-adox.md) proprietà.  
  
-   Specificare se l'indice è la chiave primaria per una tabella con il [PrimaryKey](../../../ado/reference/adox-api/primarykey-property-adox.md) proprietà.  
  
-   Specificare se i record con valori null nei relativi campi indice includono voci di indice con il [IndexNulls](../../../ado/reference/adox-api/indexnulls-property-adox.md) proprietà.  
  
-   Specificare se gli indici cluster con il [Clustered](../../../ado/reference/adox-api/clustered-property-adox.md) proprietà.  
  
-   Accedere alle proprietà di indice specifiche del provider con il [proprietà](../../../ado/reference/ado-api/properties-collection-ado.md) insieme.  
  
> [!NOTE]
>  Si verifica un errore quando si accoda un [colonna](../../../ado/reference/adox-api/column-object-adox.md) per il **colonne** raccolta di un **indice** se il **colonna** non esiste un [Tabella](../../../ado/reference/adox-api/table-object-adox.md) già aggiunto all'oggetto di [tabelle](../../../ado/reference/adox-api/tables-collection-adox.md) insieme.  
  
> [!NOTE]
>  Il provider di dati potrebbe non supportare tutte le proprietà di **indice** oggetti. Se è stato impostato un valore per una proprietà che non è supportato dal provider, si verificherà un errore. Per i nuovi **indice** oggetti, l'errore si verifica quando l'oggetto viene aggiunto alla raccolta. Per gli oggetti esistenti, l'errore si verifica quando l'impostazione della proprietà.  
  
> [!NOTE]
>  Quando si creano **indice** oggetti, l'esistenza di un valore predefinito appropriato per una proprietà facoltativa non garantisce che il provider supporta la proprietà. Per ulteriori informazioni sulle proprietà, il provider supporta, vedere la documentazione del provider.  
  
 In questa sezione contiene l'argomento seguente.  
  
-   [Proprietà, metodi ed eventi dell'oggetto Index](../../../ado/reference/adox-api/index-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Indici di esempio del metodo Append (VB)](../../../ado/reference/adox-api/indexes-append-method-example-vb.md)   
 [Esempio di proprietà IndexNulls (VB)](../../../ado/reference/adox-api/indexnulls-property-example-vb.md)   
 [Esempio PrimaryKey e proprietà univoche (VB)](../../../ado/reference/adox-api/primarykey-and-unique-properties-example-vb.md)   
 [Esempio di proprietà SortOrder (VB)](../../../ado/reference/adox-api/sortorder-property-example-vb.md)   
 [Raccolta di colonne (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)   
 [Raccolta di indici (ADOX)](../../../ado/reference/adox-api/indexes-collection-adox.md)   
 [Raccolta delle proprietà (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
