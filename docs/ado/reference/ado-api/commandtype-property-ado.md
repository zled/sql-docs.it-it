---
title: "La proprietà CommandType (ADO) | Documenti Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Command15::CommandType
helpviewer_keywords:
- CommandType property [ADO]
ms.assetid: ca44809c-8647-48b6-a7fb-0be70a02f53e
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d670a188c89ed96001c93d17a33dc0c03d601a82
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="commandtype-property-ado"></a>Proprietà CommandType (ADO)
Indica il tipo di un [comando](../../../ado/reference/ado-api/command-object-ado.md) oggetto.  
  
## <a name="settings-and-return-values"></a>Le impostazioni e valori restituiti  
 Imposta o restituisce uno o più [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md) valori.  
  
> [!NOTE]
>  Non utilizzare il **CommandTypeEnum** valori di **adCmdFile** o **adCmdTableDirect** con **CommandType**. Questi valori possono essere utilizzati solo come opzioni con il [aprire](../../../ado/reference/ado-api/open-method-ado-recordset.md) e [Requery](../../../ado/reference/ado-api/requery-method.md) metodi di un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare il **CommandType** proprietà per ottimizzare la valutazione del [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) proprietà.  
  
 Se il **CommandType** valore della proprietà è impostato sul valore predefinito, **adCmdUnknown**, si potrebbe effetti negativi sulle prestazioni poiché ADO deve eseguire chiamate al provider per determinare se il  **CommandText** proprietà è un'istruzione SQL, una stored procedure o un nome di tabella. Se si conosce il tipo di comando in uso, l'impostazione di **CommandType** proprietà indica ad ADO per passare direttamente al codice pertinente. Se il **CommandType** proprietà non corrisponde al tipo di comando nel **CommandText** proprietà, un errore si verifica quando si chiama il [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md) metodo.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di proprietà direzione (VB), CommandText, CommandTimeout, CommandType, dimensioni e ActiveConnection](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vb.md)   
 [Esempio di proprietà direzione (VC + +), CommandText, CommandTimeout, CommandType, dimensioni e ActiveConnection](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vc.md)   
 [ActiveConnection, CommandText, CommandTimeout, CommandType, dimensioni e direzione proprietà esempio (JScript)](../../../ado/reference/ado-api/activeconnection-commandtext-timeout-type-size-example-jscript.md)

