---
title: TDE - Bring Your Own Key (BYOK) - Azure SQL | Microsoft Docs
description: Supporto di BYOK (Bring Your Own Key) per TDE (Transparent Data Encryption) con Azure Key Vault per database e data warehouse SQL. Panoramica di TDE con BYOK, vantaggi, funzionamento, considerazioni e consigli.
keywords: 
services: sql-database
documentationcenter: 
author: aliceku
manager: craigg
editor: 
ms.assetid: 
ms.service: sql-database
ms.custom: security
ms.workload: Inactive
ms.tgt_pltfrm: 
ms.devlang: na
ms.topic: article
ms.date: 11/15/2017
ms.author: aliceku
ms.openlocfilehash: 5a0b56974d85f63e3382f26b1388e7d30dfbd6f8
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="transparent-data-encryption-with-bring-your-own-key-support-for-azure-sql-database-and-data-warehouse"></a>Transparent Data Encryption con supporto Bring Your Own Key per i database e data warehouse SQL di Azure
[!INCLUDE[appliesto-xx-asdb-xxxx-xxx-md](../../../includes/appliesto-xx-asdb-xxxx-xxx-md.md)]

Il supporto di Bring Your Own Key (BYOK) per [Transparent Data Encryption (TDE)](transparent-data-encryption.md) consente all'utente di assumere il controllo delle chiavi di crittografia TDE personali e di limitare chi può accedervi e quando. [Azure Key Vault](https://docs.microsoft.com/azure/key-vault/key-vault-secure-your-key-vault), il sistema di Azure per la gestione delle chiavi esterne basato sul cloud, è il primo servizio di gestione delle chiavi che offre TDE con il supporto integrato per BYOK. Con BYOK, la chiave di crittografia del database è protetta da una chiave asimmetrica archiviata in Key Vault. La chiave asimmetrica viene impostata a livello di server ed ereditata da tutti i database presenti nel server. 

Con il supporto BYOK, gli utenti possono ora controllare le attività di gestione delle chiavi, tra cui le rotazioni delle chiavi, le autorizzazioni dell'insieme di credenziali delle chiavi e l'eliminazione delle chiavi, nonché abilitare il controllo e la creazione di report relativi a tutte le chiavi di crittografia. Key Vault consente di gestire le chiavi in modo centralizzato, usa moduli di protezione hardware accuratamente monitorati e consente la separazione delle responsabilità tra la gestione delle chiavi e quella dei dati per contribuire a soddisfare la conformità alle normative. 

TDE con BYOK offre i vantaggi seguenti:
- Maggiore trasparenza e un controllo granulare con la possibilità di gestire in autonomia la protezione TDE   
- Gestione centralizzata delle chiavi di crittografia TDE (con altre chiavi e segreti usati in altri servizi di Azure), ospitate in Key Vault
- Separazione dei ruoli di gestione delle chiavi e dei dati all'interno dell'organizzazione, per supportare la separazione delle responsabilità
- Maggiore fiducia da parte dei clienti, poiché Key Vault è progettato in modo tale che Microsoft non vede né estrae chiavi di crittografia. 
- Supporto per la rotazione delle chiavi

> [!IMPORTANT]
> Per chi usa la protezione TDE gestita dal servizio e vuole iniziare a usare Key Vault, la protezione TDE rimane attiva durante il passaggio a una chiave di Key Vault. Non esistono tempi di inattività e non viene rieseguita la crittografia dei file di database. Il passaggio da una chiave gestita dal servizio a una chiave di Key Vault richiede l'esecuzione di una nuova crittografia della chiave di crittografia del database, che è una rapida operazione online.
>

## <a name="how-does-tde-with-byok-support-work"></a>Come funziona TDE con il supporto BYOK?
 
![Autenticazione del server per Key Vault](./media/transparent-data-encryption-byok-azure-sql/tde-byok-server-authentication-flow.PNG)

Quando TDE è configurato per l'uso di una chiave di Key Vault, il server invia a Key Vault la chiave di crittografia del database di ogni database abilitato per TDE per una richiesta *wrap key*. Key Vault restituisce la chiave di crittografia del database crittografato, che è archiviata nel database utente. 

È importante notare che **una chiave archiviata in Key Vault rimane sempre in Key Vault**. Una chiave basata su un modulo di protezione hardware (HSM) in Key Vault rimane sempre entro i limiti della protezione HSM. Il server può inviare richieste di operazioni relative alla chiave solo al materiale della chiave di protezione TDE all'interno di Key Vault. L'amministratore di Key Vault ha il diritto di revocare le autorizzazioni di Key Vault per il server in qualsiasi momento e in questo caso tutte le connessioni al server vengono interrotte. 

