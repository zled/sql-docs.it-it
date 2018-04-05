---
title: Tramite l'autenticazione integrata | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- integrated authentication
ms.assetid: 9499ffdf-e0ee-4d3c-8bca-605371eb52d9
caps.latest.revision: 23
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 162b94d551ea8625b6b22fafec61e19038dc2051
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/18/2017
---
# <a name="using-integrated-authentication"></a>Uso dell'autenticazione integrata
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Il [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] su Linux e macOS supporta connessioni che utilizzano l'autenticazione Kerberos l'autenticazione integrata. Supporta il centro di distribuzione chiave (KDC) di MIT Kerberos e funziona con le librerie v5 generico protezione servizi applicazione programma interfaccia GSSAPI () e Kerberos.
  
## <a name="using-integrated-authentication-to-connect-to-includessnoversionincludesssnoversionmdmd-from-an-odbc-application"></a>Utilizza l'autenticazione integrata per connettersi a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] da un'applicazione ODBC  

È possibile abilitare l'autenticazione integrata Kerberos specificando **Trusted_Connection = yes** nella stringa di connessione di **SQLDriverConnect** o **SQLConnect**. Esempio:  

```
Driver='ODBC Driver 13 for SQL Server';Server=your_server;Trusted_Connection=yes  
```
  
Quando ci si connette con un DSN, è inoltre possibile aggiungere **Trusted_Connection = yes** alla voce DSN in `odbc.ini`.
  
Il `-E` opzione di `sqlcmd` e `-T` opzione di `bcp` possono essere utilizzate anche per specificare l'autenticazione integrata, vedere [connessione con **sqlcmd** ](../../../connect/odbc/linux-mac/connecting-with-sqlcmd.md) e [ Connessione con **bcp** ](../../../connect/odbc/linux-mac/connecting-with-bcp.md) per ulteriori informazioni.

Verificare che l'entità di client che viene eseguita la connessione [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] è già autenticato con Kerberos KDC.
  
**ServerSPN** e **FailoverPartnerSPN** non sono supportati.  
  
## <a name="deploying-a-linux-or-macos-odbc-driver-application-designed-to-run-as-a-service"></a>La distribuzione di un Linux o macOS ODBC Driver applicazione progettata per l'esecuzione come servizio

Un amministratore di sistema può distribuire un'applicazione in esecuzione come servizio che utilizza l'autenticazione Kerberos per connettersi a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)].  
  
È necessario innanzitutto configurare Kerberos nel client e quindi assicurarsi che l'applicazione può utilizzare le credenziali Kerberos dell'entità di sicurezza predefinita.

Assicurarsi di usare `kinit` o PAM (modulo di autenticazione plug-) per ottenere e memorizzare nella cache il TGT per l'entità che utilizza la connessione, tramite uno dei metodi seguenti:  
  
-   Eseguire `kinit`, passando un nome dell'entità e una password.  
  
-   Eseguire `kinit`, passando un nome dell'entità e un percorso del file keytab contenente la chiave dell'entità creata da `ktutil`.  
  
-   Assicurarsi che l'account di accesso al sistema è stato eseguito utilizzando il modulo Kerberos PAM (modulo di autenticazione plug-).

Quando un'applicazione viene eseguita come servizio, perché le credenziali Kerberos hanno una scadenza, rinnovare le credenziali per garantire la disponibilità continua del servizio. Il driver ODBC non rinnovare le credenziali. Verificare che sia presente un `cron` processo o uno script che viene eseguito regolarmente per rinnovare le credenziali prima della scadenza. Per evitare di richiedere la password per ciascun rinnovo, è possibile utilizzare un file keytab.  
  
La pagina relativa a[configurazione e uso di Kerberos](http://commons.oreilly.com/wiki/index.php/Linux_in_a_Windows_World/Centralized_Authentication_Tools/Kerberos_Configuration_and_Use) fornisce informazioni dettagliate sull'uso di Kerberos per i servizi in Linux.
  
## <a name="tracking-access-to-a-database"></a>Rilevamento dell'accesso a un database

Un amministratore di database può creare un audit trail di accesso a un database quando si utilizza l'account di sistema per accedere a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] utilizzando l'autenticazione integrata.  
  
Accesso a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] utilizza l'account di sistema e vi è alcuna funzionalità in Linux per rappresentare il contesto di sicurezza. Sono pertanto necessari più dati per determinare l'utente.
  
Per controllare le attività in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] per conto di utenti diversi dall'account di sistema, l'applicazione deve utilizzare [!INCLUDE[tsql](../../../includes/tsql_md.md)] **EXECUTE AS**.  
  
