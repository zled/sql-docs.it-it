---
title: Connettersi al database SQL di Azure (SybaseToSQL) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: ssma-sybase
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 96538007-1099-40c8-9902-edd07c5620ee
caps.latest.revision: "5"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d63fac7037bfe3f3646d9fa1c36200aa682b2fe3
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2017
---
# <a name="connect-to-azure-sql-db--sybasetosql"></a>Connettersi al database SQL di Azure (SybaseToSQL)
Utilizzare la connessione a database SQL di Azure, finestra di dialogo per connettersi al database che si desidera eseguire la migrazione di database SQL di Azure.  
  
Per accedere a questa finestra di dialogo, scegliere il **File** dal menu **Connetti al database SQL di Azure**. Se in precedenza si è connessi, il comando è **riconnessione al database SQL di Azure.**  
  
## <a name="options"></a>Opzioni  
**Nome server**  
  
Selezionare o immettere il nome del Server per la connessione al database SQL di Azure.  
  
**Database**  
  
Selezionare, inserire o **Sfoglia** il nome del Database.  
  
> [!IMPORTANT]  
> SSMA per Sybase non supporta la connessione al database master nel database di SQL Azure.  
  
**User name**  
  
Immettere il nome utente utilizzato per connettersi al database del database SQL di Azure SSMA  
  
**Password**  
  
Immettere la password associata al nome utente.  
  
**Crittografare**  
  
SSMA consiglia una connessione crittografata al database SQL di Azure.  
  
## <a name="create-azure-database"></a>Creare il Database di Azure  
Se non sono disponibili database nell'account di database SQL di Azure, è possibile creare il primo database.  
  
Per creare un nuovo database per la prima volta, seguire i passaggi seguenti  
  
1.  Fare clic sul pulsante Sfoglia che è presente nella finestra Connetti a database SQL di Azure, finestra di dialogo  
  
2.  Se non sono disponibili database, vengono visualizzati i seguenti due voci di menu.  
  
    1.  **(Nessun database trovato)**  che è disabilitato e visualizzato in grigio costantemente  
  
    2.  **Crea nuovo database** cui è abilitata solo se non sono disponibili database nell'account di database SQL di Azure. Facendo clic su questa voce di menu nella finestra di dialogo Crea Database di Azure è presente con dimensioni e il nome di database.  
  
3.  Al momento della creazione del database, i due parametri seguenti vengono forniti come input:  
  
    1.  **Nome del database:** immettere il nome del Database.  
  
    2.  **Dimensioni del database:** selezionare le dimensioni del Database che si devono creare nell'account di database SQL di Azure.  
  
