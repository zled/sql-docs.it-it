---
title: "Foglio di pianificazione della capacità di Server di backup (SQL Server PDW)"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: 
ms.suite: sql
ms.custom: 
ms.technology: mpp-data-warehouse
description: "Questo foglio di lavoro Pianificazione della capacità consente di determinare i requisiti per un server di backup per l'esecuzione di backup del database di SQL Server PDW e operazioni di ripristino."
ms.date: 01/05/2017
ms.topic: article
ms.assetid: 36294bf6-6dde-481f-a190-d4382b04c030
caps.latest.revision: "6"
ms.openlocfilehash: e025410f3be18b5f8276984219dd1cb6a40c2a87
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="backup-server-capacity-planning-worksheet"></a>Foglio di lavoro di pianificazione della capacità server backup
Questo foglio di lavoro Pianificazione della capacità consente di determinare i requisiti per un server di backup per l'esecuzione di backup del database di SQL Server PDW e operazioni di ripristino. Consente di creare il piano per i server di backup di acquisto nuovo o provisioning esistente.  
  
Questo foglio di lavoro è un supplemento per le istruzioni in [acquisire e configurare un Server di Backup](acquire-and-configure-backup-server.md).  
  
## <a name="capacity-planning-worksheet-for-backup-servers"></a>Foglio di lavoro di pianificazione della capacità per i server di Backup  

### <a name="notes"></a>Note  
  
1.  Questo foglio di lavoro si applica ai server che esegue operazioni di backup e ripristino per i database PDW.  
  
2.  L'unico modo per eseguire il backup e ripristino di database PDW consiste nell'utilizzare i comandi di DATABASE di BACKUP e ripristino di DATABASE SQL. Tuttavia, dopo i dati di backup sono il server di backup, esiste come set di file di Windows. È possibile archiviare i file di backup dal server in un'altra posizione di archiviazione tramite tradizionale Windows basate su file metodi di backup.  
  
### <a name="clipboard-iconmediaclipboard-iconpng-clipboard-icon-capacity-planning-worksheet"></a>![Icona degli Appunti](media/clipboard-icon.png "icona degli Appunti") foglio di lavoro di pianificazione della capacità 
  
Questo foglio di lavoro di stampa e popolarlo con i propri requisiti.  
  
|Componente|Requisito|Compilare questa colonna con i propri requisiti|Indicazioni|  
|-------------|---------------|--------------------------------------------------|-------------------|  
|Archiviazione|Numero massimo di byte che si prevede di archiviare nel server di backup in qualsiasi periodo di tempo specificato.|![Icona della matita](media/pencil-icon.png "icona della matita")|Per determinare i requisiti di archiviazione, determinare la quantità di dati si intende archiviare nel server di backup in qualsiasi periodo di tempo specificato.<br /><br />I dati di backup vengono archiviati nel server di backup in un formato compresso. Tasso di compressione dati dipendono dalle caratteristiche dei dati.<br /><br />Ad esempio: come una stima approssimativa, si consiglia di stima di un rapporto di compressione 7:1 relativo alle dimensioni dei dati non compressi. Si presuppone che almeno l'80% dei dati vengono archiviati negli indici columnstore cluster. Ad esempio, se si dispone di 700 GB di dati non compressi in un database e viene archiviato negli indici columnstore cluster, quindi è possibile stimare che il backup del database sarà necessari circa 100 GB.<br /><br />Se si prevede di disporre di più copie di backup del database nel server di backup, è necessario tenere conto delle loro.<br /><br />Ad esempio: se si prevede di eseguire il backup di 10 database contenenti ciascuna 5 TB di dati non compressi, i database hanno una dimensione combinata di 50 TB. Se si prevede di eseguire il backup di questi ogni giorno 10 database per 5 giorni in una riga, la dimensione non compressa totale è 250 TB. Eseguire il factoring in un rapporto di compressione 7:1, sarà necessario 250 / 7 = 35.7 TB di spazio di archiviazione sul server di backup. È consigliabile being conservativo e recupero sul 30% di capacità aggiuntiva per tenere conto delle varianze e aumento delle dimensioni.  In questo esempio, sarebbe migliore 46,6 TB.|  
|Rete|Tipo di connessione di rete.|![Icona della matita](media/pencil-icon.png "icona della matita")|Determinare il tipo di connessione di rete migliori in grado di soddisfare i requisiti di velocità di carico.<br /><br />Ad esempio: InfiniBand o velocità di caricamento da 10 Gbit Ethernet fornirà ottimale. Ethernet da 1 Gbit limiterà i tassi di carico a 360 GB all'ora o meno.|  
|I/O|Byte per ogni ora per operazioni di scrittura.|![Icona della matita](media/pencil-icon.png "icona della matita")|Per scrivere i backup su disco, 4 TB all'ora di velocità di scrittura sono ottimali.<br /><br />Ad esempio: per le unità che possono essere scritte 50 MB/sec, sarà necessario almeno 24 unità e altro per il mirroring o parità.<br /><br />Capacità dei / o, prendere in considerazione tutti il / o nel server durante il caricamento in corso. Se il server durante il caricamento ha altro traffico dei / o oltre ai carichi di dati, ad esempio la ricezione di file di dati da un server ETL, aumenta i requisiti dei / o.|  
|CPU|Numero di socket.|![Icona della matita](media/pencil-icon.png "icona della matita")|Ricezione e l'archiviazione di file di backup non è un'applicazione con utilizzo intensivo della CPU.  Come requisito minimo, è consigliabile utilizzare un server socket 2 prodotta di recente.|  
|RAM|GB di memoria che consente a Windows per i file di cache durante carica.|![Icona della matita](media/pencil-icon.png "icona della matita")|Ricezione e l'archiviazione di file di backup richiede molto spazio RAM nel server durante il caricamento.<br /><br />Per determinare i requisiti di RAM, vedere Installazione di Windows Server e qualsiasi 3 requisiti dell'applicazione di terze parti. Se non si prevedono requisiti da altre origini, è consigliabile un minimo di 32 GB.|  
  
Dopo aver terminato di definizione dei requisiti di capacità, ripristinare il [acquisire e configurare un Server durante il caricamento](acquire-and-configure-loading-server.md) argomento per pianificare l'acquisto.  
  
## <a name="see-also"></a>Vedere anche  
[Backup e il caricamento di componenti hardware](backup-and-loading-hardware.md)  
  
