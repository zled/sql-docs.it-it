---
title: Opzione della funzionalità (sistema di piattaforma Analitica)
description: Visualizza le informazioni sulle opzioni di due funzionalità che sono stati introdotti in AU7 sistema di piattaforma Analitica.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 06/27/2018
ms.author: murshedz
ms.reviewer: martinle
monikerRange: '>= aps-pdw-2016-au7 || = sqlallproducts-allversions'
ms.openlocfilehash: b06c715549cd1c9cf464a13b03790764ebf40b97
ms.sourcegitcommit: 3e5f1545e5c6c92fa32e116ee3bff1018ca946a2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/29/2018
ms.locfileid: "37107179"
---
#<a name="appliance-feature-switch"></a>Opzione della funzionalità di Appliance
Il **opzione della funzionalità** pagina vengono visualizzate informazioni sulle opzioni di due funzionalità che sono stati introdotti nella piattaforma Analitica System 2016-AU7. Utilizzare questa pagina per aggiornare o attivare/disabilitare funzionalità e impostazioni di sistema di piattaforma Analitica. La modifica di valori della funzionalità commutatore richiede un riavvio del servizio.

![Opzione della funzionalità Appliance DWConig](media/feature-switch/SQL_Server_PDW_DWConfig_feature_switch.png "DWConig Appliance funzionalità commutatore") 

##<a name="autostatsenabled-switch"></a>Commutatore AutoStatsEnabled
Controlla la funzionalità statistiche automatico. Questa opzione della funzionalità è impostata su true per impostazione predefinita dopo l'aggiornamento a AU7. Qualsiasi database creato dopo l'aggiornamento erediterà la creazione automatica e l'aggiornamento asincrono delle statistiche. Per i database esistenti, gli amministratori di database possono abilitare statistiche automatico con [alter database] (/ sql/t-sql/statements/alter-database-parallel-data-warehouse). Per altre informazioni sulle statistiche, vedere [statistiche](../relational-databases/statistics/statistics.md).

##<a name="dmsprocessstopmessagetimeoutinseconds-switch"></a>Commutatore DmsProcessStopMessageTimeoutInSeconds
Controlla il tempo Data Movement Service (DMS) è in attesa per la sincronizzazione in un sistema occupato quando una query che implica lo spostamento dei dati è stata annullata. L'aggiornamento a AU7 imposta questo valore per 900 secondi (15 minuti) per impostazione predefinita. L'intervallo valido è 0 e 3600 secondi.
