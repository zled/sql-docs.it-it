---
title: Centro di sicurezza per il motore di database di SQL Server e il database SQL di Azure | Microsoft Docs
ms.custom: ''
ms.date: 09/23/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-security
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- Security [SQL Server]
helpviewer_keywords:
- SQL Server, security
- security [SQL Server]
- database security [SQL Server]
- databases [SQL Server], security
ms.assetid: dfb39d16-722a-4734-94bb-98e61e014ee7
caps.latest.revision: 50
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: fa006590558cf94095d37f009102da753a5464ed
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36054958"
---
# <a name="security-center-for-sql-server-database-engine-and-azure-sql-database"></a>Centro di sicurezza per il motore di database di SQL Server e il database SQL di Azure
  Questa pagina fornisce i collegamenti che consentono di individuare le informazioni necessarie su sicurezza e protezione nel [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]e nel [!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)].  
  
> [!NOTE]  
>  Alle funzionalità di [!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)] vengono apportati sempre nuovi miglioramenti. Vedere la versione più recente di questo argomento per le ultime novità sul [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
|Autenticazione: identità dell'utente|Autorizzazione: operazioni consentite|Crittografia: archiviazione dei dati segreti|Sicurezza della connessione: limitazioni e sicurezza|Controllo: registrazione dell'accesso|  
|----------------------------------|-------------------------------------|-------------------------------------|---------------------------------------------------|--------------------------------|  
|**Scelta del tipo di autenticazione**<br /><br /> [![Mappa del centro di sicurezza Windows autenticazione](../../database-engine/media/security-center-map-windows-authenticaion.png "mappa Centro sicurezza: autenticazione Windows")](http://msdn.microsoft.com/library/ms144284.aspx)<br /><br /> <br /><br /> [![Centro sicurezza: autenticazione Server SQL mappa](../../database-engine/media/security-center-map-sql-authenticaion.png "Centro sicurezza: autenticazione Server SQL mappa")](http://msdn.microsoft.com/library/ms144284.aspx)<br /><br /> **Dove viene eseguita l'autenticazione**<br /><br /> [![Centro sicurezza PC mapping account di accesso e utenti](../../database-engine/media/security-center-map-logins-users.png "Centro sicurezza PC mapping account di accesso e utenti")](http://msdn.microsoft.com/library/aa337562.aspx)<br /><br /> <br /><br /> [![Mappa del Centro sicurezza: utenti del Database indipendente](../../database-engine/media/security-center-map-contained-users.png "mappa del Centro sicurezza: utenti del Database indipendente")](http://msdn.microsoft.com/library/ff929188.aspx)<br /><br /> **Uso di altre identità**<br /><br /> [![Centro sicurezza PC mappa credenziali](../../database-engine/media/security-center-map-credentials.png "credenziali mappa Centro sicurezza")](http://msdn.microsoft.com/library/ms161950.aspx)<br /><br /> [![Mappa del Centro sicurezza: Execute As Login](../../database-engine/media/security-center-map-exec-as-login.png "mappa del Centro sicurezza: Execute As Login")](http://msdn.microsoft.com/library/ms181362.aspx)<br /><br /> [![Mappa del Centro sicurezza: Execute As User](../../database-engine/media/security-center-map-exec-as-user.png "mappa del Centro sicurezza: Execute As User")](http://msdn.microsoft.com/library/ms181362.aspx)<br /><br /> ![Segnaposto](../../database-engine/media/security-center-map-blankplaceholder.png "segnaposto")<br /><br /> ![Segnaposto](../../database-engine/media/security-center-map-blankplaceholder.png "segnaposto")<br /><br /> ![Segnaposto](../../database-engine/media/security-center-map-blankplaceholder.png "segnaposto")<br /><br /> ![Segnaposto](../../database-engine/media/security-center-map-blankplaceholder.png "segnaposto")|**Concessione, revoca e negazione delle autorizzazioni**<br /><br /> [![Centro sicurezza di eseguire il mapping di classi a protezione diretta](../../database-engine/media/security-center-map-securable-classes.png "Centro sicurezza di eseguire il mapping di classi a protezione diretta")](http://msdn.microsoft.com/library/ms190401.aspx)<br /><br /> [![Mappa del Centro sicurezza: autorizzazioni Server](../../database-engine/media/security-center-map-srv-perms.png "mappa del Centro sicurezza: autorizzazioni Server")](http://msdn.microsoft.com/library/ms191291.aspx)<br /><br /> [![Mappa del Centro sicurezza: autorizzazioni Database](../../database-engine/media/security-center-map-db-perms.png "mappa del Centro sicurezza: autorizzazioni Database")](http://msdn.microsoft.com/library/ms191291.aspx)<br /><br /> **Sicurezza in base ai ruoli**<br /><br /> [![Centro sicurezza: ruoli Server mappa](../../database-engine/media/security-center-map-srv-roles.png "mappa Centro sicurezza: ruoli Server")](http://msdn.microsoft.com/library/ms188659.aspx)<br /><br /> [![Centro sicurezza: ruoli Database mappa](../../database-engine/media/security-center-map-db-roles.png "Centro sicurezza: ruoli Database mappa")](http://msdn.microsoft.com/library/ms189121.aspx)<br /><br /> `Restricting Data Access to Selected Data Elements`<br /><br /> [![Visualizzazioni della mappa del centro di sicurezza e le procedure](../../database-engine/media/security-center-map-view-procs.png "visualizzazioni mappa del centro di sicurezza e procedure")](http://msdn.microsoft.com/library/ms175503.aspx)<br /><br /> [![Sicurezza a livello di riga mappa Centro sicurezza PC](../../database-engine/media/security-center-map-row-level-sec.png "sicurezza a livello di riga mappa Centro sicurezza")](http://msdn.microsoft.com/library/dn765131.aspx)<br /><br /> [![La maschera dati dinamica mappa Centro sicurezza PC](../../database-engine/media/security-center-map-data-masking.png "la maschera dati dinamica mappa Centro sicurezza")](http://azure.microsoft.com/documentation/articles/sql-database-dynamic-data-masking-get-started/)<br /><br /> [![Mappa del Centro sicurezza: oggetti firmati](../../database-engine/media/security-center-map-signed-objects.png "mappa del Centro sicurezza: oggetti firmati")](http://msdn.microsoft.com/library/ms181700.aspx)<br /><br /> ![Segnaposto](../../database-engine/media/security-center-map-blankplaceholder.png "segnaposto")|**Crittografia dei file**<br /><br /> [![Centro sicurezza PC mappa BitLocker](../../database-engine/media/security-center-map-bitlocker.png "BitLocker mappa Centro sicurezza")](http://support.microsoft.com/en-us/kb/2855131)<br /><br /> [![Mappa del Centro sicurezza: crittografia NTFS](../../database-engine/media/security-center-map-ntfs-encryp.png "mappa del Centro sicurezza: crittografia NTFS")](http://msdn.microsoft.com/library/dd163562.aspx)<br /><br /> [![Mappa del Centro sicurezza: TDE](../../database-engine/media/security-center-map-tde.png "mappa del Centro sicurezza: TDE")](http://msdn.microsoft.com/library/bb934049.aspx)<br /><br /> [![Mappa del Centro sicurezza: crittografia Backup](../../database-engine/media/security-center-map-backup-encryp.png "mappa del Centro sicurezza: crittografia Backup")](http://msdn.microsoft.com/library/dn449489.aspx)<br /><br /> **Crittografia delle origini**<br /><br /> [![Mappa del Centro sicurezza: EKM](../../database-engine/media/security-center-map-ekm.png "mappa del Centro sicurezza: EKM")](http://msdn.microsoft.com/library/bb895340.aspx)<br /><br /> [![Centro sicurezza di eseguire il mapping di insieme di credenziali chiave di Azure](../../database-engine/media/security-center-map-key-vault.png "Centro sicurezza di eseguire il mapping di insieme di credenziali chiave di Azure")](http://azure.microsoft.com/documentation/articles/key-vault-get-started/)<br /><br /> **Colonne, dati e la crittografia con chiave**<br /><br /> [![Mappa del Centro sicurezza: crittografia mediante certificato](../../database-engine/media/security-center-map-cert.png "mappa del Centro sicurezza: crittografia mediante certificato")](http://msdn.microsoft.com/library/ms188061.aspx)<br /><br /> [![Mappa del Centro sicurezza: crittografia mediante chiave simmetrica](../../database-engine/media/security-center-map-sym-key.png "mappa del Centro sicurezza: crittografia mediante chiave simmetrica")](http://msdn.microsoft.com/library/ms174361.aspx)<br /><br /> [![Mappa del Centro sicurezza: crittografia mediante chiave asimmetrica](../../database-engine/media/security-center-map-asym-key.png "mappa del Centro sicurezza: crittografia mediante chiave asimmetrica")](http://msdn.microsoft.com/library/ms186950.aspx)<br /><br /> [![Mappa del Centro sicurezza: crittografia mediante Passphrase](../../database-engine/media/security-center-map-passphrase.png "mappa del Centro sicurezza: crittografia mediante Passphrase")](http://msdn.microsoft.com/library/ms190357.aspx)|**Protezione con firewall**<br /><br /> [![Mappa del Centro sicurezza PC Windows Firewall](../../database-engine/media/security-center-map-windows-firewall.png "mappa del Centro sicurezza PC Windows Firewall")](http://msdn.microsoft.com/library/ms175043.aspx)<br /><br /> [![Mappa del centro di sicurezza del servizio Firewall](../../database-engine/media/security-center-map-service-firewall.png "mappa Centro sicurezza: Firewall del servizio")](http://msdn.microsoft.com/library/azure/ee621782.aspx)<br /><br /> [![Mappa del Centro sicurezza: Database Firewall](../../database-engine/media/security-center-map-db-firewall.png "mappa Centro sicurezza: Firewall del Database")](http://msdn.microsoft.com/library/azure/ee621782.aspx)<br /><br /> **Crittografia dei dati in transito**<br /><br /> [![Mappa del Centro sicurezza: SSL forzato](../../database-engine/media/security-center-map-forced-ssl.png "mappa del Centro sicurezza: SSL forzato")](http://msdn.microsoft.com/library/ms191192.aspx)<br /><br /> [![Eseguire il mapping di centro di sicurezza SSL facoltativo](../../database-engine/media/security-center-map-opt-ssl.png "Centro sicurezza PC mappare SSL facoltative")](http://msdn.microsoft.com/library/ms191192.aspx)<br /><br /> ![Segnaposto](../../database-engine/media/security-center-map-blankplaceholder.png "segnaposto")<br /><br /> ![Segnaposto](../../database-engine/media/security-center-map-blankplaceholder.png "segnaposto")<br /><br /> ![Segnaposto](../../database-engine/media/security-center-map-blankplaceholder.png "segnaposto")<br /><br /> ![Segnaposto](../../database-engine/media/security-center-map-blankplaceholder.png "segnaposto")<br /><br /> ![Segnaposto](../../database-engine/media/security-center-map-blankplaceholder.png "segnaposto")<br /><br /> ![Segnaposto](../../database-engine/media/security-center-map-blankplaceholder.png "segnaposto")<br /><br /> ![Segnaposto](../../database-engine/media/security-center-map-blankplaceholder.png "segnaposto")|**Controllo automatizzato**<br /><br /> [![Centro sicurezza PC mappa SQL Server Audit](../../database-engine/media/security-center-map-sql-audit.png "Centro sicurezza PC mappa SQL Server Audit")](http://msdn.microsoft.com/library/cc280386.aspx)<br /><br /> [![Centro sicurezza PC mappa SQL Database Audit](../../database-engine/media/security-center-map-sqldb-audit.png "controllo del Database SQL mappa Centro sicurezza")](http://azure.microsoft.com/documentation/articles/sql-database-auditing-get-started/)<br /><br /> **Controllo personalizzato**<br /><br /> ![Segnaposto](../../database-engine/media/security-center-map-blankplaceholder.png "segnaposto")<br /><br /> [![Centro sicurezza PC mappa trigger](../../database-engine/media/security-center-map-triggers.png "trigger mappa Centro sicurezza")](http://msdn.microsoft.com/library/ms175941.aspx)<br /><br /> **Conformità**<br /><br /> [![SecCtrCompliance](../../database-engine/media/secctrcompliance.png "SecCtrCompliance")](http://azure.microsoft.com/support/trust-center/services/)<br /><br /> ![Segnaposto](../../database-engine/media/security-center-map-blankplaceholder.png "segnaposto")<br /><br /> ![Segnaposto](../../database-engine/media/security-center-map-blankplaceholder.png "segnaposto")<br /><br /> ![Segnaposto](../../database-engine/media/security-center-map-blankplaceholder.png "segnaposto")<br /><br /> ![Segnaposto](../../database-engine/media/security-center-map-blankplaceholder.png "segnaposto")<br /><br /> ![Segnaposto](../../database-engine/media/security-center-map-blankplaceholder.png "segnaposto")<br /><br /> ![Centro sicurezza: legenda](../../database-engine/media/security-center-map-legend.png "Centro sicurezza: legenda")|  
  
## <a name="links-to-specific-related-topics"></a>Collegamenti ad argomenti correlati specifici  
 ![Icona della cartella File piccola](../../integration-services/media/filefolder-small.gif "icona della cartella File piccola") **autenticazione: utente?**  
 **Che tipo di autenticazione (Windows o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)])**  
  
