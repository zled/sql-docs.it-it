---
title: "Modalità di uso di FOR JSON delle sequenze di escape per i caratteri speciali e di controllo (SQL Server) | Microsoft Docs"
ms.custom: SQL2016_New_Updated
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: dbe-json
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: FOR JSON, special characters
ms.assetid: 4ba90025-5a09-4f0a-836a-54c886324530
caps.latest.revision: "16"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 02544dc43daaf3bc56ad78126b37c6653a770bda
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="how-for-json-escapes-special-characters-and-control-characters-sql-server"></a>Modalità di uso di FOR JSON delle sequenze di escape per i caratteri speciali e di controllo (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Questo argomento descrive il modo in cui la clausola **FOR JSON** di un'istruzione **SELECT** di SQL Server usa sequenze di escape per i caratteri speciali e rappresenta i caratteri di controllo nell'output JSON.  

> [!IMPORTANT]
> Questa pagina descrive il supporto incorporato per JSON in Microsoft SQL Server. Per informazioni generali sull'uso delle sequenze di escape e la codifica in JSON, vedere sezione la sezione 2.5 della specifica JSON RFC - [http://www.ietf.org/rfc/rfc4627.txt](http://www.ietf.org/rfc/rfc4627.txt).

## <a name="escaping-of-special-characters"></a>Escape di caratteri speciali  
Se i dati di origine contengono caratteri speciali, la clausola **FOR JSON** usa sequenze di escape per tali caratteri nell'output JSON con `\`, come illustrato nella tabella seguente. I caratteri di escape vengono usati sia nei nomi delle proprietà che nei relativi valori.  
  
|**Carattere speciale**|**Output con caratteri di escape**|  
|---------------------------|--------------------------|  
|Virgoletta (")|\\"|  
|Barra rovesciata (\\)|\\\|  
|Barra (/)|\\/|  
|Backspace|\b|  
|Avanzamento carta|\f|  
|Nuova riga|\n|  
|Ritorno a capo|\r|  
|Tabulazione orizzontale|\t|  
  
## <a name="control-characters"></a>Caratteri di controllo  
Se i dati di origine contengono caratteri di controllo, la clausola **FOR JSON** codifica tali caratteri nell'output JSON nel formato `\u<code>`, come illustrato nella tabella seguente.  
  
|**Carattere di controllo**|**Output codificato**|  
|---------------------------|--------------------------|  
|CHAR(0)|\u0000|  
|CHAR(1)|\u0001|  
|…|…|  
|CHAR(31)|\u001f|  
  
## <a name="example"></a>Esempio  
 Di seguito è riportato un esempio dell'output di **FOR JSON** per dati di origine che includono sia caratteri di escape che caratteri di controllo.  
  
 Query:  
  
```sql  
SELECT  
  'VALUE\    /  
  "' as [KEY\/"],  
  CHAR(0) as '0',  
  CHAR(1) as '1',  
  CHAR(31) as '31'  
FOR JSON PATH  
```  
  
 Risultato:  
  
```json  
{
    "KEY\\\t\/\"": "VALUE\\\t\/\r\n\"",
    "0": "\u0000",
    "1": "\u0001",
    "31": "\u001f"
}
```  

## <a name="learn-more-about-the-built-in-json-support-in-sql-server"></a>Altre informazioni sul supporto JSON integrato in SQL Server  
Per soluzioni specifiche, casi d'uso e indicazioni, vedere i [post del blog sul supporto JSON integrato](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/) in SQL Server e nel database SQL di Azure redatti da Jovan Popovic, Microsoft Program Manager.
  
## <a name="see-also"></a>Vedere anche  
 [Formattare i risultati delle query in formato JSON con FOR JSON &#40;SQL Server&#41;](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md)  
[Clausola FOR](../../t-sql/queries/select-for-clause-transact-sql.md)
