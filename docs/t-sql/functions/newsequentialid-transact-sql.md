---
title: NEWSEQUENTIALID (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 08/08/2015
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- NEWSEQUENTIALID
- NEWSEQUENTIALID_TSQL
dev_langs: TSQL
helpviewer_keywords:
- NEWSEQUENTIALID function
- GUIDs [SQL Server]
ms.assetid: e06d2cab-f1ff-42f1-8550-6aaec57be36f
caps.latest.revision: "33"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 6993a36f0c1c67ffcfbb9897bcd36354088c8c5c
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="newsequentialid-transact-sql"></a>NEWSEQUENTIALID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Crea un GUID maggiore di qualsiasi GUID generato in precedenza da questa funzione in un computer specificato dall'avvio di Windows. Dopo avere riavviato Windows, è possibile avviare di nuovo il GUID da un intervallo inferiore, ma ancora globalmente univoco. Quando una colonna GUID viene utilizzata come identificatore di riga, l'utilizzo di NEWSEQUENTIALID può essere più veloce rispetto all'utilizzo della funzione NEWID, poiché la funzione NEWID causa un'attività casuale e utilizza un numero inferiore di pagine di dati memorizzate nella cache. L'utilizzo di NEWSEQUENTIALID consente inoltre di completare le pagine di dati e di indice.  
  
> [!IMPORTANT]  
>  In caso di problemi di riservatezza, non utilizzare questa funzione. È possibile intuire il valore del GUID che verrà generato successivamente e accedere ai dati associati a tale GUID.  
  
 NEWSEQUENTIALID è un wrapper di failover di Windows [UuidCreateSequential](http://go.microsoft.com/fwlink/?LinkId=164027) funzione, con alcune [byte fuori posto applicato](https://blogs.msdn.microsoft.com/dbrowne/2012/07/03/how-to-generate-sequential-guids-for-sql-server-in-net/).
  
> [!WARNING]  
>  La funzione UuidCreateSequential presenta dipendenze di hardware. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], i cluster di valori sequenziali possono sviluppare quando i database (ad esempio i database indipendenti) vengono spostati in altri computer. Quando si usa Always On e su [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)], i cluster di valori sequenziali possono sviluppare se il database viene eseguito il failover in un altro computer.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
NEWSEQUENTIALID ( )  
```  
  
## <a name="return-type"></a>Tipo restituito  
 **uniqueidentifier**  
  
## <a name="remarks"></a>Osservazioni  
 NEWSEQUENTIALID () può essere utilizzato solo con vincoli predefiniti sulle colonne della tabella di tipo **uniqueidentifier**. Esempio:  
  
```  
CREATE TABLE myTable (ColumnA uniqueidentifier DEFAULT NEWSEQUENTIALID());   
```  
  
 Quando viene specificata in espressioni DEFAULT, la funzione NEWSEQUENTIALID() non può essere utilizzata in combinazione con altri operatori scalari. Ad esempio, la seguente operazione non è valida:  
  
```  
CREATE TABLE myTable (ColumnA uniqueidentifier DEFAULT dbo.myfunction(NEWSEQUENTIALID()));  
```  
  
 Nell'esempio precedente `myfunction()` è una funzione scalare definita dall'utente che accetta e restituisce un valore `uniqueidentifier`.  
  
 Non è possibile fare riferimento a NEWSEQUENTIALID all'interno di query.  
  
 È possibile usare NEWSEQUENTIALID per generare GUID in modo da ridurre le divisioni di pagina e le operazioni di I/O casuali a livello foglia degli indici.  
  
 Ogni GUID generato usando NEWSEQUENTIALID è univoco nel computer. I GUID generati usando NEWSEQUENTIALID sono univoci in più computer solo se il computer di origine dispone di una scheda di rete.  
  
## <a name="see-also"></a>Vedere anche  
 [NEWID &#40; Transact-SQL &#41;](../../t-sql/functions/newid-transact-sql.md)   
 [Gli operatori di confronto &#40; Transact-SQL &#41;](../../t-sql/language-elements/comparison-operators-transact-sql.md)  
  
  