-   [Scegliere una modalità di autenticazione](choose-an-authentication-mode.md)  
  
 **Autenticazione a livello di database master** (account di accesso e utenti di database)  
  
-   [Creazione di un account di accesso di SQL Server](authentication-access/create-a-login.md)  
  
-   [Gestione di database e account di accesso in Database SQL di Azure](http://msdn.microsoft.com/library/ee336235.aspx)  
  
-   [Creazione di un utente di database](authentication-access/create-a-database-user.md)  
  
 **Eseguire l'autenticazione a livello di database utente**  
  
-   [Utenti di database indipendente: rendere portabile un database](contained-database-users-making-your-database-portable.md)  
  
 **Uso di altre identità**  
  
-   [Credenziali &#40;motore di database&#41;](authentication-access/credentials-database-engine.md)  
  
-   [Esecuzione con un altro account di accesso](/sql/t-sql/statements/execute-as-transact-sql)  
  
-   [Esecuzione con un altro utente di database](/sql/t-sql/statements/execute-as-transact-sql)  
  
 ![Icona della cartella File di piccole dimensioni](../../integration-services/media/filefolder-small.gif "icona della cartella File piccola") **crittografia: archiviazione dei dati segreti**  
 **Crittografia dei file**  
  
-   [BitLocker (a livello di unità)](http://support.microsoft.com/kb/2855131)  
  
-   [Crittografia NTFS (a livello di cartella)](http://msdn.microsoft.com/library/dd163562.aspx)  
  
-   [Transparent Data Encryption (a livello di file)](encryption/transparent-data-encryption.md)  
  
-   [Crittografia dei backup (a livello di file)](../backup-restore/backup-encryption.md)  
  
 **Crittografia delle origini**  
  
-   [Modulo Extensible Key Management](encryption/extensible-key-management-ekm.md)  
  
-   [Chiavi archiviate nell'insieme di credenziali di Azure](encryption/extensible-key-management-using-azure-key-vault-sql-server.md)  
  
 **Colonne, dati e la crittografia con chiave**  
  
-   [Crittografia mediante certificato](/sql/t-sql/functions/encryptbycert-transact-sql)  
  
-   [Crittografia mediante chiave asimmetrica](/sql/t-sql/functions/encryptbyasymkey-transact-sql)  
  
-   [Crittografia mediante chiave simmetrica](/sql/t-sql/functions/encryptbykey-transact-sql)  
  
-   [Crittografia mediante passphrase](/sql/t-sql/functions/encryptbypassphrase-transact-sql)  
  
 ![Icona della cartella File piccola](../../integration-services/media/filefolder-small.gif "icona della cartella File piccola") **autorizzazione: operazioni?**  
 **Concessione, revoca e negazione delle autorizzazioni**  
  
-   [Gerarchia delle autorizzazioni &#40;motore di database&#41;](permissions-hierarchy-database-engine.md)  
  
-   [Autorizzazioni](permissions-database-engine.md)  
  
-   [Entità a protezione diretta](securables.md)  
  
 **Sicurezza in base ai ruoli**  
  
-   [Ruoli a livello di server](authentication-access/server-level-roles.md)  
  
-   [Ruoli a livello di database](authentication-access/database-level-roles.md)  
  
 `Restricting Data Access to Selected Data Elements`  
  
-   Uso di [viste](../views/views.md) e [routine](../stored-procedures/stored-procedures-database-engine.md)per limitare l'accesso ai dati  
  
-   [Sicurezza a livello di riga](http://msdn.microsoft.com/library/azure/dn765131.aspx)  
  
-   [Mascheramento dati dinamici](http://azure.microsoft.com/documentation/articles/sql-database-dynamic-data-masking-get-started/)  
  
-   [Oggetti firmati](/sql/t-sql/statements/add-signature-transact-sql)  
  
 ![Icona della cartella File di piccole dimensioni](../../integration-services/media/filefolder-small.gif "icona della cartella File piccola") **sicurezza della connessione: limitazioni e sicurezza**  
 **Protezione con firewall**  
  
-   [Configurazione di Windows Firewall per l'accesso al Motore di database](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)  
  
-   [Impostazioni del firewall del database SQL di Azure](/sql/relational-databases/system-stored-procedures/sp-set-database-firewall-rule-azure-sql-database)  
  
-   [Impostazioni del firewall dei servizi di Azure](/sql/relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database)  
  
 **Crittografia dei dati in transito**  
  
-   [Secure Sockets Layer per il motore di database](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)  
  
-   [Secure Sockets Layer per il database SQL](https://msdn.microsoft.com/library/azure/ff394108.aspx)  
  
 ![Icona della cartella File di piccole dimensioni](../../integration-services/media/filefolder-small.gif "icona della cartella File piccola") **controllo: registrazione dell'accesso**  
 **Controllo automatizzato**  
  
-   [SQL Server Audit &#40;Database Engine&#41;](auditing/sql-server-audit-database-engine.md)  
  
-   [Controllo del database SQL](http://azure.microsoft.com/documentation/articles/sql-database-auditing-get-started/)  
  
 **Implementazione di controlli personalizzati**  
  
-   Creazione di [DDL Triggers](../triggers/ddl-triggers.md) e di [DML Triggers](../triggers/dml-triggers.md)  
  
 ![Icona della cartella File di piccole dimensioni](../../integration-services/media/filefolder-small.gif "icona della cartella File piccola") **conformità**  
 **SQL Server**  
  
-   [Criteri comuni](http://go.microsoft.com/fwlink/?LinkId=616319)  
  
 **Database SQL**  
  
-   [Centro protezione di Microsoft Azure: conformità per funzionalità](http://azure.microsoft.com/support/trust-center/services/)  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza di SQL Server](securing-sql-server.md)   
 [Entità &#40;motore di database&#41;](authentication-access/principals-database-engine.md)   
 [Certificati SQL Server e chiavi simmetriche](sql-server-certificates-and-asymmetric-keys.md)   
 [Crittografia di SQL Server](encryption/sql-server-encryption.md)   
 [Configurazione superficie di attacco](surface-area-configuration.md)   
 [Password complesse](strong-passwords.md)   
 [Proprietà di database TRUSTWORTHY](trustworthy-database-property.md)   
 [Caratteristiche e attività del motore di database](../../database-engine/database-engine-features-and-tasks.md)  
  
  
