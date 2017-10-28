---
title: Installazione di SSMA per Client DB2 (DB2ToSQL) | Documenti Microsoft
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 3ae2a470-6afd-4512-b6d1-fcbe6afe88ad
caps.latest.revision: 8
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 4e003c72b6fea28c3048384701f3dc8839faacce
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="installing-ssma-for-db2-client-db2tosql"></a>Installazione di SSMA per Client DB2 (DB2ToSQL)
Il client SSMA è costituito da file di programma eseguono le attività seguenti:  
  
-   Connettersi a un database DB2.  
  
-   Connettersi a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
-   Convertire oggetti di database DB2 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] sintassi.  
  
-   Caricare gli oggetti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
-   La migrazione dei dati per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
In questo argomento fornisce le istruzioni per l'installazione di SSMA prerequisiti di installazione.  
  
## <a name="prerequisites"></a>Prerequisiti  
SSMA è progettato per funzionare con DB2 nella versione 9.0 e 10.0 z/OS o DB2 in LUW 9,8 e 10.1 o versioni successive e [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2012 e [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2014.  
  
Prima di installare SSMA, assicurarsi che il computer soddisfi i requisiti seguenti:  
  
-   Windows 7 o versioni successive o Windows Server 2008 o versioni successive.  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)]Windows Installer 3.1 o versione successiva.  
  
-   Il [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)] versione 4.0 o versione successiva. Il [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)] è disponibile nella versione 4.0 di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] supporto del prodotto. È anche possibile ottenere dal [Centro per sviluppatori di .NET Framework](http://go.microsoft.com/fwlink/?LinkId=48882).  
  
-   Provider Microsoft OLEDB per DB2 versione 5 o versione successiva e la connettività ai database di DB2 che si desidera eseguire la migrazione.  
  
-   Per l'accesso e autorizzazioni sufficienti nel computer che ospita l'istanza di destinazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o database SQL di Azure in cui si desidera migrare gli oggetti di database e i dati. Per ulteriori informazioni, vedere [connessione a SQL Server &#40; DB2eToSQL &#41;](../../ssma/db2/connecting-to-sql-server-db2etosql.md).  
  
-   4 GB di RAM consigliato.  
  
## <a name="microsoft-oledb-provider-for-db2"></a>Provider Microsoft OLE DB per DB2  
Per scaricare il provider OLE DB per DB2 versione 5.0, visitare [Feature Pack di Microsoft® SQL Server® 2014](http://www.microsoft.com/download/details.aspx?id=42295).  
  
SSMA è un download Web. Per scaricare la versione più recente, vedere il [pagina di download di SQL Server Migration Assistant](http://aka.ms/ssmafordb2).  
  
Dopo aver scaricato la versione più recente, è necessario estrarre i file di installazione da prima di poter installare SSMA.  
  
**Per installare il client SSMA**  
  
1.  Fare doppio clic su SSMA per DB2  *n* . Install.exe, in cui  *n*  è il numero di build.  
  
2.  Nella pagina di benvenuto fare clic su **Avanti**.  
  
    Se non si dispone di installati i prerequisiti, verrà visualizzato un messaggio che indica che è necessario innanzitutto installare i componenti necessari. Assicurarsi di avere installato tutti i prerequisiti e quindi eseguire nuovamente il programma di installazione.  
  
3.  Leggere il contratto di licenza. Se si accetta, selezionare **accetto i termini del contratto di licenza**, quindi fare clic su **Avanti**.  
  
4.  Nella pagina Selezione tipo di installazione, fare clic su **tipica**.  
  
5.  Fare clic su **Installa**.  
  
> [!IMPORTANT]  
> 1.  Prima di installare la nuova versione disinstallare tutte le versioni precedenti di SSMA per DB2.  
  
Il percorso di installazione predefinito è C:\Program Files\Microsoft SQL Server Migration Assistant per DB2.  
  
## <a name="see-also"></a>Vedere anche  
[Installazione dei componenti SSMA DB2ToSQL SQL Server &#40; &#41;](../../ssma/db2/installing-ssma-components-on-sql-server-db2tosql.md)  
[Migrazione di database DB2 a SQL Server &#40; DB2ToSQL &#41;](../../ssma/db2/migrating-db2-databases-to-sql-server-db2tosql.md)  
  