Per migliorare le prestazioni, l'applicazione può usare pool di connessioni con autenticazione integrata e controllo. Tuttavia, la combinazione di pool di connessioni, l'autenticazione integrata e controllo crea un rischio per la sicurezza perché Gestione driver unixODBC consente a utenti diversi di riutilizzare le connessioni in pool. Per altre informazioni, vedere la pagina relativa ai [pool di connessioni ODBC](http://www.unixodbc.org/doc/conn_pool.html).  

Prima del riutilizzo, un'applicazione è necessario reimpostare le connessioni in pool eseguendo `sp_reset_connection`.  

## <a name="using-active-directory-to-manage-user-identities"></a>Uso di Active Directory per la gestione delle identità utente

Un amministratore di sistema dell'applicazione non è necessario gestire un set separato di credenziali di accesso per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]. È possibile configurare Active Directory come centro distribuzione chiavi (KDC) per l'autenticazione integrata. Vedere [Microsoft Kerberos](https://msdn.microsoft.com/en-us/library/windows/desktop/aa378747(v=vs.85).aspx) per ulteriori informazioni.

## <a name="using-linked-server-and-distributed-queries"></a>Uso di un server collegato e di query distribuite

Gli sviluppatori possono distribuire un'applicazione che usa un server collegato o query distribuite senza che l'amministratore di database gestisca più set di credenziali SQL. In questo caso, uno sviluppatore deve configurare un'applicazione per utilizzare l'autenticazione integrata:  
  
-   L'utente accede a un computer client ed esegue l'autenticazione nel server applicazioni.  
  
-   Il server applicazioni esegue l'autenticazione come un database diverso e si connette a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)].  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]esegue l'autenticazione come utente del database a un altro database ([!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)].  
  
Dopo aver configurato l'autenticazione integrata, le credenziali vengono passate al server collegato.  
  
## <a name="integrated-authentication-and-sqlcmd"></a>Autenticazione integrata e sqlcmd
Per accedere a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] utilizzando l'autenticazione integrata, utilizzare il `-E` opzione di `sqlcmd`. Verificare che l'account che esegue `sqlcmd` associato a entità di sicurezza client Kerberos predefinita.

## <a name="integrated-authentication-and-bcp"></a>Autenticazione integrata e bcp
Per accedere a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] utilizzando l'autenticazione integrata, utilizzare il `-T` opzione di `bcp`. Verificare che l'account che esegue `bcp` associato a entità di sicurezza client Kerberos predefinita. 
  
È possibile utilizzare `-T` con il `-U` o `-P` opzione.
  
## <a name="supported-syntax-for-an-spn-registered-by-includessnoversionincludesssnoversionmdmd"></a>Sintassi supportata per un nome SPN registrato da[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]

La sintassi che utilizzano i nomi SPN nella stringa di connessione o negli attributi di connessione è come segue:  

|Sintassi|Descrizione|  
|----------|---------------|  
|MSSQLSvc/*fqdn*:*port*|Nome SPN predefinito generato dal provider quando si usa il protocollo TCP. *port* è un numero di porta TCP. *fqdn* è un nome di dominio completo.|  
  
## <a name="authenticating-a-linux-or-macos-computer-with-active-directory"></a>L'autenticazione di un Linux o macOS Computer con Active Directory

Per configurare Kerberos, l'immissione di dati di `krb5.conf` file. `krb5.conf`è in `/etc/` ma è possibile fare riferimento a un altro file tramite la sintassi, ad esempio `export KRB5_CONFIG=/home/dbapp/etc/krb5.conf`. Di seguito è riportato un esempio `krb5.conf` file:  
  
```  
[libdefaults]  
default_realm = YYYY.CORP.CONTOSO.COM  
dns_lookup_realm = false  
dns_lookup_kdc = true  
ticket_lifetime = 24h  
forwardable = yes  
  
[domain_realm]  
.yyyy.corp.contoso.com = YYYY.CORP.CONTOSO.COM  
.zzzz.corp.contoso.com = ZZZZ.CORP.CONTOSO.COM  
```  
  
Se il computer Linux o macOS è configurato per utilizzare Dynamic Host Configuration Protocol (DHCP) con un server DHCP di Windows che fornisce i server DNS da utilizzare, è possibile utilizzare **dns_lookup_kdc = true**. A questo punto, è possibile utilizzare Kerberos per accedere al dominio mediante il comando `kinit alias@YYYY.CORP.CONTOSO.COM`. I parametri passati a `kinit` tra maiuscole e minuscole e [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] computer configurato come nel dominio deve disporre di tale utente `alias@YYYY.CORP.CONTOSO.COM` aggiunto per account di accesso. A questo punto, è possibile utilizzare connessioni trusted (**Trusted_Connection = YES** in una stringa di connessione, **bcp -T**, o **sqlcmd -E**).  
  
L'ora nel computer Linux o macOS e l'ora nel centro di distribuzione chiave (KDC) Kerberos, devono essere simili. Verificare che l'ora di sistema sia impostato correttamente, ad esempio, tramite il protocollo NTP (Network Time).  

Se l'autenticazione Kerberos non riesce, il driver ODBC in Linux o macOS non utilizza l'autenticazione NTLM.  

Per ulteriori informazioni sull'autenticazione di computer Linux o Mac OS con Active Directory, vedere [autenticare client Linux con Active Directory](http://technet.microsoft.com/magazine/2008.12.linux.aspx#id0060048) e [le procedure consigliate per l'integrazione di OS X con Active Directory](http://training.apple.com/pdf/Best_Practices_for_Integrating_OS_X_with_Active_Directory.pdf). Per ulteriori informazioni sulla configurazione di Kerberos, vedere il [MIT Kerberos documentazione](https://web.mit.edu/kerberos/krb5-1.12/doc/index.html).

## <a name="see-also"></a>Vedere anche  
[Linee guida per la programmazione](../../../connect/odbc/linux-mac/programming-guidelines.md)

[Note sulla versione](../../../connect/odbc/linux-mac/release-notes.md)

[Utilizzo di Azure Active Directory](../../../connect/odbc/using-azure-active-directory.md)
