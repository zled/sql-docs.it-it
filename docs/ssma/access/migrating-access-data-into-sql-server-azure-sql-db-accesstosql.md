---
title: La migrazione dei dati di accesso in SQL Server - database SQL di Azure (AccessToSQL) | Documenti Microsoft
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
ms.openlocfilehash: 38301e26dbe4b39a2be873a2154ec791c3c9a3f6
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2018
ms.locfileid: "34773877"
---
# <a name="migrating-access-data-into-sql-server---azure-sql-db-accesstosql"></a>La migrazione dei dati di accesso in SQL Server - database SQL di Azure (AccessToSQL)
Dopo avere creato gli oggetti di database in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], è possibile migrare i dati dall'accesso al [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure.  
  
## <a name="setting-migration-options"></a>Impostazione delle opzioni di migrazione  
Prima di migrare i dati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure, esaminare le opzioni di migrazione del progetto nella **impostazioni progetto** la finestra di dialogo. In questa finestra di dialogo, è possibile impostare le dimensioni di batch migrazione, il blocco di tabella, il vincolo sul controllo, i trigger di inserimento, generazione di identità e il valore null, la gestione e come gestire le date del [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] intervallo. Per ulteriori informazioni, vedere [le impostazioni del progetto (migrazione)](http://msdn.microsoft.com/en-us/4caebc9c-8680-4b99-a8fa-89c43161c95d).  
  
## <a name="migrating-data"></a>La migrazione dei dati  
La migrazione di dati sono un'operazione di caricamento bulk che consente di spostare le righe di dati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure nelle transazioni. Il numero di righe da caricare nella [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure in ogni transazione è configurata nelle impostazioni del progetto.  
  
Per visualizzare i messaggi di migrazione, verificare che il riquadro di Output è visibile. In caso contrario, nel **vista** dal menu **Output**.  
  
**Per eseguire la migrazione dei dati**  
  
1.  Assicurarsi che sono stati caricati gli oggetti di database di Access in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure.  
  
2.  Nel Visualizzatore metadati di accesso, selezionare gli oggetti che contengono i dati che si desidera eseguire la migrazione:  
  
    -   Per eseguire la migrazione dei dati per un intero database, selezionare la casella di controllo accanto al nome del database.  
  
    -   Per migrare i dati di singole tabelle, espandere il database, **tabelle**, quindi selezionare la casella di controllo accanto alla tabella. Per omettere i dati di singole tabelle, deselezionare la casella di controllo.  
  
3.  Fare doppio clic su **database** e quindi selezionare **eseguire la migrazione di dati**.  
  
È inoltre possibile migrare i dati all'esterno di SSMA utilizzando il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **bcp** utilità della riga di comando o [!INCLUDE[ssISnoversion](../../includes/ssisnoversion_md.md)]. Per ulteriori informazioni su questi strumenti, vedere [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] documentazione in linea.  
  
## <a name="next-step"></a>Passaggio successivo  
Se si dispone di applicazioni di database di Access che si desidera continuare a utilizzare dopo la migrazione, collegare le tabelle di database di Access per il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o tabelle di SQL Azure. Per ulteriori informazioni, vedere [il collegamento di applicazioni di accesso a SQL Server](http://msdn.microsoft.com/en-us/82374ad2-7737-4164-a489-13261ba393d4).  
  
## <a name="see-also"></a>Vedere anche  
[La migrazione dei database di Access a SQL Server](http://msdn.microsoft.com/en-us/76a3abcf-2998-4712-9490-fe8d872c89ca)  
[Impostazione conversione e le opzioni di migrazione](http://msdn.microsoft.com/en-us/0a7304df-2f35-4453-96ef-7ac83dea1167)  
  
