---
title: Tipi di eventi | Documenti Microsoft
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- EventComplete event [ADO]
- events [ADO], types
- Will events [ADO]
- complete events [ADO]
- WillEvent event [ADO]
ms.assetid: f3327ea0-635a-43d4-bd78-c1674f62f1a2
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 502c77b55eb0e3a60497fa10bf9fe8c8a412dc4d
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="types-of-events"></a>Tipi di eventi
Esistono due tipi principali di eventi. "Verrà eventi," che vengono chiamati prima dell'avvio di un'operazione, in genere includono "Sarà" nei relativi nomi, ad esempio, **WillChangeRecordset** o **WillConnect**. Gli eventi che vengono chiamati dopo che un evento è stato completato in genere includono "Completa" nei relativi nomi, ad esempio, **RecordChangeComplete** o **ConnectComplete**. Le eccezioni, ad esempio **InfoMessage** , ma si verifica una volta completata l'operazione associata.  
  
## <a name="will-events"></a>Verrà eventi  
 Gestori eventi chiamati prima dell'inizio dell'operazione offre la possibilità di esaminare o modificare i parametri dell'operazione, quindi annullare l'operazione o consentire il completamento. Queste routine del gestore eventi in genere hanno il formato dei nomi * *verrà*evento** *.  
  
## <a name="complete-events"></a>Eventi complete  
 Chiamato dopo il completamento di un'operazione di gestori di eventi possono inviare una notifica all'applicazione che ha concluso un'operazione. Il gestore eventi è anche una notifica quando un gestore dell'evento verrà Annulla un'operazione in sospeso. Queste routine del gestore eventi in genere hanno il formato dei nomi ** *evento*completa**.  
  
 Verrà gli eventi e Complete in genere vengono utilizzati insieme.  
  
## <a name="other-events"></a>Altri eventi  
 Altri gestori di eventi, gli eventi in cui nomi non sono nel formato * *verrà*evento** * o ** *evento*completa** , vengono chiamati solo Dopo il completamento di un'operazione. Questi eventi sono **Disconnect**, **EndOfRecordset**, e **InfoMessage**.  
  
## <a name="see-also"></a>Vedere anche  
 [Riepilogo dei gestori di eventi ADO](../../../ado/guide/data/ado-event-handler-summary.md)   
 [Creazione di istanze di ADO evento dal linguaggio](../../../ado/guide/data/ado-event-instantiation-by-language.md)   
 [Parametri di evento](../../../ado/guide/data/event-parameters.md)   
 [Dell'interazione tra i gestori eventi](../../../ado/guide/data/how-event-handlers-work-together.md)
