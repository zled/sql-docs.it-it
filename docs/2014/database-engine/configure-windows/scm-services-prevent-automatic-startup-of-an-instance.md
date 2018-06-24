---
title: Impedire l'avvio automatico di un'istanza di SQL Server (Gestione configurazione SQL Server) | Documenti Microsoft
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
- automatic SQL Server startup
- SQL Server, stopping
- SQL Server, automatic startup
- canceling automatic startup
- stopping SQL Server
- preventing automatic startups [SQL Server]
ms.assetid: 782663cf-f3d7-4cc6-b621-21e4550f0322
caps.latest.revision: 33
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: b21ac71b54c9bfee76079f86c1d6d1a32fc0f9dc
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36063401"
---
# <a name="prevent-automatic-startup-of-an-instance-of-sql-server-sql-server-configuration-manager"></a>Impedire l'avvio automatico di un'istanza di SQL Server (Gestione configurazione SQL Server)
  In questo argomento viene illustrato come impedire che un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] venga avviata automaticamente in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] utilizzando Gestione configurazione SQL Server. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è normalmente configurato per l'avvio automatico. È possibile modificare questa configurazione impostando su manuale la modalità di avvio per l'istanza.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di Gestione configurazione SQL Server  
  
#### <a name="to-prevent-automatic-startup-of-an-instance-of-sql-server"></a>Per impedire l'avvio automatico di un'istanza di SQL Server  
  
1.  Fare clic sul menu **Start** , scegliere **Tutti i programmi**, [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], **Strumenti di configurazione**e quindi **Gestione configurazione SQL Server**.  
  
2.  In Gestione configurazione SQL Server espandere **Servizi**e quindi fare clic su **SQL Server**.  
  
3.  Nel riquadro dei dettagli fare clic con il pulsante destro del mouse su **MSSQLServer**quindi scegliere **Proprietà**.  
  
4.  Nel **SQL Server \< ***NomeIstanza***> proprietà** della finestra di dialogo il **proprietà** casella, impostare il valore di **modalità di avvio**al **manuale**.  
  
5.  Fare clic su **OK** per chiudere la finestra di dialogo**SQL Server \<***nomeistanza***> Proprietà** e chiudere Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Avviare, arrestare, sospendere, riprendere, riavviare il motore di database, SQL Server Agent o SQL Server Browser](start-stop-pause-resume-restart-sql-server-services.md)  
  
  