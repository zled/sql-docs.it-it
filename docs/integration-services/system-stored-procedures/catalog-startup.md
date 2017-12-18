---
title: catalog.startup | Microsoft Docs
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
ms.assetid: 271fd405-246a-4852-bfbe-f557241ce6ea
caps.latest.revision: "9"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b80919c3a754913ff15a5eed9ae37b39044977a0
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="catalogstartup"></a>catalog.startup
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Esegue la manutenzione dello stato delle operazioni per il catalogo SSISDB.  
  
 La stored procedure corregge lo stato di eventuali pacchetti in esecuzione in caso di arresto dell'istanza del server [!INCLUDE[ssIS](../../includes/ssis-md.md)].  
  
 È possibile scegliere di abilitare la stored procedure per l'esecuzione automatica a ogni riavvio dell'istanza del server [!INCLUDE[ssIS](../../includes/ssis-md.md)], selezionando l'opzione **Abilita l'esecuzione automatica della stored procedure di Integration Services all'avvio di SQL Server** nella finestra di dialogo **Crea catalogo**.  
  
## <a name="syntax"></a>Sintassi  
  
```sql  
catalog.startup  
```  
  
## <a name="return-code-value"></a>Valore del codice restituito  
 0 (esito positivo)  
  
## <a name="result-sets"></a>Set di risultati  
 Nessuno  
  
## <a name="permissions"></a>Permissions  
 Per questa stored procedure è necessaria una delle autorizzazioni seguenti:  
  
-   Autorizzazioni READ e MODIFY sull'istanza di esecuzione, autorizzazioni READ e EXECUTE sul progetto e, se applicabile, autorizzazioni per la lettura sull'ambiente a cui si fa riferimento  
  
-   Appartenenza al ruolo del database **ssis_admin**  
  
-   Appartenenza al ruolo del server **sysadmin**  
  
  
