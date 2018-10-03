---
title: Usare i provider di Active Directory di terze parti con SQL Server in Linux | Microsoft Docs
description: Questa esercitazione include i passaggi di configurazione per l'autenticazione di Active Directory con i provider di terze parti
author: dylan-MSFT
ms.date: 07/25/2018
ms.author: dygray
manager: mikehab
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
helpviewer_keywords:
- Linux, AD authentication
ms.openlocfilehash: beb342156098ebb5516466ad7fd4a771cc5a0616
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47787286"
---
# <a name="use-third-party-active-directory-providers-with-sql-server-on-linux"></a>Usare i provider di Active Directory di terze parti con SQL Server in Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Questo articolo illustra come configurare un [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] nel computer host di Linux con l'autenticazione di Active Directory quando si usano provider di AD di terze parti, ad esempio [PowerBroker Identity Services (PBI)](https://www.beyondtrust.com/), [Vintela autenticazione Servizi (VAS)](https://www.oneidentity.com/products/authentication-services/), e [Centrify](https://www.centrify.com/). Questa guida include i passaggi per verificare la configurazione di AD e non lo è quello di illustrare come aggiungere un computer a un dominio. Per istruzioni dettagliate sull'aggiunta di un [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] host a un dominio usando SSSD e dell'area di autenticazione, vedere [autenticazione Usa Active Directory con SQL Server in Linux](sql-server-linux-active-directory-authentication.md).

## <a name="prerequisites"></a>Prerequisiti

Prima di configurare l'autenticazione di AD, è necessario configurare un Controller di dominio Active Directory (Windows) in rete e join di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sull'host Linux a un dominio AD. È possibile usare [PBI](https://www.beyondtrust.com/), [VAS](https://www.oneidentity.com/products/authentication-services/), o [Centrify](https://www.centrify.com/).

> [!NOTE]
>
>Questa esercitazione Usa "contoso.com" e "CONTOSO.COM" rispettivamente come nomi di dominio e dell'area di autenticazione di esempio. Usa inoltre "DC1. Come esempio di nome dominio completo del controller di dominio "CONTOSO.COM. È necessario sostituire questi valori con i propri valori.

## <a name="check-connection-to-domain-controller"></a>Controllare la connessione al Controller di dominio

Controllo è possibile contattare il controller di dominio con sia il nome breve e nome completo del dominio.

   ```bash
   ping contoso

   ping contoso.com
   ```

   Se una di queste ha esito negativo, aggiornare l'elenco di ricerca di dominio.

   - **Ubuntu**:

     Modificare il `/etc/network/interfaces` file in modo che il dominio di Active Directory è presente nell'elenco di ricerca di dominio: 

     ```/etc/network/interfaces
     <...>
     # The primary network interface
     auto eth0
     iface eth0 inet dhcp
     dns-nameservers **<AD domain controller IP address>**
     dns-search **<AD domain name>**
     ```

     > [!NOTE]
     > L'interfaccia di rete (eth0) potrebbe essere differente per diverse macchine. Per individuare quella in uso, eseguire il comando ifconfig e copiare l'interfaccia che ha un indirizzo IP e che ha trasmesso e ricevuto byte.

     Dopo avere modificato questo file, riavviare il servizio di rete:

     ```bash
     sudo ifdown eth0 && sudo ifup eth0
     ```

     Verificare ora che il `/etc/resolv.conf` file contiene una riga simile al seguente:  

     ```/etc/resolv.conf
     search contoso.com com  
     nameserver **<AD domain controller IP address>**
     ```

   - **RHEL**:

     Modificare il `/etc/sysconfig/network-scripts/ifcfg-eth0` file (o altre configurazione di interfaccia di file come appropriato) in modo che il dominio di Active Directory è presente nell'elenco di ricerca di dominio:

     ```/etc/sysconfig/network-scripts/ifcfg-eth0
     <...>
     PEERDNS=no
     DNS1=**<AD domain controller IP address>**
     DOMAIN="contoso.com com"
     ```

     Dopo avere modificato questo file, riavviare il servizio di rete:

     ```bash
     sudo systemctl restart network
     ```

     Verificare ora che il `/etc/resolv.conf` file contiene una riga simile al seguente:  

     ```/etc/resolv.conf
     search contoso.com com  
     nameserver **<AD domain controller IP address>**
     ```

   Se è comunque possibile effettuare il ping di controller di dominio, trovare il nome di dominio completo (ad esempio, DC1. CONTOSO.COM) e l'indirizzo IP del controller di dominio e aggiungere la seguente voce `/etc/hosts`

   ```/etc/hosts
   **<IP address>** DC1.CONTOSO.COM CONTOSO.COM CONTOSO
   ```

   - **SLES**:

     Modificare il `/etc/sysconfig/network/config` file in modo che l'indirizzo IP controller di dominio Active Directory verrà usata per le query DNS e il dominio di Active Directory è presente nell'elenco di ricerca di dominio:

     ```/etc/sysconfig/network/config
     <...>
     NETCONFIG_DNS_STATIC_SEARCHLIST=""
     NETCONFIG_DNS_STATIC_SERVERS="**<AD domain controller IP address>**"
     ```

     Dopo avere modificato questo file, riavviare il servizio di rete:
     ```bash
     sudo systemctl restart network
     ```

     Verificare ora che il `/etc/resolv.conf` file contiene una riga simile al seguente:

     ```/etc/resolv.conf
     search contoso.com com
     nameserver **<AD domain controller IP address>**
     ```

## <a name="check-reverse-dns-is-properly-configured"></a>Verificare che il Reverse DNS sia configurato correttamente

Questo comando deve restituire il nome di dominio completo dell'host che esegue SQL Server (ad esempio "SqlHost.contoso.com").

   ```bash
   host **<IP address of SQL Server host>**
   # **<reversed IP address>**.in-addr.arpa domain name pointerSqlHost.contoso.com.
   ```

   Se questo non viene restituito alcun nome di dominio completo dell'host o se il nome FQDN non è corretto, aggiungere una voce DNS inversa per i [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sull'host Linux al server DNS.

## <a name="check-your-krb5-configuration-is-correct"></a>Verificare che la configurazione KRB5 sia corretta

Controllare il `/etc/krb5.conf` sia configurato correttamente. Per la maggior parte dei provider di AD di terze parti, questa operazione viene eseguita automaticamente. Tuttavia, controllare `/etc/krb5.conf` per i valori seguenti evitare eventuali problemi futuri:

   ```/etc/krb5.conf
   [libdefaults]
   default_realm = CONTOSO.COM

   [realms]
   CONTOSO.COM = {
   }

   [domain_realm]
   contoso.com = CONTOSO.COM
   .contoso.com = CONTOSO.COM
   ```

## <a name="next-steps"></a>Passaggi successivi

In questo articolo è stato illustrato come configurare un [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] nel computer host di Linux con l'autenticazione di Active Directory quando si usano provider di terze parti AD. Per completare la configurazione [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] in Linux per supportare gli account di Active Directory, seguire le istruzioni in [autenticazione Usa Active Directory con SQL Server in Linux](sql-server-linux-active-directory-authentication.md).

> [!div class="nextstepaction"]
> [Usare l'autenticazione di Active Directory con SQL Server in Linux](sql-server-linux-active-directory-authentication.md)

> [!NOTE]
>
> È possibile ignorare la sezione "Host di SQL Server aggiunta al dominio Active Directory" nella [autenticazione Usa Active Directory con SQL Server in Linux](sql-server-linux-active-directory-authentication.md) sono state eseguite solo che in questa esercitazione.
