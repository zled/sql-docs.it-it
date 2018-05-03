---
title: Note (Driver ODBC per SQL Server) | Documenti Microsoft
ms.custom: ''
ms.date: 04/04/2018
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: b8459ed8-625e-4d8b-891c-e7e78c9977cc
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9d07b570a30ca915ad95bcfcca63d250a9d18e09
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="release-notes"></a>Note sulla versione
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

  Note sulla versione per Microsoft ODBC Driver for SQL Server in Windows.  

## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-171-for-includessnoversionincludesssnoversionmdmd-on-windows"></a>Novità di [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 17.1 per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] in Windows

**Funzionalità aggiunte**:

Supporto per `SQL_COPT_SS_CEKCACHETTL` e `SQL_COPT_SS_TRUSTEDCMKPATHS` attributi di connessione (per altre informazioni, vedere [utilizzo di Always Encrypted con il Driver ODBC per SQL Server](../using-always-encrypted-with-the-odbc-driver.md))
- `SQL_COPT_SS_CEKCACHETTL` Consente di controllare l'ora in cui è presente nella cache locale delle chiavi di crittografia di colonna, nonché lo scaricamento
- `SQL_COPT_SS_TRUSTEDCMKPATHS` Consente all'applicazione di limitare le operazioni di AE per usare solo l'elenco specificato di chiavi Master della colonna


Supporto dell'autenticazione interattivo Azure Active Directory

[Correzioni di bug](../bug-fixes.md)


## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-17-for-includessnoversionincludesssnoversionmdmd-on-windows"></a>Novità di [!INCLUDE[msCoName](../../../includes/msconame_md.md)] il Driver ODBC 17 per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] in Windows

**Funzionalità aggiunte**:

Always Encrypted supporto per API BCP

Nuovo attributo di stringa di connessione UseFMTOnly causa del driver per l'uso di metadati legacy in casi particolari richiede che le tabelle temporanee.

Supporto per l'istanza gestita di SQL Azure (anteprima privata estesa). 
> [!NOTE]
> Quando si utilizza l'istanza gestita, esistono alcune differenze:
> -   FILESTREAM non è supportato 
> -   Accesso ai file System locale non è supportata, ma necessari per elementi quali tracefiles 
> -   Il nome di tipo definito dall'utente locale percorso non è supportato. 
> -   Autenticazione integrata di Windows non è supportata. 
> -   DTC non è supportata. 
> -   l'account 'sa' non è presente (l'account predefinito viene chiamato 'cloudSA')
> -   Errore nel token TDS (0xAA) restituisce il nome server errato
> -   Non sono supportati i caratteri speciali nei nomi di database 
> -   ALTER DATABASE [dbname1] MODIFY NAME = [dbname2] non è supportata.
> -   I messaggi di errore vengono sempre visualizzati in inglese, indipendentemente dal linguaggio impostazioni (come Azure) 
  

## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-131-for-includessnoversionincludesssnoversionmdmd-on-windows"></a>Novità di [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 13.1 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] in Windows  
 ODBC Driver 13.1 per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] aggiunge il supporto per [Always Encrypted](../../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md) e [Azure Active Directory](../../../connect/odbc/using-azure-active-directory.md) quando utilizzato in combinazione con Microsoft SQL Server 2016.  Connessione corrispondente pooling parole chiave o attributi sono descritti in [Driver compatibile con il pool di connessioni nel Driver ODBC per SQL Server](../../../connect/odbc/windows/driver-aware-connection-pooling-in-the-odbc-driver-for-sql-server.md).

 ## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-13-for-includessnoversionincludesssnoversionmdmd-on-windows"></a>Novità di [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 13 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] in Windows  
 ODBC Driver 13 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] include la funzionalità precedente da ODBC Driver 11 per SQL Server e aggiunge il supporto per Microsoft SQL Server 2016.

## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-11-for-includessnoversionincludesssnoversionmdmd-on-windows"></a>Novità di [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 11 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] in Windows  
 ODBC Driver 11 for SQL Server contiene nuove [funzionalità](./features-of-the-microsoft-odbc-driver-for-sql-server-on-windows.md) nonché tutte le funzionalità fornite con ODBC in SQL Server 2012 Native Client.  
