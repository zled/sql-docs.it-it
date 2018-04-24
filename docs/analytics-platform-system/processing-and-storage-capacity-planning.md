---
title: Capacità di elaborazione e archiviazione - Analitica Platform System | Documenti Microsoft
description: I requisiti aziendali determinano il numero di unità di scala di dati e le dimensioni dei dischi di nodo di calcolo che è necessario che nel dispositivo Analitica piattaforma di strumenti analitici.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: f552372ac108d219ad410b88ec9911ecaea63ab3
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="processing-and-storage-capacity-in-analytics-platform-system"></a>Capacità di elaborazione e archiviazione in Analitica Platform System
I requisiti aziendali determinano il numero di unità di scala di dati e le dimensioni dei dischi di nodo di calcolo che è necessario che nel dispositivo Analitica piattaforma di strumenti analitici. Utilizzare questi calcoli di elaborazione e archiviazione per la capacità di acquisto e decisioni relative alla pianificazione.  
  
  
## <a name="section1"></a>Pianificazione della capacità di elaborazione  
Le prestazioni delle query per SQL Server Parallel Data Warehouse (PDW) dipendono molto il numero di core CPU lavorando i dati in parallelo. Entro i limiti, aumentare il parallelismo migliora le prestazioni delle query di elaborazione parallela massiva (. MPP). Anche se la dimensione dei dati è relativamente piccola, la potenza del motore di query MPP è stata migliorata con parallelismo maggiore.  
  
Ad esempio, un accessorio con 12 nodi di calcolo 192 core di CPU che elaborano i dati in parallelo. Che è il parallelismo vie 192! Un dispositivo con nodi di calcolo 56 ha 896 core tutti eseguiti in parallelo. La grandezza di parallelismo non è raggiungibile senza MPP computing.  
  
Man mano che aumenta il numero di nodi di calcolo, la scalabilità del dispositivo richiede l'aggiunta di più di un nodo di calcolo in un momento per ottenere un vantaggio evidente. I fornitori di hardware supportano configurazioni specifiche solo dati di unità di scala per assicurarsi che il vantaggio della scalabilità del dispositivo supera il costo di ridistribuzione dei dati tra più nodi di calcolo.  
  
### <a name="data-scale-unit-configuration-examples---hpe"></a>Esempi di configurazione di unità di scala dati - HPE  
Questi sono esempi di configurazioni supportate HPE per Uunits scala dei dati. Possono variare dalle configurazioni supportate più recenti, ma vengono forniti come un esempio su come aumentare la capacità di circa il 20%.  
  
Il sollevamento è il miglioramento percentuale di capacità, aumentando la Uunits scala dei dati da una riga a quella successiva. Ad esempio, aumentare le unità di scala di dati da 6 a 8 offre un 33% sollevamento core CPU e memoria.  Aumenta anche lo spazio su disco che non è visualizzata in questa tabella.  
  
|Unità di scala di dati|Nodi di calcolo|Core CPU|Memoria (GB)|Incremento|  
|--------------------|-----------------|-------------|-----------------|----------|  
|1|2|32|512|-|  
|2|4|64|1024|100%|  
|3|6|96|1536|50%|  
|4|8|128|2048|33%|  
|5|10|160|2560|25%|  
|6|12|192|3072|20%|  
|8|16|256|4096|33%|  
|10|20|320|5120|25%|  
|12|24|384|6144|20%|  
|16|32|512|8192|33%|  
|20|40|640|10240|25%|  
|24|48|768|12288|20%|  
|28|56|896|14336|17%|  
  
Spiegazione:  
  
-   **Unità di scala dati** per ogni dispositivo. Per ulteriori informazioni sulle unità di scala di dati, vedere [componenti Hardware del sistema di piattaforma Analitica](hardware-components.md).  
  
-   **Nodi di calcolo** per ogni dispositivo.  
  
-   **Core CPU** per ogni dispositivo. Sono disponibili 16 core per ogni nodo di calcolo, uno dei core per ogni coppia di disco con mirroring. Per struttura disco nodo di calcolo, vedere [componenti Hardware del sistema di piattaforma Analitica](hardware-components.md).  
  
-   **Memoria** per ogni dispositivo. Ciascun core è 256 GB di memoria.  
  
