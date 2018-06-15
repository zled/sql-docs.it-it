---
title: Opzione della funzionalità (Analitica Platform System)
description: Visualizza informazioni sulle opzioni di due funzionalità che sono stati introdotti in Analitica piattaforma sistema AU7.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/24/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: e384a252584fed0e7543a7a4000fc9a70f6533e7
ms.sourcegitcommit: fc3cd23685c6b9b6972d6a7bab2cc2fc5ebab5f2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/25/2018
ms.locfileid: "34550902"
---
#<a name="appliance-feature-switch"></a>Opzione della funzionalità dello strumento
Il **opzione della funzionalità** pagina vengono visualizzate informazioni sulle opzioni di due funzionalità che sono stati introdotti in Analitica piattaforma sistema AU7. Utilizzare questa pagina per aggiornare o attivare/disattivare funzionalità e impostazioni di sistema della piattaforma Analitica. Modificare i valori delle funzionalità commutatore, è necessario un riavvio del servizio.

![Opzione della funzionalità dello strumento DWConig](media/feature-switch/SQL_Server_PDW_DWConfig_feature_switch.png "DWConig accessorio funzionalità commutatore") 

##<a name="autostatsenabled-switch"></a>Commutatore AutoStatsEnabled
Controlla la funzionalità di statistiche automatico. Questa opzione della funzionalità è impostata su true per impostazione predefinita dopo l'aggiornamento a AU7. Qualsiasi database creato dopo l'aggiornamento erediterà automaticamente creazione e l'aggiornamento asincrono delle statistiche. Per i database esistenti, gli amministratori di database possono abilitare automatica statistiche con [alter database] (/ sql/t-sql/statements/alter-database-parallel-data-warehouse). Per ulteriori informazioni sulle statistiche, vedere [statistiche](../relational-databases/statistics/statistics.md).

##<a name="dmsprocessstopmessagetimeoutinseconds-switch"></a>Commutatore DmsProcessStopMessageTimeoutInSeconds
Controlla il tempo di attesa di servizio lo spostamento dei dati (DMS) per eseguire la sincronizzazione in un sistema occupato quando una query che implica lo spostamento dei dati è stata annullata. L'aggiornamento a AU7 imposta questo valore 900 secondi (15 minuti) per impostazione predefinita. L'intervallo valido è 0 e 3600 secondi.
