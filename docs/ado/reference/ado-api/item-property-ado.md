---
title: "Elemento proprietà (ADO) | Documenti Microsoft"
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
- Parameters::GetItem
- Indexes::GetItem
- Parameters::Item
- Tables::Item
- Procedures::Item
- Users::GetItem
- Tables::GetItem
- Procedures::GetItem
- Users::get_Item
- Users::Item
- Views::GetItem
- Groups::Item
- Groups::get_Item
- Columns::Item
- Indexes::Item
- Fields15::GetItem
- Columns::GetItem
- Fields::Item
- Indexes::get_Item
- Columns::get_Item
- Fields15::Item
- Views::get_Item
- Groups::GetItem
- Errors::get_Item
- Fields15::get_Item
- Tables::get_Item
- Views::Item
- Errors::GetItem
- Parameters::get_Item
- Errors::Item
- Procedures::get_Item
helpviewer_keywords:
- Item property [ADO]
ms.assetid: e11484bb-c5c7-42d8-9bb8-21572125d727
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 59779714027c0ff619293d01de851daec7bbe158
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="item-property-ado"></a>Proprietà dell'elemento (ADO)
Indica un membro specifico di una raccolta, per nome o numero ordinale.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Set object = collection.Item ( Index )  
```  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un riferimento all'oggetto.  
  
## <a name="parameters"></a>Parametri  
 *Indice*  
 Oggetto **Variant** espressione che restituisce il nome o il numero ordinale di un oggetto in una raccolta.  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare il **elemento** proprietà per restituire un oggetto specifico in una raccolta. Se **elemento** Impossibile trovare un oggetto nella raccolta corrispondente di *indice* si verifica un errore di argomento. Inoltre, alcuni insiemi non supportano gli oggetti denominati. Per queste raccolte, è necessario utilizzare riferimenti di un numero ordinale.  
  
 Il **elemento** proprietà è la proprietà predefinita per tutte le raccolte, di conseguenza, le forme di sintassi seguenti sono intercambiabili:  
  
```  
collection.Item (Index)  
collection (Index)  
```  
  
## <a name="applies-to"></a>Si applica a  
  
||||  
|-|-|-|  
|[Raccolta assi (ADO MD)](../../../ado/reference/ado-md-api/axes-collection-ado-md.md)|[Raccolta di colonne (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)|[Insieme CubeDefs (ADO MD)](../../../ado/reference/ado-md-api/cubedefs-collection-ado-md.md)|  
|[Raccolta di dimensioni (ADO MD)](../../../ado/reference/ado-md-api/dimensions-collection-ado-md.md)|[Raccolta di errori (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)|[Raccolta di campi (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)|  
|[Raccolta di gruppi (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)|[Raccolta hierarchies (ADO MD)](../../../ado/reference/ado-md-api/hierarchies-collection-ado-md.md)|[Raccolta di indici (ADOX)](../../../ado/reference/adox-api/indexes-collection-adox.md)|  
|[Raccolta di chiavi (ADOX)](../../../ado/reference/adox-api/keys-collection-adox.md)|[Raccolta di livelli (ADO MD)](../../../ado/reference/ado-md-api/levels-collection-ado-md.md)|[Raccolta di membri (ADO MD)](../../../ado/reference/ado-md-api/members-collection-ado-md.md)|  
|[Raccolta di parametri (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)|[Raccolta di posizioni (ADO MD)](../../../ado/reference/ado-md-api/positions-collection-ado-md.md)|[Raccolta di procedure (ADOX)](../../../ado/reference/adox-api/procedures-collection-adox.md)|  
|[Raccolta delle proprietà (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)|[Raccolta di tabelle (ADOX)](../../../ado/reference/adox-api/tables-collection-adox.md)|[Raccolta di utenti (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)|  
|[Raccolta di visualizzazioni (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)|||  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di proprietà Item (VB)](../../../ado/reference/ado-api/item-property-example-vb.md)   
 [Esempio di proprietà Item (VC + +)](../../../ado/reference/ado-api/item-property-example-vc.md)   

