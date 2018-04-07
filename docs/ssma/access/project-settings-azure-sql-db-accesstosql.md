---
title: Impostazioni (database SQL Azure) del progetto (AccessToSQL) | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-access
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Project Settings dialog box, SQL Azure
- SQL Azure settings
ms.assetid: bbb8a204-d0e4-4f0b-9709-271feb1f136e
caps.latest.revision: 11
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ca33c5cfd48b8ebc9c9b98bd6a0b606fec61ef96
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2018
---
# <a name="project-settings-azure-sql-db-accesstosql"></a>Impostazioni (database SQL Azure) del progetto (AccessToSQL)
Le impostazioni di progetto di SQL Azure consentono di configurare il suffisso del database di SQL Azure per essere aggiunto nella finestra di dialogo di connessione e consentire l'implementazione di meccanismo di heartbeat in connessione a SQL Azure.  
  
Il riquadro SQL Azure è disponibile nel **impostazioni progetto** e **impostazioni di progetto predefinite** finestre di dialogo.  
  
-   Utilizzare la finestra di dialogo Impostazioni di progetto per impostare le opzioni di configurazione per il progetto corrente. Per accedere alle impostazioni di SQL Azure, sul **strumenti** dal menu **impostazioni progetto**, fare clic su **generale** nella parte inferiore del riquadro sinistro, quindi scegliere **SQL Azure**.  
  
-   Utilizzare la finestra di dialogo Impostazioni di progetto predefinite per impostare le opzioni di configurazione per tutti i progetti. Per accedere alle impostazioni di SQL Azure, sul **strumenti** dal menu **DefaultProject impostazioni**, selezionare il tipo di progetto come "SQL Azure" in **versione di destinazione della migrazione** casella combinata per accedere alle impostazioni nel riquadro SQL Azure, fare clic su **generale** nella parte inferiore del riquadro sinistro, quindi scegliere **SQL Azure**.  
  
## <a name="options"></a>Opzioni  
  
## <a name="connectivity"></a>Connettività  
**Intervallo heartbeat**  
  
Specifica un intervallo di tempo da utilizzare per il meccanismo di heartbeat per mantenere la connessione a SQL Azure attivo in ' minuti: formato secondi.  
  
**Il valore predefinito**:' 4:45 '  
  
Il valore deve essere specificato in corso: formato degli ss (ad esempio, "4:45 ' o ' 0:50 ').  
  
**SQL Server Azure suffisso**  
  
Specifica il suffisso del server SQL Azure  
  
**Il valore predefinito**: 'database.windows.net'.  
  
