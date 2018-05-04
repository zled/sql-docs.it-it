---
title: Connettersi al database SQL di Azure (SybaseToSQL) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-sybase
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 96538007-1099-40c8-9902-edd07c5620ee
caps.latest.revision: 5
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: d04ec5e24a98a5ab995e57d3b3a540c09f6c3bdf
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="connect-to-azure-sql-db--sybasetosql"></a>Connettersi al database SQL di Azure (SybaseToSQL)
Utilizzare la connessione a database SQL di Azure, finestra di dialogo per connettersi al database che si desidera eseguire la migrazione di database SQL di Azure.  
  
Per accedere a questa finestra di dialogo, scegliere il **File** dal menu **Connetti al database SQL di Azure**. Se si è già connessa, il comando è **riconnessione al database SQL di Azure.**  
  
## <a name="options"></a>Opzioni  
**Nome server**  
  
Selezionare o immettere il nome del Server per la connessione al database SQL di Azure.  
  
**Database**  
  
Selezionare, inserire o **Sfoglia** il nome del Database.  
  
> [!IMPORTANT]  
> SSMA per Sybase non supporta la connessione al database master nel database di SQL Azure.  
  
**Nome utente**  
  
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
  
    1.  **(Nessun database trovato)**  che è disabilitata e costantemente in grigio  
  
    2.  **Crea nuovo database** cui è abilitata solo se non sono disponibili database nell'account di database SQL di Azure. Facendo clic su questa voce di menu nella finestra di dialogo Crea Database di Azure è presente con dimensioni e il nome di database.  
  
3.  Al momento della creazione del database, i due parametri seguenti vengono forniti come input:  
  
    1.  **Nome del database:** immettere il nome del Database.  
  
    2.  **Dimensioni del database:** selezionare le dimensioni del Database che è necessario creare account di database SQL di Azure.  
  
