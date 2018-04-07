---
title: Supporto UTF-16 in OLE DB Driver per SQL Server | Documenti Microsoft
description: Supporto UTF-16 in OLE DB Driver per SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: oledb|features
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a0f710e6f567f789771a80677beb24d24b1c8f5d
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2018
---
# <a name="utf-16-support-in-ole-db-driver-for-sql-server"></a>Supporto UTF-16 in OLE DB Driver per SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  A partire da [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], se si fornisce un buffer a lunghezza fissa quando si associa un parametro di risultato o di output di colonna e il **wchar** carattere scritto nel buffer prima che il carattere di terminazione è un punto di codice surrogato alto di una coppia di surrogati e se alla successiva **wchar** carattere è un punto di codice surrogato basso, il Driver OLE DB per SQL Server non aggiungerà il punto di codice surrogato alto nel buffer.  
  
## <a name="see-also"></a>Vedere anche  
 [Driver OLE DB per funzionalità di SQL Server](../../oledb/features/oledb-driver-for-sql-server-features.md)   
  
  
