---
title: Considerazioni sulla sicurezza per machine learning in SQL Server | Documenti Microsoft
ms.date: 11/16/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d5065197-69e6-4fce-9654-00acaecc148b
caps.latest.revision: "15"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: a32980d02215435e5bbcc3a2ca0f95b3f57f8d14
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/01/2017
---
# <a name="security-considerations-for-machine-learning-in-sql-server"></a>Considerazioni sulla sicurezza per machine learning in SQL Server

Questo articolo illustra considerazioni sulla sicurezza che l'amministratore o un architetto tenere presente quando si utilizza servizi di machine learning.

**Si applica a:** R Services SQL Server 2016, SQL Server 2017 di Machine Learning Services

## <a name="use-a-firewall-to-restrict-network-access"></a>Usa un firewall per limitare l'accesso alla rete

In un'installazione predefinita, una regola del firewall di Windows viene utilizzata per bloccare l'accesso di rete in uscita da processi esterni di runtime. Le regole del firewall devono essere create per evitare che i processi del runtime esterno scarichi pacchetti o effettui altre chiamate di rete che potrebbero essere potenzialmente dannose.

Se si utilizza un programma firewall diverso, è anche possibile creare regole per bloccare la connessione di rete in uscita per il runtime esterni, impostando regole per gli account utente locale o per il gruppo rappresentato dal pool di account utente.

Si consiglia di attivare Windows Firewall (o un altro firewall di propria scelta) per impedire l'accesso alla rete senza restrizioni per i runtime R o Python.

## <a name="authentication-methods-supported-for-remote-compute-contexts"></a>Metodi di autenticazione supportati per i contesti di calcolo remoto

[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]supporta gli account di accesso sia l'autenticazione integrata di Windows e SQL durante la creazione di connessioni tra [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e un client di analisi scientifica dei dati remota.

Ad esempio, si sviluppa una soluzione di R in un computer portatile e per eseguire calcoli sul computer SQL Server. Creare un'origine dati di SQL Server in R, usando il **rx** funzioni e la definizione di una stringa di connessione in base alle credenziali di Windows.

Quando si modifica il _contesto di calcolo_ dal portatile al computer SQL Server, viene eseguito tutto il codice R nel computer SQL Server, se l'account di Windows disponga delle autorizzazioni necessarie. Inoltre, qualsiasi query SQL eseguite come parte del codice R vengono eseguite anche le credenziali.

In questo scenario è inoltre supportato l'utilizzo di account di accesso SQL. Tuttavia, ciò richiede che l'istanza di SQL Server deve essere configurata per consentire l'autenticazione in modalità mista.

### <a name="implied-authentication"></a>Autenticazione implicita

 In generale, il [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] avvia la fase di esecuzione dello script esterno ed esegue gli script con il proprio account. Tuttavia, se il runtime esterno effettua una chiamata ODBC, il [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] rappresenta le credenziali dell'utente che ha inviato il comando per assicurarsi che la chiamata ODBC non abbiano esito negativo. In questo caso si parla di *autenticazione implicita*.
 
 > [!IMPORTANT]
 > Affinché l'autenticazione implicita abbia esito positivo, il gruppo di utenti Windows che contiene gli account di lavoro (per impostazione predefinita, **SQLRUser**) deve avere un account nel database master per l'istanza e questo account deve disporre delle autorizzazioni per connettersi all'istanza.
 > 
 > Il gruppo **SQLRUser** viene utilizzato anche quando l'esecuzione di script Python. 

In generale, è consigliabile che è possibile spostare in anticipo i set di dati più grande in SQL Server anziché tentare di leggere i dati utilizzando RODBC o un'altra raccolta. Inoltre, utilizzare una query di SQL Server o una vista come origine dati primaria, per ottenere prestazioni migliori. 

Ad esempio, si potrebbe ottenere i dati di training (in genere i dati più grande) da SQL Server e ottenere un elenco dei fattori da un'origine esterna. È possibile definire un server collegato per ottenere dati da origini di dati ODBC. Per ulteriori informazioni, vedere [creare un server collegato](https://docs.microsoft.com/sql/relational-databases/linked-servers/create-linked-servers-sql-server-database-engine).

Per ridurre la dipendenza da chiamate ODBC alle origini dati esterne, è anche possibile engineering dati come un processo distinto, eseguire e salvare i risultati in una tabella o utilizzare T-SQL. Vedere l'esercitazione per un buon esempio di progettazione di dati in Visual Studio SQL. R: [creare funzionalità di dati con T-SQL](../tutorials/sqldev-create-data-features-using-t-sql.md).

## <a name="no-support-for-encryption-at-rest"></a>Nessun supporto per la crittografia inattivi

[Transparent Data Encryption (TDE)](https://docs.microsoft.com/sql/relational-databases/security/encryption/transparent-data-encryption) non è supportata per i dati inviati o ricevuti dalla fase di esecuzione dello script esterno. Il motivo è che R (o Python) viene eseguito all'esterno del processo di SQL Server; di conseguenza, dati utilizzati dal runtime esterno non è protetto dalle funzionalità di crittografia del motore di database.  Questo comportamento non è diverso rispetto a qualsiasi altro client in esecuzione nel computer SQL Server che legge i dati dal database e crea una copia.

Di conseguenza, TDE **non** applicata a tutti i dati utilizzati negli script R o Python o a tutti i dati salvati su disco, o ai risultati intermedi persistenti. Tuttavia, altri tipi di crittografia, ad esempio la crittografia BitLocker di Windows o terze parti applicata a livello di file o una cartella, vengono mantenuti.

In caso di [Always Encrypted](https://docs.microsoft.com/sql/relational-databases/security/encryption/overview-of-key-management-for-always-encrypted), runtime esterni non hanno accesso alle chiavi di crittografia; pertanto, i dati non è possibile inviare agli script.

## <a name="resources"></a>Risorse

Per ulteriori informazioni sulla gestione del servizio e su come eseguire il provisioning di account utente utilizzato per eseguire gli script di machine learning, vedere [configurare e gestire le estensioni Analitica avanzate](../../advanced-analytics/r/configure-and-manage-advanced-analytics-extensions.md).

Per una spiegazione dell'architettura di sicurezza generali, vedere:

+ [Panoramica sulla sicurezza per R](security-overview-sql-server-r.md)
+ [Cenni preliminari sulla sicurezza per Python](../python/security-overview-sql-server-python-services.md)
