---
title: Considerazioni sulla sicurezza per machine learning in SQL Server | Documenti Microsoft
ms.custom:
- SQL2016_New_Updated
ms.date: 07/31/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d5065197-69e6-4fce-9654-00acaecc148b
caps.latest.revision: 15
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d9b5fba856cc40c11f218faf0a61f66ee5451aa4
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="security-considerations-for-machine-learning-in-sql-server"></a>Considerazioni sulla sicurezza per machine learning in SQL Server

Questo articolo illustra considerazioni sulla sicurezza che l'amministratore o un architetto tenere presente quando si utilizza servizi di machine learning.

**Si applica a:** R Services SQL Server 2016, SQL Server 2017 di Machine Learning Services

## <a name="use-a-firewall-to-restrict-network-access-by-r"></a>Usa un firewall per limitare l'accesso alla rete per R

In un'installazione predefinita, una regola del firewall di Windows viene utilizzata per bloccare l'accesso di rete in uscita da processi del runtime R. È consigliabile creare regole del firewall per impedire che il processo del runtime R scarichi pacchetti o effettui altre chiamate di rete che potrebbero essere potenzialmente dannose.

Se si usa un programma firewall diverso, è anche possibile creare regole per bloccare la connessione di rete in uscita per il runtime R, impostando regole per gli account utente locali o per il gruppo rappresentato dal pool di account utente.

Si consiglia di attivare Windows Firewall (o un altro firewall di propria scelta) per impedire l'accesso alla rete libero per i runtime R o Python.

## <a name="authentication-methods-supported-for-remote-compute-contexts"></a>Metodi di autenticazione supportati per i contesti di calcolo remoto

[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]supporta gli account di accesso sia l'autenticazione integrata di Windows e SQL durante la creazione di connessioni tra [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e un client di analisi scientifica dei dati remota.

Se ad esempio si sta sviluppando una soluzione R nel computer portatile e si vuole eseguire i calcoli nel computer SQL Server, è necessario creare un'origine dati di SQL Server in R, usando le funzioni **rx** e definendo una stringa di connessione basata sulle credenziali di Windows.

Quando si modifica il _contesto di calcolo_ dal portatile al computer SQL Server, se l'account di Windows disponga delle autorizzazioni necessarie, viene eseguito tutto il codice R nel computer SQL Server. Inoltre, qualsiasi query SQL eseguite come parte del codice R vengono eseguite anche le credenziali.

L'utilizzo di account di accesso SQL è supportata anche in questo scenario, che è necessario che l'istanza di SQL Server sia configurato per consentire l'autenticazione in modalità mista.

### <a name="implied-authentication"></a>Autenticazione implicita

 In generale, il [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] avvia la fase di esecuzione dello script esterno ed esegue gli script con il proprio account. Tuttavia, se il runtime esterno effettua una chiamata ODBC, il [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] rappresenta le credenziali dell'utente che ha inviato il comando per assicurarsi che la chiamata ODBC non abbiano esito negativo. In questo caso si parla di *autenticazione implicita*.
 
 > [!IMPORTANT]
 >
 > Affinché l'autenticazione implicita abbia esito positivo, il gruppo di utenti Windows che contiene gli account di lavoro (per impostazione predefinita, **SQLRUser**) deve avere un account nel database master per l'istanza e questo account deve disporre delle autorizzazioni per connettersi all'istanza.
 > 
 > Il gruppo **SQLRUser** viene utilizzato anche quando l'esecuzione di script Python. 

## <a name="no-support-for-encryption-at-rest"></a>Nessun supporto per la crittografia inattivi

Transparent Data Encryption non è supportata per i dati inviati o ricevuti dalla fase di esecuzione dello script esterno. Di conseguenza, la crittografia **non** essere applicato a tutti i dati utilizzati negli script R o Python, nonché ai dati salvati su disco o ai risultati intermedi persistenti.

## <a name="resources"></a>Risorse

Per ulteriori informazioni sulla gestione del servizio e su come eseguire il provisioning di account utente utilizzato per eseguire gli script R, vedere [configurare e gestire le estensioni Analitica avanzate](../../advanced-analytics/r/configure-and-manage-advanced-analytics-extensions.md).

Per una descrizione dell'architettura di sicurezza, vedere:

+ [Panoramica sulla sicurezza per R](security-overview-sql-server-r.md)
+ [Cenni preliminari sulla sicurezza per Python](../python/security-overview-sql-server-python-services.md)
