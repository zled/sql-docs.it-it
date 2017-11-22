---
title: Installazione di SSMA per SAP ASE (SybaseToSQL) | Documenti Microsoft
ms.custom: 
ms.date: 09/30/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 8d5a4ce6-b747-46e3-9184-645d56e8b35c
caps.latest.revision: "6"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 41931c08813cb4836b799b97f2fba0fbbc645a8c
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="installing-ssma-for-sap-ase-sybasetosql"></a>Installazione di SSMA per SAP ASE (SybaseToSQL)
[!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]Migration Assistant (SSMA) per SAP ASE è costituito da un'applicazione client che consentono di eseguire una migrazione da SAP Adaptive Server Enterprise (ASE) a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o Database SQL di Azure. Include anche un pacchetto di estensione che supporta la migrazione dei dati e l'utilizzo delle funzioni di sistema ASE nei database migrati.  
  
Installare l'applicazione client nel computer da cui si eseguirà i passaggi della migrazione. È necessario installare i file di pacchetto di estensione nel computer in cui è in esecuzione [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] in cui verranno ospitati database migrati.  
  
## <a name="upgrading-ssma-for-sybase"></a>L'aggiornamento di SSMA per Sybase  
Se si desidera eseguire l'aggiornamento a una versione successiva di SSMA per SAP ASE, è necessario prima disinstallare il client e il pacchetto di estensione del server e quindi installare la versione più recente.  
  
Se si apre un progetto da una versione precedente di SSMA per SAP ASE, SSMA viene chiesto se si desidera convertire il progetto alla versione più recente. È necessario fare clic su **Sì** per funzionare con il progetto alla versione più recente di SSMA.  
  
## <a name="contents"></a>Sommario  
  
|Argomento|Description|  
|---------|---------------|  
|[Installazione di SSMA per SAP ASE Client &#40; SybaseToSQL &#41;](../../ssma/sybase/installing-ssma-for-sybase-client-sybasetosql.md)|Fornisce informazioni e istruzioni per l'installazione del client SSMA.|  
|[Installazione dei componenti SSMA in SQL Server &#40; SybaseToSQL &#41;](../../ssma/sybase/installing-ssma-components-on-sql-server-sybasetosql.md)|Fornisce informazioni e istruzioni per installare il pacchetto di estensione in istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].|  
|[Rimozione di SSMA per SAP ASE componenti &#40; SybaseToSQL &#41;](../../ssma/sybase/removing-ssma-for-sybase-components-sybasetosql.md)|Vengono fornite istruzioni per la disinstallazione del client pack programma e l'estensione.|  
  
## <a name="see-also"></a>Vedere anche  
[Migrazione SAP ASE di database a SQL Server: Database SQL di Azure &#40; SybaseToSQL &#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
