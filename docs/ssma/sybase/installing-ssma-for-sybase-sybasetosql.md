---
title: Installazione di SSMA per SAP ASE (SybaseToSQL) | Microsoft Docs
ms.custom: ''
ms.date: 11/29/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 8d5a4ce6-b747-46e3-9184-645d56e8b35c
caps.latest.revision: 6
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 1ef07d51a854e8c2e9842ea15f7224a4ce437862
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/14/2018
ms.locfileid: "40392519"
---
# <a name="installing-ssma-for-sap-ase-sybasetosql"></a>Installazione di SSMA per SAP ASE (SybaseToSQL)
[!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration Assistant (SSMA) per SAP Adaptive Server Enterprise (ASE) è costituito da un'applicazione client che consente di eseguire una migrazione da SAP ASE a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o Database SQL di Azure. Contiene anche un pacchetto di estensione che supporta la migrazione dei dati e l'utilizzo di ambiente del servizio app di funzioni di sistema nei database migrati.  
  
Installare l'applicazione client nel computer da cui si prevede di eseguire i passaggi della migrazione. Installare i file di pacchetto di estensione nel computer che esegue [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in cui i database migrati devono essere ospitate.  
  
## <a name="upgrading-ssma-for-sap-ase"></a>L'aggiornamento di SSMA per ASE SAP  
Se si desidera eseguire l'aggiornamento a una versione successiva di SSMA per ASE SAP, è innanzitutto necessario disinstallare il client e il pacchetto di estensione di server. Quindi installare la versione più recente.  
  
Se si apre un progetto da una versione precedente di SSMA per ASE SAP, SSMA chiede se si vuole convertire il progetto alla versione più recente. Fare clic su **Sì** per lavorare con il progetto alla versione più recente di SSMA.  
  
## <a name="contents"></a>Sommario  
  
|Articolo|Description|  
|---------|---------------|  
|[Installazione di SSMA per SAP ASE Client &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-for-sybase-client-sybasetosql.md)|Include informazioni e istruzioni sull'installazione di SSMA per il client di SAP ASE.|  
|[Installazione di componenti SSMA in SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-components-on-sql-server-sybasetosql.md)|Include informazioni e istruzioni per installare il pacchetto di estensione nelle istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Rimozione di SSMA per componenti SAP ASE &#40;SybaseToSQL&#41;](../../ssma/sybase/removing-ssma-for-sybase-components-sybasetosql.md)|Vengono fornite istruzioni per la disinstallazione del client pack programma e l'estensione.|  
  
## <a name="see-also"></a>Vedere anche  
[Database SAP ASE la migrazione a SQL Server - Database SQL di Azure &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
