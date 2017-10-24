---
title: Concessione dell'accesso a un oggetto di Database | Documenti Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- granting access to database objects
ms.assetid: a44d9bbf-f58e-4734-b7f4-eb3b492b777b
caps.latest.revision: 14
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7cc5c15a44f16e4049974ff76095a389348707c7
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="lesson-2-4---granting-access-to-a-database-object"></a>Lezione 2-4-la concessione dell'accesso a un oggetto di Database
In qualità di amministratore, l'utente è autorizzato a eseguire l'istruzione SELECT dalla tabella **Products** e dalla vista **vw_Names** , nonché a eseguire la procedura **pr_Names** . All'utente Mary non sono tuttavia concesse tali autorizzazioni. Per concedere a tale utente le autorizzazioni necessarie, utilizzare l'istruzione GRANT.  
  
### <a name="procedure-title"></a>Titolo della procedura  
  
1.  Eseguire l'istruzione seguente per concedere a `Mary` l'autorizzazione `EXECUTE` per la stored procedure `pr_Names` .  
  
    ```  
    GRANT EXECUTE ON pr_Names TO Mary;  
    GO  
    ```  
  
In questo scenario, all'utente Mary è consentito solo l'accesso alla tabella **Products** usando la stored procedure. Se si desidera autorizzare l'utente Mary a eseguire un'istruzione SELECT sulla vista, è inoltre necessario eseguire `GRANT SELECT ON vw_Names TO Mary`. Per rimuovere l'accesso agli oggetti di database, utilizzare l'istruzione REVOKE.  
  
> [!NOTE]  
> Se la tabella, la vista e la stored procedure non appartengono allo stesso schema, la procedura per la concessione delle autorizzazioni risulta più complessa.  
  
## <a name="about-grant"></a>Informazioni sull'istruzione GRANT  
È necessario disporre dell'autorizzazione EXECUTE per eseguire una stored procedure. Per accedere e modificare i dati, è necessario disporre delle autorizzazioni SELECT, INSERT, UPDATE e DELETE. L'istruzione GRANT è inoltre utilizzata per altre autorizzazioni , ad esempio quella per creare tabelle.  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
[Riepilogo: Configurazione delle autorizzazioni per gli oggetti di database](../t-sql/lesson-2-5-summary-configuring-permissions-on-database-objects.md)  
  
## <a name="see-also"></a>Vedere anche  
[GRANT &#40;Transact-SQL&#41;](../t-sql/statements/grant-transact-sql.md)  
[REVOKE &#40;Transact-SQL&#41;](../t-sql/statements/revoke-transact-sql.md)  
  
  
  

