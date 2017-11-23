---
title: "Proprietà SQLState | Documenti Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Error::GetSQLState
- Error::SQLState
- Error::get_SQLState
helpviewer_keywords: SQLState property
ms.assetid: f9e25967-54b0-444d-af2a-0d2c75365d3e
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e6709e1e538db77b1aed5b281ffd826d90448daf
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="sqlstate-property"></a>Proprietà SQLState
Indica lo stato SQL per un determinato [errore](../../../ado/reference/ado-api/error-object.md) oggetto.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un carattere di cinque **stringa** valore conforme allo standard ANSI SQL e indica il codice di errore.  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare il **SQLState** proprietà per leggere il codice di errore di cinque caratteri che il provider restituisce quando si verifica un errore durante l'elaborazione di un'istruzione SQL. Ad esempio, quando si utilizza il Provider Microsoft OLE DB per ODBC con un database di Microsoft SQL Server, i codici di errore di stato SQL provengono da ODBC, in base agli errori specifici di ODBC o sugli errori che derivano da Microsoft SQL Server e quindi vengono eseguito il mapping a ODBC errori. Questi codici di errore sono documentati in standard ANSI SQL, ma possono essere implementati in modo diverso da origini dati diverse.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Error](../../../ado/reference/ado-api/error-object.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di proprietà SQLState (VB), HelpContext, HelpFile, NativeError, numero, origine e descrizione](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Esempio di proprietà SQLState (VC + +), HelpContext, HelpFile, NativeError, numero, origine e descrizione](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
