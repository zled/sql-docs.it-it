---
title: Sicurezza per l'apprendimento di SQL Server | Microsoft Docs
description: Panoramica sulla sicurezza per il framework di estendibilità in SQL Server Machine Learning Services. Sicurezza per gli account utente e account di accesso, il servizio Launchpad di SQL Server, account di lavoro, che esegue più script e le autorizzazioni del file.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/10/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: bee8e2162c56ac1b26273873943d848c2167dbda
ms.sourcegitcommit: 485e4e05d88813d2a8bb8e7296dbd721d125f940
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/11/2018
ms.locfileid: "49100402"
---
# <a name="security-overview-for-the-extensibility-framework-in-sql-server-machine-learning-services"></a>Panoramica sulla sicurezza per il framework di estendibilità in SQL Server Machine Learning Services

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Questo articolo descrive l'architettura complessiva di sicurezza che consente di connettere il motore di database di SQL Server e i relativi componenti per il framework di estendibilità. Descrive le interazioni e parti di componente. 

<a name="launchpad"></a>

## <a name="sql-server-launchpad-service"></a>Servizio Launchpad di SQL Server

Per creare un'istanza di processi esterni, il motore di database fornisce il servizio Launchpad di SQL Server per creare una sessione di R o Python. Un oggetto separato [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] viene creato per l'istanza del motore di database a cui è stato aggiunto machine learning (R o Python) integrazione in SQL Server, un servizio per ogni istanza del servizio.

Per impostazione predefinita [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] è configurato per l'esecuzione **NT Service\MSSQLLaunchpad**, che viene eseguito il provisioning con tutte le autorizzazioni necessarie per eseguire gli script esterni. Rimozione delle autorizzazioni da questo account può comportare [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] Impossibile avviare o accedere all'istanza di SQL Server in cui devono essere eseguiti gli script esterni. Servizio LaunchPad viene in genere utilizzato come-è, ma per altre informazioni sulle opzioni configurabili, vedere [configurazione del servizio Launchpad di SQL Server](../security/sql-server-launchpad-service-account.md).

<a name="sqlrusergroup"></a>

## <a name="sqlrusergroup-and-worker-accounts"></a>Account SQLRUserGroup e ruolo di lavoro

Gli script esterni eseguiti in processi esterni, con l'identità dell'account di lavoro locali con privilegi minimi, soggette all'elenco di controllo di accesso (ACL) dell'elemento padre **SQLRUserGroup** (gruppo di utenti limitati SQL). 

**SQLRUserGroup** viene creato dal programma di installazione di SQL Server e contiene il pool di account utente di Windows locale. Quando è necessario un processo esterno, Launchpad richiede un account di lavoro disponibile e lo usa per eseguire un processo. In particolare, Launchpad attiva un account di lavoro disponibili, viene eseguito il mapping all'identità dell'utente chiamante ed esegue lo script con l'account di lavoro. 

+ **SQLRUserGroup** è collegato a un'istanza specifica. Per ogni istanza del computer in cui è stata abilitata l'apprendimento, è necessario un pool separato di account di lavoro. Gli account non possono essere condivisi tra istanze.

+ Le dimensioni del pool di account utente sono statica e il valore predefinito è 20, che supporta 20 sessioni simultanee. Il numero di sessioni del runtime esterni che possono essere avviate simultaneamente è limitato dalle dimensioni del pool di account utente. 

+ I nomi degli account di lavoro nel pool sono nel formato SQLInstanceName*nn*. Ad esempio, in un'istanza predefinita **SQLRUserGroup** contiene account denominato MSSQLSERVER01, MSSQLSERVER02 e così via in un massimo di MSSQLSERVER20.

