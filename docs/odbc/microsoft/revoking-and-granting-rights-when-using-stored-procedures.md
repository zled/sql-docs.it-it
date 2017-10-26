---
title: Revoca e concedere diritti quando si utilizzano Stored procedure | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- stored procedures [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], stored procedures
ms.assetid: 24070039-03ab-4623-a681-6308802eb399
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 67bad57e201d10c5eb29aafb19fa9f513c43b172
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="revoking-and-granting-rights-when-using-stored-procedures"></a>Concedere e revocare i diritti quando si utilizzano Stored procedure
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. In alternativa, utilizzare il driver ODBC fornito da Oracle.  
  
 Il Driver ODBC di Microsoft per Oracle restituisce il seguente messaggio di errore quando i diritti utente vengono concesse e quindi revocare per una tabella a cui accede una stored procedure:  
  
 SQL_ERROR =-1  
  
 szErrorMsg = "[Microsoft] [driver ODBC per Oracle] numero errato di parametri"  
  
 szErrorMsg = "[Microsoft] [driver ODBC per Oracle] sintassi o violazione di accesso"  
  
 La chiamata alla funzione Oracle OCI Odessp() ha esito negativo in questo scenario, ma è necessaria per implementare i parametri predefiniti. Dopo che vengono modificate le autorizzazioni nella tabella sottostante, è necessario ricompilare la stored procedure prima di eseguirlo nuovamente.

