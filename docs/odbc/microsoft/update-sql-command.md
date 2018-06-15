---
title: Comando SQL UPDATE - | Documenti Microsoft
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
- update [ODBC]
ms.assetid: ff1e0331-c060-4304-b280-039725b45f63
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 748a405ba63fb934eee162d3cc023b5935251cea
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32908676"
---
# <a name="update---sql-command"></a>Comando SQL UPDATE-
Aggiorna i record in una tabella con i nuovi valori.  
  
 Il Driver ODBC di Visual FoxPro supporta la sintassi del linguaggio Visual FoxPro native per questo comando. Per informazioni specifiche del driver, vedere **Driver osservazioni**.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
UPDATE [DatabaseName1!]TableName1  
SET Column_Name1 = eExpression1  
   [, Column_Name2 = eExpression2 ...]  
   WHERE FilterCondition1 [AND | OR FilterCondition2 ...]  
```  
  
## <a name="arguments"></a>Argomenti  
 AGGIORNAMENTO [ *DatabaseName1!*] *TableName1*  
 Specifica la tabella in cui vengono aggiornati i record con nuovi valori.  
  
 *DatabaseName1!* Specifica il nome di un database diverso da quello specificato con l'origine dati contenente la tabella. È necessario includere il nome del database contenente la tabella, se il database non è quello corrente. Include il delimitatore punto esclamativo (!) dopo il nome del database e prima del nome di tabella.  
  
 IMPOSTARE *Column_Name1*= *eExpression1*[, *Column_Name2*= *eExpression2*  
 Specifica le colonne che vengono aggiornate e i nuovi valori. Se si omette la clausola WHERE, ogni riga nella colonna viene aggiornata con lo stesso valore.  
  
 In cui *FilterCondition1*[AND &#124; o *FilterCondition2*...]  
 Specifica i record che vengono aggiornati con nuovi valori.  
  
 *FilterCondition* specifica i criteri che i record devono soddisfare per essere aggiornati con nuovi valori. È possibile includere molte condizioni di filtro nel modo desiderato, la connessione con l'operatore AND o OR (operatore). È inoltre possibile utilizzare l'operatore NOT per invertire il valore di un'espressione logica, o è possibile utilizzare **vuoto**() per verificare la presenza di un campo vuoto.  
  
## <a name="remarks"></a>Osservazioni  
 UPDATE - è possibile aggiornare solo i record in una singola tabella SQL.  
  
 A differenza di sostituzione, aggiornamento di SQL - utilizza blocco dei record durante l'aggiornamento di più record nelle tabelle aperto per l'accesso condiviso. Questo riduce la contesa dei record in situazioni multiutente, ma può ridurre le prestazioni. Per ottenere prestazioni ottimali, aprire la tabella per esclusivo utilizzare o **gruppo**() per bloccare la tabella.  
  
## <a name="driver-remarks"></a>Sezione Osservazioni di driver  
 Quando l'applicazione invia l'istruzione ODBC SQL UPDATE all'origine dati, il Driver ODBC di Visual FoxPro converte il comando al comando FoxProUPDATE Visual senza conversione.  
  
## <a name="see-also"></a>Vedere anche  
 [DELETE - comando SQL](../../odbc/microsoft/delete-sql-command.md)   
 [INSERT (comando SQL)](../../odbc/microsoft/insert-sql-command.md)
