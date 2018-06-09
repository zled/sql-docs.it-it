---
title: L'installazione di SSMA per Sybase Client (SybaseToSQL) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: e770c2f2-52b9-4471-a207-0d35df41399c
caps.latest.revision: 18
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 1e4db8a57c7928290ed97e32a897ee03544462a3
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2018
ms.locfileid: "34778807"
---
# <a name="installing-ssma--for-sybase-client-sybasetosql"></a>L'installazione di SSMA per Sybase Client (SybaseToSQL)
Il client SSMA è costituito da file di programma vengono utilizzati per connettersi a un server di database di Sybase Adaptive Server Enterprise (ASE) e un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o database SQL di Azure, convertire gli oggetti di database ASE a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o sintassi di database SQL di Azure, caricare gli oggetti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o database SQL di Azure, e quindi la migrazione dei dati per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o Azure SQLDB.  
  
In questo argomento fornisce le istruzioni per l'installazione di SSMA prerequisiti di installazione.  
  
## <a name="prerequisites"></a>Prerequisiti  
SSMA è progettato per funzionare con ASE 11.9.2 o versioni successive e tutte le edizioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
Prima di installare SSMA, assicurarsi che il computer soddisfi i requisiti seguenti:  
  
-   Windows 7 o versioni successive o Windows Server 2008 o versioni successive.  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows Installer 3.1 o versione successiva.  
  
-   Il [!INCLUDE[msCoName](../../includes/msconame_md.md)] .NET Framework versione 4.0 o versione successiva. È disponibile in .NET Framework versione 4.0 di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] supporto del prodotto. È anche possibile ottenere dal [Centro per sviluppatori di .NET Framework](http://go.microsoft.com/fwlink/?LinkId=48882).  
  
-   Il provider Sybase OLEDB/ADO.Net/ODBC e la connettività al server di database Sybase ASE che contiene i database che si desidera eseguire la migrazione. È possibile installare i provider dal supporto del prodotto Sybase ASE. Per informazioni sulla connettività, vedere [ci si connette per Sybase ASE &#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-sybase-ase-sybasetosql.md).  
  
-   Per l'accesso e autorizzazioni sufficienti nel computer che ospita l'istanza di destinazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o database SQL di Azure in cui si desidera migrare gli oggetti di database e i dati. Per altre informazioni, vedere [connessione a SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-sql-server-sybasetosql.md)/[la connessione al database SQL di Azure &#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-azure-sql-db-sybasetosql.md).  
  
-   4 GB di RAM consigliato.  
  
## <a name="installing-the-ssma-for-sybase-client"></a>L'installazione di SSMA per Sybase Client  
SSMA è un download Web. Per scaricare la versione più recente, vedere il [pagina di download di SQL Server Migration Assistant](http://aka.ms/ssmaforsybase).  
  
Dopo aver scaricato la versione più recente, è necessario estrarre i file di installazione da prima di poter installare SSMA.  
  
**Per installare il client SSMA**  
  
1.  Fare doppio clic su SSMA per Sybase *n*. Install.exe, dove *n* è il numero di build.  
  
2.  Nella pagina di benvenuto fare clic su **Avanti**.  
  
    Se non si dispone di installati i prerequisiti, verrà visualizzato un messaggio che indica che è necessario innanzitutto installare i componenti necessari. Assicurarsi di avere installato tutti i prerequisiti e quindi eseguire nuovamente il programma di installazione.  
  
3.  Leggere il contratto di licenza. Se si accetta, selezionare **accetto i termini del contratto di licenza**, quindi fare clic su **Avanti**.  
  
4.  Nella pagina Selezione tipo di installazione, fare clic su **tipica**.  
  
5.  Fare clic su **Installa**.  
  
> [!IMPORTANT]  
> 1.  Disinstallare tutte le versioni precedenti di SSMA per Sybase prima di installare la nuova versione.  
  
Il percorso di installazione predefinito è C:\Program Files\Microsoft SQL Server Migration Assistant per Sybase.  
  
Oltre ai file di programma SSMA, è necessario installare anche SSMA per Sybase estensione Pack su [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] . Per altre informazioni, vedere [installazione dei componenti di SSMA in SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-components-on-sql-server-sybasetosql.md).  
  
## <a name="see-also"></a>Vedere anche  
[Installazione dei componenti di SSMA in SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-components-on-sql-server-sybasetosql.md)  
[Migrazione di database Sybase ASE a SQL Server: SQL Azure database &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
