---
title: Eseguire la migrazione di database di Access a SQL Server - database SQL di Azure | Documenti Microsoft
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
helpviewer_keywords:
- instructions, migration
- migrating databases, overview
- overview, migration process
- procedure, migration
- recommended migration process
ms.assetid: 76a3abcf-2998-4712-9490-fe8d872c89ca
caps.latest.revision: 23
author: sabotta
ms.author: carlasab
manager: lonnyb
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 6d3c44ed3c73edae1b2b8d9cd244a2530c5748cf
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="migrating-access-databases-to-sql-server---azure-sql-db-accesstosql"></a>Migrazione di database di Access a SQL Server: database SQL di Azure (AccessToSQL)
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]Migration Assistant (SSMA) è un ambiente completo che consente di rapidamente la migrazione dei database di Access per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure. Tramite SSMA, è possibile controllare l'accesso e [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure oggetti di database, valutare il database di Access per la migrazione, convertire gli oggetti di database di Access, caricarli in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure, quindi eseguire la migrazione dei dati.  
  
## <a name="recommended-migration-process"></a>Consiglia di processo di migrazione  
Eseguire correttamente la migrazione di oggetti e dati dall'accesso al [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure, procedere come segue:  
  
1.  [Creare un nuovo progetto SSMA](http://msdn.microsoft.com/en-us/f2d1f0b0-5394-4adb-b3f3-abd71eb68ca7). Dopo aver creato il progetto, è possibile [impostare le opzioni progetto](http://msdn.microsoft.com/en-us/0a7304df-2f35-4453-96ef-7ac83dea1167). Tra le opzioni di conversione, opzioni di migrazione e mapping dei tipi di dati.  
  
2.  [Aggiungere il file di database di Access](http://msdn.microsoft.com/en-us/e944c740-4c8a-4bc1-b0ed-be57bc06dced) al progetto.  
  
    È possibile aggiungere file singoli oppure è possibile aggiungere i file che trova nel computer o nella rete.  
  
3.  [Connettersi all'istanza di destinazione di SQL Server](http://msdn.microsoft.com/en-us/f84cf007-ddf1-4396-a07c-3e0729abc769) o [Connetti all'istanza di destinazione di SQL Azure](http://msdn.microsoft.com/en-us/1ba0d113-dc05-4431-8689-e14a8821bafd).  
  
    Connessione a SQL Server o SQL Azure.  
  
4.  Per personalizzare il mapping tra uno o più database di Access e [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o schemi di SQL Azure, [eseguire il mapping di database di origine e destinazione](http://msdn.microsoft.com/en-us/69bee937-7b2c-49ee-8866-7518c683fad4).  
  
5.  Facoltativamente, è possibile [creare una relazione di valutazione](http://msdn.microsoft.com/en-us/8b9e23d6-da62-437a-8c05-8ad2628b9441)per determinare se gli oggetti di database di Access possono essere convertiti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure.  
  
6.  [Convertire gli oggetti di database di Access](http://msdn.microsoft.com/en-us/e0ef67bf-80a6-4e6c-a82d-5d46e0623c6c) a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o le definizioni degli oggetti di SQL Azure.  
  
7.  [Caricare gli oggetti di database convertito in SQL Server](http://msdn.microsoft.com/en-us/4e854eee-b10c-4f0b-9d9e-d92416e6f2ba).  
  
    È possibile entrambi carica gli oggetti di database in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure tramite SSMA oppure è possibile salvare [!INCLUDE[tsql](../../includes/tsql_md.md)] script.  
  
8.  [Eseguire la migrazione di accesso ai dati in SQL Server](http://msdn.microsoft.com/en-us/f3b18af7-1af0-499d-a00d-a0af94895625).  
  
    > [!NOTE]  
    > È possibile convertire, caricare e la migrazione di schemi e dati in un unico passaggio. Per eseguire la migrazione di un solo clic, fare clic su di **Converti, carica ed eseguire la migrazione** pulsante.  
  
9. Se si desidera che le applicazioni di accesso per utilizzare i dati nella [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure, utilizzare [collegare le tabelle di accesso alle tabelle di SQL Server](http://msdn.microsoft.com/en-us/82374ad2-7737-4164-a489-13261ba393d4).  
  
Per questa procedura, è possibile utilizzare anche la migrazione guidata. Per ulteriori informazioni, vedere [la migrazione guidata](http://msdn.microsoft.com/en-us/5bab5914-b2ae-4795-8cf5-83e42d64bef2).  
  
## <a name="see-also"></a>Vedere anche  
[Introduzione a SQL Server Migration Assistant per Access](http://msdn.microsoft.com/en-us/462a731f-08f1-44e1-9eeb-4deac6d2f6c5)  
[Preparazione dei database di Access per la migrazione](http://msdn.microsoft.com/en-us/9b80a9e0-08e7-4b4d-b5ec-cc998d3f5114)  
  

