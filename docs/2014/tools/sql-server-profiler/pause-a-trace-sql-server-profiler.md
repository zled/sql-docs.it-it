---
title: Sospendere una traccia (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- pausing traces
- temporarily stopping traces
- traces [SQL Server], pausing
- stopping traces
ms.assetid: 432b9b0c-b5e7-47f3-a71b-310fb3bf2445
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d213e6b680bfe0d020a7c95b4e3924ef5679d7e2
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48077101"
---
# <a name="pause-a-trace-sql-server-profiler"></a>Sospendere una traccia (SQL Server Profiler)
  La sospensione di una traccia consente di impedire l'ulteriore acquisizione dei dati evento fino al riavvio della traccia.  
  
 Quando si sospende una traccia, è possibile impedire l'acquisizione dei dati evento fino al riavvio della traccia. Il riavvio di una traccia consente di riprendere le operazioni di acquisizione. Dopo il riavvio, gli eventuali dati acquisiti in precedenza non andranno perduti. Quando si riavvia la traccia, l'acquisizione dei dati riprende dal momento del riavvio. Durante la sospensione di una traccia è possibile modificarne il nome, gli eventi, le colonne e i filtri. Non è invece possibile modificare le destinazioni di invio dei dati della traccia o la connessione al server.  
  
### <a name="to-pause-a-trace"></a>Per sospendere una traccia  
  
1.  Selezionare una finestra contenente una traccia in esecuzione.  
  
2.  Nel menu **File** fare clic su **Sospendi traccia**.  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server Profiler](sql-server-profiler.md)  
  
  
