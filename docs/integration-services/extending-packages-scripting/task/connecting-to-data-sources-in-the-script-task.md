---
title: "Connessione a origini dati nell'attività Script | Documenti Microsoft"
ms.custom: 
ms.date: 03/14/2017
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
- connections [Integration Services], scripts
- Integration Services packages, connections
- connection managers [Integration Services], scripts
- scripts [Integration Services], connections
- SSIS packages, connections
- packages [Integration Services], connections
- Script task [Integration Services], connections
- Connections property
- SQL Server Integration Services packages, connections
- SSIS Script task, connections
ms.assetid: 9c008380-715b-455b-9da7-22572d67c388
caps.latest.revision: 59
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 825ff059476614085a338dd9c568031885bed64b
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="connecting-to-data-sources-in-the-script-task"></a>Connessione a origini dati nell'attività Script
  Le gestioni connessioni forniscono accesso a origini dati configurate nel pacchetto. Per altre informazioni, vedere [Connessioni in Integration Services &#40;SSIS&#41;](../../../integration-services/connection-manager/integration-services-ssis-connections.md).  
  
 L'attività Script può accedere a queste gestioni connessioni tramite il <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Connections%2A> proprietà del **Dts** oggetto. Ogni gestione connessione nella raccolta <xref:Microsoft.SqlServer.Dts.Runtime.Connections> archivia informazioni su come eseguire la connessione all'origine dati sottostante.  
  
 Quando si chiama il metodo <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.AcquireConnection%2A> di una gestione connessione, la gestione connessione si connette all'origine dati, se non è già connessa, e restituisce la connessione o le informazioni di connessione appropriate da utilizzare nel codice dell'attività Script.  
  
> [!NOTE]  
>  È necessario conoscere il tipo di connessione restituito dalla gestione connessione prima di chiamare **AcquireConnection**. Poiché l'attività Script deve **Option Strict** abilitato, è necessario eseguire il cast della connessione, che viene restituita come tipo **oggetto**, per il tipo di connessione appropriato prima che sia possibile utilizzarlo.  
  
 È possibile utilizzare il metodo <xref:Microsoft.SqlServer.Dts.Runtime.Connections.Contains%2A> della raccolta <xref:Microsoft.SqlServer.Dts.Runtime.Connections> restituita dalla proprietà <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Connections%2A> per cercare una connessione esistente prima di utilizzare la connessione nel codice.  
  
> [!IMPORTANT]  
>  È possibile chiamare il metodo AcquireConnection delle gestioni connessioni che restituiscono oggetti non gestiti, ad esempio la gestione connessione OLE DB e la gestione connessione Excel, nel codice gestito di un'attività Script. Tuttavia, è possibile leggere la proprietà ConnectionString di queste gestioni connessioni e connettersi all'origine dati direttamente nel codice utilizzando la stringa di connessione con un **OledbConnection** dal **OleDb** dello spazio dei nomi.  
>   
>  Se è necessario chiamare il metodo AcquireConnection di una connessione di gestione che restituisce un oggetto non gestito, utilizzare un [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] gestione connessione. Quando si configura la gestione connessione [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] per l'utilizzo di un provider OLE DB, la connessione viene eseguita tramite il provider di dati [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] per OLE DB. In questo caso, il metodo AcquireConnection restituisce un **OleDbConnection** anziché un oggetto non gestito. Per configurare un [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] gestione connessione per l'utilizzo con un'origine di dati di Excel, seleziona il [!INCLUDE[msCoName](../../../includes/msconame-md.md)] il Provider OLE DB per Jet, specificare un file di Excel e immettere `Excel 8.0` (per Excel 97 e versioni successive) come valore di **proprietà estese** sul **tutti** pagina del **Connection Manager** la finestra di dialogo.  
  
## <a name="connections-example"></a>Esempio di connessioni  
 Nell'esempio seguente viene illustrato come accedere alle gestioni connessioni dall'attività Script. Nell'esempio si presuppone di avere creato e configurato un [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] gestione connessione denominata **Test ADO.NET Connection** e una gestione connessione File Flat denominata **Test Flat File Connection**. Si noti che il [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] gestione connessione restituisce un **SqlConnection** oggetto che è possibile utilizzare immediatamente per connettersi all'origine dati. La gestione connessione file flat, al contrario, restituisce solo una stringa che contiene il percorso e il nome di file. È necessario utilizzare i metodi di **System.IO** spazio dei nomi da aprire e utilizzare il file flat.  
  
```vb  
Public Sub Main()  
  
    Dim myADONETConnection As SqlClient.SqlConnection  
    myADONETConnection = _  
        DirectCast(Dts.Connections("Test ADO.NET Connection").AcquireConnection(Dts.Transaction), _  
        SqlClient.SqlConnection)  
    MsgBox(myADONETConnection.ConnectionString, _  
        MsgBoxStyle.Information, "ADO.NET Connection")  
  
    Dim myFlatFileConnection As String  
    myFlatFileConnection = _  
        DirectCast(Dts.Connections("Test Flat File Connection").AcquireConnection(Dts.Transaction), _  
        String)  
    MsgBox(myFlatFileConnection, MsgBoxStyle.Information, "Flat File Connection")  
  
    Dts.TaskResult = ScriptResults.Success  
  
End Sub  
```  
  
```csharp  
using System;  
using System.Data.SqlClient;  
using Microsoft.SqlServer.Dts.Runtime;  
using System.Windows.Forms;  
  
public class ScriptMain  
{  
  
        public void Main()  
        {  
            SqlConnection myADONETConnection = new SqlConnection();  
            myADONETConnection = (SqlConnection)(Dts.Connections["Test ADO.NET Connection"].AcquireConnection(Dts.Transaction)as SqlConnection);  
            MessageBox.Show(myADONETConnection.ConnectionString, "ADO.NET Connection");  
  
            string myFlatFileConnection;  
            myFlatFileConnection = (string)(Dts.Connections["Test Flat File Connection"].AcquireConnection(Dts.Transaction) as String);  
            MessageBox.Show(myFlatFileConnection, "Flat File Connection");  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
  
        }  
  
}  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Integration Services &#40; SSIS &#41; Connessioni](../../../integration-services/connection-manager/integration-services-ssis-connections.md)   
 [Creare gestioni connessioni](http://msdn.microsoft.com/library/6ca317b8-0061-4d9d-b830-ee8c21268345)  
  
  

