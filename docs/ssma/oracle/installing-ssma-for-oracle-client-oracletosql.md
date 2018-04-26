---
title: Installazione di SSMA per Client Oracle (OracleToSQL) | Documenti Microsoft
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-oracle
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Licensing SSMA
ms.assetid: d5d4903d-e296-4bbf-8780-63674c4d62d5
caps.latest.revision: 19
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.workload: On Demand
ms.openlocfilehash: bfbc8486c74a6bd90832ab86ec3fee7cf236275d
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="installing-ssma-for-oracle-client-oracletosql"></a>Installazione di SSMA per Client Oracle (OracleToSQL)
Il client SSMA è costituito da file di programma eseguono le attività seguenti:  
  
-   Connettersi a un database Oracle.  
  
-   Connettersi a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
-   Convertire gli oggetti di database Oracle per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] sintassi.  
  
-   Caricare gli oggetti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
-   La migrazione dei dati per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
In questo argomento fornisce le istruzioni per l'installazione di SSMA prerequisiti di installazione.  
  
## <a name="prerequisites"></a>Prerequisiti  
SSMA è progettato per funzionare con Oracle 9 o versioni successive e tutte le edizioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
Prima di installare SSMA, assicurarsi che il computer soddisfi i requisiti seguenti:  
  
-   Windows 7 o versioni successive o Windows Server 2008 o versioni successive.  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows Installer 3.1 o versione successiva.  
  
-   Il [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)] versione 4.0 o versione successiva. Il [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)] è disponibile nella versione 4.0 di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] supporto del prodotto. È anche possibile ottenere dal [Centro per sviluppatori di .NET Framework](http://go.microsoft.com/fwlink/?LinkId=48882).  
  
-   Client Oracle 9.0 o una versione successiva e la connettività ai database Oracle che si desidera eseguire la migrazione. La versione del client Oracle deve essere la stessa versione o una versione successiva, la versione del database Oracle.  
  
    È possibile installare il Client Oracle dal supporto del prodotto Oracle o dal sito Web Oracle. Per informazioni sulla connettività, vedere [connessione a Oracle Database &#40;OracleToSQL&#41;](../../ssma/oracle/connecting-to-oracle-database-oracletosql.md).  
  
-   Per l'accesso e autorizzazioni sufficienti nel computer che ospita l'istanza di destinazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o database SQL di Azure in cui si desidera migrare gli oggetti di database e i dati. Per altre informazioni, vedere [connessione a SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/connecting-to-sql-server-oracletosql.md).  
  
-   4 GB di RAM consigliato.  
  
## <a name="installing-the-ssma-for-oracle-client"></a>Installazione di SSMA per Client Oracle  
SSMA è un download Web. Per scaricare la versione più recente, vedere il [pagina di download di SQL Server Migration Assistant](http://aka.ms/ssmafororacle).  
  
Dopo aver scaricato la versione più recente, è necessario estrarre i file di installazione da prima di poter installare SSMA.  
  
**Per installare il client SSMA**  
  
1.  Fare doppio clic su SSMA per Oracle *n*. Install.exe, dove *n* è il numero di build.  
  
2.  Nella pagina di benvenuto fare clic su **Avanti**.  
  
    Se non si dispone di installati i prerequisiti, verrà visualizzato un messaggio che indica che è necessario innanzitutto installare i componenti necessari. Assicurarsi di avere installato tutti i prerequisiti e quindi eseguire nuovamente il programma di installazione.  
  
3.  Leggere il contratto di licenza. Se si accetta, selezionare **accetto i termini del contratto di licenza**, quindi fare clic su **Avanti**.  
  
4.  Nella pagina Selezione tipo di installazione, fare clic su **tipica**.  
  
5.  Fare clic su **Installa**.  
  
> [!IMPORTANT]  
> 1.  Prima di installare la nuova versione disinstallare tutte le versioni precedenti di SSMA per Oracle.  
  
Il percorso di installazione predefinito è C:\Program Files\Microsoft SQL Server Migration Assistant per Oracle.  
  
Oltre ai file di programma SSMA, è necessario installare anche SSMA per il pacchetto di estensione Oracle in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Per altre informazioni, vedere [installazione dei componenti di SSMA in SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/installing-ssma-components-on-sql-server-oracletosql.md).  
  
## <a name="see-also"></a>Vedere anche  
[Installazione dei componenti di SSMA in SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/installing-ssma-components-on-sql-server-oracletosql.md)  
[Migrazione di Oracle database a SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
  
