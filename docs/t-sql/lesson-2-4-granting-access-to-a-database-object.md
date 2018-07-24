---
title: Concessione dell'accesso a un oggetto di database | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.technology: t-sql
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- SQL Server 2016
helpviewer_keywords:
- granting access to database objects
ms.assetid: a44d9bbf-f58e-4734-b7f4-eb3b492b777b
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: e5641055b11a53bcf39e2eb87ca547553521f9bf
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38014599"
---
# <a name="lesson-2-4---granting-access-to-a-database-object"></a>Lezione 2-4 - Concessione dell'accesso a un oggetto di database
[!INCLUDE[tsql-appliesto-ss2008-all-md](../includes/tsql-appliesto-ss2008-all-md.md)]
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
  
  
  
