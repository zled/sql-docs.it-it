---
title: Ridistribuzione di ADOMD.NET | Documenti Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- ADOMD.NET, redistributing
- redistributing ADOMD.NET
ms.assetid: f8db3c99-0243-4b92-b486-0d8786c264f4
caps.latest.revision: "35"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 6587a23e479522453feb01bf7190cebc9fb505df
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="redistributing-adomdnet"></a>Ridistribuzione di ADOMD.NET
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Quando si scrivono applicazioni che utilizzano ADOMD.NET, è necessario ridistribuire la versione appropriata di ADOMD.NET insieme all'applicazione. Per ridistribuire ADOMD.NET, includere il programma di installazione di ADOMD.NET nel programma di installazione dell'applicazione.  
  
 Il programma di installazione di ADOMD.NET, nonché la versione più recente di ADOMD.NET, sono disponibili nell'Area download Microsoft come parte di SQL Server Feature Pack.  
  
 Il programma di installazione ADOMD.NET installa i file ADOMD.NET in \< *unità di sistema*>: \Program Files\Microsoft.NET\ADOMD.NET\\*numero di versione*.  
  
 Dopo avere incluso il programma di installazione di ADOMD.NET, avviarlo dal programma di installazione dell'applicazione e installare ADOMD.NET. A seconda dell'ambiente, potrebbe inoltre essere necessario verificare che gli assembly correlati siano considerati attendibili da SQL Server.  
  
 Per ulteriori informazioni:  
  
 [Feature Pack per Microsoft SQL Server](http://go.microsoft.com/fwlink/?LinkId=389949)  
  
 [Microsoft Connect: Dipendenze di ADOMD.NET](http://go.microsoft.com/fwlink/?LinkId=389950)  
  
## <a name="see-also"></a>Vedere anche  
 [Programmazione di Client ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/adomd-net-client-programming.md)   
 [Programmazione di server ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-server/adomd-net-server-programming.md)  
  
  
