---
title: Rendere persistenti i dati | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- persisting data [ADO]
- data updates [ADO], persisting data
- data persistence [ADO]
- updating data [ADO], persisting data
ms.assetid: 21c162ca-2845-4dd8-a49d-e715aba8c461
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d3f4fed35b629f8dd1eae89c42895fb8a780c4cb
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="persisting-data"></a>Rendere persistenti i dati
Computer portatili (ad esempio, usando i computer portatili) ha generato la necessità per le applicazioni che possono essere eseguiti in uno stato connesso e disconnesso. ADO ha aggiunto il supporto per questo offrendo agli sviluppatori la possibilità di salvare un cursore client **Recordset** su disco e ricaricare il file in un secondo momento.  
  
 Esistono diversi scenari in cui è possibile utilizzare questo tipo di funzionalità, inclusi i seguenti:  
  
-   **In viaggio:** quando si esegue l'applicazione in viaggio, è essenziale per fornire la possibilità di apportare modifiche e aggiungere nuovi record che può essere riconnesso al database in un secondo momento e il commit.  
  
-   **Aggiornati di rado ricerche:** spesso in un'applicazione, le tabelle vengono utilizzate come ricerche, ad esempio, definiscono tabelle imposte. Che vengono aggiornati di rado e sono di sola lettura. Invece di rileggere i dati dal server ogni volta che l'applicazione viene avviata, l'applicazione può semplicemente caricare i dati da un locale persistente **Recordset**.  
  
 In ADO, per salvare e caricare **recordset**, utilizzare il **Recordset. Save** e **Recordset.Open(,,,adCmdFile)** metodi sull'oggetto ADO **Recordset**oggetto.  
  
 È possibile utilizzare il **Salva Recordset** metodo per rendere persistenti le ADO **Recordset** in un file su disco. (È anche possibile salvare un **Recordset** per un oggetto ADO **flusso** oggetto. **Flusso** vengono descritti gli oggetti in un secondo momento nella Guida.) Successivamente, è possibile utilizzare il **aprire** metodo per riaprire il **Recordset** quando si è pronti a usarlo. Per impostazione predefinita, ADO Salva il **Recordset** in formato proprietario di Microsoft Advanced dati viene (ADTG). Questo formato binario viene specificato utilizzando il **adPersistADTG PersistFormatEnum** valore. In alternativa, è possibile scegliere di salvare il **Recordset** out come XML utilizzando invece **il valore adPersistXML**. Per ulteriori informazioni sul salvataggio di recordset in formato XML, vedere [salvataggio di record in formato XML](../../../ado/guide/data/persisting-records-in-xml-format.md).  
  
 La sintassi del **salvare** metodo è il seguente:  
  
```  
  
recordset.  
Save  
Destination, PersistFormat  
  
```  
  
 La prima volta che salva il **Recordset**, è possibile specificare facoltativamente *destinazione*. Se si omette *destinazione*, verrà creato un nuovo file con un nome di impostare il valore di [origine](../../../ado/reference/ado-api/source-property-ado-recordset.md) proprietà del **Recordset**.  
  
 Omettere *destinazione* quando si chiama successivamente **salvare** dopo il primo salvataggio o un errore di run-time si verificherà. Se si chiama successivamente **salvare** con un nuovo *destinazione*, **Recordset** viene salvato nella nuova destinazione. Tuttavia, la nuova destinazione e la destinazione originale sia sarà aperti.  
  
 **Salvare** non chiude il **Recordset** o *destinazione*, pertanto è possibile continuare a lavorare con i **Recordset** e salvare le modifiche più recenti. *Destinazione* rimane aperto fino a quando il **Recordset** viene chiusa, durante il quale le altre applicazioni possono leggere, ma non scrivere *destinazione*.  
  
 Per motivi di sicurezza, il **salvare** metodo consente solo l'utilizzo di impostazioni di protezione basso e personalizzato da uno script eseguito da Microsoft Internet Explorer.  
  
 Se il **salvare** metodo viene chiamato durante asincrono **Recordset** recuperare, eseguire o aggiornare è in corso, operazione **salvare** attendere fino a che l'operazione asincrona completare.  
  
 I record vengono salvati a partire dalla prima riga del **Recordset**. Quando il **salvare** metodo termina, la posizione della riga corrente viene spostata nella prima riga del **Recordset**.  
  
 Per ottenere risultati ottimali, impostare il [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) proprietà **adUseClient** con **salvare**. Se il provider non supporta tutte le funzionalità necessarie per salvare **Recordset** oggetti, il servizio cursore fornirà tale funzionalità.  
  
 Quando un **Recordset** vengono rese persistenti con la **CursorLocation** proprietà impostata su **adUseServer**, la funzionalità di aggiornamento per il **Recordset**è limitato. In genere, gli aggiornamenti a tabella singola, inserimenti ed eliminazioni sono consentite (dipende dalla funzionalità del provider). Il [Resync](../../../ado/reference/ado-api/resync-method.md) metodo inoltre è disponibile in questa configurazione.  
  
 Poiché il *destinazione* parametro può accettare qualsiasi oggetto che supporta OLE DB **IStream** interfaccia, è possibile salvare un **Recordset** direttamente a ASP  **Risposta** oggetto.  
  
 Nell'esempio seguente, il **salvare** e **aprire** metodi vengono utilizzati per mantenere un **Recordset** e riaprirlo successivamente:  
  
```  
'BeginPersist  
   conn.ConnectionString = _  
   "Provider=SQLOLEDB;Data Source=MySQLServer;" _  
      & "Integrated Security=SSPI;Initial Catalog=pubs"  
   conn.Open  
  
   conn.Execute "create table testtable (dbkey int " & _  
      "primary key, field1 char(10))"  
   conn.Execute "insert into testtable values (1, 'string1')"  
  
   Set rst.ActiveConnection = conn  
   rst.CursorLocation = adUseClient  
  
   rst.Open "select * from testtable", conn, adOpenStatic, _  
      adLockBatchOptimistic  
  
   'Change the row on the client  
   rst!field1 = "NewValue"  
  
   'Save to a file--the .dat extension is an example; choose  
   'your own extension. The changes will be saved in the file  
   'as well as the original data.  
   MyFile = Dir("c:\temp\temptbl.dat")  
   If MyFile <> "" Then  
       Kill "c:\temp\temptbl.dat"  
   End If  
  
   rst.Save "c:\temp\temptbl.dat", adPersistADTG  
   Set rst = Nothing  
  
   'Now reload the data from the file  
   Set rst = New ADODB.Recordset  
   rst.Open "c:\temp\temptbl.dat", , adOpenStatic, _  
      adLockBatchOptimistic, adCmdFile  
  
   Debug.Print "After Loading the file from disk"  
   Debug.Print "   Current Edited Value: " & rst!field1.Value  
   Debug.Print "   Value Before Editing: " & rst!field1.OriginalValue  
  
   'Note that you can reconnect to a connection and  
   'submit the changes to the data source  
   Set rst.ActiveConnection = conn  
   rst.UpdateBatch  
'EndPersist  
```  
  
## <a name="remarks"></a>Osservazioni  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Altre informazioni sulla persistenza dei recordset](../../../ado/guide/data/more-about-recordset-persistence.md)  
  
-   [Persistenza di recordset filtrati e gerarchici](../../../ado/guide/data/persisting-filtered-and-hierarchical-recordsets.md)  
  
-   [Persistenza di record in formato XML](../../../ado/guide/data/persisting-records-in-xml-format.md)
