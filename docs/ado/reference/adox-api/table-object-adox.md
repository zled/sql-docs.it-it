---
title: Tabella oggetti (ADOX) | Documenti Microsoft
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
- Table
helpviewer_keywords:
- Table object [ADOX]
ms.assetid: a6d74000-0828-49ba-850a-63da865f8802
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: da9c76799df8983b50298ee7005f5a357905e4d7
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="table-object-adox"></a>Oggetto Table (ADOX)
Rappresenta una tabella di database, incluse le colonne, indici e chiavi.  
  
## <a name="remarks"></a>Osservazioni  
 Il codice seguente crea un nuovo **tabella**:  
  
```  
Dim obj As New Table  
```  
  
 Con le proprietà e raccolte di un **tabella** dell'oggetto, è possibile:  
  
-   Identificare la tabella con il [nome proprietà (ADOX)](../../../ado/reference/adox-api/name-property-adox.md) proprietà.  
  
-   Determinare il tipo di tabella con il [proprietà Type (tabella) (ADOX)](../../../ado/reference/adox-api/type-property-table-adox.md) proprietà.  
  
-   Accedere alle colonne di database della tabella con il [la raccolta di colonne (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md) insieme.  
  
-   Accedere agli indici della tabella con il [la raccolta di indici (ADOX)](../../../ado/reference/adox-api/indexes-collection-adox.md).  
  
-   Accesso alle chiavi della tabella con il [la raccolta di chiavi (ADOX)](../../../ado/reference/adox-api/keys-collection-adox.md).  
  
-   Specificare il catalogo a cui appartiene la tabella con il [proprietà ParentCatalog (ADOX)](../../../ado/reference/adox-api/parentcatalog-property-adox.md) proprietà.  
  
-   Restituire informazioni relative alla data con la [proprietà DateCreated (ADOX)](../../../ado/reference/adox-api/datecreated-property-adox.md) e [proprietà DateModified (ADOX)](../../../ado/reference/adox-api/datemodified-property-adox.md) proprietà.  
  
-   Accedere alle proprietà di tabella specifico del provider con il [la raccolta di proprietà (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md) insieme.  
  
> [!NOTE]
>  Il provider di dati potrebbe non supportare tutte le proprietà di **tabella** oggetti. Se è stato impostato un valore per una proprietà non è supportata dal provider, si verificherà un errore. Per i nuovi **tabella** oggetti, l'errore si verifica quando l'oggetto viene aggiunto alla raccolta. Per gli oggetti esistenti, l'errore si verifica quando l'impostazione della proprietà.  
>   
>  Quando si creano **tabella** oggetti, l'esistenza di un valore predefinito appropriato per una proprietà facoltativa non garantisce che il provider supporta la proprietà. Per ulteriori informazioni sulle proprietà, il provider supporta, vedere la documentazione del provider.  
  
 In questa sezione contiene l'argomento seguente.  
  
-   [Proprietà, metodi ed eventi dell'oggetto Table](../../../ado/reference/adox-api/table-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di proprietà ActiveConnection catalogo (VB)](../../../ado/reference/adox-api/catalog-activeconnection-property-example-vb.md)   
 [Le colonne e tabelle aggiungere metodi, esempio di proprietà Name (VB)](../../../ado/reference/adox-api/columns-and-tables-append-methods-name-property-example-vb.md)   
 [Connessione Close (metodo), esempio di proprietà di tipo tabella (Visual Basic)](../../../ado/reference/adox-api/connection-close-method-table-type-property-example-vb.md)   
 [Chiavi Aggiungi metodo, tipo di chiave, RelatedColumn, RelatedTable e UpdateRule proprietà esempio (VB)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Esempio di proprietà ParentCatalog (VB)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)   
 [Raccolta di colonne (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)   
 [Raccolta di indici (ADOX)](../../../ado/reference/adox-api/indexes-collection-adox.md)   
 [Raccolta di chiavi (ADOX)](../../../ado/reference/adox-api/keys-collection-adox.md)   
 [Raccolta delle proprietà (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)   
 [Raccolta di oggetti Table (ADOX)](../../../ado/reference/adox-api/tables-collection-adox.md)
