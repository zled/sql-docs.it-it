---
title: L'autenticazione di Active Directory con SQL Server in Linux | Documenti Microsoft
description: Passaggi di configurazione per l'autenticazione AAD per SQL Server in Linux
author: tmullaney
ms.date: 08/23/2017
ms.author: rickbyh
manager: jhubbard
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
helpviewer_keywords:
- Linux, AAD authentication
ms.translationtype: MT
ms.sourcegitcommit: 21f0cfd102a6fcc44dfc9151750f1b3c936aa053
ms.openlocfilehash: 4358a69b354964841e5e1f58a9a0d046afd85052
ms.contentlocale: it-it
ms.lasthandoff: 08/28/2017

---
# <a name="active-directory-authentication-with-sql-server-on-linux"></a>Autenticazione di Active Directory con SQL Server in Linux

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

Questo documento viene illustrato come configurare [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] in Linux per supportare l'autenticazione di Active Directory (AD), noto anche come l'autenticazione. L'autenticazione di Active Directory consente ai client di dominio su Windows o Linux per l'autenticazione [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] utilizzando le credenziali di dominio e il protocollo Kerberos.

L'autenticazione di Active Directory offre i vantaggi seguenti su [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] autenticazione:

* Gli utenti autenticati tramite l'accesso single sign-on, senza che venga richiesta una password.   
* Tramite la creazione di account di accesso per gruppi di Active Directory, è possibile gestire l'accesso e le autorizzazioni in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] tramite l'appartenenza al gruppo Active Directory.  
* Ogni utente dispone di una singola identità dell'organizzazione, quindi non è necessario tenere traccia di cui [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] gli account di accesso corrispondenti per gli utenti che.   
* Active Directory consente di applicare i criteri password centralizzata all'interno dell'organizzazione.   

## <a name="prerequisites"></a>Prerequisiti

Prima di configurare l'autenticazione di Active Directory, è necessario:

