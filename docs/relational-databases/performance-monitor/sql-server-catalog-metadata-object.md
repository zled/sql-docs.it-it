---
title: Oggetto Catalog Metadata di SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:Catalog Metadata
ms.assetid: 665e63e6-4bd2-4091-92a5-327364db2f8d
author: dagiro
ms.author: v-dagir
manager: craigg
ms.openlocfilehash: 1f92f446ebd8d3f8efdd2c3ff8e62ec46c55b60a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47826039"
---
# <a name="sql-server-catalog-metadata-object"></a>SQL Server, oggetto Catalog Metadata
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
L'oggetto prestazione **SQLServer:Catalog Metadata** fornisce contatori per i metadati del catalogo per SQL Server.

La tabella seguente descrive gli oggetti prestazioni **Catalog Metadata** di SQL Server.


|**Contatori dell'oggetto Catalog Metadata di SQL Server**|Descrizione|  
|-------------|-----------------|  
|**Conteggio voci cache**|Numero di voci nella cache dei metadati del catalogo.|
|**Conteggio voci cache bloccate**|Numero di voci bloccate nella cache dei metadati del catalogo.|
|**Percentuale riscontri cache**|Rapporto tra riscontri e ricerche nella cache dei metadati del catalogo.|
|**Base percentuale riscontri cache**|Solo per uso interno.|

C'è un'istanza del contatore per ogni database.

## <a name="see-also"></a>Vedere anche  
[Monitoraggio dell'utilizzo delle risorse (Monitor di sistema)](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)
