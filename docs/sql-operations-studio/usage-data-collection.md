---
title: Abilitare o disabilitare la raccolta di dati di utilizzo e di arresto anomalo del reporting per SQL Operations Studio (anteprima) | Microsoft Docs
description: In questo articolo viene illustrato come controllare se vengono raccolti e inviati a Microsoft informazioni sull'utilizzo e dati di segnalazione arresto anomalo del sistema.
ms.custom: tools|sos
ms.date: 11/15/2017
ms.prod: sql-non-specified
ms.reviewer: alayu; erickang; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: ''
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
# <a name="enable-or-disable-usage-data-collection-for-includename-sosincludesname-sos-shortmd"></a>Abilitare o disabilitare la raccolta di dati di utilizzo per [!INCLUDE[name-sos](../includes/name-sos-short.md)]

## <a name="how-to-disable-telemetry-reporting"></a>Come disabilitare la segnalazione di telemetria

[!INCLUDE[name-sos](../includes/name-sos-short.md)] raccoglie dati sull'utilizzo e li invia a Microsoft per contribuire a migliorare i prodotti e i servizi. Per altre informazioni, leggere l'[informativa sulla privacy](https://go.microsoft.com/fwlink/?LinkID=528096&clcid=0x409).

Se non si desidera inviare i dati di utilizzo a Microsoft, è possibile impostare l'opzione *telemetry.enableTelemetry* a *false*.

Per silenziare tutti gli eventi di telemetria di [!INCLUDE[name-sos](../includes/name-sos-short.md)], modificare **File**>**Preferenze**>**Impostazioni** (**sqlops**>**Preferenze**>**Impostazioni** su mac) con la seguente opzione:

```json
    "telemetry.enableTelemetry": false
```

**Avviso importante**: questa opzione richiede il riavvio di [!INCLUDE[name-sos](../includes/name-sos-short.md)] per far sì che le modifiche diventino effettive.

## <a name="how-to-disable-crash-reporting"></a>Come disabilitare la segnalazione di arresto anomalo del sistema

Per disabilitare la segnalazione di arresto anomalo del sistema, modificare **File**>**Preferenze**>**Impostazioni** (**sqlops**>**Preferenze**>**Impostazioni** su mac) con la seguente opzione:

```json
    "telemetry.enableCrashReporter": false
```

**Avviso importante**: questa opzione richiede il riavvio di [!INCLUDE[name-sos](../includes/name-sos-short.md)] per far sì che le modifiche diventino effettive.

## <a name="additional-resources"></a>Risorse aggiuntive
- [Area di lavoro e impostazioni utente](settings.md)
