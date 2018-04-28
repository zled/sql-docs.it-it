---
title: Installazione di gestione Driver, Driver ODBC per SQL Server | Documenti Microsoft
ms.custom: ''
ms.date: 02/14/2018
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
helpviewer_keywords:
- Driver Manager, installing
ms.assetid: 7c4b6fb4-f45a-4973-adb9-a4d83f0a2a7a
caps.latest.revision: 59
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: a396bd0cab8ad6298eec79c48fdf541178194c8a
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="installing-the-driver-manager"></a>Installazione di Gestione driver
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Questo articolo sono contenute le istruzioni per installare Gestione Driver unixODBC per l'utilizzo con tutte le versioni di Microsoft ODBC Driver for SQL Server in Linux e macOS.  

> [!IMPORTANT]  
> Eliminare tutti i pacchetti di gestione dei driver installati nel computer prima di installare Gestione driver unixODBC. L'installazione di Gestione driver unixODBC potrebbe interrompere l'esecuzione di un programma di gestione dei driver esistente.  

## <a name="installing-the-driver-manager-for-microsoft-odbc-driver-13-131-and-17"></a>Installazione di gestione Driver per Microsoft ODBC Driver 13 e 13.1 17
La dipendenza di Gestione driver viene risolto automaticamente dal sistema di gestione del pacchetto quando si installa Microsoft ODBC Driver 13, 13.1 o 17 per SQL Server in Linux o macOS seguendo le istruzioni in [l'installazione del Driver ODBC di Microsoft per SQL Server in Linux o macOS](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md). 

## <a name="installing-the-driver-manager-for-microsoft-odbc-driver-11-for-sql-server"></a>Installazione di Gestione driver per Microsoft ODBC Driver 11 for SQL Server  

(SUSE e Red Hat Linux solo).

**Utilizzando lo Script di installazione**  
  
> [!IMPORTANT]  
> Queste istruzioni fanno riferimento a `msodbcsql-11.0.2270.0.tar.gz`, ovvero il file di installazione per Red Hat Linux. Se si sta installando l'anteprima per SUSE Linux, il nome del file è `msodbcsql-11.0.2260.0.tar.gz`.  

Per installare Gestione driver:  
  
1.  Assicurarsi di disporre dell'autorizzazione di radice.  
  
2.  Passare alla directory in cui il [!INCLUDE[msCoName](../../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] download del Driver ODBC è inserito il file denominato `msodbcsql-11.0.2270.0.tar.gz`. Verificare di avere il file \*.tar.gz corrispondente alla versione di Linux in uso. Per estrarre i file, eseguire il comando seguente: **tar xvzf msodbcsql-11.0.2270.0.tar.gz**.  

3.  Modificare il `msodbcsql-11.0.2270.0` directory si dovrebbe essere possibile visualizzare un file denominato `build_dm.sh`. È possibile eseguire `build_dm.sh` per installare Gestione Driver unixODBC.

4.  Per visualizzare un elenco delle opzioni disponibili, eseguire il comando seguente: **./build_dm.sh - Guida**.  
  
5.  Quando si è pronti per installare e il computer può accedere a un sito esterno tramite FTP, eseguire il comando seguente: **./build_dm.sh**.

Se il computer non è possibile accedere a un sito esterno tramite FTP, ottenere `unixODBC-2.3.0.tar.gz`. È possibile ottenere `unixODBC-2.3.0.tar.gz` da [ http://www.unixodbc.org ](http://www.unixodbc.org/). Fare clic sui **scaricare** collegamento sul lato sinistro della pagina per passare alla pagina di download. Fare clic sul collegamento appropriato per scaricare unixODBC-2.3.0 (non unixODBC-2.3.1). UnixODBC-2.3.1 non è supportato con questa versione di [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 11 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]. Eseguire il comando seguente per iniziare l'installazione di gestione Driver unixODBC: **./build_dm.sh - url di download = file://unixODBC-2.3.0.tar.gz**.  

6.  Tipo **Sì** per procedere all'estrazione dei file. Questa parte del processo può richiedere fino a cinque minuti.  

7.  Al termine dell'esecuzione dello script, seguire le istruzioni visualizzate per installare Gestione driver unixODBC.

A questo punto si è pronti per l'installazione del driver. Per ulteriori informazioni, vedere [l'installazione di Microsoft ODBC Driver for SQL Server in Linux e macOS](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md).  

**Installazione manuale**

Se l'esecuzione dello script di installazione non viene completata, configurare e creare il programma di gestione dei driver manualmente.

1.  Rimuovere qualsiasi versione precedente di unixODBC, ad esempio unixODBC 2.2.11. In Red Hat Enterprise Linux 5 o 6, eseguire il comando seguente: **yum rimuovere unixODBC**. In SUSE Linux Enterprise, **zypper rimuovere unixODBC**.  
  
2.  Passare a [ http://www.unixodbc.org ](http://www.unixodbc.org/). Fare clic su di **scaricare** collegamento sul lato sinistro della pagina per passare alla pagina di download. Fare clic sul collegamento appropriato per salvare il file unixODBC-2.3.0.tar.gz nel computer. UnixODBC-2.3.1 non è supportato con questa versione di [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 11 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)].  
  
3.  Nel computer Linux, eseguire il comando: **tar xvzf unixodbc-2.3.0.tar.gz**.  
  
4.  Passare alla directory unixODBC-2.3.0.  
  
5.  Al prompt dei comandi eseguire il comando: **CPPFLAGS = "-DSIZEOF_LONG_INT = 8"**.  
  
6.  Al prompt dei comandi eseguire il comando: **esportare CPPFLAGS**.  
  
7.  Al prompt dei comandi eseguire il comando: **". / configurare - prefix = / usr - libdir = / usr/lib64 - sysconfdir = e così via-enable gui = no - enable-driver = no - iconv-enable con-iconv-char-enc = UTF8 - con-iconv-ucode-enc = UTF16LE"**.  
  
8.  A un prompt dei comandi (connesso come radice), eseguire il comando: **rendere**.  
  
9. A un prompt dei comandi (connesso come radice), eseguire il comando: **installare**.  

A questo punto si è pronti per l'installazione del driver. Per ulteriori informazioni, vedere [l'installazione di Microsoft ODBC Driver for SQL Server in Linux e macOS](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md).  
  
## <a name="see-also"></a>Vedere anche
[L'installazione di Microsoft ODBC Driver for SQL Server in Linux e macOS](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)

[Problemi noti in questa versione del driver](../../../connect/odbc/linux-mac/known-issues-in-this-version-of-the-driver.md)

[Note sulla versione](../../../connect/odbc/linux-mac/release-notes.md)
