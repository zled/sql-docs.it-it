---
title: Connessione a origini dati nel componente Script | Documenti Microsoft
ms.custom: 
ms.date: 03/17/2017
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
- Script component [Integration Services], connecting to data sources
ms.assetid: 96de63ab-ff48-4e7e-89e0-ffd6a89c63b6
caps.latest.revision: 15
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: e2accca553f1bd9c536076fd0bbcebbff0ff2c42
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="connecting-to-data-sources-in-the-script-component"></a>Connessione a origini dati nel componente script
  Una gestione connessione è un'unità pratica che incapsula e archivia le informazioni necessarie per la connessione a un'origine dati di un determinato tipo. Per altre informazioni, vedere [Connessioni in Integration Services &#40;SSIS&#41;](../../../integration-services/connection-manager/integration-services-ssis-connections.md).  
  
 È possibile rendere gestioni connessioni esistenti disponibili per l'accesso tramite lo script personalizzato nel componente di origine o destinazione facendo clic il **Aggiungi** e **rimuovere** pulsanti il **gestioni connessioni** pagina del **Editor trasformazione Script**. È tuttavia necessario scrivere codice personalizzato per caricare o salvare i dati e possibilmente per aprire e chiudere la connessione all'origine dati. Per ulteriori informazioni sul **gestioni connessioni** pagina del **Editor trasformazione Script**, vedere [configurazione del componente Script nell'Editor del componente di Script](../../../integration-services/extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md) e [Editor trasformazione Script &#40; Pagina gestioni connessioni &#41; ](../../../integration-services/data-flow/transformations/script-transformation-editor-connection-managers-page.md).  
  
 Il componente Script crea un **connessioni** classe di raccolte nel **ComponentWrapper** elemento di progetto che contiene una funzione di accesso fortemente tipizzate per ogni gestione connessione che ha lo stesso nome della gestione connessione stessa. Questa raccolta viene esposta tramite il **connessioni** proprietà del **la classe ScriptMain** classe. La proprietà della funzione di accesso restituisce un riferimento alla gestione connessione come istanza di <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.IDTSConnectionManager100>. Ad esempio, se è stata aggiunta una gestione connessione denominata `MyADONETConnection` nella pagina Gestioni connessioni della finestra di dialogo, è possibile ottenere un riferimento ad essa nello script tramite il codice seguente:  
  
 `Dim myADONETConnectionManager As IDTSConnectionManager100 = _`  
  
 `Me.Connections.MyADONETConnection`  
  
> [!NOTE]  
>  È necessario conoscere il tipo di connessione restituito dalla gestione connessione prima di chiamare **AcquireConnection**. Poiché l'attività Script deve **Option Strict** abilitato, è necessario eseguire il cast della connessione, che viene restituita come tipo **oggetto**, per il tipo di connessione appropriato prima che sia possibile utilizzarlo.  
  
 Chiamare quindi il **AcquireConnection** metodo della gestione connessione specifica per ottenere la connessione sottostante o le informazioni necessarie per connettersi all'origine dati. Ad esempio, ottenere un riferimento di **System.Data.SqlConnection** racchiuso tra una gestione connessione ADO.NET con il codice seguente:  
  
 `Dim myADOConnection As SqlConnection = _`  
  
 `CType(MyADONETConnectionManager.AcquireConnection(Nothing), SqlConnection)`  
  
 Viceversa, la stessa chiamata a una gestione connessione file flat restituisce solo il percorso e il nome di file dell'origine dati del file.  
  
 `Dim myFlatFile As String = _`  
  
 `CType(MyFlatFileConnectionManager.AcquireConnection(Nothing), String)`  
  
 È quindi necessario fornire il percorso e nome file da un **System.IO** o **Streamwriter** per leggere o scrivere i dati nel file flat.  
  
> [!IMPORTANT]  
>  Quando si scrive codice gestito in un componente Script, è possibile chiamare il metodo AcquireConnection di connessione Gestioni che restituiscono oggetti non gestiti, ad esempio la gestione connessione OLE DB e la gestione connessione Excel. Tuttavia, è possibile leggere la proprietà ConnectionString di queste gestioni connessioni e connettersi all'origine dati direttamente nel codice utilizzando la stringa di connessione di un OLEDB **connessione** dal **OleDb** dello spazio dei nomi.  
>   
>  Se è necessario chiamare il metodo AcquireConnection di una gestione connessione che restituisce un oggetto non gestito, utilizzare una gestione connessione ADO.NET. Quando si configura la gestione connessione ADO.NET per l'utilizzo di un provider OLE DB, la connessione viene eseguita tramite il provider di dati .NET Framework per OLE DB. In questo caso, il metodo AcquireConnection restituisce un **OleDbConnection** anziché un oggetto non gestito. Per configurare una gestione connessione ADO.NET per l'utilizzo con un'origine dati di Excel, selezionare il Provider Microsoft OLE DB per Jet, specificare una cartella di lavoro di Excel e quindi immettere `Excel 8.0` (per Excel 97 e versioni successive) come valore di **proprietà estese** sul **tutti** pagina del **Connection Manager** la finestra di dialogo.  
  
 Per ulteriori informazioni sull'utilizzo delle gestioni connessioni con il componente script, vedere [creazione di un'origine con il componente Script](../../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-source-with-the-script-component.md) e [creazione di una destinazione con il componente Script](../../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Integration Services &#40; SSIS &#41; Connessioni](../../../integration-services/connection-manager/integration-services-ssis-connections.md)   
 [Creare gestioni connessioni](http://msdn.microsoft.com/library/6ca317b8-0061-4d9d-b830-ee8c21268345)  
  
  

