---
title: Comando SQL - DELETE | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- DELETE [ODBC]
ms.assetid: 0d5bd477-626f-4f22-a05a-f531d9f8c5e7
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9e00f1d819f792f88ffb4495385be5abd754af21
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
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
  
 In cui *FilterCondition1*[AND &#124; o *FilterCondition2*...]  
 Specifica che Visual FoxPro contrassegnare determinati record per l'eliminazione.  
  
 *FilterCondition* specifica i criteri che i record devono soddisfare per essere contrassegnato per l'eliminazione. È possibile includere molte condizioni di filtro desiderati, la connessione con l'operatore AND o OR (operatore). È inoltre possibile utilizzare l'operatore NOT per invertire il valore di un'espressione logica, o è possibile utilizzare **vuoto**() per verificare la presenza di un campo vuoto.  
  
## <a name="remarks"></a>Osservazioni  
 Se impostato eliminato è impostato su ON, i record contrassegnati per l'eliminazione vengono ignorati da tutti i comandi che includono un ambito.  
  
 DELETE - utilizza SQL blocco del record quando si contrassegna più record per l'eliminazione nelle tabelle aperto per l'accesso condiviso. Questo riduce la contesa dei record in situazioni multiutente, ma può ridurre le prestazioni. Per ottenere prestazioni ottimali, aprire la tabella per l'uso esclusivo.  
  
## <a name="driver-remarks"></a>Sezione Osservazioni di driver  
 Quando l'applicazione invia l'istruzione ODBC SQL DELETE all'origine dati, il Driver ODBC di Visual FoxPro converte il comando al comando di Visual FoxPro eliminare senza conversione.  
  
## <a name="see-also"></a>Vedere anche  
 [SET DELETED (comando)](../../odbc/microsoft/set-deleted-command.md)
