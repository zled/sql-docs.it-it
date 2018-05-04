---
title: 'La creazione di istanze di evento ADO: ADO e WFC | Documenti Microsoft'
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 02/15/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 9ee4be21-657b-407a-afa4-0b27a6b096ce
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 89fefc8d733f515ef6f085e39b69268a808cefd4
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="ado-event-instantiation-ado-and-wfc"></a>La creazione di istanze di evento ADO: ADO e WFC
ADO per Windows Foundation Classes (ADO/WFC) si basa sul modello di eventi ADO e presenta un'interfaccia di programmazione semplificata dell'applicazione. In generale, ADO/WFC intercetta gli eventi di ADO, consente di consolidare i parametri dell'evento in una classe di evento singolo e quindi chiama il gestore eventi.  
  
### <a name="to-use-ado-events-in-adowfc"></a>Utilizzare gli eventi di ADO in ADO/WFC  
  
1.  Definire un proprio gestore eventi per elaborare un evento. Ad esempio, se si desidera elaborare il **ConnectComplete** evento nel **ConnectionEvent** famiglia, è possibile utilizzare questo codice:  
  
    ```  
    public void onConnectComplete(Object sender,ConnectionEvent e)  
    {  
        System.out.println("onConnectComplete:" + e);  
    }  
    ```  
  
2.  Definire un oggetto gestore per rappresentare il gestore eventi. L'oggetto gestore deve essere di tipo di dati **ConnectEventHandler** per un evento di tipo **ConnectionEvent**, tipo di dati o **RecordsetEventHandler** per un evento di tipo  **RecordsetEvent**. Ad esempio di codice seguente per il **ConnectComplete** gestore eventi:  
  
    ```  
    ConnectionEventHandler handler =   
        new ConnectionEventHandler(this, "onConnectComplete");  
    ```  
  
     Il primo argomento del **ConnectionEventHandler** costruttore è un riferimento alla classe che contiene il gestore dell'evento denominato nel secondo argomento.  
  
3.  Aggiungere il gestore eventi per un elenco di gestori designati per l'elaborazione di un particolare tipo di evento. Utilizzare il metodo con un nome, ad esempio **addOn * * * EventName*(*gestore*).  
  
4.  Internamente, ADO/WFC implementa tutti i gestori di eventi di ADO. Pertanto, un evento è causato da un **connessione** o **Recordset** operazione viene intercettata da un gestore eventi ADO/WFC.  
  
     Il gestore dell'evento ADO/WFC passa ADO **ConnectionEvent** parametri in un'istanza di ADO/WFC **ConnectionEvent** , classe o ADO **RecordsetEvent** parametri in un istanza di ADO/WFC **RecordsetEvent** classe. Queste classi ADO/WFC consolidano i parametri dell'evento ADO; che ogni classe ADO/WFC contiene un membro di dati per ogni parametro univoco in tutti i ADO **ConnectionEvent** o **RecordsetEvent** metodi.  
  
5.  ADO/WFC chiama quindi il gestore eventi con l'oggetto evento ADO/WFC. Ad esempio, il **onConnectComplete** gestore ha una firma simile al seguente:  
  
    ```  
    public void onConnectComplete(Object sender,ConnectionEvent e)  
    ```  
  
     Il primo argomento è il tipo di oggetto che ha inviato l'evento ([connessione](../../../ado/reference/ado-api/connection-object-ado.md) o [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)), e il secondo argomento è l'oggetto evento ADO/WFC (**ConnectionEvent** o **RecordsetEvent**).  
  
     La firma del gestore eventi è più semplice rispetto a un evento di ADO. Tuttavia, è comunque necessario comprendere il modello di eventi di ADO per sapere quali i parametri vengono applicati a un evento e come rispondere.  
  
6.  Restituito dal gestore eventi per il gestore di ADO/WFC per l'evento di ADO. ADO/WFC copia i membri di dati dell'evento ADO/WFC pertinenti ai parametri dell'evento ADO e restituisce quindi il gestore dell'evento ADO.  
  
7.  Quando si è terminato l'elaborazione, rimuovere il gestore dall'elenco di gestori di eventi ADO/WFC. Utilizzare il metodo con un nome, ad esempio **removeOn * * * EventName*(*gestore*).  
  
## <a name="see-also"></a>Vedere anche  
 [Riepilogo dei gestori di eventi ADO](../../../ado/guide/data/ado-event-handler-summary.md)   
 [ADO - WFC sintassi indice](../../../ado/reference/ado-api/ado-wfc-syntax-index.md)   
 [Parametri di evento](../../../ado/guide/data/event-parameters.md)   
 [Dell'interazione tra i gestori eventi](../../../ado/guide/data/how-event-handlers-work-together.md)   
 [Tipi di eventi](../../../ado/guide/data/types-of-events.md)