Attività eseguita in parallelo non usano gli account aggiuntivi. Ad esempio, se un utente esegue un'attività di assegnazione dei punteggi che usa l'elaborazione parallela, viene riutilizzato lo stesso account di lavoro per tutti i thread. Se si prevede un uso massiccio di machine learning, è possibile aumentare il numero di account usato per eseguire gli script esterni. Per altre informazioni, vedere [modificare il pool di account utente per l'apprendimento](../../advanced-analytics/administration/modify-user-account-pool.md).

### <a name="permissions-granted-to-sqlrusergroup"></a>Autorizzazioni concesse a SQLRUserGroup

Per impostazione predefinita, i membri del **SQLRUserGroup** hanno autorizzazioni read ed execute sul file in SQL Server **Binn**, **R_SERVICES**, e **PYTHON_SERVICES** directory, con accesso a file eseguibili, librerie e set di dati incorporati nelle distribuzioni R e Python installate con SQL Server. 

Per proteggere le risorse sensibili in SQL Server, è possibile definire un elenco di controllo di accesso (ACL) che nega l'accesso **SQLRUserGroup**. Al contrario, potrebbe inoltre accadere di concedere le autorizzazioni alle risorse dati locali esistenti nel computer host, oltre a SQL Server. 

Per impostazione predefinita, **SQLRUserGroup** non dispone di un account di accesso di database o delle autorizzazioni per tutti i dati. In determinate circostanze, potrebbe voler creare un account di accesso per consentire le connessioni di back-ciclo, in particolare quando un'identità Windows attendibile è l'utente chiamante. Questa funzionalità è denominata [ *l'autenticazione implicita*](#implied-authentication). Per altre informazioni, vedere [aggiungere SQLRUserGroup come utente del database](../../advanced-analytics/security/add-sqlrusergroup-to-database.md).

::: moniker range=">=sql-server-ver15||=sqlallproducts-allversions"
### <a name="appcontainer-isolation-in-sql-server-2019"></a>Isolamento di AppContainer in SQL Server 2019

In SQL Server 2019, il programma di installazione non crea più account di lavoro per **SQLRUserGroup**. Al contrario, l'isolamento viene ottenuto tramite [AppContainers](https://docs.microsoft.com/windows/desktop/secauthz/appcontainer-isolation). In fase di esecuzione degli script incorporati o il codice quando viene rilevata in una stored procedure o query, SQL Server chiama Launchpad con una richiesta per un'utilità di avvio specifiche dell'estensione. Finestra di avvio richiama l'ambiente di runtime appropriato in un processo con la propria identità e crea un'istanza di un AppContainer per contenerlo. Questa modifica è vantaggiosa perché Gestione account e una password locale non è più necessaria. Inoltre, nelle installazioni dei componenti in cui non sono consentiti gli account utente locali, azzerare la dipendenza dall'account utente locale significa che è ora possibile usare questa funzionalità.

Come è implementato da SQL Server, AppContainers sono un meccanismo interno. Sono disponibili per constatare fisico AppContainers in Monitoraggio di processo, è possibile trovarli nelle regole del firewall in uscita create dal programma di installazione per impedire l'esecuzione di chiamate di rete di processi.

> [!Note]
> In SQL Server 2019, **SQLRUserGroup** ha solo un membro che è ora il singolo account di servizio Launchpad di SQL Server invece di più account di lavoro.
::: moniker-end

## <a name="user-security"></a>Sicurezza utente

Modello di sicurezza di SQL Server i dati dell'account di accesso di database e i ruoli estendere allo script R e Python. Gli account di accesso di database può basarsi su identità di Windows o un utente del database SQL Server. 

Come utente del database, se si dispone delle autorizzazioni per eseguire una determinata query, tutti gli script R o Python eseguito in SQL Server dispone anche dell'autorizzazione per recuperare gli stessi dati. La possibilità di utilizzare, creare e salvare database oggetti dipende dalle autorizzazioni di database. Per altre informazioni, vedere [consentire agli utenti di SQL Server Machine Learning Services](../../advanced-analytics/security/user-permission.md).

### <a name="mapping-user-identities-to-worker-accounts"></a>Mapping di identità utente per gli account di lavoro

Quando viene avviata una sessione, Launchpad viene eseguito il mapping di identità dell'utente chiamante a un account di lavoro. Il mapping di un utente esterno di Windows o un account di accesso SQL valido per un account di lavoro è valido solo per la durata del SQL stored procedure che esegue lo script esterno. Le query parallele dallo stesso account di accesso sono mappate allo stesso account utente di lavoro.

Durante l'esecuzione, Launchpad crea le cartelle temporanee per archiviare i dati della sessione, vengono eliminati quando la sessione si conclude. Le directory sono l'accesso limitato. Per R, RLauncher esegue questa attività. Per Python, PythonLauncher esegue questa attività. Ogni account di lavoro singoli sarà limitato alla propria cartella e non può accedere ai file nelle cartelle sopra il proprio livello. Tuttavia, l'account di lavoro può leggere, scrivere o eliminare gli elementi figlio sotto la cartella di lavoro di sessione che è stato creato. Un amministratore del computer può visualizzare le directory create per ogni processo. Ogni directory è identificata dal relativo GUID di sessione.

<a name="implied-authentication"></a>

### <a name="implied-authentication"></a>Autenticazione implicita

*L'autenticazione implicita* descrive il comportamento della richiesta di connessione in cui i processi esterni in esecuzione come account di lavoro con privilegi limitati vengono presentati come un'identità utente trusted a SQL Server in ciclo back-le richieste di dati o le operazioni. Come concetto, l'autenticazione implicita è univoco per l'autenticazione di Windows, le stringhe di connessione di SQL Server specificando una connessione trusted, nelle richieste che hanno origine da processi esterni, ad esempio script R o Python. Si è talvolta detta anche un *loopback*.

Le connessioni trusted sono utilizzabile dallo script R e Python, ma solo con una configurazione aggiuntiva. Nell'architettura di estendibilità, i processi R e Python eseguiti con account di lavoro, che eredita autorizzazioni dall'elemento padre **SQLRUserGroup**. Quando una stringa di connessione specifica "Trusted_Connection = True", l'identità dell'account del ruolo di lavoro viene presentato nella richiesta di connessione, ovvero come sconosciuta per impostazione predefinita per SQL Server. 

Per rendere le connessioni trusted ha esito positivo, è necessario creare un account di accesso di database per il **SQLRUserGroup**. Al termine dell'operazione, qualsiasi attendibile connessione da qualsiasi membro del **SQLRUserGroup** disponga dei diritti di accesso a SQL Server. Per istruzioni dettagliate, vedere [aggiungere SQLRUserGroup per un accesso al database](../../advanced-analytics/security/add-sqlrusergroup-to-database.md).

Le connessioni trusted non sono più ampiamente usata formulazione di una richiesta di connessione. Quando lo script R o Python specifica una connessione, può essere più comune usare un account di accesso SQL o un nome utente completo e una password se la connessione a un'origine dati ODBC.

#### <a name="how-implied-authentication-works-for-r-and-python-sessions"></a>Funzionamento dell'autenticazione come implicita per le sessioni di R e Python

Il diagramma seguente mostra l'interazione dei componenti di SQL Server con il runtime di R e come vengono eseguite l'autenticazione implicita per R.

![Autenticazione implicita per R](../security/media/implied-auth-rsql.png)

Il diagramma seguente mostra l'interazione dei componenti di SQL Server con il runtime di Python e il modo in cui avviene l'autenticazione implicita per Python.

![Autenticazione implicita per Python](../security/media/implied-auth-python2.png)

## <a name="no-support-for-transparent-data-encryption-at-rest"></a>Nessun supporto per Transparent Data Encryption inattivi

[Transparent Data Encryption (TDE)](../../relational-databases/security/encryption/transparent-data-encryption.md) non è supportata per i dati inviati o ricevuti dalla fase di esecuzione dello script esterno. Il motivo è che il processo esterno (R o Python) viene eseguito all'esterno del processo di SQL Server. Di conseguenza, i dati usati dal runtime esterno non sono protetto dalle funzionalità di crittografia del motore di database. Questo comportamento non è diverso rispetto a qualsiasi altro client in esecuzione nel computer SQL Server che legge i dati dal database e crea una copia.

Di conseguenza, la TDE **non è** applicate a tutti i dati usati in script R o Python, o a tutti i dati salvati su disco, o ai risultati intermedi persistenti. Tuttavia, altri tipi di crittografia, ad esempio la crittografia BitLocker di Windows o terze parti applicata a livello di file o una cartella, vengono mantenuti.

Nel caso del [Always Encrypted](../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md), runtime esterni non hanno accesso alle chiavi di crittografia. Di conseguenza, i dati non è possibile inviare agli script.


## <a name="next-steps"></a>Passaggi successivi

In questo articolo si è appreso i componenti e il modello di interazione dell'architettura di sicurezza integrate le [framework di estendibilità](../../advanced-analytics/concepts/extensibility-framework.md). Punti chiave trattati in questo articolo includono lo scopo dell'account di lavoro, SQLRUserGroup e Launchpad, isolamento dei processi di R e Python e il mapping tra le identità degli utenti e account di lavoro. 

Come passaggio successivo, esaminare le istruzioni relative [concessione di autorizzazioni](../../advanced-analytics/security/user-permission.md). Per i server che usano l'autenticazione di Windows, è inoltre necessario esaminare [aggiungere SQLRUserGroup per un accesso al database](../../advanced-analytics/security/add-sqlrusergroup-to-database.md) per informazioni su quando è necessaria una configurazione aggiuntiva.