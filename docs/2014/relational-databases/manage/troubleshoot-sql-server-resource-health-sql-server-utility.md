---
title: Risolvere i problemi relativi all'integrità delle risorse di SQL Server (Utilità SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 614f07b5-f221-4013-9f8d-22964cf42270
caps.latest.revision: 6
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 743186343c288b4ea49255acb5651c6b4716173c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37219241"
---
# <a name="troubleshoot-sql-server-resource-health-sql-server-utility"></a>Risoluzione dei problemi relativi all'integrità delle risorse di SQL Server (Utilità SQL Server)
  La risoluzione dei problemi di integrità delle risorse identificati da un punto di controllo dell'utilità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] potrebbe includere la riduzione di una CPU sovrautilizzata su un computer o su un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]oppure la riduzione di una CPU sovrautilizzata per un'applicazione del livello dati. Altri problemi potrebbero includere la risoluzione dello spazio file sovrautilizzato per i file di database o la risoluzione del sovrautilizzo dello spazio su disco allocato su un volume di archiviazione.  
  
 Notare che se il database si trova nello stato di "emergenza", lo stato di integrità visualizzerà lo spazio sovrautilizzato del file di log.  
  
 Per altre informazioni sulla raccolta dati con errori che comporta icone di stato grigie nella visualizzazione elenco dell'istanza gestita su un punto di controllo dell'utilità, vedere [Risoluzione dei problemi relativi a Utilità SQL Server](../../database-engine/troubleshoot-the-sql-server-utility.md). Per altre informazioni sulle attività iniziali con Utilità [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , vedere [Attività e funzionalità di Utilità SQL Server](sql-server-utility-features-and-tasks.md).  
  
 Per ulteriori informazioni sulla riduzione dei problemi di integrità specifici delle risorse identificati da un punto di controllo dell'utilità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , vedere gli argomenti seguenti.  
  
-   [Identificazione della versione e dell'edizione di SQL Server](http://go.microsoft.com/fwlink/?LinkID=178504)  
  
-   [Risoluzione dei problemi relativi alle prestazioni in SQL Server 2008](http://go.microsoft.com/fwlink/?LinkId=151354)  
  
  
