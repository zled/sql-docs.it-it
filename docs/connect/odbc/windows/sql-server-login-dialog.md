---
title: Finestra di dialogo account di accesso SQL Server (ODBC) | Documenti Microsoft
ms.custom: ''
ms.date: 03/21/2018
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76326eeb-1144-4b9f-85db-50524c655d30
caps.latest.revision: 22
author: MightyPen
ms.author: v-jizho2
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f0269dc584bbc2b6b95deee6de85a3c52d7a731f
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sql-server-login-dialog-box-odbc"></a>Finestra di dialogo Account di accesso di SQL Server (ODBC)

Quando si chiama una connessione ODBC senza specificare informazioni sufficienti per il driver per la connessione a SQL Server, viene visualizzato il driver ODBC di **account di accesso di SQL Server** la finestra di dialogo.

## <a name="options"></a>Opzioni

### <a name="server"></a>Server

Il nome di un'istanza di SQL Server nella rete. Selezionare un nome dell'istanza dall'elenco o digitare il nome dell'istanza nel **Server** casella. Facoltativamente, è possibile creare un alias server sul computer client utilizzando **Gestione configurazione SQL Server**e digitare il nome nel **Server** casella.

È possibile immettere "(local)" quando si utilizza lo stesso computer di SQL Server. È quindi possibile connettersi a un'istanza locale di SQL Server, anche quando si esegue una versione non in rete di SQL Server.

Per ulteriori informazioni sui nomi di server per diversi tipi di reti, vedere la documentazione di installazione di SQL Server nella documentazione Online di SQL Server.

### <a name="authentication-mode"></a>Modalità di autenticazione

Seleziona la modalità di autenticazione da uno dei valori seguenti:
- **SQL Server** con ID di accesso e password
- **Sicurezza integrata di Windows** autenticazione mediante account dell'utente connesso
- **Password di Active Directory** con ID di accesso e password
- **Active Directory Integrated** autenticazione mediante account dell'utente connesso
- **Active Directory interattivo** l'autenticazione con ID di accesso

Vedere [2 di schermata Creazione guidata origine dati](../../../connect/odbc/windows/dsn-wizard-2.md) per ulteriori informazioni sulle modalità di autenticazione.

### <a name="server-spn"></a>SPN server

Se si utilizza una connessione trusted, è possibile specificare un nome dell'entità servizio (SPN) per il server.

### <a name="login-id"></a>ID accesso

Specifica l'ID di accesso di SQL Server o Azure Active Directory da utilizzare per la connessione se **modalità di autenticazione** è impostata su **SQL Server** oppure **Password di Active Directory** o **Active Directory interattivo**. In caso contrario, il **ID di accesso** casella è disabilitata.

### <a name="password"></a>Password

Specifica la password per l'ID di accesso di SQL Server o Azure Active Directory utilizzato per la connessione se **modalità di autenticazione** è impostato su **SQL Server** o **PassworddiActiveDirectory**. In caso contrario, il **Password** casella è disabilitata.

### <a name="options"></a>Opzioni

Visualizza o nasconde il **opzioni** gruppo. Il **opzioni** pulsante viene abilitato se **Server** ha un valore.

### <a name="change-password"></a>Comando Cambia password

Quando questa casella è selezionata, viene visualizzato il **nuova Password** e **Conferma nuova Password** caselle.

### <a name="new-password"></a>Nuova password

Consente di specificare la nuova password.

### <a name="confirm-new-password"></a>Conferma nuova password

Consente di specificare la nuova password una seconda volta, per conferma.

### <a name="database"></a>Database

Indica il database predefinito da utilizzare per la connessione. Questa impostazione è prioritaria rispetto al database predefinito specificato per l'accesso nel server. Se non è specificato alcun database, viene utilizzato il database predefinito specificato per l'account di accesso nel server.

### <a name="mirror-server"></a>Server mirror

Indica il nome del partner di failover del database da sottoporre a mirroring.

### <a name="mirror-spn"></a>SPN mirror

Se si desidera, è possibile specificare un nome SPN per il server mirror. Tale nome verrà utilizzato per l'autenticazione reciproca tra client e server.

### <a name="language"></a>Lingua

Specifica la lingua da utilizzare per i messaggi di sistema di SQL Server. Il computer che esegue SQL Server deve essere la lingua installata. Questa impostazione è prioritaria rispetto alla lingua predefinita specificata per l'account di accesso nel server. Se non è specificata alcuna lingua, viene utilizzata la lingua predefinita specificata per l'account di accesso nel server.

### <a name="application-name"></a>Application Name

(Facoltativo) Specifica il nome dell'applicazione da archiviare nel **program_name** colonna nella riga relativa alla connessione corrente in **Sys. sysprocesses**.

### <a name="workstation-id"></a>ID workstation

(Facoltativo) Specifica l'ID della workstation da archiviare nel **hostname** colonna nella riga relativa alla connessione corrente in **Sys. sysprocesses**.

### <a name="use-strong-encryption-for-data"></a>Usa crittografia avanzata per i dati

Se selezionata, i dati che viene passati tramite la connessione verranno crittografati. Gli account di accesso sono crittografati per impostazione predefinita, anche se questa casella di controllo è deselezionata.

### <a name="trust-server-certificate"></a>Certificato server attendibile

Questa opzione è applicabile solo quando **Usa crittografia avanzata per i dati** è abilitata. Se selezionata, il certificato del server non verrà convalidato con il nome host corretto del server, essere emesso da un'autorità di certificazione.

## <a name="see-also"></a>Vedere anche

[Microsoft ODBC Driver for SQL Server in Windows](../../../connect/odbc/windows/microsoft-odbc-driver-for-sql-server-on-windows.md)
