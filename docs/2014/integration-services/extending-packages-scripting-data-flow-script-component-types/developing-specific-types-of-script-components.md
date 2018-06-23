---
title: Sviluppo di tipi specifici di componenti script | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- integration-services
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Script component [Integration Services], examples
ms.assetid: dfbbe959-6b4e-4b47-b9dd-bcc31929482d
caps.latest.revision: 11
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 4737f7723f7403d823ca950557bcccd41c7a750a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36069420"
---
# <a name="developing-specific-types-of-script-components"></a>Sviluppo di tipi specifici di componenti script
  Il componente script è uno strumento configurabile che è possibile utilizzare nel flusso di dati di un pacchetto per rispondere ai requisiti non soddisfatti dalle origini, dalle trasformazioni e dalle destinazioni incluse in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Questa sezione contiene esempi di codice del componente script che dimostrano le quattro opzioni disponibili per la configurazione di questo componente.  
  
-   Come origine.  
  
-   Come trasformazione con output sincroni.  
  
-   Come trasformazione con output asincroni.  
  
-   Come destinazione.  
  
 Per altri esempi del componente script, vedere [Ulteriori esempi di componente script](../extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md).  
  
## <a name="in-this-section"></a>Argomenti della sezione  
 [Creazione di un'origine con il componente script](creating-a-source-with-the-script-component.md)  
 Viene descritto e illustrato come creare un'origine del flusso di dati tramite il componente script.  
  
 [Creazione di una trasformazione sincrona con il componente script](creating-a-synchronous-transformation-with-the-script-component.md)  
 Viene descritto e illustrato come creare una trasformazione del flusso di dati con output sincroni tramite il componente script. Questo tipo di trasformazione modifica righe di dati sul posto non appena attraversano il componente.  
  
 [Creazione di una trasformazione asincrona con il componente script](../extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md)  
 Viene descritto e illustrato come creare una trasformazione del flusso di dati con output asincroni tramite il componente script. Questo tipo di trasformazione deve leggere tutte le righe di dati prima di poter aggiungere ulteriori informazioni, ad esempio aggregazioni calcolate, ai dati che attraversano il componente.  
  
 [Creazione di una destinazione con il componente script](../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md)  
 Viene descritto e illustrato come creare una destinazione del flusso di dati tramite il componente script.  
  
![Icona di Integration Services (piccola)](../media/dts-16.gif "icona di Integration Services (piccola)")**Avvisa con Integration Services** <br /> Per i download, gli articoli, gli esempi e i video Microsoft più recenti, oltre alle soluzioni selezionate dalla community, visitare la pagina [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sul sito MSDN:<br /><br /> [Visitare la pagina di Integration Services su MSDN](http://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Per ricevere una notifica automatica su questi aggiornamenti, sottoscrivere i feed RSS disponibili nella pagina.  
  
## <a name="see-also"></a>Vedere anche  
 [Confronto tra soluzioni di scripting e oggetti personalizzati](../extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md)   
 [Sviluppo di tipi specifici di componenti del flusso di dati](../extending-packages-custom-objects-data-flow-types/developing-specific-types-of-data-flow-components.md)  
  
  