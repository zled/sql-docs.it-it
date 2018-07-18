---
title: Oggetto Column (ADOX) | Documenti Microsoft
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
f1_keywords:
- Column
helpviewer_keywords:
- Column object [ADOX]
ms.assetid: 6e772783-1bc8-4ea7-94b2-7d7a52ea5c47
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8dc7319f20e50ccbdbc14d60f15c96af11b6188a
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35285291"
---
# <a name="column-object-adox"></a>Oggetto Column (ADOX)
Rappresenta una colonna di una tabella, indice o chiave.  
  
## <a name="remarks"></a>Remarks  
 Il codice seguente crea un nuovo **colonna**:  
  
 `Dim obj As New Column`  
  
 Con le proprietà e raccolte di un **colonna** dell'oggetto, è possibile:  
  
-   Identificare la colonna con il [nome proprietà (ADOX)](../../../ado/reference/adox-api/name-property-adox.md) proprietà.  
  
-   Specificare il tipo di dati della colonna con il [proprietà Type (chiave) (ADOX)](../../../ado/reference/adox-api/type-property-key-adox.md) proprietà.  
  
-   Determinare se la colonna a lunghezza fissa, o se può contenere valori null con il [proprietà attributi (ADOX)](../../../ado/reference/adox-api/attributes-property-adox.md) proprietà.  
  
-   Specificare le dimensioni massime della colonna con il [proprietà DefinedSize (ADOX)](../../../ado/reference/adox-api/definedsize-property-adox.md) proprietà.  
  
-   Per i valori di dati numerici, specificare la scala con il [proprietà NumericScale (ADOX)](../../../ado/reference/adox-api/numericscale-property-adox.md) proprietà.  
  
-   Per il valore di dati numerici, specificare la precisione massima con il [proprietà Precision (ADOX)](../../../ado/reference/adox-api/precision-property-adox.md) proprietà.  
  
-   Specificare il [oggetto catalogo (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md) cui appartiene la colonna con il [proprietà ParentCatalog (ADOX)](../../../ado/reference/adox-api/parentcatalog-property-adox.md) proprietà.  
  
-   Per le colonne chiave, specificare il nome della colonna correlata nella tabella correlata con il [proprietà RelatedColumn (ADOX)](../../../ado/reference/adox-api/relatedcolumn-property-adox.md) proprietà.  
  
-   Per le colonne di indice, specificare se l'ordinamento è crescente o decrescente con il [proprietà SortOrder (ADOX)](../../../ado/reference/adox-api/sortorder-property-adox.md) proprietà.  
  
-   Accedere a proprietà specifiche del provider con il [la raccolta di proprietà (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md) insieme.  
  
> [!NOTE]
>  Non tutte le proprietà di **colonna** oggetti possono essere supportati da provider di dati. Se è stato impostato un valore per una proprietà non è supportata dal provider, si verificherà un errore. Per i nuovi **colonna** oggetti, l'errore si verifica quando l'oggetto viene aggiunto alla raccolta. Per gli oggetti esistenti, l'errore si verifica quando l'impostazione della proprietà.  
>   
>  Quando si creano **colonna** oggetti, l'esistenza di un valore predefinito appropriato per una proprietà facoltativa non garantisce che il provider supporta la proprietà. Per ulteriori informazioni sulle proprietà, il provider supporta, vedere la documentazione del provider.  
  
 In questa sezione contiene l'argomento seguente.  
  
-   [Proprietà, metodi ed eventi dell'oggetto Column](../../../ado/reference/adox-api/column-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Le colonne e tabelle aggiungere metodi, esempio di proprietà Name (VB)](../../../ado/reference/adox-api/columns-and-tables-append-methods-name-property-example-vb.md)   
 [Connessione Close (metodo), esempio di proprietà di tipo tabella (Visual Basic)](../../../ado/reference/adox-api/connection-close-method-table-type-property-example-vb.md)   
 [Chiavi Aggiungi metodo, tipo di chiave, RelatedColumn, RelatedTable e UpdateRule proprietà esempio (VB)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Esempio di codice ADOX: NumericScale e Precision (VB)](../../../ado/reference/adox-api/adox-code-example-numericscale-and-precision-properties-example-vb.md)   
 [Esempio di proprietà ParentCatalog (VB)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)   
 [Esempio di proprietà SortOrder (VB)](../../../ado/reference/adox-api/sortorder-property-example-vb.md)   
 [Raccolta di colonne (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)   
 [Raccolta delle proprietà (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
