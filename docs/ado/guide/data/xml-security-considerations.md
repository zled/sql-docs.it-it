---
title: Considerazioni sulla sicurezza XML | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML security in ADO
ms.assetid: fadbd38e-6e7b-4b81-96ea-85169c664374
caps.latest.revision: 3
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: fc94f80cde09f6ad55de3a108b6fd16ef74444f1
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="xml-security-considerations"></a>Considerazioni sulla sicurezza XML
Il ADO salvare e aprire metodi sull'oggetto Recordset non sono considerati operazioni sicure per l'esecuzione in Internet Explorer. Pertanto, se questi metodi vengono utilizzati in un codice di script che è in esecuzione in un'applicazione o un controllo che è ospitato in un browser, la configurazione della sicurezza del browser avrà un effetto sul relativo comportamento.  
  
 Per impostazione predefinita nelle aree Internet, Internet Explorer 5 fornisce le restrizioni di sicurezza per tali operazioni. Con questa configurazione, il Recordset non è possibile apportare qualsiasi accesso al file system locale sul client o accedere a origini dati all'esterno del dominio del server da cui è stata scaricata la pagina. In particolare, quando in esecuzione all'interno dell'host del browser, un Recordset può essere salvato in un file solo se nello stesso server da cui è stata scaricata la pagina. Analogamente, è possibile aprire un Recordset caricandola da un file solo se tale file è lo stesso server da cui è stata scaricata la pagina.  
  
## <a name="see-also"></a>Vedere anche  
 [Salvataggio di record in formato XML](../../../ado/guide/data/persisting-records-in-xml-format.md)

