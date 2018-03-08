---
title: Abilitare o disabilitare la raccolta di dati di utilizzo e di arresto anomalo del reporting per Studio operazioni SQL (anteprima) | Documenti Microsoft
description: In questo articolo viene illustrato come controllare se vengono raccolti e inviate a Microsoft informazioni sull'utilizzo e dati di segnalazione arresto anomalo del sistema.
ms.custom: tools|sos
ms.date: 11/15/2017
ms.prod: sql-non-specified
ms.reviewer: alayu; erickang; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: 
ms.topic: article
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ae620951028ba8e0e82f89c4251238c92bc614ca
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="enable-or-disable-usage-data-collection-for-includename-sosincludesname-sos-shortmd"></a>Abilitare o disabilitare la raccolta di dati di utilizzo per[!INCLUDE[name-sos](../includes/name-sos-short.md)]

## <a name="how-to-disable-telemetry-reporting"></a>Come disabilitare la segnalazione di telemetria

[!INCLUDE[name-sos](../includes/name-sos-short.md)]raccoglie dati sull'utilizzo e lo invia a Microsoft per contribuire a migliorare i prodotti e servizi. Per altre informazioni, leggere la [informativa sulla privacy](https://go.microsoft.com/fwlink/?LinkID=528096&clcid=0x409).

Se non si desidera inviare i dati di utilizzo a Microsoft, è possibile impostare il *telemetry.enableTelemetry* impostando su *false*.

Per tutti gli eventi di telemetria da disattiva [!INCLUDE[name-sos](../includes/name-sos-short.md)], da **File** > **preferenze** > **impostazioni**, aggiungere la seguente opzione:

```json
    "telemetry.enableTelemetry": false
```

**Avviso importante**: questa opzione richiede il riavvio del [!INCLUDE[name-sos](../includes/name-sos-short.md)] diventino effettive. 

## <a name="how-to-disable-crash-reporting"></a>Come disabilitare la segnalazione di arresto anomalo del sistema

Per disabilitare la segnalazione di arresto anomalo del sistema, da **File** > **preferenze** > **impostazioni**, aggiungere la seguente opzione:

```json
    "telemetry.enableCrashReporter": false
```

**Avviso importante**: questa opzione richiede il riavvio del [!INCLUDE[name-sos](../includes/name-sos-short.md)] diventino effettive.

## <a name="additional-resources"></a>Risorse aggiuntive
- [Area di lavoro e le impostazioni utente](settings.md)