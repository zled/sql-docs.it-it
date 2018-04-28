---
title: Microsoft ODBC Driver for SQL Server | Documenti Microsoft
ms.custom: ''
ms.date: 08/09/2017
ms.prod: sql
ms.prod_service: drivers
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9f2ae91b-06af-4c9a-9d24-062df7bc4662
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Active
ms.openlocfilehash: a9e480bd8ab948c02be27aa82a8bcd8caa2d7015
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="microsoft-odbc-driver-for-sql-server"></a>Microsoft ODBC Driver for SQL Server

![Download-FRECCIAGIÙ cerchiato](../../ssdt/media/download.png)[scaricare il driver ODBC](../sql-connection-libraries.md#anchor-20-drivers-relational-access)

ODBC è l'API di accesso ai dati nativa principale per le applicazioni scritte in C e C++ per SQL Server. È un driver ODBC per la maggior parte delle origini dati. Altri linguaggi che è possono utilizzare ODBC includono COBOL, Perl, PHP e Python. ODBC viene ampiamente impiegato negli scenari di integrazione dati.

Il driver ODBC viene fornito con strumenti quali [ **sqlcmd** ](../../tools/sqlcmd-utility.md) e [ **bcp**](../../tools/bcp-utility.md). Il **sqlcmd** utilità consente di eseguire istruzioni Transact-SQL, procedure di sistema e gli script SQL. Il **bcp** utilità copia bulk dei dati tra un'istanza di Microsoft SQL Server e un file di dati in un formato scelto. È possibile utilizzare **bcp** per importare di nuovo numero di righe in tabelle di SQL Server oppure per esportare dati dalle tabelle in file di dati.  

## <a name="code-example-in-c"></a>Esempio di codice in C++

Si dispone di un file di piccole dimensioni con estensione zip che contiene il codice sorgente di un programma C++ che utilizza ODBC:

- [Esempio di codice C++, tramite ODBC](../../odbc/reference/sample-odbc-program.md)

## <a name="download"></a>Scarica

- ![Download-FRECCIAGIÙ cerchiato](../../ssdt/media/download.png)[scaricare il driver ODBC](../sql-connection-libraries.md#anchor-20-drivers-relational-access)

## <a name="documentation"></a>Documentazione  

### <a name="features"></a>Funzionalità

- [Provider di archivio chiavi personalizzato](../../connect/odbc/custom-keystore-providers.md)
- [DSN e parole chiave delle stringhe di connessione e gli attributi](dsn-connection-string-attribute.md)
- [SQL Server Native Client](../../relational-databases/native-client/features/sql-server-native-client-features.md) (le funzionalità disponibili sono applicabili anche, senza OLEDB per il Driver ODBC per SQL Server)
- [Utilizzando sempre crittografato](../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md)
- [Utilizzo di Azure Active Directory](../../connect/odbc/using-azure-active-directory.md)
- [Utilizzando la risoluzione IP di rete Transparent](../../connect/odbc/using-transparent-network-ip-resolution.md)

### <a name="linux-and-macos"></a>Linux e macOS

- [Installazione del Driver](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)
- [Connessione a SQL Server](../../connect/odbc/linux-mac/connection-string-keywords-and-data-source-names-dsns.md)
- [La connessione con **bcp**](../../connect/odbc/linux-mac/connecting-with-bcp.md)
- [La connessione con **sqlcmd**](../../connect/odbc/linux-mac/connecting-with-sqlcmd.md)
- [Traccia di accesso ai dati](../../connect/odbc/linux-mac/data-access-tracing-with-the-odbc-driver-on-linux.md)
- [Domande frequenti](../../connect/odbc/linux-mac/frequently-asked-questions-faq-for-odbc-linux.md)
- [Installazione di Gestione driver](../../connect/odbc/linux-mac/installing-the-driver-manager.md)
- [Problemi noti](../../connect/odbc/linux-mac/known-issues-in-this-version-of-the-driver.md)
- [Linee guida per la programmazione](../../connect/odbc/linux-mac/programming-guidelines.md)
- [Note sulla versione](../../connect/odbc/linux-mac/release-notes.md)
- [Supporto per la disponibilità elevata e ripristino di emergenza](../../connect/odbc/linux-mac/odbc-driver-on-linux-support-for-high-availability-disaster-recovery.md)
- [Tramite l'autenticazione integrata (Kerberos)](../../connect/odbc/linux-mac/using-integrated-authentication.md)

### <a name="windows"></a>Windows

- [Esempio di esecuzione asincrona (metodo di notifica)](../../connect/odbc/windows/asynchronous-execution-notification-method-sample.md)
- [Resilienza di connessione nel driver ODBC di Windows](../../connect/odbc/windows/connection-resiliency-in-the-windows-odbc-driver.md)
- [Pool di connessioni compatibile con il driver](../../connect/odbc/windows/driver-aware-connection-pooling-in-the-odbc-driver-for-sql-server.md)
- [Funzionalità e modifiche del comportamento](../../connect/odbc/windows/features-of-the-microsoft-odbc-driver-for-sql-server-on-windows.md)
- [Note sulla versione](../../connect/odbc/windows/release-notes.md)
- [Requisiti di sistema, installazione e file del driver](../../connect/odbc/windows/system-requirements-installation-and-driver-files.md)



## <a name="community"></a>Community  
- [Blog del team di Microsoft ODBC Driver for SQL Server](http://blogs.msdn.com/sqlnativeclient/default.aspx)  
- [Forum di accesso ai dati di SQL Server](http://social.technet.microsoft.com/Forums/en/sqldataaccess/threads)  
