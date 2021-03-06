---
title: Sviluppo di un'interfaccia utente per un enumeratore Foreach personalizzato | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- integration-services
ms.topic: reference
helpviewer_keywords:
- custom user interface [Integration Services], custom foreach enumerators
- custom foreach enumerators [Integration Services], developing custom user interface
ms.assetid: 8aa4aa80-c9ba-42b3-ba87-ae5ea5d3cac3
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 95223c47925b55edbe9357cd04387fd54185a9f0
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48088871"
---
# <a name="developing-a-user-interface-for-a-custom-foreach-enumerator"></a>Sviluppo di un'interfaccia utente per un enumeratore Foreach personalizzato
  Dopo avere eseguito l'override dell'implementazione delle proprietà e dei metodi della classe di base per fornire la funzionalità personalizzata, è possibile creare un'interfaccia utente personalizzata per l'enumeratore Foreach. Se non si crea un'interfaccia utente personalizzata, gli utenti possono configurare il nuovo enumeratore ForEach solo utilizzando la finestra delle proprietà.  
  
 In un progetto o assembly di interfaccia utente personalizzata, creare una classe che implementa <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumeratorUI>. Questa classe deriva dall'oggetto System.Windows.Forms.UserControl, che viene in genere usato per creare un controllo composito per ospitare altri controlli Windows Forms. Il controllo creato viene visualizzato nell'area **Configurazione enumeratore** della scheda **Raccolta** di **Editor ciclo Foreach**.  
  
> [!IMPORTANT]  
>  Dopo aver firmato, compilato e installato l'interfaccia utente nella Global Assembly Cache, come descritto in [Compilazione, distribuzione e debug di oggetti personalizzati](../building-deploying-and-debugging-custom-objects.md), specificare il nome completo di questa classe nella proprietà <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute.UITypeName%2A> dell'oggetto <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute>.  
  
## <a name="coding-the-user-interface-control-class"></a>Scrittura del codice della classe del controllo interfaccia utente  
  
### <a name="initializing-the-user-interface"></a>Inizializzazione dell'interfaccia utente  
 Eseguire l'override del metodo <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumeratorUI.Initialize%2A> per memorizzare nella cache i riferimenti all'oggetto host e alle raccolte di gestioni connessioni e variabili definite nel pacchetto.  
  
### <a name="setting-properties-on-the-user-interface-control"></a>Impostazione di proprietà sul controllo interfaccia utente  
 La classe UserControl, da cui deriva la classe dell'interfaccia utente, viene usata come controllo composito per ospitare altri controlli Windows Forms. Poiché questa classe ospita altri controlli, è possibile progettare l'interfaccia utente personalizzata trascinando e rilasciando controlli, disponendoli, impostando le relative proprietà e rispondendo in fase di esecuzione agli eventi in qualsiasi applicazione Windows Form.  
  
### <a name="saving-settings"></a>Salvataggio delle impostazioni  
 Eseguire l'override del metodo <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumeratorUI.SaveSettings%2A> per copiare i valori selezionati dall'utente dai controlli nelle proprietà dell'enumeratore quando l'utente chiude l'editor.  
  
![Icona di Integration Services (piccola)](../../media/dts-16.gif "icona di Integration Services (piccola)")**rimangono fino a Date con Integration Services** <br /> Per i download, gli articoli, gli esempi e i video Microsoft più recenti, oltre alle soluzioni selezionate dalla community, visitare la pagina [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] sul sito MSDN:<br /><br /> [Visita la pagina di Integration Services su MSDN](http://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Per ricevere una notifica automatica su questi aggiornamenti, sottoscrivere i feed RSS disponibili nella pagina.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di un enumeratore Foreach personalizzato](creating-a-custom-foreach-enumerator.md)   
 [Scrittura del codice di un enumeratore Foreach personalizzato](coding-a-custom-foreach-enumerator.md)  
  
  