* Configurare un Controller di dominio Active Directory (Windows) nella rete  
* Installare [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]
  * [Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
  * [SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
  * [Ubuntu](quickstart-install-connect-ubuntu.md)

> [!IMPORTANT]
> A questo punto, l'unico metodo di autenticazione supportato per l'endpoint del mirroring del database è certificato. Il metodo di autenticazione di WINDOWS verrà abilitato in una versione futura.

## <a name="step-1-join-includessnoversionincludesssnoversion-mdmd-host-to-ad-domain"></a>Passaggio 1: Creare un Join [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] host al dominio Active Directory

Sono disponibili numerosi strumenti che consentono di creare un join di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] computer host al dominio di Active Directory. Questa procedura dettagliata Usa  **[realmd](https://www.freedesktop.org/software/realmd/docs/guide-active-directory-join.html)**, un pacchetto open source comuni. Se hai già fatto, installare i realmd e i pacchetti client Kerberos nel [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] computer host tramite Gestione pacchetti di distribuzione Linux:

```bash
# RHEL
sudo yum install realmd krb5-workstation

# SUSE
sudo zypper install realmd krb5-client

# Ubuntu
sudo apt-get install realmd krb5-user software-properties-common python-software-properties packagekit
```

Se l'installazione del pacchetto client Kerberos viene chiesto di immettere un nome dell'area di autenticazione, immettere il nome di dominio in lettere maiuscole.

> [!NOTE]
> Questa procedura dettagliata viene utilizzato "contoso.com" e "CONTOSO.COM" come nomi di dominio e dell'area di autenticazione riportato, rispettivamente. È necessario sostituirli con valori personalizzati. Questi comandi tra maiuscole e minuscole, pertanto assicurarsi di utilizzare maiuscole ovunque venga usato in questa procedura dettagliata.

Eseguire il comando seguente per verificare che il [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] computer host è configurato per utilizzare il controller di dominio Active Directory come un server dei nomi DNS:

```bash
sudo realm discover contoso.com -v
```

Se il dominio non viene trovato, è necessario configurare il [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] computer host da utilizzare l'indirizzo IP del controller di dominio Active Directory come un server dei nomi DNS. I passaggi specifici per eseguire questa operazione dipendono dalla configurazione di dispositivo di rete e configurazione del dominio, la distribuzione di Linux. Ecco alcuni esempi.

### <a name="example-dns-configuration-ubuntu"></a>Esempio di configurazione DNS: Ubuntu

Modificare il `/etc/network/interfaces` file in modo che l'indirizzo IP del controller di dominio Active Directory è elencato come un dns server dei nomi. Esempio: 

```/etc/network/interfaces
<...>
# The primary network interface
auth eth0
iface eth0 inet dhcp
dns-nameservers **<AD domain controller IP address>**
dns-search **<AD domain name>**
```

> [!NOTE]
> L'interfaccia di rete (eth0) potrebbero essere diversi per le macchine diverso. Per individuare quello in uso, eseguire il comando ifconfig e copiare l'interfaccia che ha un indirizzo IP e trasmessi e ricevuti byte.

Dopo avere modificato questo file, riavviare il servizio di rete:

```bash
sudo ifdown eth0 && sudo ifup eth0
```

Controllare che il `/etc/resolv.conf` file contiene una riga simile alla seguente:  

```Code
nameserver **<AD domain controller IP address>**
```

### <a name="example-dns-configuration-rhel"></a>Esempio di configurazione DNS: RHEL

Modificare il `/etc/sysconfig/network-scripts/ifcfg-eth0` file (o altra configurazione interfaccia file a seconda dei casi) in modo che l'indirizzo IP del controller di dominio Active Directory è elencato come server DNS:

```/etc/sysconfig/network-scripts/ifcfg-eth0
<...>
PEERDNS=no
DNS1=**<AD domain controller IP address>**
```

Dopo avere modificato questo file, riavviare il servizio di rete:

```bash
sudo systemctl restart network
```

Controllare che il `/etc/resolv.conf` file contiene una riga simile alla seguente:  

```Code
nameserver **<AD domain controller IP address>**
```

### <a name="join-the-domain"></a>Aggiunta al dominio

Dopo aver verificato che il DNS sia configurato correttamente, aggiungere il dominio eseguendo il comando seguente. È necessario eseguire l'autenticazione utilizzando un account di Active Directory che disponga di privilegi sufficienti in Active Directory per aggiungere un nuovo computer al dominio.

In particolare, questo comando verranno creare un nuovo account computer in Active Directory, creare il `/etc/krb5.keytab` ospitare file keytab e configurare il dominio in `/etc/sssd/sssd.conf`:

```bash
sudo realm join contoso.com -U 'user@CONTOSO.COM' -v
<...>
 * Successfully enrolled machine in realm
```

> [!NOTE]
> Se viene visualizzato un errore, "non sono installati i pacchetti necessari", quindi è necessario installare i pacchetti tramite Gestione pacchetti di distribuzione Linux prima di eseguire il `realm join` nuovo il comando.
>
> Se si riceve un errore, "Autorizzazioni insufficienti per aggiungere il dominio" è necessario verificare con un amministratore di dominio di disporre di autorizzazioni sufficienti per aggiungere i computer Linux al dominio.

Verificare che ora è possibile raccogliere informazioni relative a un utente del dominio e che è possibile acquisire un ticket Kerberos come tale utente.

We will use **id**, **[kinit](https://web.mit.edu/kerberos/krb5-1.12/doc/user/user_commands/kinit.html)** and **[klist](https://web.mit.edu/kerberos/krb5-1.12/doc/user/user_commands/klist.html)** commands for this.

```bash
id user@contoso.com
uid=1348601103(user@contoso.com) gid=1348600513(domain group@contoso.com) groups=1348600513(domain group@contoso.com)

kinit user@CONTOSO.COM
Password for user@CONTOSO.COM:

klist
Ticket cache: FILE:/tmp/krb5cc_1000
Default principal: user@CONTOSO.COM
<...>
```

> [!NOTE]
> Se `id user@contoso.com` restituisce un valore "Nessuna tale utente," assicurarsi che il servizio SSSD avviato correttamente eseguendo il comando `sudo systemctl status sssd`. Se il servizio è in esecuzione e viene comunque visualizzato l'errore "Nessun utente", provare ad abilitare la registrazione dettagliata per SSSD. Per ulteriori informazioni, vedere la documentazione di Red Hat per [risoluzione dei problemi SSSD](https://access.redhat.com/documentation/Red_Hat_Enterprise_Linux/7/html/System-Level_Authentication_Guide/trouble.html#SSSD-Troubleshooting).
>
> Se `kinit user@CONTOSO.COM` restituisce un valore, "risposta KDC non corrisponde alle aspettative durante il recupero delle credenziali iniziale," assicurarsi che l'area di autenticazione specificato in maiuscolo.

Per ulteriori informazioni, vedere la documentazione di Red Hat per [alla scoperta e aggiunta di domini di identità](https://access.redhat.com/documentation/Red_Hat_Enterprise_Linux/7/html/Windows_Integration_Guide/realmd-domain.html). 

## <a name="step-2-create-ad-user-for-includessnoversionincludesssnoversion-mdmd-and-set-spn"></a>Passaggio 2: Creare l'utente di Active Directory per [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] e impostare SPN

> [!NOTE]
> Nei passaggi successivi si utilizzerà il [nome di dominio completo](https://en.wikipedia.org/wiki/Fully_qualified_domain_name). Se si utilizza **Azure**, sarà necessario  **[crearlo](https://docs.microsoft.com/en-us/azure/virtual-machines/linux/portal-create-fqdn)**  prima di procedere.

Nel controller di dominio, eseguire il [New-ADUser](https://technet.microsoft.com/library/ee617253.aspx) comando di PowerShell per creare un nuovo utente di Active Directory con una password che non scade mai. Questo esempio attribuisce un nome account "mssql", ma il nome dell'account può essere liberamente. Verrà richiesto di immettere una nuova password per l'account:

```PowerShell
Import-Module ActiveDirectory

New-ADUser mssql -AccountPassword (Read-Host -AsSecureString "Enter Password") -PasswordNeverExpires $true -Enabled $true
```

> [!NOTE]
> È una procedura consigliata di disporre di un account di Active Directory dedicato per SQL Server, in modo che le credenziali di SQL Server non sono condivise con altri servizi che utilizzano lo stesso account. Tuttavia, è possibile riutilizzare un account di Active Directory esistente se si preferisce, se si conosce la password dell'account (obbligatorio per generare un file keytab nel passaggio successivo).

Ora impostare ServicePrincipalName (SPN) per questo account utilizzando il `setspn.exe` dello strumento. Il nome SPN deve essere formattato esattamente come specificato nell'esempio seguente: È possibile trovare il nome di dominio completo il [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] macchina host eseguendo `hostname --all-fqdns` sul [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] host e la porta TCP deve essere 1433 a meno che non è stato configurato [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] di utilizzare un numero di porta diverso.

```PowerShell
setspn -A MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>** mssql
```

> [!NOTE]
> Se si riceve un errore, "diritti di accesso insufficienti", è necessario verificare con un amministratore di dominio che si dispone di autorizzazioni sufficienti per impostare un nome SPN per l'account.
>
> Se si modifica la porta TCP in futuro, è necessario eseguire nuovamente il comando di setspn con il nuovo numero di porta. È inoltre necessario aggiungere il nuovo nome SPN per il keytab del servizio SQL Server seguendo i passaggi descritti nella sezione successiva.

Per altre informazioni, vedere [Registrazione di un nome dell'entità servizio per le connessioni Kerberos](../database-engine/configure-windows/register-a-service-principal-name-for-kerberos-connections.md).

## <a name="step-3-configure-includessnoversionincludesssnoversion-mdmd-service-keytab"></a>Passaggio 3: Configurare [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] keytab servizio

Innanzitutto, controllare il numero di versione della chiave (kvno) per l'account di Active Directory creato nel passaggio precedente. In genere sarà 2, ma può trattarsi di un altro numero intero se è stata modificata la password dell'account più volte. Nel [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] macchina host, eseguire il comando seguente:

```bash
kinit user@CONTOSO.COM

kvno MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>**
```

Creare un file keytab per l'utente di Active Directory che è stato creato nel passaggio precedente. A tale scopo si utilizzerà  **[ktutil](https://web.mit.edu/kerberos/krb5-1.12/doc/admin/admin_commands/ktutil.html)**. Quando richiesto, immettere la password per l'account di Active Directory.

```bash
sudo ktutil

ktutil: addent -password -p MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>**@CONTOSO.COM -k **<kvno from above>** -e aes256-cts-hmac-sha1-96

ktutil: addent -password -p MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>**@CONTOSO.COM -k **<kvno from above>** -e rc4-hmac

ktutil: wkt /var/opt/mssql/secrets/mssql.keytab

quit
```

> [!NOTE]
> Lo strumento ktutil non convalidare la password, assicurarsi che immettere correttamente.

Chiunque abbia accesso a questo `keytab` file può rappresentare [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sul dominio, assicurarsi limitare l'accesso a tali file solo il `mssql` account abbia accesso in lettura:

```bash
sudo chown mssql:mssql /var/opt/mssql/secrets/mssql.keytab
sudo chmod 400 /var/opt/mssql/secrets/mssql.keytab
```

A questo punto, configurare [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] utilizzato `keytab` file per l'autenticazione Kerberos:

```bash
sudo /opt/mssql/bin/mssql-conf set network.kerberoskeytabfile /var/opt/mssql/secrets/mssql.keytab
sudo systemctl restart mssql-server
```

## <a name="step-4-create-ad-based-logins-in-transact-sql"></a>Passaggio 4: Creare gli account di accesso basato su Active Directory in Transact-SQL

Connettersi a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] e creare un account di accesso di nuovo, basato su Active Directory:

```sql
CREATE LOGIN [CONTOSO\user] FROM WINDOWS;
```

Verificare che l'account di accesso viene ora elencata nel [Sys. server_principals](../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md) vista del catalogo di sistema:

```sql
SELECT name FROM sys.server_principals;
```

## <a name="step-5-connect-to-includessnoversionincludesssnoversion-mdmd-using-ad-authentication"></a>Passaggio 5: Connettersi a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] utilizzando l'autenticazione di Active Directory

Accedere a un computer client utilizzando le credenziali di dominio. Ora è possibile connettersi a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] senza immettere di nuovo la password, tramite l'autenticazione di Active Directory. Se si crea un account di accesso per un gruppo di Active Directory, qualsiasi utente di Active Directory che è un membro del gruppo può connettersi allo stesso modo.

Il parametro della stringa di connessione specifiche per i client di utilizzare l'autenticazione di Active Directory dipende dal driver che in uso. Alcuni esempi sono inferiori.

## <a name="examples"></a>Esempi

### <a name="example-1-sqlcmd-on-a-domain-joined-linux-client"></a>Esempio 1: `sqlcmd` in un dominio client Linux

Accedere a un client Linux dominio utilizzando `ssh` e le credenziali di dominio:

```bash
ssh -l user@contoso.com client.contoso.com
```

Verificare di aver installato il [mssql strumenti](sql-server-linux-setup-tools.md) del pacchetto, quindi tramite `sqlcmd` senza specificare le credenziali:

```bash
sqlcmd -S mssql.contoso.com
```

### <a name="example-2-ssms-on-a-domain-joined-windows-client"></a>Esempio 2: SQL Server Management Studio in un client Windows di dominio

Accedere a un client di Windows appartenenti a un dominio utilizzando le credenziali del dominio. Assicurarsi che [!INCLUDE[ssmanstudiofull-md](../includes/ssmanstudiofull-md.md)] è installato, quindi connettersi al [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] istanza specificando **l'autenticazione di Windows** nel **Connetti al Server** finestra di dialogo.

### <a name="ad-authentication-using-other-client-drivers"></a>Autenticazione di Active Directory con altri driver client

* JDBC: [Kerberos mediante l'autenticazione integrata di connettersi a SQL Server](https://docs.microsoft.com/sql/connect/jdbc/using-kerberos-integrated-authentication-to-connect-to-sql-server)
* ODBC: [utilizzando l'autenticazione integrata](https://docs.microsoft.com/sql/connect/odbc/linux/using-integrated-authentication)
* ADO.NET: [sintassi della stringa di connessione](https://docs.microsoft.com/dotnet/framework/data/adonet/connection-string-syntax)

