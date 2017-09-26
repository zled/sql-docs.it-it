---
title: Catalog. Startup | Documenti Microsoft
ms.custom:
- SQL2016_New_Updated
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 271fd405-246a-4852-bfbe-f557241ce6ea
caps.latest.revision: 9
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 3a8c89be0541be1861f45240b891d349019a8935
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="catalogstartup"></a>catalog.startup
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Esegue la manutenzione dello stato delle operazioni per il catalogo SSISDB.  
  
 La stored procedure corregge lo stato di eventuali pacchetti in esecuzione in caso di arresto dell'istanza del server [!INCLUDE[ssIS](../../includes/ssis-md.md)].  
  
 È possibile scegliere di abilitare la stored procedure eseguita automaticamente ogni volta il [!INCLUDE[ssIS](../../includes/ssis-md.md)] istanza del server viene riavviata, selezionando il **stored procedure all'avvio di SQL Serverdiabilitarel'esecuzioneautomaticadiIntegrationServices** opzione il **Crea catalogo** la finestra di dialogo.  
  
## <a name="syntax"></a>Sintassi  
  
```tsql  
Catalog.startup  
```  
  
## <a name="return-code-value"></a>Valore del codice restituito  
 0 (esito positivo)  
  
## <a name="result-sets"></a>Set di risultati  
 Nessuno  
  
## <a name="permissions"></a>Permissions  
 Per questa stored procedure è necessaria una delle autorizzazioni seguenti:  
  
-   Autorizzazioni READ e MODIFY sull'istanza di esecuzione, autorizzazioni READ e EXECUTE sul progetto e, se applicabile, autorizzazioni per la lettura sull'ambiente a cui si fa riferimento  
  
-   L'appartenenza al **ssis_admin** ruolo del database  
  
-   L'appartenenza al **sysadmin** ruolo del server  
  
  
