---
title: "La registrazione nell'attività Script | Documenti Microsoft"
ms.custom: 
ms.date: 03/06/2017
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
- SQL Server Integration Services packages, logs
- SSIS packages, logs
- logs [Integration Services], scripts
- Integration Services packages, logs
- Log method
- SSIS Script task, logs
- Script task [Integration Services], logs
- packages [Integration Services], logs
ms.assetid: 2e11fc15-df18-4309-bd2d-fc58aa4b9b7a
caps.latest.revision: 57
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 98859dafe0b023954f10239fe11e8b76f36ab28b
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="logging-in-the-script-task"></a>Registrazione nell'attività Script
  L'utilizzo della registrazione nei pacchetti di [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] consente di registrare informazioni dettagliate su stato di esecuzione, risultati e problemi, tramite la registrazione di eventi predefiniti o di messaggi definiti dall'utente da analizzare in un secondo momento. L'attività Script può utilizzare il <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A> metodo il **Dts** oggetto da registrare dati definiti dall'utente. Se la registrazione è abilitata e il **ScriptTaskLogEntry** evento è selezionato per l'accesso il **dettagli** scheda della finestra il **Configura log SSIS** la finestra di dialogo, una singola chiamata al <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A> metodo archivia le informazioni sugli eventi in tutti i provider di log configurati per l'attività.  
  
> [!NOTE]  
>  Anche se è possibile eseguire direttamente la registrazione dall'attività Script, è consigliabile implementare eventi anziché registrare. Quando si utilizzano gli eventi, oltre ad abilitare la registrazione dei messaggi di eventi, è anche possibile rispondere all'evento con gestori eventi predefiniti o definiti dall'utente.  
  
 Per ulteriori informazioni sulla registrazione, vedere [Integration Services &#40; SSIS &#41; Registrazione](../../../integration-services/performance/integration-services-ssis-logging.md).  
  
## <a name="logging-example"></a>Esempio di registrazione  
 Nell'esempio seguente è illustrata la registrazione dall'attività Script registrando un valore che rappresenta il numero di righe elaborate.  
  
```vb  
Public Sub Main()  
  
    Dim rowsProcessed As Integer = 100  
    Dim emptyBytes(0) As Byte  
  
    Try  
        Dts.Log("Rows processed: " & rowsProcessed.ToString, _  
            0, _  
            emptyBytes)  
        Dts.TaskResult = ScriptResults.Success  
    Catch ex As Exception  
        'An error occurred.  
        Dts.Events.FireError(0, "Script Task Example", _  
            ex.Message & ControlChars.CrLf & ex.StackTrace, _  
            String.Empty, 0)  
        Dts.TaskResult = ScriptResults.Failure  
    End Try  
  
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
            //  
            int rowsProcessed = 100;  
            byte[] emptyBytes = new byte[0];  
  
            try  
            {  
                Dts.Log("Rows processed: " + rowsProcessed.ToString(), 0, emptyBytes);  
                Dts.TaskResult = (int)ScriptResults.Success;  
            }  
            catch (Exception ex)  
            {  
                //An error occurred.  
                Dts.Events.FireError(0, "Script Task Example", ex.Message + "\r" + ex.StackTrace, String.Empty, 0);  
                Dts.TaskResult = (int)ScriptResults.Failure;  
            }  
  
        }  
```  
  
 }  
  
## <a name="external-resources"></a>Risorse esterne  
  
-   Post di blog, [registrazione di eventi personalizzati per le attività di Integration Services](http://go.microsoft.com/fwlink/?LinkId=165644), su dougbert.com  
  
## <a name="see-also"></a>Vedere anche  
 [Integration Services &#40; SSIS &#41; Registrazione](../../../integration-services/performance/integration-services-ssis-logging.md)  
  
  