### <a name="data-scale-unit-configuration-examples--dell-quanta"></a>Dati scala unità esempi di configurazione, Dell, quantum  
Questi sono esempi di configurazioni supportate Dell e quantum per Uunits scala dei dati. Possono variare dalle configurazioni supportate più recenti, ma vengono forniti come un esempio su come aumentare la capacità di circa il 20%.  
  
Il sollevamento è il miglioramento percentuale di capacità, aumentando la Uunits scala dei dati da una riga a quella successiva. Ad esempio, aumentare le unità di scala di dati da 6 a 8 offre un 33% sollevamento core CPU e memoria. Aumenta anche lo spazio su disco che non è visualizzata in questa tabella.  
  
|Unità di scala di dati|Nodi di calcolo|Core CPU|Memoria (GB)|Incremento|  
|--------------------|-----------------|-------------|-----------------|----------|  
|1|3|48|768|-|  
|2|6|96|1536|100%|  
|3|9|144|2,304|50%|  
|4|12|192|3,072|33%|  
|5|15|240|3,840|25%|  
|6|18|288|4,608|20%|  
|7|21|336|5,376|17%|  
|8|24|384|6,144|14%|  
|9|27|432|6,912|13%|  
|12|36|576|9,216|33%|  
|15|45|720|11,520|25%|  
|18|54|864|13,824|20%|  
  
## <a name="section2"></a>Pianificazione della capacità di archiviazione  
Questa tabella stima che è possibile caricare e archiviare fino a 6 petabyte di dati non compressi in un dispositivo di sistema della piattaforma Analitica completamente compilato. 
  
|Fornitore|Dimensioni dell'unità|Per ogni calcolo nodo di archiviazione fisica dei dati|Numero massimo di nodi di calcolo per rack|Archiviazione fisica massima dei dati per ogni rack|Archiviazione massima dei dati per ogni rack stimato|Massimo rack|Archiviazione dei dati per ogni dispositivo utente massimo stimato|  
|----------|--------------|------------------------------------------|----------------------------------|------------------------------------------|------------------------------------------------|-----------------|-----------------------------------------------------|  
|HPE|1 TB|16 TB|8|128 TB|320 TB|7|2,240 TB|  
|HPE|2 TB|32 TB|8|256 TB|640 TB|7|4,480 TB|  
|HPE|3 TB|48 TB|8|384 TB|960 TB|7|6,720 TB|  
|DELL|1 TB|16 TB|9|144 TB|360 TB|6|2160 TB|  
|DELL|2 TB|32 TB|9|288 TB|720 TB|6|4.320 TB|  
|DELL|3 TB|48 TB|9|432 TB|1080 TB|6|6,480 TB|  
  
Spiegazione:  
  
-   **Dimensioni dell'unità** è 1, 2 o 3 TB per ogni fornitore dell'Hardware.  
  
-   **Archivio dati fisico per ogni nodo di calcolo** = (dimensioni dell'unità) * (16 dischi per ogni nodo di calcolo). Non sono inclusi i dischi con mirroring poiché sono per la ridondanza.  
  
-   **Nodi di calcolo massima per ogni rack** è specifico per il fornitore dell'hardware.  
  
-   **Archiviazione fisica massima dei dati per ogni rack** = (archivio dati fisico per ogni nodo di calcolo) * (nodi di calcolo massima per rack).  
  
-   **Stimato massimo archiviazione dei dati per ogni rack** = (archiviazione fisica massima dei dati per ogni rack) * (5 per un rapporto di compressione 5:1) \* (50% per i log e tempDB). Si tratta di una stima per i dati utente non compresso che possono essere caricati e memorizzati nel dispositivo. Si tratta di una stima e non viene applicata dal software. L'archiviazione dei dati utente effettivo varia a seconda dei dati e la configurazione.  
  
-   **Rack massimo** è specifico per ogni fornitore dell'Hardware.  
  
-   **Stimato archiviazione massima dei dati per ogni dispositivo** = (archiviazione stimato massima dei dati per ogni rack) * (massimo sistemi rack). Si tratta di una stima della dimensione totale complessivo dei dati utente che è stato possibile caricare e archiviare in un dispositivo completamente compilato.  
  
