---
title: Risolvere i problemi relativi all'integrità delle risorse di SQL Server (Utilità SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: maintenance-plans
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 614f07b5-f221-4013-9f8d-22964cf42270
caps.latest.revision: 7
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 5157d55bedf199d907247c1c13e3b4a11de01061
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32942376"
---
# <a name="troubleshoot-sql-server-resource-health-sql-server-utility"></a>Risoluzione dei problemi relativi all'integrità delle risorse di SQL Server (Utilità SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  La risoluzione dei problemi di integrità delle risorse identificati da un punto di controllo dell'utilità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] potrebbe includere la riduzione di una CPU sovrautilizzata su un computer o su un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]oppure la riduzione di una CPU sovrautilizzata per un'applicazione del livello dati. Altri problemi potrebbero includere la risoluzione dello spazio file sovrautilizzato per i file di database o la risoluzione del sovrautilizzo dello spazio su disco allocato su un volume di archiviazione.  
  
 Notare che se il database si trova nello stato di "emergenza", lo stato di integrità visualizzerà lo spazio sovrautilizzato del file di log.  
  
 Per altre informazioni sulla raccolta dati con errori che comporta icone di stato grigie nella visualizzazione elenco dell'istanza gestita su un punto di controllo dell'utilità, vedere [Risoluzione dei problemi relativi a Utilità SQL Server](http://msdn.microsoft.com/library/f5f47c2a-38ea-40f8-9767-9bc138d14453). Per altre informazioni sulle attività iniziali con Utilità [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , vedere [Attività e funzionalità di Utilità SQL Server](../../relational-databases/manage/sql-server-utility-features-and-tasks.md).  
  
 Per ulteriori informazioni sulla riduzione dei problemi di integrità specifici delle risorse identificati da un punto di controllo dell'utilità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , vedere gli argomenti seguenti.  
  
-   [Identificazione della versione e dell'edizione di SQL Server](http://go.microsoft.com/fwlink/?LinkID=178504)  
  
-   [Risoluzione dei problemi relativi alle prestazioni in SQL Server 2008](http://go.microsoft.com/fwlink/?LinkId=151354)  
  
  
