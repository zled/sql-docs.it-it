---
title: Installazione di SSMA per SAP ASE (SybaseToSQL) | Documenti Microsoft
ms.custom: ''
ms.date: 11/29/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-sybase
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 8d5a4ce6-b747-46e3-9184-645d56e8b35c
caps.latest.revision: 6
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4f926ea51868f7833b3b275602d4e241fc18e327
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2018
---
# <a name="installing-ssma-for-sap-ase-sybasetosql"></a>Installazione di SSMA per SAP ASE (SybaseToSQL)
[!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Migration Assistant (SSMA) per SAP Adaptive Server Enterprise (ASE) è costituito da un'applicazione client che consente di eseguire una migrazione da SAP ASE a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o Database SQL di Azure. Include anche un pacchetto di estensione che supporta la migrazione dei dati e l'utilizzo delle funzioni di sistema ASE nei database migrati.  
  
Installare l'applicazione client nel computer da cui si prevede di eseguire i passaggi della migrazione. Installare i file di estensione pack nel computer in cui è in esecuzione [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] in cui i database migrati devono essere ospitate.  
  
## <a name="upgrading-ssma-for-sap-ase"></a>Aggiornamento di SSMA per SAP ASE  
Se si desidera eseguire l'aggiornamento a una versione successiva di SSMA per SAP ASE, è innanzitutto necessario disinstallare il client e il pacchetto di estensione del server. Quindi installare la versione più recente.  
  
Se si apre un progetto da una versione precedente di SSMA per SAP ASE, SSMA viene chiesto se si desidera convertire il progetto alla versione più recente. Fare clic su **Sì** per funzionare con il progetto alla versione più recente di SSMA.  
  
## <a name="contents"></a>Sommario  
  
|Articolo|Description|  
|---------|---------------|  
|[Installazione di SSMA per SAP ASE Client &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-for-sybase-client-sybasetosql.md)|Fornisce informazioni e istruzioni per l'installazione di SSMA per client SAP ASE.|  
|[Installazione dei componenti di SSMA in SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-components-on-sql-server-sybasetosql.md)|Fornisce informazioni e istruzioni per installare il pacchetto di estensione in istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].|  
|[Rimozione di SSMA per componenti SAP ASE &#40;SybaseToSQL&#41;](../../ssma/sybase/removing-ssma-for-sybase-components-sybasetosql.md)|Vengono fornite istruzioni per la disinstallazione del client pack programma e l'estensione.|  
  
## <a name="see-also"></a>Vedere anche  
[Migrazione SAP ASE database a SQL Server - Database SQL di Azure &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
