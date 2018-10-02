---
title: Visualizzatore dati | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.dataviewer.f1
helpviewer_keywords:
- Data Viewer dialog box
ms.assetid: 6351309a-688f-4e82-9697-1712130f10a1
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: c186241a51a0d3c282e8ae12e7ef4ff6737497d3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47662969"
---
# <a name="data-viewer"></a>Visualizzatore dati
  Se viene configurato un percorso per utilizzare un visualizzatore dati, in quest'ultimo viene visualizzato il buffer di dati in base al buffer durante lo spostamento dei dati tra due componenti di flusso di dati.  
  
## <a name="options"></a>Opzioni  
 **Freccia verde**  
 Fare clic sulla freccia per visualizzare i dati nel buffer successivo. Se i dati possono essere spostati in un unico buffer, l'opzione non è disponibile.  
  
 **Scollega**  
 Consente di scollegare il visualizzatore dati.  
  
 **Nota** Se si scollega un visualizzatore dati, questo non viene eliminato. Se il visualizzatore dati è stato scollegato, il flusso di dati continua attraverso il percorso, ma i dati nel visualizzatore non vengono aggiornati in base a quelli effettivamente presenti nei buffer.  
  
 **Collega**  
 Consente di collegare un visualizzatore dati.  
  
 **Nota** Quando il visualizzatore dati è collegato, vengono visualizzate informazioni derivate da ogni buffer nel flusso di dati e quindi si verifica una sospensione. È possibile avanzare attraverso i buffer mediante la freccia verde.  
  
 **Copia dati**  
 Consente di copiare i dati nel buffer corrente negli Appunti.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug di un flusso di dati](../../integration-services/troubleshooting/debugging-data-flow.md)  
  
  
