---
title: Utilizzo di variabili nel componente Script | Documenti Microsoft
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
- Script component [Integration Services], using variables
ms.assetid: 92d1881a-1ef1-43ae-b1ca-48d0536bdbc2
caps.latest.revision: 13
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: bac1e6d96e872be0355282c3e12fc81054ca41cd
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="using-variables-in-the-script-component"></a>Utilizzo di variabili nel componente script
  Nelle variabili vengono archiviati valori che possono essere utilizzati in fase di esecuzione da un pacchetto e dai relativi contenitori, attività e gestori eventi. Per altre informazioni, vedere [Integration Services &#40;SSIS&#41; Variables](../../../integration-services/integration-services-ssis-variables.md).  
  
 È possibile rendere disponibili per le variabili esistenti di sola lettura o accesso in lettura/scrittura per lo script personalizzato immettendo elenchi delimitati da virgole di variabili nel **ReadOnlyVariables** e **ReadWriteVariables** campi di **Script** pagina del **Editor trasformazione Script**. Tenere presente che per i nomi delle variabili viene applicata la distinzione tra maiuscole e minuscole. Utilizzare il **valore** proprietà da leggere e scrivere in singole variabili. Il componente script gestisce automaticamente l'eventuale blocco richiesto mentre lo script modifica le variabili in fase di esecuzione.  
  
> [!IMPORTANT]  
>  La raccolta di **ReadWriteVariables** è disponibile solo nel **PostExecute** per ottimizzare le prestazioni e ridurre al minimo il rischio di conflitti di blocco. Pertanto, non è possibile incrementare direttamente il valore di una variabile del pacchetto durante l'elaborazione di ogni riga di dati. Incrementare il valore di una variabile locale invece e impostare il valore della variabile del pacchetto per il valore della variabile locale nel **PostExecute** metodo dopo tutti i dati è stata elaborata. È anche possibile utilizzare la proprietà <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.VariableDispenser%2A> per ovviare a questa limitazione, come descritto più avanti in questo argomento. Tuttavia, se si scrive direttamente in una variabile del pacchetto durante l'elaborazione di ogni riga, si verificano effetti negativi sulle prestazioni e aumenta il rischio di conflitti di blocco.  
  
 Per ulteriori informazioni sul **Script** pagina del **Editor trasformazione Script**, vedere [configurazione del componente Script nell'Editor del componente di Script](../../../integration-services/extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md) e [Editor trasformazione Script &#40; Pagina di script &#41; ](../../../integration-services/data-flow/transformations/script-transformation-editor-script-page.md).  
  
 Il componente Script crea un **variabili** classe di raccolte nel **ComponentWrapper** elemento del progetto con una proprietà della funzione di accesso fortemente tipizzate per il valore di ogni variabile preconfigurata in cui la proprietà ha lo stesso nome della variabile stessa. Questa raccolta viene esposta tramite il **variabili** proprietà del **la classe ScriptMain** classe. La proprietà della funzione di accesso fornisce autorizzazioni di sola lettura o di lettura/scrittura al valore della variabile, a seconda dei casi. Ad esempio, se è stata aggiunta una variabile integer denominata `MyIntegerVariable` per il **ReadOnlyVariables** elenco, è possibile recuperare il relativo valore nello script usando il codice seguente:  
  
 `Dim myIntegerVariableValue As Integer = Me.Variables.MyIntegerVariable`  
  
 È anche possibile utilizzare la proprietà <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.VariableDispenser%2A>, accessibile tramite una chiamata a `Me.VariableDispenser`, per utilizzare le variabili nel componente script. In questo caso, non si utilizzano le proprietà delle funzioni di accesso tipizzate e denominate per le variabili, ma si accede alle variabili direttamente. Quando si utilizza <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.VariableDispenser%2A>, è necessario gestire sia la semantica di blocco che il cast dei tipi di dati per i valori delle variabili nel codice personalizzato. È necessario utilizzare la proprietà <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.VariableDispenser%2A> anziché le proprietà delle funzioni di accesso denominate e tipizzate se si desidera utilizzare una variabile non disponibile in fase di progettazione ma che viene creata a livello di codice in fase di esecuzione.  
  
## <a name="see-also"></a>Vedere anche  
 [Integration Services &#40; SSIS &#41; Variabili](../../../integration-services/integration-services-ssis-variables.md)   
 [Utilizzare le variabili nei pacchetti](http://msdn.microsoft.com/library/7742e92d-46c5-4cc4-b9a3-45b688ddb787)  
  
  

