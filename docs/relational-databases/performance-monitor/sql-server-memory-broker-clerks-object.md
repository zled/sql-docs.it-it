---
title: Oggetto Memory Broker Clerks di SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:Memory Broker Clerks
ms.assetid: 47b9c236-66a3-4c42-97ee-da5555bdc046
author: dagiro
ms.author: v-dagir
manager: craigg
ms.openlocfilehash: 546d5052c2b97b40b4f7e979c0447c947fdf487a
ms.sourcegitcommit: 110e5e09ab3f301c530c3f6363013239febf0ce5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/10/2018
ms.locfileid: "48906031"
---
# <a name="sql-server-memory-broker-clerks-object"></a>SQL Server, oggetto Memory Broker Clerks
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
L'oggetto prestazione **SQLServer:Memory Broker Clerks** fornisce contatori per statistiche correlate ai clerk broker di memoria.

La tabella seguente descrive gli oggetti prestazioni **Memory Broker Clerks** di SQL Server.

|**Contatori dell'oggetto Memory Broker Clerks di SQL Server**|Descrizione|  
|-------------|-----------------|  
|**Vantaggio interno**|Valore interno di memoria per il numero di richieste di pagine, in ms per pagina per ms, moltiplicato per 10 miliardi e troncato a un intero.|
|**Dimensioni clerk broker di memoria**|Dimensioni in pagine del clerk.|
|**Eliminazioni periodiche (pagine)**|Numero di pagine eliminate dal clerk broker durante l'ultima eliminazione periodica.|
|**Eliminazioni richieste di pagine (pagine/sec)**|Numero di pagine al secondo eliminate dal clerk broker dal numero di richieste di memoria.|
|**Vantaggio simulazione**|Valore di memoria per il clerk, in ms per pagina per ms, moltiplicato per 10 miliardi e troncato a un intero.|
|**Dimensioni simulazione**|Dimensioni correnti in pagine della simulazione del clerk.|

C'è un'istanza del contatore per il pool di buffer e il pool di oggetti dell'archivio colonne.

## <a name="see-also"></a>Vedere anche  
[Monitoraggio dell'utilizzo delle risorse (Monitor di sistema)](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)
