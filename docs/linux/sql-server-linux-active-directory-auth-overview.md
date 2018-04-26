---
title: L'autenticazione di Active Directory per SQL Server in Linux | Documenti Microsoft
description: In questo articolo viene fornita una panoramica dell'autenticazione di Active Directory per SQL Server in Linux.
author: rothja
ms.date: 02/23/2018
ms.author: jroth
manager: craigg
ms.topic: article
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
helpviewer_keywords:
- Linux, AAD authentication
ms.workload: On Demand
ms.openlocfilehash: bd4ba9f12b7567f618db2aef1adb87a8f1f080f5
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="active-directory-authentication-for-sql-server-on-linux"></a>Autenticazione di Active Directory per SQL Server in Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

In questo articolo viene fornita una panoramica dell'autenticazione di Active Directory (AD) per [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] in Linux. L'autenticazione di Active Directory è noto anche come autenticazione integrata in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. 

## <a name="ad-authentication-overview"></a>Cenni preliminari sull'autenticazione di Active Directory

L'autenticazione di Active Directory consente ai client di dominio su Windows o Linux per l'autenticazione [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] utilizzando le credenziali di dominio e il protocollo Kerberos.

L'autenticazione di Active Directory offre i vantaggi seguenti su [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] autenticazione:

- Gli utenti autenticati tramite l'accesso single sign-on, senza che venga richiesta una password.   
- Tramite la creazione di account di accesso per gruppi di Active Directory, è possibile gestire l'accesso e le autorizzazioni in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] tramite l'appartenenza al gruppo Active Directory.  
- Ogni utente dispone di una singola identità dell'organizzazione, quindi non è necessario tenere traccia di cui [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] gli account di accesso corrispondenti per gli utenti che.   
- Active Directory consente di applicare i criteri password centralizzata all'interno dell'organizzazione.   

## <a name="configuration-steps"></a>Passaggi di configurazione

Per usare l'autenticazione di Active Directory, è necessario disporre di un Controller di dominio Active Directory (Windows) nella rete.

Vengono forniti i dettagli su come configurare l'autenticazione di Active Directory nell'esercitazione di [esercitazione: l'autenticazione utilizza Active Directory con SQL Server in Linux](sql-server-linux-active-directory-authentication.md). Nell'elenco seguente fornisce un riepilogo con un collegamento a ogni sezione dell'esercitazione:

1. [Aggiungere un host di SQL Server a un dominio di Active Directory](sql-server-linux-active-directory-authentication.md#join).
1. [Creare un utente di Active Directory per SQL Server e impostare ServicePrincipalName](sql-server-linux-active-directory-authentication.md#createuser).
1. [Configurare il keytab del servizio SQL Server](sql-server-linux-active-directory-authentication.md#configurekeytab).
1. [Creare account di accesso di SQL Server basato su Active Directory in Transact-SQL](sql-server-linux-active-directory-authentication.md#createsqllogins).
1. [Connettersi a SQL Server utilizzando l'autenticazione AD](sql-server-linux-active-directory-authentication.md#connect).

## <a name="known-issues"></a>Problemi noti

- A questo punto, l'unico metodo di autenticazione supportato per l'endpoint del mirroring del database è certificato. Il metodo di autenticazione di WINDOWS verrà abilitato in una versione futura.
- Strumenti di terze parti AD come Centrify, Powerbroker, e Vintela non sono supportati.

## <a name="next-steps"></a>Passaggi successivi

Per ulteriori informazioni su come implementare l'autenticazione di Active Directory per SQL Server in Linux, vedere [esercitazione: l'autenticazione utilizza Active Directory con SQL Server in Linux](sql-server-linux-active-directory-authentication.md).