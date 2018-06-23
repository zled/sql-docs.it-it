---
title: Rilevato un gruppo di servizi Web ReportServer di SQL Server 2005 Report (Upgrade Advisor) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- deployment [Reporting Services]
ms.assetid: 699d24eb-7756-4b41-9294-ef1a94b2f267
caps.latest.revision: 15
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: 7d3affeac1976b82ba269c4d86eac94cdc04335f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36170697"
---
# <a name="sql-server-2005-report-server-web-service-group-detected-upgrade-advisor"></a>Rilevato un gruppo di servizi Web ReportServer di SQL Server 2005 (Upgrade Advisor)
  Upgrade Advisor ha rilevato che il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] istanza è associata un [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] gruppo di servizio Web ReportServer.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .|  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Description  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] non utilizza il [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] gruppo di servizio Web ReportServer. Quando si esegue l'aggiornamento da [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], questo gruppo di servizi viene eliminato e gli elenchi di controllo di accesso (ACL) personalizzati o gli utenti che appartengono al gruppo non vengono mantenuti durante l'aggiornamento.  
  
## <a name="corrective-action"></a>Azione correttiva  
 Prima di eseguire l'aggiornamento, eseguire il backup di tutti gli elenchi di controllo di accesso o utenti che appartengono al gruppo di servizi Web ReportServer di [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. A tale scopo, è possibile usare il **Icacls.exe** strumento da riga di comando [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] SP2 e versioni successive o lo strumento da riga di comando Cacls.exe nei sistemi operativi Windows precedenti a [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] SP2. Per ulteriori informazioni sulla sintassi per questi strumenti, vedere la documentazione di Windows. Dopo che l'installazione è stata completata, applicare gli elenchi di controllo di accesso personalizzati o gli utenti al gruppo Windows del server di report di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] per l'istanza del server di report. Il [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] gruppo di Windows del Server di Report assume la forma SQLServerReportServerUser$\<*nome_computer*>$\<*nome_istanza*>.  
  
## <a name="see-also"></a>Vedere anche  
 [Problemi di aggiornamento di Reporting Services &#40;Preparazione aggiornamento&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  