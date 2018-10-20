---
title: Abilitare o disabilitare la raccolta dati di utilizzo e arresto anomalo del sistema reporting per Studio di Azure Data | Microsoft Docs
description: In questo articolo viene illustrato come controllare se vengono raccolti e inviati a Microsoft informazioni sull'utilizzo e dati di segnalazione arresto anomalo del sistema.
ms.custom: tools|sos
ms.date: 09/24/2018
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: conceptual
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b0a5adf802ab07e05f1041b1385044e2d580db32
ms.sourcegitcommit: 35e4c71bfbf2c330a9688f95de784ce9ca5d7547
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2018
ms.locfileid: "49356482"
---
# <a name="enable-or-disable-usage-data-collection-for-includename-sosincludesname-sos-shortmd"></a>Abilitare o disabilitare la raccolta di dati di utilizzo per [!INCLUDE[name-sos](../includes/name-sos-short.md)]

## <a name="how-to-disable-telemetry-reporting"></a>Come disabilitare la segnalazione di dati di telemetria

[!INCLUDE[name-sos](../includes/name-sos-short.md)]raccoglie dati sull'utilizzo e li invia a Microsoft per contribuire a migliorare i prodotti e i servizi. Per altre informazioni, leggere l'[informativa sulla privacy](https://go.microsoft.com/fwlink/?LinkID=528096&clcid=0x409).

Se non si desidera inviare i dati di utilizzo a Microsoft, è possibile impostare l'opzione *telemetry.enableTelemetry* su *false*.

Per tutti gli eventi di telemetria da disattiva [!INCLUDE[name-sos](../includes/name-sos-short.md)], da **File** > **preferenze** > **impostazioni**, aggiungere la seguente opzione:

```json
    "telemetry.enableTelemetry": false
```

**Avviso importante**: per rendere effettiva la modifica è [!INCLUDE[name-sos](../includes/name-sos-short.md)] necessario riavviare SQL Operations Studio (anteprima). 

## <a name="how-to-disable-crash-reporting"></a>Come disabilitare la segnalazione degli arresti anomali

Per disabilitare la segnalazione di arresto anomalo del sistema, scegliere File  >  Preferenze  >  Impostazioni e aggiungere l'opzione seguente:

```json
    "telemetry.enableCrashReporter": false
```

**Avviso importante**: per rendere effettiva la modifica è [!INCLUDE[name-sos](../includes/name-sos-short.md)] necessario riavviare SQL Operations Studio (anteprima).

## <a name="additional-resources"></a>Risorse aggiuntive
- [Area di lavoro e impostazioni utente](settings.md)
