---
title: CommandTypeEnum | Documenti Microsoft
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
- CommandTypeEnum
helpviewer_keywords:
- CommandTypeEnum enumeration [ADO]
ms.assetid: 4b1feb9c-a855-40fe-a906-efe688687e9f
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 09f6a05473c8acc47f600acd8a8858f99aeef00e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="commandtypeenum"></a>CommandTypeEnum
Specifica la modalità di interpretazione di un argomento del comando.  
  
 È importante convalidare fornito dall'utente *CommandString* valori per evitare che gli utenti dell'applicazione la possibilità di inserire comandi potenzialmente pericolosi per ADO eseguire.  
  
|Costante|Value|Description|  
|--------------|-----------|-----------------|  
|**adCmdUnspecified**|-1|Non specificare l'argomento di tipo di comando.|  
|**adCmdText**|1|Valuta [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) come una definizione testuale di un comando o stored procedure chiamata.|  
|**adCmdTable**|2|Valuta **CommandText** come un nome di tabella le cui colonne vengono restituite da una query SQL generata internamente.|  
|**adCmdStoredProc**|4|Valuta **CommandText** come nome di una stored procedure.|  
|**adCmdUnknown**|8|Valore predefinito. Indica che il tipo di comando di **CommandText** proprietà non è noto.<br /><br /> Quando il tipo di comando non è noto, ADO effettua diversi tentativi per interpretare il **CommandText**.<br /><br /> -   **CommandText** viene interpretato come una definizione testuale di una chiamata di comando o stored procedure. Questo è lo stesso comportamento di **adCmdText**.<br />-   **CommandText** è il nome di una stored procedure. Questo è lo stesso comportamento di **adCmdStoredProc**.<br />-   **CommandText** viene interpretato come il nome di una tabella. Vengono restituite tutte le colonne da una query SQL generata internamente. Questo è lo stesso comportamento di **adCmdTable**.|  
|**adCmdFile**|256|Valuta **CommandText** come il nome del file di memorizzato in modo permanente [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md). Utilizzato con **Recordset.** [Aprire](../../../ado/reference/ado-api/open-method-ado-recordset.md) o [Requery](../../../ado/reference/ado-api/requery-method.md) solo.|  
|**adCmdTableDirect**|512|Valuta **CommandText** come un nome di tabella le cui colonne vengono tutte restituite. Utilizzato con **Open** o **Requery** solo. Utilizzare il [Seek](../../../ado/reference/ado-api/seek-method.md) (metodo), il **Recordset** deve essere aperto con **adCmdTableDirect**.<br /><br /> Questo valore non può essere combinato con il [ExecuteOptionEnum](../../../ado/reference/ado-api/executeoptionenum.md) valore **adAsyncExecute**.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC equivalente  
 Package: **com.ms.wfc.data**  
  
|Costante|  
|--------------|  
|AdoEnums.CommandType.UNSPECIFIED|  
|AdoEnums.CommandType.TEXT|  
|AdoEnums.CommandType.TABLE|  
|AdoEnums.CommandType.STOREDPROC|  
|AdoEnums.CommandType.UNKNOWN|  
|AdoEnums.CommandType.FILE|  
|AdoEnums.CommandType.TABLEDIRECT|  
  
## <a name="applies-to"></a>Si applica a  
  
|||  
|-|-|  
|[Proprietà CommandType (ADO)](../../../ado/reference/ado-api/commandtype-property-ado.md)|[Metodo Execute (comando ADO)](../../../ado/reference/ado-api/execute-method-ado-command.md)|  
|[Metodo Execute (connessione ADO)](../../../ado/reference/ado-api/execute-method-ado-connection.md)|[Metodo Open (Recordset ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md)|  
|[Metodo Requery](../../../ado/reference/ado-api/requery-method.md)||
