---
title: catalog.add_execution_worker (database SSISDB) | Microsoft Docs
ms.custom: 
ms.date: 12/16/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d587cedd-6402-4d5c-9526-7cd25627a037
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d5ecc54863b47ef55269a068353cbc25bbd5d008
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="catalogaddexecutionworker-ssisdb-database"></a>catalog.add_execution_worker (database SSISDB)
[!INCLUDE[tsql-appliesto-ssvnxt-xxxx-xxxx-xxx.md](../../includes/tsql-appliesto-ssvnxt-xxxx-xxxx-xxx.md)]

Aggiunge un servizio [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Scale Out Worker a un'istanza di esecuzione in Scale Out.

## <a name="syntax"></a>Sintassi

```sql
catalog.add_execution_worker [@execution_id = ] execution_id, [@workeragent_id = ] workeragent_id
```

## <a name="arguments"></a>Argomenti
[ @execution_id = ] *execution_id*  
 Identificatore univoco per l'istanza di esecuzione. *execution_id* è di tipo **bigint**.  
 
[@workeragent_id = ] *workeragent_id*  
ID agente di lavoro di uno Scale Out Worker. *workeragent_id* è di tipo **uniqueIdentifier**.

## <a name="return-code-value"></a>Valore del codice restituito  
 0 (esito positivo)  
  
## <a name="result-sets"></a>Set di risultati  
 Nessuno  

## <a name="permissions"></a>Permissions  
 Per questa stored procedure è necessaria una delle autorizzazioni seguenti:  
  
-   Autorizzazioni READ e MODIFY per l'istanza di esecuzione  
  
-   Appartenenza al ruolo del database **ssis_admin**  
  
-   Appartenenza al ruolo del server **sysadmin**  
 
## <a name="errors-and-warnings"></a>Errori e avvisi  
 Nell'elenco seguente vengono descritte alcune condizioni che possono generare un errore o un avviso:  
 
- Utente senza autorizzazioni appropriate.

- Identificatore di esecuzione non valido.

- ID agente di lavoro non valido.

- Esecuzione non inclusa in Scale Out.

## <a name="see-also"></a>Vedere anche
[Eseguire pacchetti in Scale Out](~/integration-services/scale-out/run-packages-in-integration-services-ssis-scale-out.md).

