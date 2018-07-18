---
title: Architettura del Driver ODBC | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- ODBC drivers [ODBC], architecture
ms.assetid: 21a62c7c-192e-4718-a16e-aa12b0de4419
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9566599b68ac931604ab68c06da2f6cd624673fe
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32917326"
---
# <a name="odbc-driver-architecture"></a>Architettura del Driver ODBC
Gli sviluppatori di driver è necessario che l'architettura del driver può influire se un'applicazione può utilizzare SQL DBMS specifici.  
  
 ![Architettura del driver ODBC](../../../odbc/reference/develop-driver/media/odbcdriverovruarch.gif "ODBCDriverOvruArch")  
  
 [Driver basati su file](../../../odbc/reference/file-based-drivers.md)  
  
 Quando il driver accede direttamente i dati fisici, il driver funziona come driver e i dati di origine. Il driver deve elaborare chiamate ODBC sia istruzioni SQL. Gli sviluppatori di driver basati su file è necessario scrivere i propri motori di database.  
  
 [Driver basati su DBMS](../../../odbc/reference/dbms-based-drivers.md)  
  
 Quando un motore di database separato viene utilizzato per accedere ai dati fisici, il driver elabora solo le chiamate ODBC. Passa istruzioni SQL per motore di database per l'elaborazione.  
  
 [Architettura di rete](../../../odbc/reference/network-example.md)  
  
 Configurazioni di file, DBMS ODBC può essere presente una singola rete.  
  
 [Altre architetture di driver](../../../odbc/reference/other-driver-architectures.md)  
  
 Quando è necessario un driver per funzionare con un'ampia gamma di origini dati, può essere utilizzato come middleware. Architettura del motore di join eterogeneo può rendere il driver vengono visualizzati come una Gestione driver. I driver possono anche essere installati nei server, in cui può essere condiviso da una serie di client.  
  
 Per ulteriori informazioni sull'architettura di driver, vedere [gestione Driver](../../../odbc/reference/the-driver-manager.md) e [architettura Driver](../../../odbc/reference/driver-architecture.md) nella sezione [architettura ODBC](../../../odbc/reference/odbc-architecture.md).  
  
 Ulteriori informazioni sui problemi di driver sono reperibile in percorsi descritti nella tabella seguente.  
  
|Problema|Argomento|Percorso|  
|-----------|-----------|--------------|  
|Problemi di compatibilità con applicazioni e driver|[Compatibilità dell'applicazione/Driver](../../../odbc/reference/develop-app/application-and-driver-compatibility.md)|[Considerazioni sulla programmazione](../../../odbc/reference/develop-app/programming-considerations.md), in riferimento per programmatori ODBC|  
|Driver ODBC di scrittura|[Scrittura di driver ODBC 3.x](../../../odbc/reference/develop-app/writing-odbc-3-x-drivers.md)|[Considerazioni sulla programmazione](../../../odbc/reference/develop-app/programming-considerations.md), in riferimento per programmatori ODBC|  
|Linee guida di driver per la compatibilità con le versioni precedenti|[Linee guida di driver per la compatibilità con le versioni precedenti](../../../odbc/reference/appendixes/appendix-g-driver-guidelines-for-backward-compatibility.md)|[Appendice g: Driver le linee guida per la compatibilità con le versioni precedenti](../../../odbc/reference/appendixes/appendix-g-driver-guidelines-for-backward-compatibility.md), in riferimento per programmatori ODBC|  
|Connessione a un driver|[Scelta di un'origine dati o driver](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md)|[La connessione a una Data origine o il Driver](../../../odbc/reference/develop-app/connecting-to-a-data-source-or-driver.md), in riferimento per programmatori ODBC|  
|Identificazione dei driver|[Visualizzazione dei driver](../../../odbc/admin/viewing-drivers.md)|[Visualizzazione dei driver](../../../odbc/admin/viewing-drivers.md), nella Guida in linea Amministrazione origine dati ODBC di Microsoft|  
|Abilitazione del pool di connessioni|[Pool di connessioni ODBC](../../../odbc/reference/develop-app/driver-manager-connection-pooling.md)|[La connessione a una Data origine o il Driver](../../../odbc/reference/develop-app/connecting-to-a-data-source-or-driver.md), in riferimento per programmatori ODBC|  
|Problemi di driver e connessione Unicode o ANSI.|[Driver di Unicode](../../../odbc/reference/develop-app/unicode-drivers.md)|[Considerazioni sulla programmazione](../../../odbc/reference/develop-app/programming-considerations.md), in riferimento per programmatori ODBC|  
  
## <a name="see-also"></a>Vedere anche  
 [Sviluppo di un driver ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)
