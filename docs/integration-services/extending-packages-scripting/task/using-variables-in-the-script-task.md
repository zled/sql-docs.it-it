---
title: "Utilizzo di variabili nell'attività Script | Documenti Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
helpviewer_keywords:
- Foreach Loop containers
- Script task [Integration Services], variables
- scripts [Integration Services], variables
- Variables property
- Variable object
- SSIS Script task, variables
- variables [Integration Services], Script task
ms.assetid: 593b5961-4bfa-4ce1-9531-a251c34e89d3
caps.latest.revision: 63
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: ccfd7ce8e8f53d12dac3b021d5f62bd03947413d
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="using-variables-in-the-script-task"></a>Utilizzo di variabili nell'attività Script
  Le variabili rendono possibile lo scambio di dati tra l'attività Script e altri oggetti del pacchetto. Per altre informazioni, vedere [Integration Services &#40;SSIS&#41; Variables](../../../integration-services/integration-services-ssis-variables.md).  
  
 L'attività Script utilizza il <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> proprietà del **Dts** oggetto da leggere e scrivere <xref:Microsoft.SqlServer.Dts.Runtime.Variable> oggetti nel pacchetto.  
  
> [!NOTE]  
>  Il <xref:Microsoft.SqlServer.Dts.Runtime.Variable.Value%2A> proprietà del <xref:Microsoft.SqlServer.Dts.Runtime.Variable> classe è di tipo **oggetto**. Poiché l'attività Script deve **Option Strict** abilitato, è necessario eseguire il cast di <xref:Microsoft.SqlServer.Dts.Runtime.Variable.Value%2A> proprietà nel tipo appropriato prima che sia possibile utilizzarlo.  
  
 Aggiungere variabili esistenti per il <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptTask.ReadOnlyVariables%2A> e <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptTask.ReadWriteVariables%2A> Elenca il **Editor attività Script** per renderli disponibili per lo script personalizzato. Tenere presente che per i nomi delle variabili viene applicata la distinzione tra maiuscole e minuscole. All'interno dello script, accedere alle variabili di entrambi i tipi tramite il <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> proprietà del **Dts** oggetto. Utilizzare il **valore** proprietà da leggere e scrivere in singole variabili. L'attività Script gestisce in modo trasparente il blocco mentre lo script legge e modifica i valori delle variabili.  
  
 È possibile utilizzare il metodo <xref:Microsoft.SqlServer.Dts.Runtime.Variables.Contains%2A> della raccolta <xref:Microsoft.SqlServer.Dts.Runtime.Variables> restituita dalla proprietà <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> per verificare l'esistenza di una variabile prima di utilizzarla nel codice.  
  
 È inoltre possibile utilizzare il <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A> proprietà (Dts.VariableDispenser) per l'utilizzo di variabili nell'attività Script. Quando si utilizza <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A>, è necessario gestire sia la semantica di blocco che il cast dei tipi di dati per i valori delle variabili nel codice personalizzato. Può essere necessario utilizzare la proprietà <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A> anziché la proprietà <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> se si desidera utilizzare una variabile non disponibile in fase di progettazione ma che viene creata a livello di programmazione in fase di esecuzione.  
  
## <a name="using-the-script-task-within-a-foreach-loop-container"></a>Utilizzo dell'attività Script in un contenitore Ciclo Foreach  
 Quando un'attività Script viene eseguita ripetutamente in un contenitore Ciclo Foreach, lo script deve in genere gestire il contenuto dell'elemento corrente nell'enumeratore. Ad esempio, se si utilizza l'enumeratore Foreach File, lo script deve riconoscere il nome di file corrente. Se si utilizza l'enumeratore Foreach ADO, lo script deve conoscere il contenuto delle colonne nella riga di dati corrente.  
  
 Le variabili rendono possibile questa comunicazione tra il contenitore Ciclo Foreach e l'attività Script. Nel **mapping variabili** pagina del **Editor ciclo Foreach**, assegnare variabili a ogni elemento di dati restituito da un singolo elemento enumerato. Ad esempio, un enumeratore Foreach File restituisce solo un nome di file in corrispondenza dell'indice 0 e pertanto richiede solo un mapping di variabili, mentre un enumeratore che restituisce diverse colonne di dati in ogni riga richiede che venga eseguito il mapping di una variabile diversa a ogni colonna che si desidera utilizzare nell'attività Script.  
  
 Dopo che è stato eseguito il mapping degli elementi enumerati alle variabili, è necessario aggiungere le variabili mappate al **ReadOnlyVariables** proprietà il **Script** pagina del **Editor attività Script** per renderli disponibili per lo script. Per un esempio di un'attività Script all'interno di un contenitore ciclo Foreach che elabora i file di immagine in una cartella, vedere [utilizzo delle immagini con l'attività Script](../../../integration-services/extending-packages-scripting-task-examples/working-with-images-with-the-script-task.md).  
  
## <a name="variables-example"></a>Esempio di variabili  
 Nell'esempio seguente viene illustrato come accedere e utilizzare le variabili in un'attività Script per determinare il percorso del flusso di lavoro del pacchetto. Nell'esempio si presuppone di aver creato le variabili integer denominate `CustomerCount` e `MaxRecordCount` e aggiunte al **ReadOnlyVariables** insieme il **Editor attività Script**. La variabile `CustomerCount` contiene il numero di record di clienti da importare. Se il valore è maggiore del valore `MaxRecordCount`, l'attività Script riporta un errore. Quando si verifica un errore perché la soglia `MaxRecordCount` è stata superata, il percorso di errore del flusso di lavoro può implementare l'eventuale pulizia richiesta.  
  
 Per compilare correttamente l'esempio, è necessario aggiungere un riferimento all'assembly Microsoft.SqlServer.ScriptTask.  
  
```vb  
Public Sub Main()  
  
    Dim customerCount As Integer  
    Dim maxRecordCount As Integer  
  
    If Dts.Variables.Contains("CustomerCount") = True AndAlso _  
        Dts.Variables.Contains("MaxRecordCount") = True Then  
  
        customerCount = _  
            CType(Dts.Variables("CustomerCount").Value, Integer)  
        maxRecordCount = _  
            CType(Dts.Variables("MaxRecordCount").Value, Integer)  
  
    End If  
  
    If customerCount > maxRecordCount Then  
            Dts.TaskResult = ScriptResults.Failure  
    Else  
            Dts.TaskResult = ScriptResults.Success  
    End If  
  
End Sub  
```  
  
```csharp  
using System;  
using System.Data;  
using Microsoft.SqlServer.Dts.Runtime;  
  
public class ScriptMain  
{  
  
    public void Main()  
    {  
        int customerCount;  
        int maxRecordCount;  
  
        if (Dts.Variables.Contains("CustomerCount")==true&&Dts.Variables.Contains("MaxRecordCount")==true)  
  
        {  
            customerCount = (int) Dts.Variables["CustomerCount"].Value;  
            maxRecordCount = (int) Dts.Variables["MaxRecordCount"].Value;  
  
        }  
  
        if (customerCount>maxRecordCount)  
        {  
            Dts.TaskResult = (int)ScriptResults.Failure;  
        }  
        else  
        {  
            Dts.TaskResult = (int)ScriptResults.Success;  
        }  
  
    }  
  
}  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Integration Services &#40; SSIS &#41; Variabili](../../../integration-services/integration-services-ssis-variables.md)   
 [Utilizzare le variabili nei pacchetti](http://msdn.microsoft.com/library/7742e92d-46c5-4cc4-b9a3-45b688ddb787)  
  
  

