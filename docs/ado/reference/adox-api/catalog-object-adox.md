---
title: Oggetto Catalog (ADOX) | Documenti Microsoft
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
f1_keywords: Catalog
helpviewer_keywords: Catalog object [ADOX]
ms.assetid: bb651639-a488-4e38-b6de-0ed99fa4dd92
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1a7b82a70fadffd904d1da5a84f813c015faf80b
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="catalog-object-adox"></a>Oggetto del catalogo (ADOX)
Contiene raccolte ([tabelle](../../../ado/reference/adox-api/tables-collection-adox.md), [viste](../../../ado/reference/adox-api/views-collection-adox.md), [utenti](../../../ado/reference/adox-api/users-collection-adox.md), [gruppi](../../../ado/reference/adox-api/groups-collection-adox.md), e [procedure](../../../ado/reference/adox-api/procedures-collection-adox.md)) che vengono descritti il catalogo dello schema di un'origine dati.  
  
## <a name="remarks"></a>Osservazioni  
 È possibile modificare il **catalogo** oggetto aggiungendo o rimuovendo oggetti o modificando gli oggetti esistenti. Alcuni provider potrebbero non supportare tutte le **catalogo** oggetti o può supportare solo la visualizzazione delle informazioni sullo schema.  
  
 Con le proprietà e metodi di un **catalogo** dell'oggetto, è possibile:  
  
-   Aprire il catalogo impostando il [ActiveConnection](../../../ado/reference/adox-api/activeconnection-property-adox.md) proprietà per un oggetto ADO [connessione](../../../ado/reference/ado-api/connection-object-ado.md) oggetto o una stringa di connessione valida.  
  
-   Creare un nuovo catalogo con il [crea](../../../ado/reference/adox-api/create-method-adox.md) metodo.  
  
-   Determinare i proprietari degli oggetti in un **catalogo** con il [GetObjectOwner](../../../ado/reference/adox-api/getobjectowner-method-adox.md) e [SetObjectOwner](../../../ado/reference/adox-api/setobjectowner-method.md) metodi.  
  
 In questa sezione contiene l'argomento seguente.  
  
-   [Proprietà, metodi ed eventi dell'oggetto Catalog](../../../ado/reference/adox-api/catalog-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di proprietà ActiveConnection catalogo (VB)](../../../ado/reference/adox-api/catalog-activeconnection-property-example-vb.md)   
 [Comando e l'esempio di proprietà CommandText (VB)](../../../ado/reference/adox-api/command-and-commandtext-properties-example-vb.md)   
 [Connessione Close (metodo), esempio di proprietà di tipo tabella (Visual Basic)](../../../ado/reference/adox-api/connection-close-method-table-type-property-example-vb.md)   
 [Creare l'esempio di metodo (VB)](../../../ado/reference/adox-api/create-method-example-vb.md)   
 [Chiavi Aggiungi metodo, tipo di chiave, RelatedColumn, RelatedTable e UpdateRule proprietà esempio (VB)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Raccolta di parametri, esempio di proprietà di comando (Visual Basic)](../../../ado/reference/adox-api/parameters-collection-command-property-example-vb.md)   
 [Esempio di proprietà ParentCatalog (VB)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)   
 [Procedure di esempio del metodo Append (VB)](../../../ado/reference/adox-api/procedures-append-method-example-vb.md)   
 [Procedure di esempio del metodo Delete (VB)](../../../ado/reference/adox-api/procedures-delete-method-example-vb.md)   
 [Procedure di esempio del metodo Refresh (VB)](../../../ado/reference/adox-api/procedures-refresh-method-example-vb.md)   
 [Esempio di raccolte di campi (VB) e viste](../../../ado/reference/adox-api/views-and-fields-collections-example-vb.md)   
 [Viste di esempio del metodo Append (VB)](../../../ado/reference/adox-api/views-append-method-example-vb.md)   
 [Raccolta di visualizzazioni, esempio di proprietà CommandText (VB)](../../../ado/reference/adox-api/views-collection-commandtext-property-example-vb.md)   
 [Viste di esempio del metodo Delete (VB)](../../../ado/reference/adox-api/views-delete-method-example-vb.md)   
 [Viste di esempio del metodo Refresh (VB)](../../../ado/reference/adox-api/views-refresh-method-example-vb.md)   
 [Raccolta di gruppi (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)   
 [Raccolta di procedure (ADOX)](../../../ado/reference/adox-api/procedures-collection-adox.md)   
 [Raccolta di tabelle (ADOX)](../../../ado/reference/adox-api/tables-collection-adox.md)   
 [Raccolta di utenti (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)   
 [Raccolta di oggetti View (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)
