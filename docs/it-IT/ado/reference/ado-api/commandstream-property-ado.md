---
title: La proprietà CommandStream (ADO) | Documenti Microsoft
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
- _Command::CommandStream
helpviewer_keywords:
- CommandStream property [ADO]
ms.assetid: f78f61b6-87e0-48dc-961e-83d0e20da58e
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d7bfaf04f8be778aac51d08c93eb9e9b7290b8df
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="commandstream-property-ado"></a>Proprietà CommandStream (ADO)
Indica il flusso utilizzato come input per un [comando](../../../ado/reference/ado-api/command-object-ado.md) oggetto.  
  
## <a name="settings-and-return-values"></a>Le impostazioni e valori restituiti  
 Imposta o restituisce il flusso utilizzato come input per un **comando** oggetto. Il formato per il flusso è specifico del provider; vedere la documentazione del provider per ulteriori informazioni. Questa proprietà è simile al [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) proprietà, che consente di specificare una stringa per l'input di un **comando**.  
  
## <a name="remarks"></a>Osservazioni  
 **CommandStream** e **CommandText** si escludono a vicenda. Quando l'utente imposta il **CommandStream** proprietà, il **CommandText** verrà impostata su una stringa vuota (""). Se l'utente imposta il **CommandText** proprietà, il **CommandStream** verrà impostata su **nulla**.  
  
 I comportamenti del **Command.Parameters.Refresh** e **Command. Prepare** metodi definiti dal provider. I valori dei parametri in un flusso non possono essere aggiornati.  
  
 Il flusso di input non è disponibile ad altri oggetti ADO che restituiscono l'origine di un **comando**. Ad esempio, se il [origine](../../../ado/reference/ado-api/source-property-ado-recordset.md) di un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) è impostata su un **comando** oggetto che dispone di un flusso come input, **Recordset.Source** continua a restituire il **CommandText** proprietà, che contiene una stringa vuota (""), anziché il contenuto del flusso di **CommandStream** proprietà.  
  
 Quando si utilizza un flusso del comando (come specificato da **CommandStream**), valido solo [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md) valori per il [CommandType](../../../ado/reference/ado-api/commandtype-property-ado.md) sono proprietà  **adCmdText** e **adCmdUnknown**. Qualsiasi altro valore causa un errore.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà CommandText (ADO)](../../../ado/reference/ado-api/commandtext-property-ado.md)   
 [Proprietà Dialect](../../../ado/reference/ado-api/dialect-property.md)   
 [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md)
