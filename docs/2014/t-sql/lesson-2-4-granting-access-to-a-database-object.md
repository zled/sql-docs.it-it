---
title: Concessione dell'accesso a un oggetto di database | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- granting access to database objects
ms.assetid: a44d9bbf-f58e-4734-b7f4-eb3b492b777b
caps.latest.revision: 14
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: d07ed4bc46ef1872f656adb09ce1883b04514f02
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37187568"
---
# <a name="granting-access-to-a-database-object"></a>Concessione dell'accesso a un oggetto di database
  In qualità di amministratore, l'utente è autorizzato a eseguire l'istruzione SELECT dalla tabella **Products** e dalla vista **vw_Names**, nonché a eseguire la procedura **pr_Names**. All'utente Mary non sono tuttavia concesse tali autorizzazioni. Per concedere a tale utente le autorizzazioni necessarie, utilizzare l'istruzione GRANT.  
  
### <a name="procedure-title"></a>Titolo della procedura  
  
1.  Eseguire l'istruzione seguente per concedere a `Mary` l'autorizzazione `EXECUTE` per la stored procedure `pr_Names` .  
  
    ```  
    GRANT EXECUTE ON pr_Names TO Mary;  
    GO  
    ```  
  
 In questo scenario, all'utente Mary è consentito solo l'accesso alla tabella **Products** usando la stored procedure. Se si desidera autorizzare l'utente Mary a eseguire un'istruzione SELECT sulla vista, è inoltre necessario eseguire `GRANT SELECT ON vw_Names TO Mary`. Per rimuovere l'accesso agli oggetti di database, utilizzare l'istruzione REVOKE.  
  
> [!NOTE]  
>  Se la tabella, la vista e la stored procedure non appartengono allo stesso schema, la procedura per la concessione delle autorizzazioni risulta più complessa.  
  
## <a name="about-grant"></a>Informazioni sull'istruzione GRANT  
 È necessario disporre dell'autorizzazione EXECUTE per eseguire una stored procedure. Per accedere e modificare i dati, è necessario disporre delle autorizzazioni SELECT, INSERT, UPDATE e DELETE. L'istruzione GRANT è inoltre utilizzata per altre autorizzazioni , ad esempio quella per creare tabelle.  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
 [Riepilogo: Configurazione delle autorizzazioni per gli oggetti di database](lesson-2-5-summary-configuring-permissions-on-database-objects.md)  
  
## <a name="see-also"></a>Vedere anche  
 [GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql)   
 [REVOKE- &#40;Transact-SQL&#41;](/sql/t-sql/statements/revoke-transact-sql)  
  
  
