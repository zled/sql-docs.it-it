---
title: Esercitazione di servizi desktop remoto (VBScript) | Documenti Microsoft
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 02/14/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- RDS tutorial [ADO], VBScript
ms.assetid: e2a48c4d-88b1-43ff-a202-9cdec54997d2
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6f339f4ce8ab4a0bc536960e63fd53ccbfe08d6b
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="rds-tutorial-vbscript"></a>Esercitazione di servizi desktop remoto (VBScript)
Si tratta dell'esercitazione di servizi desktop remoto, scritto in Microsoft Visual Basic Scripting Edition. Per una descrizione dello scopo di questa esercitazione, vedere il [esercitazione su RDS](../../../ado/guide/remote-data-service/rds-tutorial.md).  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
 In questa esercitazione, [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) e [RDS. DataSpace](../../../ado/reference/rds-api/dataspace-object-rds.md) vengono creati in fase di progettazione, ovvero, vengono definite tag object, simile al seguente: `<OBJECT>...</OBJECT>`. In alternativa, possono essere creati in fase di esecuzione con il [metodo CreateObject (RDS)](../../../ado/reference/rds-api/createobject-method-rds.md) metodo. Ad esempio, il **RDS. DataControl** Impossibile creare l'oggetto simile al seguente:  
  
```  
Set DC = Server.CreateObject("RDS.DataControl")  
   <!-- RDS.DataControl -->  
   <OBJECT   
      ID="DC1" CLASSID="CLSID:BD96C556-65A3-11D0-983A-00C04FC29E33">  
   </OBJECT>  
  
   <!-- RDS.DataSpace -->  
   <OBJECT   
      ID="DS1" WIDTH=1 HEIGHT=1  
      CLASSID="CLSID:BD96C556-65A3-11D0-983A-00C04FC29E36">  
   </OBJECT>  
  
   <SCRIPT LANGUAGE="VBScript">  
  
   Sub RDSTutorial()  
   Dim DF1   
```  
  
## <a name="step-1--specify-a-server-program"></a>Passaggio 1: Specificare un'applicazione server  
 VBScript può individuare il nome del server Web IIS in cui viene eseguito mediante l'accesso VBScript **Request. ServerVariables** metodo disponibile per Active Server Pages:  
  
```  
"http://<%=Request.ServerVariables("SERVER_NAME")%>"  
```  
  
 Tuttavia, per questa esercitazione, è possibile utilizzare il server, "server".  
  
> [!NOTE]
>  Prestare attenzione al tipo di dati di **ByRef** argomenti. VBScript non consentono di specificare il tipo di variabile, pertanto è necessario passare sempre un **Variant**. Quando si Usa HTTP, servizi desktop remoto consente di passare un valore Variant a un metodo che prevede un non-Variant se viene richiamato con il **RDS. DataSpace** oggetto [CreateObject](../../../ado/reference/rds-api/createobject-method-rds.md) metodo. Quando si utilizza DCOM o un server in-process, devono corrispondere ai tipi di parametro sui lati client e server o si riceverà un errore "Tipo non corrispondente".  
  
```  
Set DF1 = DS1.CreateObject("RDSServer.DataFactory", "http://yourServer")  
```  
  
## <a name="step-2a--invoke-the-server-program-with-rdsdatacontrol"></a>Passaggio 2a: richiamare il programma del server con RDS. DataControl  
 Questo esempio è semplicemente un commento che illustra il comportamento predefinito del **RDS. DataControl** consiste nell'eseguire la query specificata.  
  
```  
<OBJECT CLASSID="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33" ID="DC1">  
   <PARAM NAME="SQL" VALUE="SELECT * FROM Authors">  
   <PARAM NAME="Connect" VALUE="DSN=Pubs;">  
   <PARAM NAME="Server" VALUE="http://yourServer/">  
</OBJECT>  
...  
<SCRIPT LANGUAGE="VBScript">  
  
Sub RDSTutorial2A()  
   Dim RS  
   DC1.Refresh  
   Set RS = DC1.Recordset  
...  
```  
  
## <a name="step-2b--invoke-the-server-program-with-rdsserverdatafactory"></a>Passaggio 2b: richiamare il programma del server con RDSServer  
  
## <a name="step-3--server-obtains-a-recordset"></a>Passaggio 3: Server Ottiene un oggetto Recordset  
  
## <a name="step-4--server-returns-the-recordset"></a>Passaggio 4: Server restituisce l'oggetto Recordset  
  
```  
Set RS = DF1.Query("DSN=Pubs;", "SELECT * FROM Authors")  
```  
  
## <a name="step-5--datacontrol-is-made-usable-by-visual-controls"></a>Passaggio 5: Rendere utilizzabile DataControl tramite controlli visivi  
  
```  
' Assign the returned recordset to the DataControl.  
  
DC1.SourceRecordset = RS  
```  
  
## <a name="step-6a--changes-are-sent-to-the-server-with-rdsdatacontrol"></a>Passaggio 6a: le modifiche vengono inviate al server con RDS. DataControl  
 Questo esempio è semplicemente un commento che illustra come **RDS. DataControl** esegue gli aggiornamenti.  
  
```  
<OBJECT CLASSID="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33" ID="DC1">  
   <PARAM NAME="SQL" VALUE="SELECT * FROM Authors">  
   <PARAM NAME="Connect" VALUE="DSN=Pubs;">  
   <PARAM NAME="Server" VALUE="http://yourServer/">  
</OBJECT>  
...  
<SCRIPT LANGUAGE="VBScript">  
  
Sub RDSTutorial6A()  
Dim RS  
DC1.Refresh  
...  
Set RS = DC1.Recordset  
' Edit the Recordset object...  
' The SERVER and CONNECT properties are already set from Step 2A.  
Set DC1.SourceRecordset = RS  
...  
DC1.SubmitChanges  
```  
  
## <a name="step-6b--changes-are-sent-to-the-server-with-rdsserverdatafactory"></a>Passaggio 6b: le modifiche vengono inviate al server con RDSServer  
  
```  
DF.SubmitChanges "DSN=Pubs", RS  
  
End Sub  
</SCRIPT>  
</BODY>  
</HTML>  
```  
  
 **Questa è la fine dell'esercitazione.**  
  
## <a name="see-also"></a>Vedere anche  
 [Esercitazione su RDS](../../../ado/guide/remote-data-service/rds-tutorial.md)   

