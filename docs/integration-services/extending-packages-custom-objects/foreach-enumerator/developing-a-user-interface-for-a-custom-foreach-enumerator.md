---
title: Sviluppo di un'interfaccia utente per un enumeratore ForEach personalizzato | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- custom user interface [Integration Services], custom foreach enumerators
- custom foreach enumerators [Integration Services], developing custom user interface
ms.assetid: 8aa4aa80-c9ba-42b3-ba87-ae5ea5d3cac3
caps.latest.revision: 22
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: e743464fcf482ea51f0cde78d692b367c2be525b
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="developing-a-user-interface-for-a-custom-foreach-enumerator"></a>Sviluppo di un'interfaccia utente per un enumeratore Foreach personalizzato
  Dopo avere eseguito l'override dell'implementazione delle proprietà e dei metodi della classe di base per fornire la funzionalità personalizzata, è possibile creare un'interfaccia utente personalizzata per l'enumeratore Foreach. Se non si crea un'interfaccia utente personalizzata, gli utenti possono configurare il nuovo enumeratore ForEach solo utilizzando la finestra delle proprietà.  
  
 In un progetto o assembly di interfaccia utente personalizzata, creare una classe che implementa <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumeratorUI>. Questa classe deriva da UserControl, in genere utilizzato per creare un controllo composito per ospitare altri controlli Windows Form. Il controllo creato viene visualizzato nel **configurazione enumeratore** area della **raccolta** scheda della finestra il **Editor ciclo Foreach**.  
  
> [!IMPORTANT]  
>  Dopo la firma e la creazione di un'interfaccia utente personalizzata e installarlo nella global assembly cache, come descritto in [compilazione, distribuzione e debug di oggetti personalizzati](../../../integration-services/extending-packages-custom-objects/building-deploying-and-debugging-custom-objects.md), ricordarsi di specificare il nome completo di questa classe nella <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute.UITypeName%2A> proprietà del <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute>.  
  
## <a name="coding-the-user-interface-control-class"></a>Scrittura del codice della classe del controllo interfaccia utente  
  
### <a name="initializing-the-user-interface"></a>Inizializzazione dell'interfaccia utente  
 Eseguire l'override del metodo <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumeratorUI.Initialize%2A> per memorizzare nella cache i riferimenti all'oggetto host e alle raccolte di gestioni connessioni e variabili definite nel pacchetto.  
  
### <a name="setting-properties-on-the-user-interface-control"></a>Impostazione di proprietà sul controllo interfaccia utente  
 La classe UserControl, da cui deriva la classe dell'interfaccia utente, deve essere utilizzato come un controllo composito per ospitare altri controlli Windows Form. Poiché questa classe ospita altri controlli, è possibile progettare l'interfaccia utente personalizzata trascinando e rilasciando controlli, disponendoli, impostando le relative proprietà e rispondendo in fase di esecuzione agli eventi in qualsiasi applicazione Windows Form.  
  
### <a name="saving-settings"></a>Salvataggio delle impostazioni  
 Eseguire l'override del metodo <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumeratorUI.SaveSettings%2A> per copiare i valori selezionati dall'utente dai controlli nelle proprietà dell'enumeratore quando l'utente chiude l'editor.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di un enumeratore Foreach personalizzato](../../../integration-services/extending-packages-custom-objects/foreach-enumerator/creating-a-custom-foreach-enumerator.md)   
 [Codifica un enumeratore Foreach personalizzato](../../../integration-services/extending-packages-custom-objects/foreach-enumerator/coding-a-custom-foreach-enumerator.md)  
  
  

