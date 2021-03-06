---
title: Comando SQL - DELETE | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- DELETE [ODBC]
ms.assetid: 0d5bd477-626f-4f22-a05a-f531d9f8c5e7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 674c2d9d259d09456bc97edc4a6b9e842f9a4519
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47676199"
---
# <a name="delete---sql-command"></a>DELETE (comando SQL)
Contrassegna i record per l'eliminazione.  
  
 Il Driver ODBC Visual FoxPro supporta la sintassi del linguaggio Visual FoxPro nativa per questo comando. Per informazioni specifiche del driver, vedere la sezione Osservazioni.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DELETE FROM [DatabaseName!]TableName  
   [WHERE FilterCondition1 [AND | OR FilterCondition2 ...]]  
```  
  
## <a name="arguments"></a>Argomenti  
 DA [ *DatabaseName!*] *TableName*  
 Specifica la tabella in cui i record sono contrassegnati per l'eliminazione.  
  
 *DatabaseName!* Specifica il nome di un database contenente la tabella se il database che lo contiene non è il database specificato con l'origine dati. È necessario includere il nome di un database contenente la tabella se il database non è il database specificato con l'origine dati. Includere il delimitatore punto esclamativo (!) dopo il nome del database e prima del nome di tabella.  
  
 In cui *FilterCondition1*[AND &#124; oppure *FilterCondition2*...]  
 Specifica che Visual FoxPro contrassegnare determinati record per l'eliminazione.  
  
 *FilterCondition* specifica i criteri che i record devono soddisfare per essere contrassegnato per l'eliminazione. È possibile includere le condizioni di filtro desiderati, connetterle con l'operatore AND o l'operatore OR. È anche possibile usare l'operatore NOT per invertire il valore di un'espressione logica oppure è possibile usare **vuoto**() per verificare la presenza di un campo vuoto.  
  
## <a name="remarks"></a>Note  
 Se SET DELETED è impostata su ON, i record contrassegnati per l'eliminazione vengono ignorati da tutti i comandi che includono un ambito.  
  
 DELETE - utilizzi SQL blocco del record quando si contrassegna più record per l'eliminazione nelle tabelle aperto per l'accesso condiviso. Questo riduce la contesa dei record in situazioni multiutente ma può ridurre le prestazioni. Per ottenere prestazioni ottimali, aprire la tabella per l'uso esclusivo.  
  
## <a name="driver-remarks"></a>Sezione Osservazioni di driver  
 Quando l'applicazione invia l'istruzione ODBC SQL DELETE nell'origine dati, il Driver ODBC Visual FoxPro converte il comando al comando Visual FoxPro DELETE senza la conversione.  
  
## <a name="see-also"></a>Vedere anche  
 [SET DELETED (comando)](../../odbc/microsoft/set-deleted-command.md)
