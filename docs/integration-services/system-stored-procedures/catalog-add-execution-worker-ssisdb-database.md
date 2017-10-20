---
title: Catalog.add_execution_worker (Database SSISDB) | Documenti Microsoft
ms.custom: 
ms.date: 12/16/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d587cedd-6402-4d5c-9526-7cd25627a037
caps.latest.revision: 4
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 8ce83f2678a1f3dcae6539f33beb33070b8e771b
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="catalogaddexecutionworker-ssisdb-database"></a>Catalog.add_execution_worker (Database SSISDB)
[!INCLUDE[tsql-appliesto-ssvnxt-xxxx-xxxx-xxx.md](../../includes/tsql-appliesto-ssvnxt-xxxx-xxxx-xxx.md)]

Aggiunge un [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] scala il lavoro a un'istanza di esecuzione in orizzontale.

## <a name="syntax"></a>Sintassi

```sql
catalog.add_execution_worker [@execution_id = ] execution_id, [@workeragent_id = ] workeragent_id
```

## <a name="arguments"></a>Argomenti
[ @execution_id =] *valore di execution_id*  
 Identificatore univoco per l'istanza di esecuzione. Il *valore di execution_id* è **bigint**.  
 
[@workeragent_id =] *workeragent_id*  
L'id di agente di lavoro di una scala Out Worker. Il *workeragent_id* è **uniqueIdentifier**.

## <a name="return-code-value"></a>Valore del codice restituito  
 0 (esito positivo)  
  
## <a name="result-sets"></a>Set di risultati  
 Nessuno  

## <a name="permissions"></a>Autorizzazioni  
 Per questa stored procedure è necessaria una delle autorizzazioni seguenti:  
  
-   Autorizzazioni READ e MODIFY per l'istanza di esecuzione  
  
-   L'appartenenza al **ssis_admin** ruolo del database  
  
-   L'appartenenza al **sysadmin** ruolo del server  
 
## <a name="errors-and-warnings"></a>Errori e avvisi  
 Nell'elenco seguente vengono descritte alcune condizioni che possono generare un errore o un avviso:  
 
- Utente senza autorizzazioni appropriate.

- L'identificatore di esecuzione non è valido.

- L'id di agente di lavoro non è valido.

- L'esecuzione non è presente in orizzontale.

## <a name="see-also"></a>Vedere anche
[Esecuzione di pacchetti in orizzontale](~/integration-services/scale-out/run-packages-in-integration-services-ssis-scale-out.md).


