---
title: Visualizzare il log degli errori di SQL Server (SQL Server Management Studio) | Microsoft Docs
ms.custom: 
ms.date: 09/29/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- viewing logs
- displaying logs
- errors [SQL Server], logs
- logs [SQL Server], SQL Server error logs
- logs [SQL Server], viewing
ms.assetid: 55f468ba-146c-4ab3-95cd-d35d051afd12
caps.latest.revision: "14"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 177b287f4a107d87ed96acd96bd7a06efe5ecde4
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="view-the-sql-server-error-log-sql-server-management-studio"></a>Visualizzazione del log degli errori di SQL Server (SQL Server Management Studio)

Il log degli errori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contiene eventi definiti dall'utente e alcuni eventi di sistema necessari per la risoluzione dei problemi. 

## <a name="how-to-view-the-logs"></a>Come visualizzare i log

1.  In SSMS selezionare **Esplora oggetti**. Per **aprire** Esplora oggetti, la scelta rapida da tastiera è **F8**. In alternativa, nel menu principale fare clic su **Visualizza** e quindi selezionare **Esplora oggetti**:
    
    ![Object_explorer](../../relational-databases/performance/media/object-explorer.png) 

2.  In **Esplora oggetti**connettersi a un'istanza di SQL Server e quindi espandere l'istanza.
  
3.  Trovare ed espandere la sezione **Gestione** (presupponendo di avere le autorizzazioni necessarie per visualizzarla).

4.  Fare clic con il pulsante destro del mouse su **Log di SQL Server**, scegliere **Visualizza** e quindi **Visualizza log di SQL Server**.

    ![Visualizza log di SQL server in SSMS](../../relational-databases/performance/media/view-sqlserver-log-ssms.png) 
 
5.  Verrà visualizzato il Visualizzatore file di log (potrebbero essere necessari alcuni minuti), con un elenco dei log che è possibile visualizzare.
  
6. Diverse persone hanno consigliato l'utile post di [MSSQLTips.com](https://www.mssqltips.com/) [Identify location of the SQL Server Error Log file (Identificare la posizione del file di log degli errori di SQL Server)](https://www.mssqltips.com/sqlservertip/2506/identify-location-of-the-sql-server-error-log-file/). Assicurarsi di leggere questo post, in quanto contiene informazioni interessantissime.

