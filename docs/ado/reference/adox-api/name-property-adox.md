---
title: "Nome proprietà (ADOX) | Documenti Microsoft"
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
- _Table::PutName
- _Table::GetName
- _Key::Name
- _Key::get_Name
- _Column::GetName
- _Index::Name
- _Index::put_Name
- _Column::PutName
- _Key::put_Name
- _Table::put_Name
- _User25::PutName
- _Index::get_Name
- _Column::get_Name
- _Group25::Name
- _Group25::get_Name
- _Column::Name
- _User25::get_Name
- _Table::Name
- _Group25::GetName
- _Index::PutName
- _Column::put_Name
- _Key::GetName
- _Table::get_Name
- _User25::Name
- _User25::put_Name
- _Index::GetName
- _User25::GetName
helpviewer_keywords:
- Name property [ADOX]
ms.assetid: 81b92baf-b6b9-4f4e-9f33-4503795518cd
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 96a4d83770ee986c781efb9859eb071d197b112c
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="name-property-adox"></a>Nome proprietà (ADOX)
Indica il nome dell'oggetto.  
  
## <a name="settings-and-return-values"></a>Le impostazioni e valori restituiti  
 Restituisce o imposta un **stringa** valore.  
  
## <a name="remarks"></a>Osservazioni  
 Nome non deve essere univoco all'interno di una raccolta.  
  
 Il **nome** proprietà è di lettura/scrittura in [colonna](../../../ado/reference/adox-api/column-object-adox.md), [gruppo](../../../ado/reference/adox-api/group-object-adox.md), [chiave](../../../ado/reference/adox-api/key-object-adox.md), [indice](../../../ado/reference/adox-api/index-object-adox.md), [ Tabella](../../../ado/reference/adox-api/table-object-adox.md), e [utente](../../../ado/reference/adox-api/user-object-adox.md) oggetti. Il **nome** proprietà è di sola lettura su [catalogo](../../../ado/reference/adox-api/catalog-object-adox.md), [procedura](../../../ado/reference/adox-api/procedure-object-adox.md), e [visualizzazione](../../../ado/reference/adox-api/view-object-adox.md) oggetti.  
  
 Per gli oggetti di lettura/scrittura (**colonna**, **gruppo**, **chiave**, **indice**, **tabella** e  **Utente** oggetti), il valore predefinito è una stringa vuota ("").  
  
> [!NOTE]
>  Per le chiavi, questa proprietà è di sola lettura su **chiave** già aggiunti a una raccolta di oggetti. Per le tabelle, questa proprietà è di sola lettura per **tabella** già aggiunti a una raccolta di oggetti.  
  
## <a name="applies-to"></a>Si applica a  
  
||||  
|-|-|-|  
|[Oggetto Column (ADOX)](../../../ado/reference/adox-api/column-object-adox.md)|[Oggetto di gruppo (ADOX)](../../../ado/reference/adox-api/group-object-adox.md)|[Oggetto Index (ADOX)](../../../ado/reference/adox-api/index-object-adox.md)|  
|[Oggetto chiave (ADOX)](../../../ado/reference/adox-api/key-object-adox.md)|[Oggetto procedure (ADOX)](../../../ado/reference/adox-api/procedure-object-adox.md)|[Oggetto di proprietà (ADO)](../../../ado/reference/ado-api/property-object-ado.md)|  
|[Oggetto Table (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)|[Oggetto utente (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)|[Oggetto visualizzazione (ADOX)](../../../ado/reference/adox-api/view-object-adox.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Le colonne e tabelle aggiungere metodi, esempio di proprietà Name (VB)](../../../ado/reference/adox-api/columns-and-tables-append-methods-name-property-example-vb.md)   
 [Chiavi Aggiungi metodo, tipo di chiave, RelatedColumn, RelatedTable e UpdateRule proprietà esempio (VB)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Esempio di proprietà ParentCatalog (VB)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)

