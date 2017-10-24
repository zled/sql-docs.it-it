---
title: "Proprietà Dialect | Documenti Microsoft"
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
- _Command::Dialect
helpviewer_keywords:
- Dialect property
ms.assetid: 329c3a71-ba88-4009-b04f-2f52195a5957
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 73c7dfd6fe5aec706d5e27ce6d55f489285748c4
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="dialect-property"></a>Proprietà Dialect
Indica il sottolinguaggio di [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) o [CommandStream](../../../ado/reference/ado-api/commandstream-property-ado.md) proprietà. Il sottolinguaggio definisce la sintassi e regole generali che il provider utilizzato per analizzare la stringa o nel flusso.  
  
## <a name="settings-and-return-values"></a>Le impostazioni e valori restituiti  
 Il **sottolinguaggio** proprietà contiene un GUID valido che rappresenta il sottolinguaggio del comando testo o del flusso. Il valore predefinito per questa proprietà è {C8B521FB-5CF3-11CE-ADE5-00AA0044773D}, che indica che il provider deve scegliere come interpretare il testo del comando o nel flusso.  
  
## <a name="remarks"></a>Osservazioni  
 ADO non esegue la query il provider quando l'utente legge il valore di questa proprietà. Restituisce una rappresentazione di stringa del valore attualmente archiviato nel [comando](../../../ado/reference/ado-api/command-object-ado.md) oggetto.  
  
 Quando l'utente imposta il **sottolinguaggio** convalida il GUID di proprietà, ADO e genera un errore se il valore fornito non è un GUID valido. Vedere la documentazione relativa al provider per determinare i valori GUID supportati dal **sottolinguaggio** proprietà.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Eseguire il metodo (comando ADO)](../../../ado/reference/ado-api/execute-method-ado-command.md)

