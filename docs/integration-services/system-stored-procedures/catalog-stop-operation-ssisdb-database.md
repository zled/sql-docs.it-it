---
title: catalog.stop_operation (database SSISDB) | Microsoft Docs
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 97fd9d22-03dd-4eda-8f6c-ba8b67acec68
caps.latest.revision: "11"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: bf33675e591fbb16417bc3b251a1a47693b59673
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="catalogstopoperation-ssisdb-database"></a>catalog.stop_operation (database SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Arresta una convalida o un'istanza di esecuzione nel catalogo di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Sintassi  
  
```sql  
catalog.stop_operation [ @operation_id = ] operation_id  
```  
  
## <a name="arguments"></a>Argomenti  
 [ @operation_id = ] *operation_id*  
 Identificatore univoco della convalida o dell'istanza di esecuzione. *operation_id* è di tipo **bigint**.  
  
## <a name="return-code-value"></a>Valore del codice restituito  
 0 (esito positivo)  
  
## <a name="result-sets"></a>Set di risultati  
 Nessuno  
  
## <a name="permissions"></a>Permissions  
 Per questa stored procedure è necessaria una delle autorizzazioni seguenti:  
  
-   Autorizzazione READ e MODIFY sulla convalida o sull'istanza di esecuzione  
  
-   Appartenenza al ruolo del database **ssis_admin**  
  
-   Appartenenza al ruolo del server **sysadmin**  
  
## <a name="errors-and-warnings"></a>Errori e avvisi  
 Nell'elenco seguente vengono descritte alcune condizioni che possono generare un errore o un avviso:  
  
-   Utente senza autorizzazioni appropriate.  
  
-   Identificatore di operazione non valido.  
  
-   Operazione già arrestata.  
  
## <a name="remarks"></a>Osservazioni  
 Solo un utente per volta deve arrestare un'operazione nel catalogo di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Se più utenti tentano di arrestare l'operazione, tramite la stored procedure verrà restituito l'esito positivo (valore `0`) al primo tentativo, ma verrà generato un errore ai tentativi successivi.  
  
  
