---
title: Configurazioni hardware (Analitica piattaforma sistema)
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
description: "L'hardware Analitica piattaforma di strumenti analitici viene progettato con unità scalabili in modo che si acquista la giusta quantità di elaborazione e archiviazione in base alle esigenze aziendali."
ms.date: 01/05/2017
ms.topic: article
ms.assetid: f95945b7-97ae-4ab9-bae5-c792a516acea
caps.latest.revision: "9"
ms.openlocfilehash: 6762775fdec3cd3a01a372ed5c16fbc4a93c1426
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="hardware-configurations"></a>Configurazioni hardware
L'hardware Analitica piattaforma di strumenti analitici viene progettato con unità scalabili in modo che si acquista la giusta quantità di elaborazione e archiviazione in base alle esigenze aziendali. Il dispositivo di scala di archiviazione per SQL Server Parallel Data Wareouse (PDW) da qualche terabyte per oltre 6 petabyte di dati.  
  
## <a name="contents"></a>Sommario  
  
-   [Configurazioni di un Rack](#section1)  
  
-   [Configurazioni più Rack](#section2)  

  
## <a name="section1"></a>Configurazioni di un Rack  
Il primo rack del dispositivo contiene i componenti richiesti per l'esecuzione di PDW. La configurazione del dispositivo minima è un Rack e di rete più di un'unità di scala di Base. Questi diagrammi mostrano i modi che possono essere configurate prima rack del dispositivo. È possibile avere tra 2 e 9 nodi di calcolo nel primo rack, a seconda dell'hardware.  
  
### <a name="first-rack-configurations---dell"></a>Prima di tutto Rack configurazioni - DELL  
La configurazione minima per un dispositivo DELL con 3 nodi di calcolo. È possibile aggiungere fino a 2 unità di scala di dati per il primo rack per un totale di nodi di calcolo 9.  
  
![Configurazioni del primo rack Dell](media/first-rack-configurations-dell.png "configurazioni del primo rack Dell")  
  
### <a name="first-rack-configurations---hpe"></a>Prima di tutto Rack configurazioni - HPE  
La configurazione minima per un dispositivo HPE con 2 nodi di calcolo. È possibile aggiungere fino a 3 unità di scala di dati per il primo rack per un totale di 8 nodi di calcolo.  
  
![HPE rack innanzitutto le configurazioni per HPE](media/first-rack-configurations-hpe.png "HPE rack innanzitutto le configurazioni")  
  
## <a name="section2"></a>Configurazioni più rack  
Per aggiungere capacità a PDW aggiungere unità di scala di dati, insieme ai componenti aggiuntivi di Rack & rete necessarie per raggiungere la potenza corretta, rete e infrastruttura rack. Ogni aggiuntive Rack & rete richiede un host passivo.  
  
Ogni fornitore di hardware specifica il numero di unità di scala di dati che è possibile aggiungere la capacità del dispositivo specificato. È consigliabile aggiungere sufficiente unità di scala di dati per visualizzare almeno un sollevamento del 20% delle prestazioni. Ad esempio, l'aggiunta di una scala dei dati unità da un dispositivo che dispone già di 20 unità di scala di dati potrebbe essere un miglioramento delle prestazioni trascurabile. Il guadagno netto sarebbe opportuno il costo e la fatica.  
  
### <a name="scale-out-example---hpe"></a>Scalabilità orizzontale esempio - HPE  
Questo diagramma mostra un accessorio 3 rack HP che contiene 20 nodi di calcolo.  
  
![Dispositivo HPE con 20 nodi di calcolo](media/scale-out-hpe.png "accessorio HPE con 20 nodi di calcolo")  
  
### <a name="scale-out-example--dell-quanta"></a>Esempio: DELL, quantum con scalabilità  
Questo diagramma mostra 3 rack DELL o Quanta appliance che contiene i nodi di calcolo 21.  
  
![Il dispositivo Dell con nodi di calcolo 21](media/scale-out-dell.png "dispositivo Dell con 21 nodi di calcolo")  
 
