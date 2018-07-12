---
title: Modifiche di rilievo alla gestione delle funzionalità degli strumenti in SQL Server 2014 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 3ff3fad8-b569-4516-bd58-5a3efeb537e2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f206da123659c750f955d2132142dcae76df6a46
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37165352"
---
# <a name="breaking-changes-to-management-tools-features-in-sql-server-2014"></a>Modifiche di rilievo nelle funzionalità degli strumenti di gestione in SQL Server 2014
  In questo argomento vengono descritte le modifiche di rilievo apportate alle funzionalità degli strumenti di gestione. Tali modifiche potrebbero interrompere il funzionamento di applicazioni, funzionalità o script basati su versioni precedenti di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. È possibile che questi problemi si verifichino quando viene effettuato un aggiornamento. Per altre informazioni, vedere [Use Upgrade Advisor to Prepare for Upgrades](../../2014/sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md).  
  
## <a name="breaking-changes-in-includesssql14includessssql14-mdmd"></a>Modifiche di rilievo in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]  
 Informazioni disponibili in futuro.  
  
## <a name="breaking-changes-in-includesssql11includessssql11-mdmd"></a>Modifiche di rilievo in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]  
  
### <a name="you-cannot-use-includesssql11includessssql11-mdmd-management-tools-to-create-a-utility-control-point-on-a-includesskilimanjaroincludessskilimanjaro-mdmd-instance-of-sql-server"></a>Non è possibile utilizzare gli strumenti di gestione di [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] per creare un punto di controllo dell'utilità in un'istanza di [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] di SQL Server  
 Per creare un punto di controllo dell'utilità in un'istanza di [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)], utilizzare gli strumenti di gestione di [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] .  
  
### <a name="smo-has-been-reversioned-in-includesssql11includessssql11-mdmd"></a>SMO è stato modificato in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]  
 È possibile che il codice sviluppato con SMO da [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] o versioni precedenti non venga compilato in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] senza modifiche minori. Per altre informazioni, vedere [Compatibilità con le versioni precedenti in SMO](../relational-databases/server-management-objects-smo/backward-compatibility-in-smo.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Compatibilità con le versioni precedenti](../../2014/getting-started/backward-compatibility.md)  
  
  
