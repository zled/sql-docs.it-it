---
title: Impostazioni (database SQL Azure) del progetto (MySQLToSQL) | Documenti Microsoft
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-mysql
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
ms.assetid: 8c06420a-533b-4de0-948d-a0c6b368c544
caps.latest.revision: 10
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 91e0055b7a345b5746f8f14f3c3684683c443cc1
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="project-settings-azure-sql-db-mysqltosql"></a>Impostazioni (database SQL Azure) del progetto (MySQLToSQL)
Le impostazioni di progetto di SQL Azure consentono di configurare il suffisso del database di SQL Azure per essere aggiunto nella finestra di dialogo di connessione e consentire l'implementazione di meccanismo di heartbeat in connessione a SQL Azure.  
  
Il riquadro SQL Azure è disponibile nel **impostazioni progetto** e **impostazioni di progetto predefinite** finestre di dialogo.  
  
-   Utilizzare la finestra di dialogo Impostazioni di progetto per impostare le opzioni di configurazione per il progetto corrente. Per accedere alle impostazioni di SQL Azure, sul **strumenti** dal menu **impostazioni progetto**, fare clic su **generale** nella parte inferiore del riquadro sinistro, quindi scegliere **SQL Azure**.  
  
-   Utilizzare la finestra di dialogo Impostazioni di progetto predefinite per impostare le opzioni di configurazione per tutti i progetti. Per accedere alle impostazioni di SQL Azure, sul **strumenti** dal menu **DefaultProject impostazioni**, selezionare il tipo di progetto di migrazione come SQL Azure da **versione di destinazione della migrazione** elenco a discesa per accedere alle impostazioni nel riquadro SQL Azure, fare clic su **generale** nella parte inferiore del riquadro sinistro, quindi scegliere **SQL Azure**.  
  
## <a name="options"></a>Opzioni  
  
## <a name="connectivity"></a>Connettività  
**Intervallo heartbeat**  
  
Specifica un intervallo di tempo da utilizzare per il meccanismo di heartbeat per mantenere la connessione a SQL Azure attivo in ' minuti: formato secondi.  
  
**Il valore predefinito**:' 4:45 '  
  
Il valore deve essere specificato in corso: formato degli ss (ad esempio, "4:45 ' o ' 0:50 ').  
  
**SQL Server Azure suffisso**  
  
Specifica il suffisso del server SQL Azure  
  
**Il valore predefinito**: 'database.windows.net'.  
  
