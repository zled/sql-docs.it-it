---
title: Considerazioni sulla sicurezza per il Driver SQL PHP | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: php
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: security considerations
ms.assetid: a8c1a570-9204-454f-b94c-ba34f54d487c
caps.latest.revision: "37"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6e60c87b9ec5f327460cdbc781ed40cb4a75edb0
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/18/2017
---
# <a name="security-considerations-for-php-sql-driver"></a>Considerazioni sulla sicurezza per il driver SQL PHP
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

In questo argomento vengono descritte considerazioni sulla sicurezza specifiche per lo sviluppo, la distribuzione e l'esecuzione di applicazioni che usano [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]. Per informazioni più dettagliate sulla sicurezza di SQL Server, vedere la pagina relativa a [sicurezza e conformità](http://go.microsoft.com/fwlink/?LinkId=129225).  
  
## <a name="connect-using-windows-authentication"></a>Connettersi con l'autenticazione di Windows  
L'autenticazione di Windows deve essere usata per connettersi a SQL Server ogni volta che è possibile per i motivi seguenti:  
  
-   **Durante l'autenticazione le credenziali non vengono trasmesse attraverso la rete.** Nomi utente e password non sono incorporati nella stringa di connessione al database. In questo modo utenti non autorizzati o malintenzionati non possono ottenere le credenziali monitorando la rete o visualizzando le stringhe di connessione nei file di configurazione.  
  
-   **Gli utenti sono soggetti a una gestione centralizzata degli account.** Vengono applicati criteri di sicurezza, ad esempio i periodi di scadenza delle password, la lunghezza minima delle password e il blocco degli account dopo più richieste di accesso non valide.  
  
Per informazioni su come connettersi a un server con l'autenticazione di Windows, vedere [Procedura: Connessione con l'autenticazione di Windows](../../connect/php/how-to-connect-using-windows-authentication.md).  
  
Quando ci si connette tramite l'autenticazione di Windows, è consigliabile configurare l'ambiente in modo che SQL Server possa usare il protocollo di autenticazione Kerberos. Per altre informazioni, vedere [Come assicurarsi che si utilizza l'autenticazione Kerberos quando si crea una connessione remota a un'istanza di SQL Server 2005](http://go.microsoft.com/fwlink/?LinkId=121862) o [Autenticazione Kerberos e SQL Server](http://go.microsoft.com/fwlink/?LinkId=129226).  
  
## <a name="use-encrypted-connections-when-transferring-sensitive-data"></a>Usare connessioni crittografate durante il trasferimento di dati sensibili  
È necessario usare connessioni crittografate ogni volta che si inviano o si recuperano dati sensibili da SQL Server. Per informazioni su come abilitare connessioni crittografate, vedere [come abilitare connessioni crittografate al motore di Database (Gestione configurazione SQL Server)](http://go.microsoft.com/fwlink/?LinkId=121864). Per stabilire una connessione protetta con [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)], usare l'attributo di connessione Encrypt durante la connessione al server. Per altre informazioni sugli attributi di connessione, vedere [Connection Options](../../connect/php/connection-options.md).  
  
## <a name="use-parameterized-queries"></a>Usare query con parametri  
Per ridurre il rischio di attacchi intrusivi nel codice SQL, usare query con parametri. Per esempi di esecuzione di query con parametri, vedere [How to: Perform Parameterized Queries](../../connect/php/how-to-perform-parameterized-queries.md).  
  
Per altre informazioni sugli attacchi intrusivi nel codice SQL e considerazioni di sicurezza correlate, vedere [Attacco intrusivo nel codice SQL](http://go.microsoft.com/fwlink/?LinkId=104224).  
  
## <a name="do-not-accept-server-or-connection-string-information-from-end-users"></a>Non accettare informazioni relative a server o stringhe di connessione da utenti finali  
Il codice dell'applicazione deve evitare che gli utenti finali possano inviare informazioni relative a server o stringhe di connessione all'applicazione stessa. Mantenendo uno stretto controllo sulle informazioni relative a server o a stringhe di connessione si riduce l'esposizione agli attacchi di attività dannose.  
  
## <a name="turn-warningsaserrors-on-during-application-development"></a>Attivare WarningsAsErrors durante lo sviluppo di applicazioni  
Sviluppare applicazioni con l'impostazione **WarningsAsErrors** su **true** in modo che gli avvisi generati dal driver vengano considerati errori. Ciò consente allo sviluppatore di risolvere gli avvisi prima di distribuire l'applicazione. Per altre informazioni, vedere [Handling Errors and Warnings](../../connect/php/handling-errors-and-warnings.md).  
  
## <a name="secure-logs-for-deployed-application"></a>Proteggere i log delle applicazioni distribuite  
Per le applicazioni distribuite, assicurarsi che i log vengano scritti in un percorso protetto o che la registrazione sia disabilitata. Ciò consente di evitare la possibilità che utenti finali accedano alle informazioni scritte nei file di log. Per altre informazioni, vedere [Logging Activity](../../connect/php/logging-activity.md).  
  
## <a name="see-also"></a>Vedere anche  
[Guida di programmazione per il driver SQL PHP](../../connect/php/programming-guide-for-php-sql-driver.md)
  