## <a name="considerations"></a>Considerazioni

L'uso di TDE con BYOK comporta un maggior impegno da parte dell'utente in termini di attività di gestione e di costi correlati all'uso dell'insieme di credenziali delle chiavi. Queste considerazioni sono trattate nelle due sezioni successive.

### <a name="key-management-responsibilities"></a>Responsabilità di gestione delle chiavi

Assumere la gestione delle chiavi di crittografia delle risorse di un'applicazione è una responsabilità importante. Se gestisce la protezione TDE con supporto BYOK usando Key Vault, l'utente si assume le seguenti responsabilità riguardo alla gestione delle chiavi:
- **Rotazioni delle chiavi:** le protezioni TDE devono essere ruotate in base ai criteri interni o ai requisiti di conformità. Le rotazioni delle chiavi possono essere eseguite usando l'insieme di credenziali delle chiavi della protezione TDE.  
- **Autorizzazioni dell'insieme di credenziali delle chiavi**: il provisioning delle autorizzazioni di Key Vault viene eseguito a livello di server e di insieme di credenziali delle chiavi. Le autorizzazioni del server per un insieme di credenziali delle chiavi possono essere revocate in qualsiasi momento usando i criteri di accesso dell'insieme di credenziali.
- **Eliminazione di chiavi**: le chiavi possono essere eliminate da Key Vault e dal server SQL per garantire una maggiore sicurezza o rispettare i requisiti di conformità.
- **Controllo/creazione di report per tutte le chiavi di crittografia**: Key Vault offre log che si inseriscono facilmente in altri strumenti per la gestione delle informazioni e degli eventi relativi alla sicurezza (SIEM). [Log Analytics](https://docs.microsoft.com/azure/log-analytics/log-analytics-azure-key-vault) di Operations Management Suite (OMS) è un esempio di servizio già integrato.

### <a name="pricing-considerations"></a>Considerazioni sui prezzi 

TDE con supporto BYOK è una funzionalità di protezione integrata nel database e data warehouse SQL di Azure senza tariffe aggiuntive. Tuttavia, esistono costi correlati all'uso di Key Vault. Le operazioni di Key Vault eseguite dal server vengono addebitate come normali operazioni per l'insieme di credenziali in base alle [tariffe](https://azure.microsoft.com/pricing/details/key-vault/) previste per Key Vault. Il server invia le richieste a Key Vault per gli eventi seguenti:
- Riavvio dell'istanza SQL
- Rollover delle chiavi
- Ogni 6 ore per verificare se sono state apportate modifiche alle autorizzazioni del server per l'insieme di credenziali delle chiavi

## <a name="important-warnings"></a>Avvisi importanti

### <a name="loss-of-access-to-keys"></a>Perdita dell'accesso alle chiavi

Dal momento in cui un server non ha più accesso alla protezione TDE, perché sono state rimosse autorizzazioni di Key Vault o una chiave è stata eliminata, **tutte le connessioni ai database crittografati nel server vengono bloccate e i database vengono portati offline ed eliminati entro 24 ore**. I backup meno recenti crittografati con la chiave non disponibile non sono più accessibili. Se c'è la possibilità che una chiave sia stata compromessa, ad esempio se un servizio o un utente accede alla chiave senza autorizzazione, è consigliabile eliminare la chiave seguendo le istruzioni su come [rimuovere una chiave potenzialmente compromessa](transparent-data-encryption-byok-azure-sql-remove-tde-protector.md). I database devono essere eliminati prima di eliminare una protezione TDE attiva per evitare potenziali perdite di dati relativi a fino 10 minuti di attività.  

### <a name="expired-keys"></a>Chiavi scadute

Poiché la disponibilità della protezione TDE influisce direttamente sulla disponibilità del database, non è consentito aggiungere una chiave con data di scadenza a un server SQL. Se una chiave viene già usata come protezione TDE per un server e successivamente viene configurata con una data di scadenza in Azure Key Vault, **quando la chiave scade i database crittografati non hanno più accesso alla relativa protezione TDE e vengono rimossi entro 24 ore.**

### <a name="deleted-server-identities"></a>Identità del server eliminate 

L'accesso di un server a Key Vault è gestito usando l'identità Azure Active Directory (AAD) univoca del server. Se l'identità del server viene eliminata da AAD, il server perde quindi l'accesso ai propri insiemi di credenziali delle chiavi. Di conseguenza, **tutte le connessioni ai database crittografati nel server vengono bloccate e i database vengono portati offline ed eliminati entro 24 ore.**

## <a name="limitations"></a>Limitazioni

Gli insiemi di credenziali delle chiavi usati per TDE devono essere nello stesso tenant di Azure Active Directory del server del database o data warehouse SQL. Le interazioni tra tenant di insieme di credenziali delle chiavi e server non sono supportate. Una risorsa che viene crittografata con una chiave di Key Vault non può essere spostata tra sottoscrizioni di Azure. Lo spostamento della risorsa tra le sottoscrizioni interrompe i controlli di accesso necessari di Key Vault che hanno reso possibile la protezione TDE con BYOK. Se si devono spostare risorse in un'altra sottoscrizione, modificare la modalità TDE da BYOK a [TDE gestita dal servizio](transparent-data-encryption-azure-sql.md). 

Le protezioni TDE univoche per un database o data warehouse non sono supportate. La protezione TDE è impostata a livello di server e viene ereditata da tutte le risorse del server. 

## <a name="guidelines-for-managing-encrypted-databases"></a>Linee guida per la gestione dei database crittografati

### <a name="high-availability-and-disaster-recovery"></a>Disponibilità elevata e ripristino di emergenza
  
Esistono due modalità di configurazione della replica geografica per i server con Key Vault: 

- **Insieme di credenziali delle chiavi separato**: ogni server ha accesso a un insieme di credenziali delle chiavi separato, idealmente ognuno all'interno della propria area di Azure. Questa è la configurazione consigliata, poiché ogni server ha una propria copia della protezione TDE per i database con replica geografica crittografati. Se una delle aree di Azure del server è offline, gli altri server possono continuare ad accedere ai database con replica geografica.   

- **Insieme di credenziali delle chiavi condiviso**: tutti i server condividono lo stesso insieme di credenziali delle chiavi. Questa configurazione è più semplice da configurare, ma se l'area di Azure in cui si trova l'insieme di credenziali delle chiavi passa in modalità offline, nessun server sarà più in grado di leggere i database con replica geografica crittografati o i propri database crittografati. 
 
Per iniziare, usare il cmdlet [Add-AzureRmSqlServerKeyVaultKey](/powershell/module/azurerm.sql/add-azurermsqlserverkeyvaultkey) per aggiungere la chiave Key Vault di ogni server agli altri server nel collegamento alla replica geografica.  
Un esempio di ID chiave di Key Vault: *https://contosokeyvault.vault.azure.net/keys/Key1/1a1a2b2b3c3c4d4d5e5e6f6f7g7g8h8h*

   ```powershell
   <# Include the version guid in the KeyId #>
   Add-AzureRmSqlServerKeyVaultKey `
   -KeyId <KeyVaultKeyId> `
   -ServerName <LogicalServerName> `
   -ResourceGroup <SQLDatabaseResourceGroupName>
   ```

>[!NOTE]
>La lunghezza combinata dei caratteri del nome dell'insieme di credenziali delle chiavi e del nome della chiave non può superare 94 caratteri.
>

Seguire i passaggi nella [panoramica sulla replica geografica attiva](https://docs.microsoft.com/azure/sql-database/sql-database-geo-replication-overview) per configurare la replica geografica attiva con questi server e attivare un failover.  

### <a name="backup-and-restore"></a>Backup e ripristino

Se un database viene crittografato con TDE usando una chiave di Key Vault, vengono crittografati con la stessa protezione TDE anche gli eventuali backup generati.

Per ripristinare un backup crittografato con una protezione TDE di Key Vault, verificare che il materiale della chiave sia ancora nell'insieme di credenziali originale con il nome originale della chiave. Quando la protezione TDE viene modificata per un database, i backup più datati del database **non** vengono aggiornati in modo da usare la protezione TDE più recente. È quindi consigliabile mantenere tutte le versioni precedenti della protezione TDE in Key Vault in modo che sia possibile ripristinare i backup del database. 

Se una chiave che potrebbe essere necessaria per ripristinare un backup non è più nell'insieme di credenziali delle chiavi originale, un messaggio di errore indica che il server di destinazione <Servername> non ha accesso a tutti gli URI AKV creati tra <Timestamp #1> e <Timestamp #2>. e che è possibile ritentare l'operazione dopo il ripristino di tutti gli URI AKV.

Per evitare questo problema, eseguire il cmdlet [Get-AzureRmSqlServerKeyVaultKey](/powershell/module/azurerm.sql/get-azurermsqlserverkeyvaultkey) per restituire l'elenco delle chiavi di Key Vault aggiunte al server. Per garantire che tutti i backup possano essere ripristinati, verificare che il server di destinazione per il backup abbia accesso a tutte queste chiavi.

   ```powershell
   Get-AzureRmSqlServerKeyVaultKey `
   -ServerName <LogicalServerName> `
   -ResourceGroup <SQLDatabaseResourceGroupName>
   ```
Per altre informazioni sul ripristino dei backup per il database SQL, vedere [Ripristinare un database SQL di Azure mediante i backup automatici del database](https://docs.microsoft.com/azure/sql-database/sql-database-recovery-using-backups). Per altre informazioni sul ripristino dei backup per il data warehouse SQL, vedere [Ripristino di SQL Data Warehouse](https://docs.microsoft.com/azure/sql-data-warehouse/sql-data-warehouse-restore-database-overview).

## <a name="best-practices"></a>Procedure consigliate

### <a name="key-management"></a>Gestione delle chiavi 

Per garantire un recupero rapido delle chiavi e l'accesso ai dati all'esterno di Azure, si consiglia quanto segue:
- Creare la chiave di crittografia in locale in un dispositivo HSM locale. Verificare che si tratti di una chiave RSA 2048 asimmetrica, in modo che possa essere archiviata in Azure Key Vault.
- Importare il file della chiave di crittografia (PFX, BYOK o BACKUP) in Azure Key Vault. Valutare la possibilità di usare un insieme di credenziali chiave con [eliminazione temporanea](https://docs.microsoft.com/azure/key-vault/key-vault-ovw-soft-delete) abilitata, per la protezione del ripristino in caso di eliminazione accidentale della chiave.
- Prima di usare la chiave nell'insieme di credenziali delle chiavi di Azure per la prima volta, eseguire un backup di questa chiave. Altre informazioni sul comando [Backup-AzureKeyVaultKey](https://msdn.microsoft.com/library/mt126292.aspx) .
- Ogni volta che vengono apportate modifiche alla chiave, ad esempio si aggiungono elenchi di controllo di accesso, tag o attributi chiave, assicurarsi di eseguire un altro backup della chiave di Azure Key Vault.
- Durante un rollover della chiave, **mantenere le versioni precedenti della chiave** nell'insieme di credenziali delle chiavi in modo che si possano ripristinare i backup meno recenti dei database. 

Creare prima la chiave di crittografia TDE a livello locale e quindi importare la chiave asimmetrica è una procedura vivamente consigliata per gli scenari di produzione poiché consente all'amministratore di depositare la chiave in un sistema di deposito delle chiavi. Se la chiave asimmetrica viene creata in Azure Key Vault, non potrà essere depositata perché la chiave privata non può mai lasciare l'insieme di credenziali. È consigliabile depositare le chiavi usate per proteggere i dati critici. Se si perde una chiave asimmetrica, non sarà più possibile recuperare i dati.

### <a name="pre-configuration-for-replicated-databases"></a>Pre-configurazione per i database replicati

Se un database crittografato viene replicato in un altro server, verificare che il server abbia accesso a una copia del materiale della chiave di Key Vault usato nell'altro server **prima** di spostare o replicare il database.  

È consigliabile consentire a ogni server l'accesso a una copia del materiale relativo alle chiavi di Key Vault usato nell'altro server, che viene archiviato in un insieme di credenziali delle chiavi separato (idealmente ognuno nella stessa area di Azure del server). Con questa configurazione, ogni server ha una propria copia della protezione TDE per i database replicati crittografati. Se una delle aree di Azure dei server è offline, gli altri server possono continuare ad accedere ai database replicati.

## <a name="next-steps"></a>Passaggi successivi

- Per un'introduzione al supporto Bring Your Own Key (BYOK) per TDE, vedere [PowerShell: abilitare TDE usando la propria chiave di Azure Key Vault](transparent-data-encryption-byok-azure-sql-configure.md)
- Per informazioni su come eseguire la rotazione della protezione TDE di un server per soddisfare i criteri di sicurezza, vedere [Ruotare la protezione Transparent Data Encryption (TDE) con PowerShell](transparent-data-encryption-byok-azure-sql-key-rotation.md)
- In caso di eventi di sicurezza imprevisti, vedere le indicazioni su come [rimuovere una protezione TDE potenzialmente compromessa](transparent-data-encryption-byok-azure-sql-remove-tde-protector.md) 
