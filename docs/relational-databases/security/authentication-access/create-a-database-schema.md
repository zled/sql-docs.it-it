---
title: Creare uno schema di database | Microsoft Docs
ms.custom: 
ms.date: 07/05/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: security
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.schemas.general.f1
helpviewer_keywords:
- creating schemas with Management Studio
- CREATE SCHEMA [Management Studio]
- database schemas
- schemas [SQL Server], creating
ms.assetid: ed2a5522-f4d2-4111-95a4-d3e1e5081739
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 67fa7df893601b65f5c27d55c4007386672d9e17
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="create-a-database-schema"></a>Creazione di uno schema di database
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] Questo argomento illustra come creare uno schema in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] usando [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Limitazioni e restrizioni](#Restrictions)  
  
     [Sicurezza](#Security)  
  
-   **Per creare un schema mediante:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Restrictions"></a> Limitazioni e restrizioni  
  
-   Il nuovo schema è di proprietà di una delle seguenti entità a livello di database: utente di database, ruolo di database o ruolo applicazione. Gli oggetti creati all'interno di uno schema appartengono al proprietario dello schema e hanno un valore NULL per **principal_id** in **sys.objects**. La proprietà degli oggetti contenuti in uno schema può essere trasferita a qualsiasi entità a livello di database, ma il proprietario dello schema mantiene sempre l'autorizzazione CONTROL per gli oggetti all'interno dello schema.  
  
-   Quando si crea un oggetto di database, se si specifica un'entità del dominio valida (utente o gruppo) come proprietario dell'oggetto, l'entità del dominio viene aggiunta al database come uno schema. Il proprietario del nuovo schema è l'entità del dominio.  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Autorizzazioni  
  
-   È richiesta l'autorizzazione CREATE SCHEMA per il database.  
  
-   Per specificare un altro utente come proprietario dello schema che viene creato, l'utente deve disporre dell'autorizzazione IMPERSONATE per quell'utente. Se si specifica un ruolo di database come proprietario, il chiamante deve appartenere al ruolo oppure deve avere l'autorizzazione ALTER per il ruolo.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
##### <a name="to-create-a-schema"></a>Per creare uno schema  
  
1.  In Esplora oggetti espandere la cartella **Database** .  
  
2.  Espandere il database in cui si desidera creare il nuovo schema di database.  
  
3.  Fare clic con il pulsante destro del mouse sulla cartella **Sicurezza** , scegliere **Nuovo**, quindi selezionare **Schema**.  
  
4.  Nella finestra di dialogo **Schema - Nuovo** della pagina **Generale** immettere un nome per il nuovo schema nella casella **Nome schema** .  
  
5.  Nella casella **Proprietario schema** immettere il nome di un utente o ruolo del database proprietario dello schema. In alternativa, fare clic su **Cerca** per aprire la finestra di dialogo **Cerca ruoli e utenti** .  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="additional-options"></a>Opzioni aggiuntive  
 Nella finestra di dialogo **Schema - Nuovo** sono inoltre disponibili opzioni in due pagine aggiuntive, cioè **Autorizzazioni** e **Proprietà estese**.  
  
-   Nella pagina **Autorizzazioni** sono elencate tutte le possibili entità a protezione diretta e le autorizzazioni su quelle entità a protezione diretta che possono essere concesse all'account di accesso.  
  
-   La pagina **Proprietà estese** consente di aggiungere proprietà personalizzate a utenti di database.  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
  
#### <a name="to-create-a-schema"></a>Per creare uno schema  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../../includes/ssde-md.md)].  
  
2.  Sulla barra Standard fare clic su **Nuova query**.  
  
3.  Nell'esempio seguente viene creato uno schema denominato`Chains` e poi una tabella denominata `Sizes`.  
    ```sql  
    CREATE SCHEMA Chains;
    GO
    CREATE TABLE Chains.Sizes (ChainID int, width dec(10,2));
    ```

4.  È possibile eseguire opzioni aggiuntive in una singola istruzione. Nell'esempio seguente viene creato lo schema `Sprockets`, di proprietà di Annik contenente la tabella `NineProngs`. L'istruzione concede `SELECT` a Mandar e nega `SELECT` a Prasanna.  

    ```sql  
    CREATE SCHEMA Sprockets AUTHORIZATION Annik  
        CREATE TABLE NineProngs (source int, cost int, partnumber int)  
        GRANT SELECT ON SCHEMA::Sprockets TO Mandar  
        DENY SELECT ON SCHEMA::Sprockets TO Prasanna;  
    GO  
    ```  
5. Eseguire l'istruzione seguente per visualizzare gli schemi in questo database:

   ```sql
   SELECT * FROM sys.schemas;
   ```

 Per altre informazioni, vedere [CREATE SCHEMA &#40;Transact-SQL&#41;](../../../t-sql/statements/create-schema-transact-sql.md).  
  
  
