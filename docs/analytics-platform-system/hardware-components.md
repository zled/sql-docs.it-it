---
title: Componenti hardware di sistema della piattaforma Analitica
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: sql-non-specified
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: analytics-platform-system
ms.suite: sql
ms.custom: 
ms.technology: mpp-data-warehouse
description: "Analitica piattaforma di strumenti analitici Usa componenti scalabili in modo che è possibile acquistare la giusta quantità di elaborazione e archiviazione in base alle esigenze aziendali."
ms.date: 10/20/2016
ms.topic: article
ms.assetid: aa1cdcc7-cfee-4658-bbce-7d319bfb7483
caps.latest.revision: "17"
ms.openlocfilehash: 1c42436dd5a5e98dd1343e95d116bc0056ed1e2b
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="analytics-platform-system-hardware-components"></a>Componenti hardware di sistema della piattaforma Analitica

Analitica piattaforma di strumenti analitici Usa componenti scalabili in modo che è possibile acquistare la giusta quantità di elaborazione e archiviazione in base alle esigenze aziendali. Quando si ordinano i punti di accesso, occorre una combinazione di questi componenti hardware di base. I fornitori di hardware specifici potrebbero utilizzare diverse convenzioni di denominazione o i componenti aggiuntivi.  
 
  
## <a name="rackandnetwork"></a>Rack e rete 
 
Tutti i componenti di punti di accesso vengono memorizzati in uno o più rack che rientrano nel proprio data center. Ogni rack dotato di unità di distribuzione dell'alimentazione (PDU), due commutatori InfiniBand e due commutatori Ethernet.  
  
![Rack e rete](media/rack-and-network.png "APS montare su rack e di rete")  
  
## <a name="datascaleunit"></a>Unità di scala di dati
 
Un'unità di scala di dati contiene gli host di dati e l'archiviazione associata diretta (DAS) per l'elaborazione e archiviazione dei dati utente. Per aggiungere capacità di aggiungere unità di scala di dati in base alle configurazioni supportate dal fornitore dell'hardware. Man mano che aumenta il numero di unità di scala di dati, è necessario aggiungere ulteriori Rack e i componenti di rete, se necessario, per fornire informazioni di alimentazione, rete e rack infrastruttura.  
  
### <a name="data-host"></a>Host di dati  

Un host di dati è un server dedicato all'elaborazione dei dati utente. Parallel Data Warehouse (PDW), un nodo di calcolo viene eseguito in ogni host di dati. Per gli accessori HPE, l'unità di scala di dati ha due host di dati. Per accessori Dell e quantum, l'unità di scala di dati include tre host di dati.  
  
### <a name="direct-attached-storage"></a>Archiviazione associata diretta
 
L'archiviazione associata diretta (DAS) è un pool di dischi connessi agli host di dati. Tutti gli host di dati possibile accedere a tutti i dischi. Come parte di senza condivisione architettura, i nodi di calcolo in esecuzione negli host dati non condividono singoli dischi. Tuttavia, per la disponibilità elevata, l'accesso all'archiviazione è condivisa e tutti gli host di dati possibile accedere a tutti i dischi.  
  
### <a name="data-scale-unit-architecture---dell-and-quanta"></a>Scala unità architettura di dati - quantum e DELL
  
![Unità di scalabilità](media/scalability-unit-dell.png "unità scalabilità Dell")  
  
### <a name="data-scale-unit-architecture---hpe"></a>Architettura di unità di scala dei dati - HPE 
 
![Unità di scalabilità HPE](media/scalability-unit-hpe.png "unità HPE scalabilità")  
  
### <a name="data-scale-unit-description"></a>Descrizione unità di scala dei dati

Un'unità di scala di dati dispone di un server (host) per ogni nodo di calcolo e di una matrice di un disco collegato direttamente collegata con SAS Serial Attached SCSI (). All'interno dell'archivio di archiviazione, l'array di dischi è suddivisa in due metà che dispongono di alimentatori ridondanti. Spazi di archiviazione di Windows Server gestisce i dati utente, la duplicazione dei dati tra coppie di disco con mirroring RAID 1. I dischi in ogni coppia di disco vengono archiviati in due parti diverse dell'array di dischi.  
  
L'array di dischi contiene anche i dischi di riserva a caldo e un disco di sistema. Se un disco non riesce, spazi di archiviazione utilizza la copia dei dati sul disco funzionano per ricompilare una copia duplicata dei dati in una riserva a caldo. Si tratta di un'importante funzionalità di riparazione automatica che consente di prevenire la perdita di dati.  
  
Numero totale dei dischi per i nodi di calcolo:  
  
-   DELL ha 96 dischi = (3 server) * (16 dischi per ogni server) \* (2 per i dischi ridondanti).  
  
-   HPE è 64 dischi = (2 Server) * (16 dischi per ogni server) \* (2 per i dischi ridondanti).  
  
-   Inoltre, ogni array di dischi dispone di dischi di riserva a caldo e di un disco di sistema.  
  
**Per la disponibilità elevata**, quando un calcolo eseguito il failover è possibile continuano a funzionare e di accedere ai dati utente tramite l'altro host nell'unità di scala di dati. Almeno uno degli host fisici collegati direttamente deve funzionare o accesso ai dati nella risorsa di archiviazione viene perso.  
  
**Per i dischi**, l'archiviazione associata diretta può avere 1, 2 o 3 unità disco di Terabyte. Tutte le unità di scala di dati devono essere dischi delle stesse dimensioni.  
  
## <a name="basescaleunit"></a>Unità di scala di base 
 
L'unità di scala di Base contiene il numero minimo di cervello power host, host di dati e l'archiviazione associata diretta che è necessario per l'applicazione. Include questi componenti.  
  
### <a name="orchestration-host"></a>host di orchestrazione  
Il server esegue il meccanismo alla base di PDW.
  
### <a name="passive-host"></a>host passivo  
Questo server garantisce un'elevata disponibilità. È in linea e pronto per eseguire i processi nel caso in cui si verifica un errore in cui l'orchestrazione o di un host di dati. L'host di orchestrazione, passivo host e i server di unità di scala di dati sono configurati come cluster di failover di Windows. Ogni rack il dispositivo richiede un host passivo.  
  
### <a name="optional-passive-host"></a>host passivo facoltativo  
Per aggiungere un'ulteriore ridondanza, è possibile aggiungere un secondo host passivo per l'unità di scala di Base.  
  
### <a name="data-scale-unit"></a>Unità di scala di dati  
L'unità di scala di Base include un'unità di scala di dati che si trova nella parte inferiore del rack.  
  
Questo diagramma mostra l'unità di scala di Base oltre il Rack e la rete. Questa è la configurazione minima per un dispositivo di sistema della piattaforma Analitica.  
  
![Unità di scala base](media/base-scale-unit.png "unità di scala di Base")  
 
