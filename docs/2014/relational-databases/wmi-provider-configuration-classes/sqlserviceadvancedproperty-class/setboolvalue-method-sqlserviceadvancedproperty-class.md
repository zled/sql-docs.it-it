---
title: Impostare punti di interruzione | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.setbreakpoints.f1
helpviewer_keywords:
- Set Breakpoints dialog box
ms.assetid: 876e61b7-875c-43f4-bbce-d7eeb90f6730
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 9269cd8d4e01257f4af2642ad767353d09444a6e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48130339"
---
# <a name="set-breakpoints"></a>Imposta punti di interruzione
  Utilizzare la finestra di dialogo **Imposta punti di interruzione** per specificare gli eventi su cui abilitare i punti di interruzione e per controllarne il funzionamento.  
  
## <a name="options"></a>Opzioni  
 **Abilitata**  
 Consente di abilitare un punto di interruzione su un evento.  
  
 **Condizione interruzione**  
 Consente di visualizzare un elenco di eventi disponibili sui quali è possibile impostare i punti di interruzione.  
  
 **Tipo passaggi**  
 Consente di specificare quando il punto di interruzione diventa effettivo.  
  
|valore|Description|  
|-----------|-----------------|  
|**Always**|L'esecuzione viene sempre sospesa al rilevamento di un punto di interruzione.|  
|**Numero di passaggi uguale a**|L'esecuzione viene sospesa quando il punto di interruzione viene rilevato per un numero di volte uguale al numero di passaggi specificato.|  
|**Numero di passaggi maggiore o uguale a**|L'esecuzione viene sospesa quando il punto di interruzione viene rilevato per un numero di volte maggiore o uguale al numero di passaggi specificato.|  
|**Numero di passaggi multiplo di**|L'esecuzione viene sospesa quando il punto di interruzione viene rilevato per un numero di volte multiplo del numero di passaggi specificato. Se ad esempio questa opzione è impostata su 5, l'esecuzione verrà sospesa ogni cinque volte.|  
  
 **Passaggi**  
 Consente di specificare il numero di passaggi al raggiungimento del quale attivare un'interruzione. Questa opzione non è disponibile se il punto di interruzione è sempre attivo.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug del flusso di controllo](../../../integration-services/troubleshooting/debugging-control-flow.md)  
  
  
