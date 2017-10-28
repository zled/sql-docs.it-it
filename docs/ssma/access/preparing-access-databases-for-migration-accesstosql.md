---
title: Preparazione dei database di Access per la migrazione (AccessToSQL) | Documenti Microsoft
ms.prod: sql-non-specified
ms.custom: 
ms.date: 08/15/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Access databases, versions
- Access databases, when to migrate
- Access databases, workgroup security
- backing up databases
- documenting databases
- files, preparing
- migrating databases, versions
- migrating databases, when to migrate
- versions of Access
- workgroup security
ms.assetid: 9b80a9e0-08e7-4b4d-b5ec-cc998d3f5114
caps.latest.revision: 20
author: Shamikg
ms.author: Shamikg
manager: murato
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: e4a6157cb56c6db911406585f841046a431eef99
ms.openlocfilehash: 0d94578759156dcde898a23267fb91922fc98b03
ms.contentlocale: it-it
ms.lasthandoff: 08/16/2017

---
# <a name="preparing-access-databases-for-migration-accesstosql"></a>Preparazione dei database di Access per la migrazione (AccessToSQL)
Prima di migrare i database di Access per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], è necessario determinare quali database, eseguire la migrazione e verificare che tali database siano pronti per la migrazione.  
  
## <a name="determining-when-to-migrate-to-sql-server"></a>Determinazione della necessità di eseguire la migrazione a SQL Server  
Il motore di database Jet, che viene utilizzato come il motore di database per l'accesso, è una soluzione flessibile e facile da usare per la gestione dei dati. Tuttavia, come i database diventi più grandi e più mission-critical, molti utenti individuare che richiedono prestazioni superiori, sicurezza o la disponibilità. Per le applicazioni che richiedono una piattaforma dati più affidabile, prendere in considerazione lo spostamento dei database sottostanti per tali applicazioni [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Per ulteriori informazioni per decidere quando eseguire la migrazione, vedere il [pagina informazioni di migrazione](http://go.microsoft.com/fwlink/?LinkId=68571) sul [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] sito Web.  
  
Dopo la migrazione dei database [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], è possibile continuare a usare l'accesso usando le tabelle collegate o manualmente è possibile eseguire la migrazione delle applicazioni per [!INCLUDE[msCoName](../../includes/msconame_md.md)] codice basato su .NET Framework che interagisce direttamente con [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
## <a name="determining-which-databases-to-migrate"></a>Determinazione di database di cui eseguire la migrazione  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]Migration Assistant (SSMA) per l'accesso è possibile individuare i database di Access per l'utente. È quindi possibile esportare i metadati relativi a tali database per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Per ulteriori informazioni su come esportare e query sui metadati, vedere [l'esportazione di un inventario di accesso](http://msdn.microsoft.com/7e1941fb-3d14-4265-aff6-c77a4026d0ed).  

   > [!NOTE]
   > Non tutte le funzionalità di accesso e le impostazioni sono supportate da, o può essere facilmente convertite, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Prima di iniziare la migrazione di database, vedere [funzionalità di accesso non compatibili](http://msdn.microsoft.com/99d45b9c-e3b9-4d56-8c25-b594b887ace1).
  
## <a name="preparing-for-migration"></a>Preparazione per la migrazione  
Usare le linee guida seguenti per preparare i database di Access per la migrazione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
### <a name="upgrading-older-access-databases"></a>Aggiornamento del database di Access precedenti  
SSMA per Access supporta Access 97 e versioni successive. Se sono presenti database da versioni precedenti di Access, aprire e salvare i database di Access 97 o versione successiva.  
  
### <a name="removing-workgroup-protection"></a>Rimozione della protezione del gruppo di lavoro  
SSMA non è possibile eseguire la migrazione di database che utilizzano la protezione del gruppo di lavoro. Per rimuovere la protezione del gruppo di lavoro da un database di Access, eseguire la procedura seguente:  
  
1.  Copiare il file di database di Access in un'altra posizione.  
  
2.  Aprire il database copiato.  
  
3.  Nel **strumenti** dal menu **sicurezza**, quindi selezionare **autorizzazioni utenti e gruppi**.  
  
4.  Selezionare il **utenti** opzione, selezionare il **Admin** utente, quindi assicurarsi che il **Amministra** l'autorizzazione è selezionata.  
  
5.  Selezionare il **gruppi** opzione, selezionare il **utenti** gruppo e quindi verificare che il **Amministra** l'autorizzazione è selezionata.  
  
6.  Fare clic su **OK**e quindi scegliere il **File** menu, fare clic su **uscita**.  
  
È ora possibile utilizzare SSMA per eseguire la migrazione del database copiato. Dopo aver caricato lo schema in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], è possibile proteggere manualmente il database su [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
### <a name="backing-up-databases"></a>Il backup dei database  
Prima della migrazione dei database di Access per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], è consigliabile eseguire il backup di entrambi i database di Access che si desidera migrare, nonché [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] in cui verrà eseguita la migrazione di database accedono a oggetti e dati.  
  
Per eseguire il backup di un database di Access nel **strumenti** dal menu **utilità Database**, quindi selezionare **backup Database**.  
  
Per informazioni su come eseguire il backup [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database, vedere "backup e ripristino di database [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] documentazione in linea.  
  
### <a name="documenting-databases"></a>La documentazione di database  
È inoltre possibile documentare le proprietà, quali gli elenchi di oggetti di database, le dimensioni dei file e autorizzazioni di database di Access. Per generare in Access, questa documentazione sul **strumenti** dal menu **Analizza**e quindi fare clic su **documentazione**.  
  
## <a name="see-also"></a>Vedere anche  
[Migrazione di database di Access a SQL Server](http://msdn.microsoft.com/76a3abcf-2998-4712-9490-fe8d872c89ca)  
[Il collegamento alle applicazioni di accesso di SQL Server](http://msdn.microsoft.com/82374ad2-7737-4164-a489-13261ba393d4)

