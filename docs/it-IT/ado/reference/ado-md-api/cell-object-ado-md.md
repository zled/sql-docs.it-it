---
title: Cella di oggetti (ADO MD) | Documenti Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Cell
helpviewer_keywords:
- Cell object [ADO MD]
ms.assetid: dcc2f044-b785-4a29-9bc5-b673f66eedf9
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0f5af34c1a1d9a5069eac830eab8d9be8020176a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="cell-object-ado-md"></a>Oggetto Cell (ADO MD)
Rappresenta i dati in corrispondenza dell'intersezione delle coordinate dell'asse contenuti in un set di celle.  
  
## <a name="remarks"></a>Osservazioni  
 Oggetto **cella** viene restituito dal [elemento](../../../ado/reference/ado-md-api/item-property-ado-md-cellset.md) proprietà di un [set di celle](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) oggetto.  
  
 Raccolte e le proprietà di un **cella** dell'oggetto, è possibile eseguire le operazioni seguenti:  
  
-   Restituire i dati di **cella** con il [valore](../../../ado/reference/ado-md-api/value-property-ado-md.md) proprietà.  
  
-   Restituire la stringa che rappresenta la visualizzazione formattata del **valore** proprietà con il [FormattedValue](../../../ado/reference/ado-md-api/formattedvalue-property-ado-md.md) proprietà.  
  
-   Restituisce il valore ordinale del **cella** all'interno di **set di celle** con il [ordinale](../../../ado/reference/ado-md-api/ordinal-property-ado-md-cell.md) proprietà.  
  
-   Determinare la posizione del **cella** all'interno di [CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md) con il [posizioni](../../../ado/reference/ado-md-api/positions-collection-ado-md.md) insieme.  
  
-   Recuperare le informazioni relative la **cella** con ADO standard [proprietà](../../../ado/reference/ado-api/properties-collection-ado.md) insieme.  
  
 Il **proprietà** insieme contiene le proprietà specifiche del provider. Nella tabella seguente sono elencate le proprietà che potrebbero essere disponibili. L'elenco di proprietà effettivo può variare in base all'implementazione del provider. Vedere la documentazione del provider per un elenco completo delle proprietà disponibili.  
  
|Nome|Description|  
|----------|-----------------|  
|ColoreSfondo|Colore di sfondo utilizzato per la visualizzazione della cella.|  
|FontFlags|Maschera di bit in dettaglio gli effetti sul tipo di carattere.|  
|TipoCarattere|Tipo di carattere utilizzato per visualizzare il valore della cella.|  
|FontSize|Dimensioni del carattere utilizzata per visualizzare il valore della cella.|  
|ColorePrimoPiano|Colore di primo piano utilizzato per la visualizzazione della cella.|  
|FormatString|Valore di una stringa formattata.|  
  
 In questa sezione contiene l'argomento seguente.  
  
-   [Proprietà, metodi ed eventi](../../../ado/reference/ado-md-api/cell-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di asse (VBScript)](../../../ado/reference/ado-md-api/axis-example-vbscript.md)   
 [Oggetto Cellset (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)   
 [Raccolta di posizioni (ADO MD)](../../../ado/reference/ado-md-api/positions-collection-ado-md.md)   
 [Raccolta delle proprietà (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
