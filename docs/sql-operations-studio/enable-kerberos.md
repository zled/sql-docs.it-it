---
title: Utilizzare l'autenticazione di Active Directory (Kerberos) per la connessione con SQL Operations Studio (preview) | Documenti Microsoft
description: Informazioni su come abilitare Kerberos utilizzare l'autenticazione di Active Directory per SQL Operations Studio (preview)
ms.custom: tools|sos
ms.date: 11/17/2017
ms.prod: sql-non-specified
ms.reviewer: alayu; erickang; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: ''
ms.topic: article
author: meet-bhagdev
ms.author: meetb
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: dbd229a0106506f744074df760ee10f871474ebb
ms.sourcegitcommit: 094c46e7fa6de44735ed0040c65a40ec3d951b75
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2018
---
# <a name="connect-includename-sosincludesname-sos-shortmd-to-your-sql-server-using-windows-authentication---kerberos"></a>Connettersi [!INCLUDE[name-sos](../includes/name-sos-short.md)] a SQL Server utilizzando l'autenticazione di Windows - Kerberos 

[!INCLUDE[name-sos](../includes/name-sos-short.md)] supporta la connessione a SQL Server tramite Kerberos.

Per utilizzare l'autenticazione integrata (autenticazione di Windows) in macOS o Linux, è necessario impostare un **ticket Kerberos** il collegamento all'utente corrente a un account di dominio di Windows. 

## <a name="prerequisites"></a>Prerequisiti

- Accedere a un computer di dominio di Windows per eseguire query di Controller di dominio Kerberos.
- SQL Server deve essere configurato per consentire l'autenticazione Kerberos. Per il driver client in esecuzione su Unix, l'autenticazione integrata è supportata solo con Kerberos. Sono disponibili ulteriori informazioni sulla configurazione di Sql Server per l'autenticazione tramite Kerberos [qui](https://support.microsoft.com/en-us/help/319723/how-to-use-kerberos-authentication-in-sql-server). Deve esistere SPN registrati per ogni istanza di Sql Server si sta tentando di connettersi. I dettagli sul formato dei nomi SPN di SQL Server sono elencati [qui](https://technet.microsoft.com/en-us/library/ms191153%28v=sql.105%29.aspx#SPN%20Formats)


## <a name="checking-if-sql-server-has-kerberos-setup"></a>Verifica se Sql Server il programma di installazione di Kerberos

Account di accesso al computer host di Sql Server. Dal prompt dei comandi Windows, utilizzare il `setspn -L %COMPUTERNAME%` per elencare tutti i nomi dell'entità servizio per l'host. Verranno visualizzate voci che iniziano con MSSQLSvc/HostName.Domain.com indica che Sql Server è registrato un nome SPN e pronto accettare l'autenticazione Kerberos. 
- Se non si ha accesso all'Host di Sql Server, quindi da qualsiasi altro sistema operativo Windows aggiunto ad Active Directory stesso, è possibile utilizzare il comando `setspn -L <SQLSERVER_NETBIOS>` dove < SQLSERVER_NETBIOS > è il nome del computer dell'host di Sql Server.


## <a name="get-the-kerberos-key-distribution-center"></a>Ottenere il centro distribuzione chiavi Kerberos

Trovare il valore di configurazione di Kerberos KDC (Key Distribution Center). Eseguire il comando seguente in un computer Windows che viene aggiunto al dominio di Active Directory: 

Avviare `cmd.exe` ed eseguire `nltest`.

```
nltest /dsgetdc:DOMAIN.COMPANY.COM (where “DOMAIN.COMPANY.COM” maps to your domain’s name)

Sample Output
DC: \\dc-33.domain.company.com
Address: \\2111:4444:2111:33:1111:ecff:ffff:3333
...
The command completed successfully
```
Copiare il nome del controller di dominio che è il valore di configurazione KDC richiesto, in questo controller di dominio-33.domain.company.com case

## <a name="join-your-os-to-the-active-directory-domain-controller"></a>Creare un join del sistema operativo per il Controller di dominio Active Directory

### <a name="ubuntu"></a>Ubuntu
```bash
sudo apt-get install realmd krb5-user software-properties-common python-software-properties packagekit
```

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
> L'interfaccia di rete (eth0) potrebbero essere diversi per diverse macchine. Per individuare quello in uso, eseguire il comando ifconfig e copiare l'interfaccia che ha un indirizzo IP e trasmessi e ricevuti byte.

Dopo avere modificato questo file, riavviare il servizio di rete:

```bash
sudo ifdown eth0 && sudo ifup eth0
```

Controllare che il `/etc/resolv.conf` file contiene una riga simile alla seguente:  

```Code
nameserver **<AD domain controller IP address>**
```

```bash
sudo realm join contoso.com -U 'user@CONTOSO.COM' -v
<...>
* Success
```
   
### <a name="redhat-enterprise-linux"></a>RedHat Enterprise Linux
```bash
sudo yum install realmd krb5-workstation
```

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

```bash
sudo realm join contoso.com -U 'user@CONTOSO.COM' -v
<...>
* Success
   
```

### <a name="macos"></a>macOS

- Creare un join di macOS al Controller di dominio Active Directory [procedendo come segue] (https://support.apple.com/kb/PH26282?viewlocale=en_US&locale=en_US).



## <a name="configure-kdc-in-krb5conf"></a>Configurazione KDC in krb5

Modificare il `/etc/krb5.conf` in un editor di propria scelta. Configurare le chiavi seguenti

```bash
sudo vi /etc/krb5.conf

[libdefaults]
  default_realm = DOMAIN.COMPANY.COM
 
[realms]
DOMAIN.COMPANY.COM = {
   kdc = dc-33.domain.company.com
}
```

Quindi salvare il file krb5 conf e uscita

> [!NOTE]
> Il dominio deve essere in lettere maiuscole


## <a name="test-the-ticket-granting-ticket-retrieval"></a>Testare il recupero di Ticket di concessione Ticket

Ottenere un Ticket di concessione Ticket (TGT) dal KDC.

```bash
kinit username@DOMAIN.COMPANY.COM
```

Consente di visualizzare il ticket disponibile tramite kinit. Se il kinit ha avuto esito positivo, verrà visualizzato un ticket. 

```bash
klist

krbtgt/DOMAIN.COMPANY.COM@ DOMAIN.COMPANY.COM.
```

## <a name="connect-using-includename-sosincludesname-sos-shortmd"></a>Connetti tramite [!INCLUDE[name-sos](../includes/name-sos-short.md)]

* Creare un nuovo profilo di connessione

* Scegliere **l'autenticazione di Windows** come il tipo di autenticazione

* Completare il profilo di connessione, fare clic su **Connetti**

Dopo avere stabilito la connessione, il server viene visualizzata nella *server* barra laterale.
