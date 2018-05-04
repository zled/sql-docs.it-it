---
title: sp_cursoroption (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_cursoroption_TSQL
- sp_cursoroption
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cursoroption
ms.assetid: 88fc1dba-f4cb-47c0-92c2-bf398f4a382e
caps.latest.revision: 8
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: f349e89d77b3eb0112db81588c09025bbf4e6ed7
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="spcursoroption-transact-sql"></a>sp_cursoroption (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Imposta le opzioni del cursore o restituisce informazioni sul cursore create dalla routine sp_cursoropen archiviati. è possibile richiamare sp_cursoroption specificando ID = 8 in un pacchetto del flusso TDS.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_cursoroption cursor, code, value  
```  
  
## <a name="arguments"></a>Argomenti  
 *cursor*  
 È un *gestire* valore generato da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e restituito dalla routine sp_cursoropen archiviati. *cursore* richiede un' **int** valore per l'esecuzione di input.  
  
 *Codice*  
 Consente di specificare i vari fattori dei valori restituiti del cursore. *codice* richiede uno dei seguenti **int** valori di input:  
  
|Value|Nome|Description|  
|-----------|----------|-----------------|  
|0x0001|TEXTPTR_ONLY|Restituisce il puntatore di testo, anziché i dati effettivi, per determinate colonne di tipo text o image designate.<br /><br /> TEXTPTR_ONLY consente i puntatori di testo da utilizzare come *handle* per gli oggetti blob che successivamente possono essere recuperati in modo selettivo o aggiornata mediante [!INCLUDE[tsql](../../includes/tsql-md.md)] o funzionalità DBLIB (ad esempio, [!INCLUDE[tsql](../../includes/tsql-md.md)] READTEXT o DBLIB DBWRITETEXT).<br /><br /> Se viene assegnato il valore "0", tutte le colonne di tipo text e image nell'elenco di selezione restituiranno puntatori di testo anziché dati.|  
|0x0002|CURSOR_NAME|Assegna il nome specificato *valore* fino al cursore. A sua volta, consente di utilizzare ODBC [!INCLUDE[tsql](../../includes/tsql-md.md)] posizionate le istruzioni di aggiornamento/eliminazione sui cursori aperti mediante sp_cursoropen.<br /><br /> La stringa può essere specificata come qualsiasi tipo di dati Unicode o character.<br /><br /> Poiché [!INCLUDE[tsql](../../includes/tsql-md.md)] le istruzioni UPDATE/DELETE posizionate operano, per impostazione predefinita, nella prima riga nel caso di un cursore sp_cursor SETPOSITION deve essere utilizzato per posizionare il cursore prima di eseguire l'istruzione UPDATE/DELETE posizionata.|  
|0x0003|TEXTDATA|Restituisce i dati effettivi, anziché il puntatore di testo, per determinate colonne di tipo text o image in recuperi successivi, ovvero annulla l'effetto di TEXTPTR_ONLY.<br /><br /> Se per una colonna specifica è abilitato TEXTDATA, la riga viene nuovamente recuperata o aggiornata e può quindi essere nuovamente impostata su TEXTPTR_ONLY. Analogamente a quanto accade per TEXTPTR_ONLY, il parametro di valore è un intero che specifica il numero di colonna e un valore zero restituisce tutte le colonne di tipo text o image.|  
|0x0004|SCROLLOPT|Opzione di scorrimento. Per ulteriori informazioni, vedere "Valori dei codici restituiti" più avanti in questo argomento.|  
|0x0005|CCOPT|Opzioni del controllo della concorrenza. Per ulteriori informazioni, vedere "Valori dei codici restituiti" più avanti in questo argomento.|  
|0x0006|ROWCOUNT|Numero di righe correntemente nel set di risultati.<br /><br /> Nota: È possibile che ROWCOUNT sia modificato rispetto al valore restituito da sp_cursoropen, se viene utilizzato il popolamento asincrono. Se il numero di righe non è noto, viene restituito -1.|  
  
 *Valore*  
 Definisce il valore restituito da *codice*. *valore* è un parametro obbligatorio che richiede un 0x0001, 0x0002 o 0x0003 *codice* valore di input.  
  
> [!NOTE]  
>  Oggetto *codice* valore 2 è un tipo di dati stringa. Qualsiasi altro *codice* valore di input o restituito da *valore* è un numero intero.  
  
## <a name="return-code-values"></a>Valori restituiti  
 Il *valore* parametro può restituire uno dei seguenti *codice* valori.  
  
|Valore restituito|Description|  
|------------------|-----------------|  
|0x0004|SCROLLOPT|  
|0X0005|CCOPT|  
|0X0006|ROWCOUNT|  
  
 Il *valore* parametro restituisce uno dei valori di SCROLLOPT seguenti.  
  
|Valore restituito|Description|  
|------------------|-----------------|  
|0x0001|KEYSET|  
|0x0002|DYNAMIC|  
|0x0004|FORWARD_ONLY|  
|0x0008|STATIC|  
  
 Il *valore* parametro restituisce uno dei valori di CCOPT seguenti.  
  
|Valore restituito|Description|  
|------------------|-----------------|  
|0x0001|READ_ONLY|  
|0x0002|SCROLL_LOCKS|  
|0x0004 o 0x0008|OPTIMISTIC|  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sp_cursor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-cursor-transact-sql.md)   
 [sp_cursoropen &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-cursoropen-transact-sql.md)  
  
  
