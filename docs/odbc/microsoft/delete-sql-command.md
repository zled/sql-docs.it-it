---
title: Comando SQL - DELETE | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DELETE [ODBC]
ms.assetid: 0d5bd477-626f-4f22-a05a-f531d9f8c5e7
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8effde0f80a219f11af460bdc941a9b6d9681455
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="delete---sql-command"></a>DELETE - comando SQL
Contrassegna i record per l'eliminazione.  
  
 Il Driver ODBC di Visual FoxPro supporta la sintassi del linguaggio Visual FoxPro native per questo comando. Per informazioni specifiche del driver, vedere la sezione Osservazioni.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DELETE FROM [DatabaseName!]TableName  
   [WHERE FilterCondition1 [AND | OR FilterCondition2 ...]]  
```  
  
## <a name="arguments"></a>Argomenti  
 DA [ *DatabaseName!*] *TableName*  
 Specifica la tabella in cui i record sono contrassegnati per l'eliminazione.  
  
 *DatabaseName!* Specifica il nome di un database che contiene la tabella, se il database che lo contiene non è il database specificato con l'origine dati. È necessario includere il nome di un database che contiene la tabella, se il database non è il database specificato con l'origine dati. Include il delimitatore punto esclamativo (!) dopo il nome del database e prima del nome di tabella.  
  
 DOVE *FilterCondition1*[AND &#124; O *FilterCondition2*...]  
 Specifica che Visual FoxPro contrassegnare determinati record per l'eliminazione.  
  
 *FilterCondition* specifica i criteri che i record devono soddisfare per essere contrassegnato per l'eliminazione. È possibile includere molte condizioni di filtro desiderati, la connessione con l'operatore AND o OR (operatore). È inoltre possibile utilizzare l'operatore NOT per invertire il valore di un'espressione logica, o è possibile utilizzare **vuoto**() per verificare la presenza di un campo vuoto.  
  
## <a name="remarks"></a>Osservazioni  
 Se impostato eliminato è impostato su ON, i record contrassegnati per l'eliminazione vengono ignorati da tutti i comandi che includono un ambito.  
  
 DELETE - utilizza SQL blocco del record quando si contrassegna più record per l'eliminazione nelle tabelle aperto per l'accesso condiviso. Questo riduce la contesa dei record in situazioni multiutente, ma può ridurre le prestazioni. Per ottenere prestazioni ottimali, aprire la tabella per l'uso esclusivo.  
  
## <a name="driver-remarks"></a>Sezione Osservazioni di driver  
 Quando l'applicazione invia l'istruzione ODBC SQL DELETE all'origine dati, il Driver ODBC di Visual FoxPro converte il comando al comando di Visual FoxPro eliminare senza conversione.  
  
## <a name="see-also"></a>Vedere anche  
 [Comando DELETED SET](../../odbc/microsoft/set-deleted-command.md)
