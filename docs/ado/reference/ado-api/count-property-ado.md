---
title: "La proprietà Count (ADO) | Documenti Microsoft"
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
- _Collection::Count
helpviewer_keywords:
- Count property [ADO]
ms.assetid: da9ccd1f-d402-41a2-940c-45556fc5340d
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 173b2fc9073676e77ad3068e9e9dc3ca76089702
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="count-property-ado"></a>Proprietà Count (ADO)
Indica il numero di oggetti in una raccolta.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un **lungo** valore.  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare il **conteggio** proprietà per determinare il numero di oggetti presenti in una raccolta specificata.  
  
 Poiché la numerazione dei membri di una raccolta inizia da zero, è consigliabile codificare sempre i cicli a partire dal membro zero e terminando con il valore di **conteggio** proprietà meno 1. Se si utilizza Microsoft Visual Basic e si desidera per scorrere in ciclo i membri di una raccolta senza il controllo il **conteggio** proprietà, utilizzare il **For Each... Avanti** comando.  
  
 Se il **conteggio** proprietà è zero, non sono presenti oggetti nella raccolta.  
  
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
 [Esempio di proprietà Count (VB)](../../../ado/reference/ado-api/count-property-example-vb.md)   
 [Esempio di proprietà Count (VC + +)](../../../ado/reference/ado-api/count-property-example-vc.md)   
 [Metodo Refresh (ADO)](../../../ado/reference/ado-api/refresh-method-ado.md)

