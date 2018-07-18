---
title: La migrazione dei dati di accesso a SQL Server - Azure SQL database (AccessToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- bulk loading data
- data, loading into SQL Azure
- data, loading into SQL Server
- migrating databases, loading data
- migrating databases, options
- options, migrating data
- SQL Azure, migrating data into
- SQL Server, migrating data into
ms.assetid: f3b18af7-1af0-499d-a00d-a0af94895625
caps.latest.revision: 17
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 9cb790ec1b79827b7db578001633c75ef6e1b191
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/12/2018
ms.locfileid: "38979473"
---
# <a name="migrating-access-data-into-sql-server---azure-sql-db-accesstosql"></a>La migrazione dei dati di accesso a SQL Server - Azure SQL database (AccessToSQL)
Dopo avere creato gli oggetti di database in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], è possibile migrare i dati da Access a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure.  
  
## <a name="setting-migration-options"></a>Impostazione delle opzioni di migrazione  
Prima della migrazione dei dati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure, esaminare le opzioni di migrazione del progetto nella **impostazioni di progetto** nella finestra di dialogo. Nella finestra di dialogo, è possibile impostare la dimensione del batch di migrazione, blocco di tabella, vincolo controllo, i trigger di inserimento generazione, identità e il valore null, la gestione e su come gestire date fuori il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] intervallo. Per altre informazioni, vedere [impostazioni progetto (migrazione)](http://msdn.microsoft.com/4caebc9c-8680-4b99-a8fa-89c43161c95d).  
  
## <a name="migrating-data"></a>La migrazione dei dati  
Eseguire la migrazione dei dati sono un'operazione di caricamento bulk che sposta le righe di dati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure nelle transazioni. Il numero di righe da caricare nella [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure in ogni transazione è configurato nelle impostazioni del progetto.  
  
Per visualizzare i messaggi di migrazione, verificare che il riquadro di Output è visibile. Se non lo è, nel **View** dal menu **Output**.  
  
**Per eseguire la migrazione dei dati**  
  
1.  Assicurarsi che sono stati caricati gli oggetti di database di Access in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure.  
  
2.  Nel Visualizzatore metadati di accesso, selezionare gli oggetti che contengono i dati che si desidera eseguire la migrazione:  
  
    -   Per eseguire la migrazione dei dati per un intero database, selezionare la casella di controllo accanto al nome del database.  
  
    -   Per eseguire la migrazione dei dati da singole tabelle, espandere il database, espandere **tabelle**e quindi selezionare la casella di controllo accanto alla tabella. Per omettere i dati da singole tabelle, deselezionare la casella di controllo.  
  
3.  Fare doppio clic su **database** e quindi selezionare **Migrate Data**.  
  
È anche possibile eseguire la migrazione dei dati all'esterno di SSMA usando il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **bcp** utilità della riga di comando o [!INCLUDE[ssISnoversion](../../includes/ssisnoversion_md.md)]. Per altre informazioni su questi strumenti, vedere [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] documentazione Online.  
  
## <a name="next-step"></a>Passaggio successivo  
Se si dispone di accedere alle applicazioni di database che si desidera continuare a usare dopo la migrazione, collegare le tabelle di database di Access per il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o tabelle di SQL Azure. Per altre informazioni, vedere [collegamento di accesso alle applicazioni di SQL Server](http://msdn.microsoft.com/82374ad2-7737-4164-a489-13261ba393d4).  
  
## <a name="see-also"></a>Vedere anche  
[Migrazione dei database di Access a SQL Server](http://msdn.microsoft.com/76a3abcf-2998-4712-9490-fe8d872c89ca)  
[Impostazione conversione e le opzioni di migrazione](http://msdn.microsoft.com/0a7304df-2f35-4453-96ef-7ac83dea1167)  
  
