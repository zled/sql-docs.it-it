---
title: Dipendenze delle funzionalità di Microsoft JDBC Driver per SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 07/31/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 939a8773-2583-49a4-bf00-6b892fbe39dc
caps.latest.revision: 57
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 70179d55c6aae5fc01c84f0c4af860f86d528a06
ms.sourcegitcommit: e02c28b0b59531bb2e4f361d7f4950b21904fb74
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 08/02/2018
ms.locfileid: "39454225"
---
# <a name="feature-dependencies-of-microsoft-jdbc-driver-for-sql-server"></a>Dipendenze delle funzionalità di Microsoft JDBC Driver per SQL Server

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Questa pagina sono elencati le librerie che dipende da Microsoft JDBC Driver per SQL Server. Il progetto contiene le dipendenze seguenti.

## <a name="compile-time"></a>Tempo di compilazione

- `azure-keyvault`: Azure Key Vault Provider per la funzionalità Always Encrypted Azure Key Vault (facoltativa)
- `adal4j`: La libreria azure Active Directory per Java per la funzionalità di autenticazione di Azure Active Directory e funzionalità di Azure Key Vault (facoltativa)

## <a name="test-time"></a>Tempo test

È necessario dichiarare in modo esplicito le rispettive dipendenze nel file pom progetti specifici che richiedono una di queste due funzionalità:

**_Ad esempio:_**  quando si usa _funzionalità di autenticazione di Azure Active Directory_, quindi è necessario dichiarare di nuovo _adal4j_ dipendenza nel file pom del progetto. Vedere il frammento seguente:

```xml
<dependency>
    <groupId>com.microsoft.sqlserver</groupId>
    <artifactId>mssql-jdbc</artifactId>
    <version>7.0.0.jre10</version>
    <scope>compile</scope>
</dependency>

<dependency>
    <groupId>com.microsoft.azure</groupId>
    <artifactId>adal4j</artifactId>
    <version>1.6.0</version>
</dependency>
```

**_Ad esempio:_**  quando si usa _la funzionalità Azure Key Vault_, quindi è necessario dichiarare di nuovo _azure-keyvault_ dipendenza e _adal4j_ dipendenza nel file pom del progetto. Vedere il frammento seguente:

```xml
<dependency>
    <groupId>com.microsoft.sqlserver</groupId>
    <artifactId>mssql-jdbc</artifactId>
    <version>7.0.0.jre10</version>
    <scope>compile</scope>
</dependency>

<dependency>
    <groupId>com.microsoft.azure</groupId>
    <artifactId>adal4j</artifactId>
    <version>1.6.0</version>
</dependency>

<dependency>
    <groupId>com.microsoft.azure</groupId>
    <artifactId>azure-keyvault</artifactId>
    <version>1.0.0</version>
</dependency>
```

## <a name="dependency-requirements-for-the-jdbc-driver"></a>Requisiti di dipendenza per il driver JDBC

### <a name="working-with-azure-key-vault-provider"></a>Utilizzo di Azure Key Vault Provider:

- Microsoft JDBC Driver versione 7.0.0 - le versioni delle dipendenze: Azure-Keyvault (versione 1.0.0), Adal4j (versione 1.6.0) e le relative dipendenze ([applicazione di esempio](../../connect/jdbc/azure-key-vault-sample-version-7-0-0.md))
- Microsoft JDBC Driver versione 6.4.0 - le versioni delle dipendenze: Azure-Keyvault (versione 1.0.0), Adal4j (versione 1.4.0) e le relative dipendenze ([applicazione di esempio](../../connect/jdbc/azure-key-vault-sample-version-6.2.2.md))
- Microsoft JDBC Driver versione 6.2.2 - le versioni delle dipendenze: Azure-Keyvault (versione 1.0.0), Adal4j (versione 1.4.0) e le relative dipendenze ([applicazione di esempio](../../connect/jdbc/azure-key-vault-sample-version-6.2.2.md))
- Microsoft JDBC Driver versione 6.0.0 - le versioni delle dipendenze: Azure-Keyvault (versione 0.9.7), Adal4j (versione 1.3.0) e le relative dipendenze ( [applicazione di esempio](../../connect/jdbc/azure-key-vault-sample-version-6.0.0.md))

> [!NOTE]
> Con le versioni di driver v6.2.2 e versione 6.4.0, la dipendenza di azure-keyvault-java è stata aggiornata alla versione 1.0.0. Tuttavia, la nuova versione non era compatibile con la versione precedente (versione 0.9.7) e quindi si interrompe l'implementazione esistente nel driver. La nuova implementazione nel driver ha richiesto modifiche API, che a sua volta suddivide i programmi client che usano il Provider di insieme di credenziali delle chiavi di Azure.

> Questo problema è stato risolto con v7.0.0 di versione più recente del driver poiché il costruttore rimosso utilizzando il meccanismo di callback di autenticazione viene aggiunto al provider di Azure Key Vault per le versioni precedenti la compatibilità.

### <a name="working-with-azure-active-directory-authentication"></a>Utilizzo dell'autenticazione di Azure Active Directory:

- Microsoft JDBC Driver versione 7.0.0 - le versioni delle dipendenze: Ada4j (versione 1.6.0) e le relative dipendenze
- Microsoft JDBC Driver versione 6.4.0 - le versioni delle dipendenze: Adal4j (versione 1.4.0) e le relative dipendenze
- Microsoft JDBC Driver versione 6.2.2 - le versioni delle dipendenze: Adal4j (versione 1.4.0) e le relative dipendenze
- Microsoft JDBC Driver versione 6.0.0 - le versioni delle dipendenze: Adal4j (versione 1.3.0), e le relative dipendenze, In questa versione del driver, è possibile connettersi utilizzando _ActiveDirectoryIntegrated_ modalità di autenticazione solo su un sistema operativo Windows e l'utilizzo di sqljdbc_auth e Active Directory Authentication Library per SQL Server (ADALSQL. DLL).

Da driver versione 6.4.0 e versioni successive, le applicazioni non necessariamente richiedono l'uso di ADALSQL. DLL nei sistemi operativi Windows. Per la **sistemi operativi Non Windows**, il driver richiede il ticket Kerberos per lavorare con l'autenticazione ActiveDirectoryIntegrated. Per altre informazioni su come connettersi ad Active Directory usando Kerberos, vedere [ticket Kerberos impostato su Windows, Linux e Mac](https://docs.microsoft.com/sql/connect/jdbc/connecting-using-azure-active-directory-authentication#set-kerberos-ticket-on-windows-linux-and-mac).

Per la **sistemi operativi Windows**, driver Cerca sqljdbc_auth per impostazione predefinita e non richiede installazione di ticket Kerberos o le dipendenze della libreria di Azure. Tuttavia, se sqljdbc_auth non è disponibile, driver cercherà il ticket Kerberos per l'autenticazione ad Active Directory come altri sistemi operativi.

Un'applicazione di esempio Usa questa funzionalità è reperibile [qui](../../connect/jdbc/connecting-using-azure-active-directory-authentication.md).

## <a name="see-also"></a>Vedere anche

[Repository di GitHub del Driver JDBC](https://github.com/microsoft/mssql-jdbc)  
 [Informazioni di riferimento sull'API del driver JDBC](../../connect/jdbc/reference/jdbc-driver-api-reference.md)
