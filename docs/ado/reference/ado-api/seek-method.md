---
title: Metodo Seek | Documenti Microsoft
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
- Recordset21::Seek
- Recordset21::raw_Seek
helpviewer_keywords:
- Seek method [ADO]
ms.assetid: 129293d2-19d3-4940-bf64-483ee72fb4a1
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d401bca51d735b2d0d633716cee732ad2ab9a086
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="seek-method"></a>Il metodo di ricerca
Cerca l'indice di un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) per individuare rapidamente la riga che corrisponde ai valori specificati e modifica la posizione della riga corrente di tale riga.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
recordset.Seek KeyValues, SeekOption  
```  
  
#### <a name="parameters"></a>Parametri  
 *KeyValues*  
 Matrice di **Variant** valori. Un indice è costituita da uno o più colonne e la matrice contiene un valore per il confronto di ogni colonna corrispondente.  
  
 *SeekOption*  
 Oggetto [SeekEnum](../../../ado/reference/ado-api/seekenum.md) valore che specifica il tipo di confronto da eseguire tra le colonne dell'indice e il corrispondente *KeyValues*.  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare il **Seek** metodo in combinazione con il [indice](../../../ado/reference/ado-api/index-property.md) proprietà se il provider sottostante supporta gli indici di **Recordset** oggetto. Utilizzare il [supporta](../../../ado/reference/ado-api/supports-method.md)**(adSeek)** metodo per determinare se il provider sottostante supporta **Seek**e **Supports (adIndex)** metodo per determinare se il provider supporta gli indici. (Ad esempio, il [il Provider OLE DB per Microsoft Jet](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-jet.md) supporta **Seek** e **indice**.)  
  
 Se **Seek** non trovare la riga desiderata, nessun errore si verifica e la riga è posizionato alla fine del **Recordset**. Impostare il **indice** proprietà per l'indice desiderato prima dell'esecuzione di questo metodo.  
  
 Questo metodo è supportato solo con i cursori sul lato server. Ricerca non è supportata quando il **Recordset** dell'oggetto [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) valore della proprietà è **adUseClient**.  
  
 Questo metodo può essere utilizzato quando il **Recordset** oggetto è stato aperto con un [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md) valore **adCmdTableDirect**.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Recordset ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo Seek e esempio di proprietà indice (Visual Basic)](../../../ado/reference/ado-api/seek-method-and-index-property-example-vb.md)   
 [Metodo Seek e esempio di proprietà indice (VC + +)](../../../ado/reference/ado-api/seek-method-and-index-property-example-vc.md)   
 [Find (metodo) (ADO)](../../../ado/reference/ado-api/find-method-ado.md)   
 [Proprietà index](../../../ado/reference/ado-api/index-property.md)
