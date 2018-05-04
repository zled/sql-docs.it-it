---
title: Impostazioni (database SQL Azure) del progetto (SybaseToSQL) | Documenti Microsoft
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
ms.assetid: 57002374-0d4d-43c1-b4e9-cbec02355a9c
caps.latest.revision: 4
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 41c429bd09254580e705131988882402e227761c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="project-settings-azure-sql-db--sybasetosql"></a>Impostazioni (database SQL Azure) del progetto (SybaseToSQL)
Le impostazioni del progetto di database SQL di Azure consentono di configurare il suffisso del database di database SQL di Azure per essere aggiunto nella finestra di dialogo di connessione e consentire l'implementazione di meccanismo di heartbeat nella connessione di database SQL di Azure.  
  
Il riquadro database SQL di Azure è disponibile nel **impostazioni progetto** e **impostazioni di progetto predefinite** finestre di dialogo.  
  
-   Utilizzare la finestra di dialogo Impostazioni di progetto per impostare le opzioni di configurazione per il progetto corrente. Per accedere alle impostazioni di database SQL di Azure, sul **strumenti** dal menu **impostazioni progetto**, fare clic su **generale** nella parte inferiore del riquadro sinistro, quindi scegliere **database SQL di Azure**.  
  
-   Utilizzare la finestra di dialogo Impostazioni di progetto predefinite per impostare le opzioni di configurazione per tutti i progetti. Per accedere a impostazioni di database SQL di Azure, scegliere il **strumenti** dal menu **DefaultProject impostazioni**, fare clic su **generale** nella parte inferiore del riquadro sinistro, quindi scegliere **database SQL di Azure**.  
  
## <a name="connectivity"></a>Connettività  
**Intervallo heartbeat**  
  
Specifica un intervallo di tempo da utilizzare per il meccanismo di heartbeat per mantenere la connessione di database SQL di Azure attivo in ' minuti: formato secondi.  
  
**Il valore predefinito**:' 4:45 '  
  
Il valore deve essere specificato in corso: formato degli ss (ad esempio, "4:45 ' o ' 0:50 ').  
  
**Suffisso del Server di database SQL di Azure**  
  
Specifica un suffisso di server di database SQL di Azure  
  
**Il valore predefinito**: 'database.windows.net'.  
  
