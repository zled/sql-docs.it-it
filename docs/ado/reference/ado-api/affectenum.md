---
title: AffectEnum | Documenti Microsoft
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
- AffectEnum
helpviewer_keywords:
- AffectEnum enumeration [ADO]
ms.assetid: 1ab921a0-6c57-43b4-9291-701b2599f3e8
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 63bf19b58ddd79dc684011b56287f35107e568af
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="affectenum"></a>AffectEnum
Specifica i record interessati da un'operazione.  
  
|Costante|Valore|Description|  
|--------------|-----------|-----------------|  
|**adAffectAll**|3|Se non è presente un [filtro](../../../ado/reference/ado-api/filter-property.md) applicato per la **Recordset**, influisce su tutti i record.<br /><br /> Se il **filtro** è impostata su un criterio di tipo stringa (ad esempio "autore = 'Smith'"), l'operazione interesserà i record visibili nel capitolo corrente.<br /><br /> Se il **filtro** è impostata su un membro del [FilterGroupEnum](../../../ado/reference/ado-api/filtergroupenum.md) o una matrice di segnalibri, quindi l'operazione verrà applicate a tutte le righe del **Recordset**. **Nota:****adAffectAll** è nascosto nel Visualizzatore oggetti Visual Basic.  |  
|**adAffectAllChapters**|4|Interessa tutti i record in tutti i capitoli di pari livello di **Recordset**, inclusi quelli non visibili tramite qualsiasi **filtro** attualmente applicato.|  
|**adAffectCurrent**|1|Interessa solo il record corrente.|  
|**adAffectGroup**|2|Interessa solo i record che soddisfano corrente [filtro](../../../ado/reference/ado-api/filter-property.md) l'impostazione della proprietà. È necessario impostare il **filtro** proprietà per un **FilterGroupEnum** valore o una matrice di **segnalibri** per utilizzare questa opzione.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC equivalente  
 Pacchetto: **com.ms. wfc.**  
  
|Costante|  
|--------------|  
|AdoEnums.Affect.ALL|  
|AdoEnums.Affect.ALLCHAPTERS|  
|AdoEnums.Affect.CURRENT|  
|AdoEnums.Affect.GROUP|  
  
## <a name="applies-to"></a>Si applica a  
  
|||  
|-|-|  
|[Metodo CancelBatch (ADO)](../../../ado/reference/ado-api/cancelbatch-method-ado.md)|[Delete (metodo) (Recordset ADO)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)|  
|[Risincronizzazione (metodo)](../../../ado/reference/ado-api/resync-method.md)|[Metodo UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)|
