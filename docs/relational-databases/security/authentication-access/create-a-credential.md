---
title: "Creazione di credenziali | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "credenziali [SQL Server], creazione"
  - "autenticazione [SQL Server], credenziali"
  - "accesso [SQL Server], credenziali"
ms.assetid: c1e77e91-2a69-40d9-b8b3-97cffc710586
caps.latest.revision: 17
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 17
---
# Creazione di credenziali
  In questo argomento viene descritto come creare credenziali in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] utilizzando [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
 Le credenziali consentono agli utenti che utilizzano l'autenticazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] di disporre di un'identità al di fuori di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Vengono principalmente utilizzate per eseguire codice negli assembly con set di autorizzazioni EXTERNAL_ACCESS. È inoltre possibile utilizzare le credenziali quando un utente che utilizza l'autenticazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ha la necessità di accedere a una risorsa di dominio, quale il percorso di un file in cui archiviare un backup.  
  
 È possibile eseguire il mapping delle credenziali a diversi account di accesso di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] contemporaneamente. Su un account di accesso di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] è possibile eseguire il mapping a un solo set di credenziali alla volta. Dopo aver creato le credenziali, usare **Proprietà account di accesso (pagina Generale)** per eseguire il mapping di un account di accesso alle credenziali.  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Limitazioni e restrizioni](#Restrictions)  
  
     [Sicurezza](#Security)  
  
-   **Per creare le credenziali utilizzando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Restrictions"></a> Limitazioni e restrizioni  
  
-   Se non sono presenti credenziali su cui viene eseguito il mapping a un account accesso per il provider, vengono utilizzate le credenziali sui cui viene eseguito il mapping all'account del servizio [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
-   A un account di accesso è possibile eseguire il mapping di più credenziali, a condizione che vengano utilizzate con provider distinti. È possibile eseguire il mapping di una sola credenziale per provider per ogni account di accesso. ma di più accessi alla stessa credenziale.  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Autorizzazioni  
 Richiede autorizzazione ALTER ANY CREDENTIAL di creare o modificare credenziali e un autorizzazione ALTER ANY LOGIN per eseguire il mapping di un accesso a credenziali.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### Per creare una credenziale  
  
1.  In Esplora oggetti espandere la cartella **Sicurezza** .  
  
2.  Fare clic con il pulsante destro del mouse sulla cartella **Credenziali** e scegliere **Nuove credenziali**.  
  
3.  Nella casella **Nome credenziali** della finestra di dialogo **Nuove credenziali** digitare un nome per le credenziali.  
  
4.  Nella casella **Identità** digitare il nome dell'account usato per le connessioni in uscita (quando si esce dal contesto di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]). In genere, sarà un account utente di Windows, ma l'identità può essere un account di altro tipo.  
  
     In alternativa, fare clic sui puntini di sospensione **(…)** per aprire la finestra di dialogo **Seleziona utente o gruppo**.  
  
5.  Nelle caselle **Password** e **Conferma password** digitare la password dell'account specificato nella casella **Identità** . Se **Identità** corrisponde a un account utente di Windows, è la password di Windows. Se la password non è necessaria è possibile lasciare vuoto il campo **Password** .  
  
6.  Selezionare **Usa provider di crittografia** per impostare le credenziali da verificare con un provider EKM (Extensible Key Management). Per altre informazioni su Extensible Key Management, vedere [Extensible Key Management &#40;EKM&#41;](../../../relational-databases/security/encryption/extensible-key-management-ekm.md)  
  
7.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
  
#### Per creare una credenziale  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../../includes/ssde-md.md)].  
  
2.  Sulla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra Query, quindi fare clic su **Esegui**.  
  
    ```  
    -- Creates the credential called "AlterEgo.".   
    -- The credential contains the Windows user "Mary5" and a password.  
    CREATE CREDENTIAL AlterEgo WITH IDENTITY = 'Mary5',   
        SECRET = '<EnterStrongPasswordHere>';  
    GO  
    ```  
  
 Per altre informazioni, vedere [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../../t-sql/statements/create-credential-transact-sql.md).  
  
  