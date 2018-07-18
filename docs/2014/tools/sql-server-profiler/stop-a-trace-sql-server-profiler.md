---
title: Arrestare una traccia (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], stopping
- stopping traces
ms.assetid: 47c4f33d-63e0-4444-bec8-4c1c91f8e25c
caps.latest.revision: 21
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9df984950c730b94527811f9f2ea3cca3ff220d9
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37230031"
---
# <a name="stop-a-trace-sql-server-profiler"></a>Arrestare una traccia (SQL Server Profiler)
  In questo argomento viene illustrato l'arresto di una traccia in esecuzione utilizzando [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
 L'arresto di una traccia comporta l'arresto dell'acquisizione dei dati. Dopo l'arresto, non è possibile riavviare una traccia senza perdere i dati acquisiti in precedenza, a meno che non siano stati acquisiti in un file o in una tabella. È inoltre possibile salvare i dati raccolti in una tabella o file dopo l'arresto di una traccia. Tutte le proprietà della traccia precedentemente impostate vengono mantenute. In caso di arresto di una traccia, sarà possibile modificarne il nome, gli eventi, le colonne e i filtri.  
  
### <a name="to-stop-a-trace"></a>Per arrestare una traccia  
  
1.  Selezionare una traccia in esecuzione.  
  
2.  Nel menu **File** fare clic su **Arresta traccia**.  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server Profiler](sql-server-profiler.md)  
  
  
