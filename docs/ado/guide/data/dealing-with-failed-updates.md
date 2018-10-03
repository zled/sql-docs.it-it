---
title: Gestione degli aggiornamenti non riusciti | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- updates [ADO], dealing with failed updates
ms.assetid: 299c37bd-19ff-4261-8571-b9665687e075
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6ba4b4189691bf907b3ad67db91a8534268a8ec0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47616429"
---
# <a name="dealing-with-failed-updates"></a>Gestione degli aggiornamenti non riusciti
Quando un aggiornamento si conclude con errori, come è risolvere gli errori dipende la natura e la gravità degli errori e la logica dell'applicazione. Tuttavia, se il database è condiviso con altri utenti, un errore tipico è che un altro utente modifica il campo prima di procedere. Questo tipo di errore viene chiamato un conflitto. ADO rileva questa condizione e segnala un errore.  
  
## <a name="remarks"></a>Note  
 Se sono presenti errori di aggiornamento, questi verranno intercettati in una routine di gestione degli errori. Filtrare il Recordset con la costante adFilterConflictingRecords in modo che siano visibili solo le righe in conflitto. In questo esempio, la strategia di risoluzione dell'errore è semplicemente l'autore di stampare nome e cognome (au_fname e au_lname).  
  
 Il codice per avvisare l'utente per il conflitto di aggiornamento è simile alla seguente:  
  
```  
objRs.Filter = adFilterConflictingRecords  
objRs.MoveFirst  
Do While Not objRst.EOF  
   Debug.Print "Conflict: Name =  "; objRs!au_fname; " "; objRs!au_lname  
   objRs.MoveNext  
Loop  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Modalità batch](../../../ado/guide/data/batch-mode.md)
