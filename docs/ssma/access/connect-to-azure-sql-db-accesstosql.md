---
title: Connettersi al database SQL di Azure (AccessToSQL) | Documenti Microsoft
ms.prod: sql
ms.prod_service: sql-tools
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Connect to SQL Azure dialog box
ms.assetid: bf44b236-d9be-41ae-a5fd-bd73038e505f
caps.latest.revision: 17
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: b23de92a365404164109b264a8e2c8d940190c5a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="connect-to-azure-sql-db-accesstosql"></a>Connettersi al database SQL di Azure (AccessToSQL)
Utilizzare la connessione per la finestra di dialogo di SQL Azure per la connessione al database di SQL Azure che si desidera eseguire la migrazione.  
  
Per accedere a questa finestra di dialogo, scegliere il **File** dal menu **Connetti a SQL Azure**. Se si è già connessa, il comando è **Riconnetti a SQL Azure.**  
  
## <a name="options"></a>Opzioni  
**Nome server**  
  
Selezionare o immettere il nome del Server per la connessione a SQL Azure.  
  
**Database**  
  
Selezionare, inserire o **Sfoglia** il nome del Database.  
  
> [!IMPORTANT]  
> SSMA per l'accesso non supporta la connessione al database master in SQL Azure.  
  
**Nome utente**  
  
Immettere il nome utente utilizzato per connettersi al database di SQL Azure SSMA  
  
**Password**  
  
Immettere la password associata al nome utente.  
  
**Crittografare**  
  
SSMA consiglia una connessione crittografata a SQL Azure.  
  
## <a name="create-azure-database"></a>Creare il Database di Azure  
Per creare un nuovo database di azure, seguire i passaggi seguenti  
  
1.  Fare clic sul pulsante Sfoglia che è presente nella finestra Connetti per la finestra di dialogo di SQL Azure  
  
2.  Se non sono disponibili database, vengono visualizzate due voci di menu  
  
    1.  **(Nessun database trovato)**  che è disabilitata e costantemente in grigio  
  
    2.  **Crea nuovo database** è sempre abilitata, consentendo all'utente di creare un nuovo database di azure nell'account di SQL Azure. Al momento facendo clic su questa voce di menu, creare il database di azure, finestra di dialogo è presente con il nome di database e le dimensioni.  
  
3.  Al momento della creazione del database, questi due parametri viene fornito come input.  
  
    1.  **Nome del database:** immettere il nome del Database.  
  
    2.  **Dimensioni del database:** selezionare le dimensioni del Database che è necessario creare account di SQL Azure.  
  
