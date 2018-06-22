---
title: Impostare punti di interruzione | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.setbreakpoints.f1
helpviewer_keywords:
- Set Breakpoints dialog box
ms.assetid: 876e61b7-875c-43f4-bbce-d7eeb90f6730
caps.latest.revision: 23
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: acef1e3e3cc297a54471ed124bfa5984b2980d9a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36063060"
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
  
  