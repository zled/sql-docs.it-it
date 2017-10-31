---
title: Procedura guidata Always Encrypted | Microsoft Docs
ms.custom:
- SQL2016_New_Updated
ms.date: 05/04/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.alwaysencryptedwizard.encryption.f1
- sql13.swb.alwaysencryptedwizard.f1
- sql.swb.alwaysencryptedwizard.masterkey.f1
helpviewer_keywords:
- Wizard, Always Encrypted
ms.assetid: 68daddc9-ce48-49aa-917f-6dec86ad5af5
caps.latest.revision: 17
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: HT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: 8322346347568b8bb3bc56b56f363ceb7d6f5cfa
ms.contentlocale: it-it
ms.lasthandoff: 09/27/2017

---
# <a name="always-encrypted-wizard"></a>Procedura guidata Always Encrypted
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

<a name="use-the-always-encrypted-wizard-to-help-protect-sensitive-data--stored-in-a-sql-server-database-always-encrypted-allows-clients-to-encrypt-sensitive-data-inside-client-applications-and-never-reveal-the-encryption-keys-to-sql-server-as-a-result-always-encrypted-provides-a-separation-between-those-who-own-the-data-and-can-view-it-and-those-who-manage-the-data-but-should-have-no-access--for-a-full-description-of-the-feature-see-always-encrypted-40database-engine41relational-databasessecurityencryptionalways-encrypted-database-enginemd"></a>Usare la **procedura guidata Always Encrypted** per proteggere i dati sensibili archiviati in un database di SQL Server. Always Encrypted consente ai client di eseguire la crittografia dei dati sensibili all'interno delle applicazioni client e non rivelare le chiavi di crittografia di SQL Server. Di conseguenza, Always Encrypted crea una separazione tra chi possiede i dati (e può visualizzarli) e chi gestisce i dati (ma non può accedervi).  Per una descrizione completa della funzionalità, vedere [Always Encrypted &#40;Motore di database&#41;](../../../relational-databases/security/encryption/always-encrypted-database-engine.md).  
 -  
 - Per una procedura dettagliata end-to-end che spiega come configurare Always Encrypted con la procedura guidata e come usarlo in un'applicazione client, vedere [Always Encrypted - Proteggere i dati sensibili nel database SQL con la crittografia del database e archiviare le chiavi di crittografia nell'archivio certificati di Windows](https://azure.microsoft.com/documentation/articles/sql-database-always-encrypted/).  
 -  
 - Per informazioni sull'uso della procedura guidata, vedere il video relativo alla [protezione dei dati sensibili con Always Encrypted](https://channel9.msdn.com/events/DataDriven/SQLServer2016/AlwaysEncrypted). Vedere anche il blog del team di sicurezza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sulla [procedura guidata per la crittografia di SSMS e su come abilitare Always Encrypted in pochi semplici passaggi](http://blogs.msdn.com/b/sqlsecurity/archive/2015/11/01/ssms-encryption-wizard-enabling-always-encrypted-made-easy.aspx).  
 -  
 - **Autorizzazioni:** per eseguire query su colonne crittografate e selezionare chiavi usando la procedura guidata è necessario avere le autorizzazioni `VIEW ANY COLUMN MASTER KEY DEFINITION` e `VIEW ANY COLUMN ENCRYPTION KEY DEFINITION` . Per creare nuove chiavi, sono necessarie anche le autorizzazioni `ALTER ANY COLUMN MASTER KEY` e `ALTER ANY COLUMN ENCRYPTION KEY` .  
 -  
 -#### Per aprire la procedura guidata Always Encrypted  
 -  
 -1.  Connettersi a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] con il componente Esplora oggetti di [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].  
 -  
 -2.  Fare clic con il pulsante destro del mouse sul database, scegliere **Attività**, quindi fare clic su **Crittografa colonne**.  
 -  
 -## Pagina Selezione colonna  
 - Individuare una tabella e una colonna e quindi selezionare un tipo di crittografia (deterministico o casuale) e una chiave di crittografia per le colonne selezionate. Per decrittografare una colonna attualmente crittografata, selezionare **Testo non crittografato**. Per applicare una nuova chiave di crittografia a una colonna, selezionare una chiave di crittografia diversa e la procedura guidata decrittograferà la colonna per puoi crittografarla nuovamente con la nuova chiave. La crittografia di tabelle temporali e in memoria è supportata da [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , ma non può essere configurata con questa procedura guidata.  
 -  
 -## Pagina Configurazione della chiave master  
 - Creare una nuova chiave master della colonna nell'archivio certificati di Windows o in Insieme di credenziali delle chiavi di Azure. Per altre informazioni, fare clic di seguito sui collegamenti nella sezione Archiviazione della chiave.  
 -  
 - Se si sceglie una chiave di crittografia della colonna generata automaticamente nella pagina Selezione colonna, è necessario configurare una chiave master della colonna con cui verrà crittografata la chiave di crittografia della colonna generata. Se esiste già una chiave master della colonna definita nel database, è possibile selezionarla. (Per usare una chiave master della colonna esistente, è necessario avere l'autorizzazione per accedere alla chiave.) In alternativa, è possibile generare una nuova chiave master della colonna nell'archivio chiavi selezionato (archivio certificati di Windows o Insieme di credenziali delle chiavi di Azure) e definire la chiave nel database.  
 -  
 - **Archiviazione della chiave**  
 -  
 - Scegliere la posizione in cui verrà archiviata la chiave master della colonna.  
 -  
 --   **Archiviazione di una chiave master nell'archivio certificati di Windows** Per altre informazioni, vedere [Using Certificate Stores](https://msdn.microsoft.com/library/windows/desktop/aa388160.aspx) (Uso degli archivi certificati)  
 -  
 --   **Archiviazione di una chiave master in Azure Key Vault** Per altre informazioni, vedere [Introduzione ad Azure Key Vault](https://azure.microsoft.com/documentation/articles/key-vault-get-started/).  
 -  
 - Per generare una chiave master della colonna nell'insieme di credenziali delle chiavi di Azure, l'utente deve avere le autorizzazioni **WrapKey**, **UnwrapKey**, **Verify**e **Sign** per l'insieme di credenziali delle chiavi. Potrebbero essere necessarie anche le autorizzazioni **Get**, **List**, **Create**, **Delete**, **Update**, **Import**, **Backup**e **Restore** . Per altre informazioni, vedere [Che cos'è un insieme di credenziali delle chiavi di Azure?](https://azure.microsoft.com/documentation/articles/key-vault-whatis/) e   [Set-AzureRmKeyVaultAccessPolicy](https://msdn.microsoft.com/library/mt603625.aspx).  
 -  
 - La procedura guidata supporta solo queste due opzioni. I moduli di protezione hardware e gli archivi dei clienti devono essere configurati con [CREATE COLUMN MASTER KEY &#40;Transact-SQL&#41;](../../../t-sql/statements/create-column-master-key-transact-sql.md)[!INCLUDE[tsql](../../../includes/tsql-md.md)].  
 -  
 -## Terminologia di Always Encrypted  
 -  
 --   **La crittografia deterministica** usa un metodo che genera sempre lo stesso valore crittografato per qualsiasi valore di testo normale specificato. L'uso della crittografia deterministica consente di eseguire operazioni di raggruppamento, filtro di uguaglianza e join di tabelle in base ai valori crittografati, ma può anche consentire a utenti non autorizzati di indovinare le informazioni sui valori crittografati esaminando i criteri nella colonna crittografata. Questa vulnerabilità aumenta quando è presente un piccolo set di possibili valori crittografati, ad esempio True/False o area geografica Nord/Sud/Est/Ovest. La crittografia deterministica deve usare regole di confronto a livello di colonna con un ordinamento binario2 per colonne di tipo carattere.  
 -  
 --   **La crittografia casuale** usa un metodo di crittografia dei dati meno prevedibile. La crittografia casuale è più sicura, ma impedisce le ricerche di uguaglianza, il raggruppamento, l'indicizzazione e il join su colonne crittografate.  
 -  
 --   **Le chiavi master della colonna** sono chiavi di protezione usate per crittografare le chiavi di crittografia della colonna. Le chiavi master della colonna devono essere archiviate in un archivio attendibile. Le informazioni sulle chiavi master della colonna, incluso il relativo percorso, vengono archiviate nel database in viste del catalogo di sistema.  
 -  
 --   **Le chiavi di crittografia della colonna** vengono usate per crittografare dati sensibili archiviati nelle colonne del database. Tutti i valori presenti in una colonna possono essere crittografati usando una chiave di crittografia di singola colonna. I valori crittografati delle chiavi di crittografia della colonna vengono archiviati nel database in viste del catalogo di sistema. È consigliabile archiviare le chiavi di crittografia della colonna in un percorso sicuro/attendibile per il backup.  
 -  
 -## Vedere anche  
 - [Always Encrypted &#40;Motore di database&#41;](../../../relational-databases/security/encryption/always-encrypted-database-engine.md)   
 - [Extensible Key Management con l'insieme di credenziali delle chiavi di Azure &#40;SQL Server&#41;](../../../relational-databases/security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md)  

