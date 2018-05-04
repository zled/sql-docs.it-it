---
title: Abilitare o disabilitare la raccolta di dati di utilizzo e di arresto anomalo del reporting per SQL Operations Studio (anteprima) | Microsoft Docs
description: In questo articolo viene illustrato come controllare se vengono raccolti e inviati a Microsoft informazioni sull'utilizzo e dati di segnalazione arresto anomalo del sistema.
ms.custom: tools|sos
ms.date: 11/15/2017
ms.prod: sql
ms.reviewer: alayu; erickang; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3fbf952360599642497c1d7109229cba89728d61
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="enable-or-disable-usage-data-collection-for-includename-sosincludesname-sos-shortmd"></a>Abilitare o disabilitare la raccolta di dati di utilizzo per [!INCLUDE[name-sos](../includes/name-sos-short.md)]

## <a name="how-to-disable-telemetry-reporting"></a>Come disabilitare la segnalazione di telemetria

[!INCLUDE[name-sos](../includes/name-sos-short.md)]raccoglie dati sull'utilizzo e li invia a Microsoft per contribuire a migliorare i prodotti e i servizi. Per altre informazioni, leggere l'[informativa sulla privacy](https://go.microsoft.com/fwlink/?LinkID=528096&clcid=0x409).

Se non si desidera inviare i dati di utilizzo a Microsoft, è possibile impostare l'opzione *telemetry.enableTelemetry* su *false*.

Per tutti gli eventi di telemetria da disattiva [!INCLUDE[name-sos](../includes/name-sos-short.md)], da **File** > **preferenze** > **impostazioni**, aggiungere la seguente opzione:

```json
    "telemetry.enableTelemetry": false
```

**Avviso importante**: per rendere effettiva la modifica è [!INCLUDE[name-sos](../includes/name-sos-short.md)] necessario riavviare SQL Operations Studio (anteprima). 

## <a name="how-to-disable-crash-reporting"></a>Come disabilitare la segnalazione di arresto anomalo del sistema

Per disabilitare la segnalazione di arresto anomalo del sistema, scegliere File  >  Preferenze  >  Impostazioni e aggiungere l'opzione seguente:

```json
    "telemetry.enableCrashReporter": false
```

**Avviso importante**: per rendere effettiva la modifica è [!INCLUDE[name-sos](../includes/name-sos-short.md)] necessario riavviare SQL Operations Studio (anteprima).

## <a name="additional-resources"></a>Risorse aggiuntive
- [Area di lavoro e impostazioni utente](settings.md)