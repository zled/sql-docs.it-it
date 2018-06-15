---
title: Ridistribuzione di ADOMD.NET | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: adomd
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: aef9cf75270e8fccf9572669ad0487fce96c0c61
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34027298"
---
# <a name="redistributing-adomdnet"></a>Ridistribuzione di ADOMD.NET
  Quando si scrivono applicazioni che utilizzano ADOMD.NET, è necessario ridistribuire la versione appropriata di ADOMD.NET insieme all'applicazione. Per ridistribuire ADOMD.NET, includere il programma di installazione di ADOMD.NET nel programma di installazione dell'applicazione.  
  
 Il programma di installazione di ADOMD.NET, nonché la versione più recente di ADOMD.NET, sono disponibili nell'Area download Microsoft come parte di SQL Server Feature Pack.  
  
 Il programma di installazione ADOMD.NET installa i file ADOMD.NET in \< *unità di sistema*>: \Program Files\Microsoft.NET\ADOMD.NET\\*numero di versione*.  
  
 Dopo avere incluso il programma di installazione di ADOMD.NET, avviarlo dal programma di installazione dell'applicazione e installare ADOMD.NET. A seconda dell'ambiente, potrebbe inoltre essere necessario verificare che gli assembly correlati siano considerati attendibili da SQL Server.  
  
 Per ulteriori informazioni:  
  
 [Feature Pack per Microsoft SQL Server](http://go.microsoft.com/fwlink/?LinkId=389949)  
  
 [Microsoft Connect: Dipendenze di ADOMD.NET](http://go.microsoft.com/fwlink/?LinkId=389950)  
  
## <a name="see-also"></a>Vedere anche  
 [Programmazione di Client ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/adomd-net-client-programming.md)   
 [Programmazione di server ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-server/adomd-net-server-programming.md)  
  
  
