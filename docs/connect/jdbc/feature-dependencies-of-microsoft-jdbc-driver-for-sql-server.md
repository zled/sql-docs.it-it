---
title: "Funzionalità di dipendenze di Microsoft JDBC Driver per SQL Server | Documenti Microsoft"
ms.custom: 
ms.date: 02/28/2018
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 939a8773-2583-49a4-bf00-6b892fbe39dc
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 703a27220a80744c46ca0bc7667756cec1ab6596
ms.sourcegitcommit: 9d0467265e052b925547aafaca51e5a5e93b7e38
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/02/2018
---
# <a name="feature-dependencies-of-microsoft-jdbc-driver-for-sql-server"></a>Dipendenze delle funzionalità di Microsoft JDBC Driver per SQL Server
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

 Questa pagina contiene l'elenco di librerie che dipende da Microsoft JDBC Driver per SQL Server. Il progetto presenta le seguenti dipendenze.
 
 ## <a name="compile-time"></a>Fase di compilazione
 - `azure-keyvault` : Provider di insieme di credenziali delle chiavi azure per la funzionalità sempre crittografato insieme credenziali chiavi Azure (facoltativo)
 - `adal4j` : Azure Active Directory Library for Java per funzionalità di autenticazione di Azure Active Directory e la funzionalità insieme credenziali chiavi Azure (facoltativo)

 ##  <a name="test-time"></a>Tempo test
È necessario dichiarare in modo esplicito le rispettive dipendenze nel proprio file pom progetti specifici che richiedono le funzionalità due:

***Ad esempio:*** se si utilizza *funzionalità di autenticazione di Azure Active Directory*, è necessario dichiarare nuovamente *adal4j* dipendenza nel file pom del progetto. Vedere il frammento seguente: 
```xml
<dependency>
    <groupId>com.microsoft.sqlserver</groupId>
    <artifactId>mssql-jdbc</artifactId>
    <version>6.4.0.jre8</version>
    <scope>compile</scope>
</dependency>

<dependency>
    <groupId>com.microsoft.azure</groupId>
    <artifactId>adal4j</artifactId>
    <version>1.4.0</version>
</dependency>
```

***Ad esempio:*** se si utilizza *funzionalità insieme credenziali chiavi Azure* è necessario dichiarare nuovamente *azure keyvault* dipendenza e *adal4j* dipendenza nel file pom del progetto. Vedere il frammento seguente: 
```xml
<dependency>
    <groupId>com.microsoft.sqlserver</groupId>
    <artifactId>mssql-jdbc</artifactId>
    <version>6.4.0.jre8</version>
    <scope>compile</scope>
</dependency>

<dependency>
    <groupId>com.microsoft.azure</groupId>
    <artifactId>adal4j</artifactId>
    <version>1.4.0</version>
</dependency>

<dependency>
    <groupId>com.microsoft.azure</groupId>
    <artifactId>azure-keyvault</artifactId>
    <version>1.0.0</version>
</dependency>
```
 
 ## <a name="dependency-requirements-for-the-jdbc-driver"></a>Requisiti di dipendenza per il Driver JDBC

 ### <a name="azure-keyvault-feature"></a>Funzionalità Keyvault Azure:
- Driver JDBC versione 6.0.0 
    - Versioni di dipendenza: Azure-Keyvault (versione 0.9.7), Adal4j (versione 1.3.0) e le relative dipendenze ( [applicazione di esempio](../../connect/jdbc/azure-key-vault-sample-version-6.0.0.md))
- Il Driver JDBC versione 6.2.2 e versioni successive (incluso il 6.4.0 più recente)
    - Versioni di dipendenza: Azure-Keyvault (versione 1.0.0), Adal4j (versione 1.4.0) e le relative dipendenze ([applicazione di esempio](../../connect/jdbc/azure-key-vault-sample-version-6.2.2.md))

> [!NOTE]
>   A partire da v6.2.2, la dipendenza di azure-keyvault-java viene aggiornata alla versione 1.0.0. Tuttavia, la nuova versione non è compatibile con la versione precedente (versione 0.9.7) e pertanto si interrompe l'implementazione esistente nel driver. La nuova implementazione del driver richiede modifiche all'API, che a sua volta interrompono i programmi client che utilizzano la funzionalità insieme credenziali chiavi Azure.

  
 ### <a name="azure-active-directory-authentication"></a>Autenticazione di Azure Active Directory:
- Driver JDBC versione 6.0.0 
    - Versioni di dipendenza: Adal4j (versione 1.3.0) e le relative dipendenze
        - In questa versione del driver, è possibile connettersi utilizzando *ActiveDirectoryIntegrated* modalità di autenticazione solo su un Windows con sistema operativo e l'utilizzo di sqljdbc_auth.dll e Active Directory Authentication Library per SQL Server ( ADALSQL. DLL). 
- Driver JDBC versione 6.4.0
    - Versioni di dipendenza: Adal4j (versione 1.4.0) e le relative dipendenze
        - In questa versione del driver, l'applicazione non richiede l'utilizzo di ADALSQL. DLL. A seconda di sistemi operativi. Per **sistemi operativi Non Windows**, il driver richiede il ticket Kerberos per usare l'autenticazione ActiveDirectoryIntegrated. Vedere [ticket Kerberos impostato su Windows, Linux e Mac](https://docs.microsoft.com/sql/connect/jdbc/connecting-using-azure-active-directory-authentication#set-kerberos-ticket-on-windows-linux-and-mac) per altri dettagli. Per **sistemi operativi Windows**, driver per impostazione predefinita controlla se sqljdbc_auth.dll viene caricato e non richiede l'installazione o adal4j dipendenza di ticket di Kerberos. Tuttavia, se non è caricato sqljdbc_auth.dll, driver si comporta esattamente come i sistemi operativi non Windows e richiede l'installazione, come descritto in questo esempio: un'applicazione di esempio di utilizzo di questa funzionalità è reperibile [qui](../../connect/jdbc/connecting-using-azure-active-directory-authentication.md) .

 ## <a name="see-also"></a>Vedere anche  
 [Repository di GitHub Driver JDBC](https://github.com/microsoft/mssql-jdbc)  
 [Riferimento all'API del Driver JDBC](../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  