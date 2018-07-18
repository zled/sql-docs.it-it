---
title: ConnectModeEnum | Documenti Microsoft
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
- ConnectModeEnum
helpviewer_keywords:
- ConnectModeEnum enumeration [ADO]
ms.assetid: 3792c294-5161-4538-a908-22a5fc50b85f
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 94b89e379d85002fc58deb36a1b95d1b7457d4c8
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35277090"
---
# <a name="connectmodeenum"></a>ConnectModeEnum
Specifica le autorizzazioni disponibili per la modifica dei dati in un [connessione](../../../ado/reference/ado-api/connection-object-ado.md), aprire un [Record](../../../ado/reference/ado-api/record-object-ado.md), o specificando i valori per il [modalità](../../../ado/reference/ado-api/mode-property-ado.md) proprietà del  **Record** e [flusso](../../../ado/reference/ado-api/stream-object-ado.md) oggetti.  
  
|Costante|valore|Description|  
|--------------|-----------|-----------------|  
|**adModeRead**|1|Indica le autorizzazioni di sola lettura.|  
|**adModeReadWrite**|3|Indica le autorizzazioni di lettura/scrittura.|  
|**adModeRecursive**|0x400000|Usato in combinazione con le altre *\*ShareDeny\** valori (**adModeShareDenyNone**, **adModeShareDenyWrite**, o **adModeShareDenyRead**) per propagare le limitazioni di condivisione per tutti i corrente **Record**. Non produce alcun effetto se la **Record** non dispone di alcun elemento figlio. Viene generato un errore di run-time se utilizzato con **adModeShareDenyNone** solo. Tuttavia, può essere utilizzato con **adModeShareDenyNone** quando combinato con altri valori. Ad esempio, è possibile utilizzare "**adModeRead** o **adModeShareDenyNone** o **adModeRecursive**".|  
|**adModeShareDenyNone**|16|Consente ad altri utenti di aprire una connessione con le autorizzazioni. Impossibile negare l'accesso in lettura e in scrittura ad altri.|  
|**adModeShareDenyRead**|4|Impedisce ad altri l'apertura di una connessione con autorizzazioni di lettura.|  
|**adModeShareDenyWrite**|8|Impedisce ad altri l'apertura di una connessione con autorizzazioni di scrittura.|  
|**adModeShareExclusive**|12|Impedisce ad altri l'apertura di una connessione.|  
|**adModeUnknown**|0|Valore predefinito. Indica che le autorizzazioni non sono ancora state impostate o non possono essere determinate.|  
|**adModeWrite**|2|Indica le autorizzazioni di sola scrittura.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC equivalente  
 Package: **com.ms.wfc.data**  
  
|Costante|  
|--------------|  
|AdoEnums.ConnectMode.READ|  
|AdoEnums.ConnectMode.READWRITE|  
|(È disponibile un equivalente di AdoEnums.ConnectMode.RECURSIVE)|  
|AdoEnums.ConnectMode.SHAREDENYNONE|  
|AdoEnums.ConnectMode.SHAREDENYREAD|  
|AdoEnums.ConnectMode.SHAREDENYWRITE|  
|AdoEnums.ConnectMode.SHAREEXCLUSIVE|  
|AdoEnums.ConnectMode.UNKNOWN|  
|AdoEnums.ConnectMode.WRITE|  
  
## <a name="applies-to"></a>Si applica a  
  
|||  
|-|-|  
|[Proprietà Mode (ADO)](../../../ado/reference/ado-api/mode-property-ado.md)|[Metodo Open (record ADO)](../../../ado/reference/ado-api/open-method-ado-record.md)|  
|[Metodo Open (flusso ADO)](../../../ado/reference/ado-api/open-method-ado-stream.md)|[Oggetto Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)|
