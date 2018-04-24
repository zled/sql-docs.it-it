---
title: Dell'interazione tra i gestori eventi | Documenti Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- events [ADO], about event handlers
- unpaired event handlers [ADO]
- paired event handlers [ADO]
- single event handlers [ADO]
- event handlers [ADO]
- multiple object event handlers [ADO]
ms.assetid: a86c8a02-dd69-420d-8a47-0188b339858d
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6e8c279565b17cf236223c641a13c23727fd4c00
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="how-event-handlers-work-together"></a>Dell'interazione tra i gestori eventi
A meno che la programmazione in Visual Basic, tutti i gestori eventi per **connessione** e **Recordset** eventi devono essere implementati indipendentemente dall'effettiva elaborazione tutti gli eventi. La quantità di lavoro di implementazione che è necessario eseguire varia a seconda del linguaggio di programmazione. Per ulteriori informazioni, vedere [la creazione di istanze di ADO evento dal linguaggio](../../../ado/guide/data/ado-event-instantiation-by-language.md).  
  
## <a name="paired-event-handlers"></a>Gestori eventi associati  
 Ogni gestore dell'evento verrà è associato un **completa** gestore dell'evento. Ad esempio, quando l'applicazione modifica il valore di un campo, il **WillChangeField** gestore eventi viene chiamato. Se la modifica è accettabile, l'applicazione lascia il **adStatus** parametro invariato e viene eseguita l'operazione. Al termine dell'operazione, un **FieldChangeComplete** evento notifica all'applicazione che è stata completata l'operazione. Se è stata completata correttamente, **adStatus** contiene **adStatusOK**; in caso contrario, **adStatus** contiene **adStatusErrorsOccurred** e è necessario controllare il **errore** oggetto per determinare la causa dell'errore.  
  
 Quando **WillChangeField** viene chiamato, è possibile che la modifica non dovrebbe essere eseguita. In tal caso, impostare **adStatus** a **adStatusCancel.** L'operazione sia annullata e **FieldChangeComplete** evento riceve un **adStatus** valore **adStatusErrorsOccurred**. Il **errore** oggetto contiene **adErrOperationCancelled** in modo che il **FieldChangeComplete** gestore sa che l'operazione è stata annullata. Tuttavia, è necessario controllare il valore della **adStatus** parametro prima di modificarlo, poiché l'impostazione **adStatus** a **adStatusCancel** non ha alcun effetto se il parametro è stato impostato per **adStatusCantDeny** sulla voce per la procedura.  
  
 In alcuni casi, un'operazione può generare più eventi. Ad esempio, il **Recordset** oggetto dispone di eventi per accoppiati **campo** le modifiche e **Record** le modifiche. Quando l'applicazione modifica il valore di un **campo**, **WillChangeField** gestore eventi viene chiamato. Se si determina che l'operazione può continuare, la **WillChangeRecord** gestore dell'evento viene generato anche. Se questo gestore consente anche l'evento continuare, la modifica venga apportata e **FieldChangeComplete** e **RecordChangeComplete** gestori eventi vengono chiamati. L'ordine in cui vengono chiamati i gestori di eventi verrà per una determinata operazione non è definito, pertanto è consigliabile evitare di scrivere codice che dipende da una determinata sequenza di chiamata dei gestori.  
  
 Nelle istanze quando vengono generati più eventi Will, uno degli eventi può annullare l'operazione in sospeso. Ad esempio, quando l'applicazione modifica il valore di un **campo**, entrambi **WillChangeField** e **WillChangeRecord** , vengono chiamati i gestori di eventi. Tuttavia, se l'operazione verrà annullata nel primo gestore dell'evento associato **completa** gestore viene chiamato immediatamente con **adStatusOperationCancelled**. Il secondo gestore non viene mai chiamato. Se, tuttavia, il primo gestore dell'evento consente l'evento continuare, verrà chiamato il gestore dell'evento altri. Se successivamente Annulla l'operazione, entrambi **completa** eventi verranno chiamati come illustrato negli esempi precedenti.  
  
## <a name="unpaired-event-handlers"></a>Gestori eventi non abbinati  
 Fino a quando lo stato è passato per l'evento non è **adStatusCantDeny**, è possibile disattivare le notifiche degli eventi per qualsiasi evento restituendo **adStatusUnwantedEvent** nel *stato*parametro. Ad esempio, quando il **completa** gestore eventi viene chiamato la prima volta, è possibile restituire **adStatusUnwantedEvent**. Successivamente verrà visualizzato solo **verrà** eventi. Tuttavia, alcuni eventi possono essere generati per più di un motivo. In tal caso, si avrà l'evento un *motivo* parametro. Quando si torna **adStatusUnwantedEvent**, la ricezione di notifiche per l'evento solo quando si verificano per quel particolare motivo si interromperà. In altre parole, potenzialmente si riceverà la notifica per ogni possibile motivo che è possibile attivare l'evento.  
  
 Singolo **verrà** gestori eventi possono essere utili quando si desidera esaminare i parametri che verranno utilizzati in un'operazione. È possibile modificare i parametri dell'operazione o annullare l'operazione.  
  
 In alternativa, lasciare **completa** attivata la notifica evento. Quando viene chiamato il primo gestore dell'evento verrà restituito **adStatusUnwantedEvent**. Successivamente verrà visualizzato solo **completa** eventi.  
  
 Singolo **completa** gestori eventi possono essere utili per la gestione di operazioni asincrone. Ogni operazione asincrona è un oggetto appropriato **completa** evento.  
  
 Ad esempio, può richiedere molto tempo per popolare una grande [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetto. Se l'applicazione è scritta correttamente, è possibile avviare un `Recordset.Open(...,adAsyncExecute)` operazione e continuare con altre attività di elaborazione. Verrà infine una notifica quando il **Recordset** è popolato da un **ExecuteComplete** evento.  
  
## <a name="single-event-handlers-and-multiple-objects"></a>I gestori eventi singolo e più oggetti  
 La flessibilità di un linguaggio di programmazione come Microsoft Visual C++® consente di disporre di un evento gestore elaborare gli eventi da più oggetti. Ad esempio, è possibile creare uno **Disconnect** eventi di processo del gestore eventi da diversi **connessione** oggetti. Se una delle connessioni è terminata, il **Disconnect** gestore dell'evento deve essere chiamato. È Impossibile stabilire la connessione che ha causato l'evento perché il parametro dell'oggetto del gestore eventi potrebbe essere impostato su corrispondente **connessione** oggetto.  
  
> [!NOTE]
>  Questa tecnica non può essere utilizzata in Visual Basic perché tale lingua è in grado di correlare un solo oggetto a un gestore eventi.  
  
## <a name="see-also"></a>Vedere anche  
 [Riepilogo dei gestori di eventi ADO](../../../ado/guide/data/ado-event-handler-summary.md)   
 [Creazione di istanze di ADO evento dal linguaggio](../../../ado/guide/data/ado-event-instantiation-by-language.md)   
 [Parametri di evento](../../../ado/guide/data/event-parameters.md)   
 [Tipi di eventi](../../../ado/guide/data/types-of-events.md)
