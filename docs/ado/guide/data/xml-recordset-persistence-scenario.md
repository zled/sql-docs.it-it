---
title: Scenario di persistenza Recordset XML | Documenti Microsoft
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML persistence [ADO], persistence scenario
ms.assetid: 353d569a-043a-4397-9ee6-564c4af8d5f6
caps.latest.revision: 4
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: fd47944f218c6cb4d3bea571b27be990c5f7f530
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="xml-recordset-persistence-scenario"></a>Scenario di persistenza Recordset XML
In questo scenario, si creerà un'applicazione di pagine ASP (Active Server) che consente di salvare il contenuto di un oggetto Recordset direttamente all'oggetto ASP Response.  
  
> [!NOTE]
>  Questo scenario richiede che il server Internet Information Server 5.0 (IIS) o versione successiva.  
  
 L'oggetto Recordset restituito viene visualizzato in Internet Explorer utilizzando un [oggetto DataControl (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md).  
  
 I passaggi seguenti sono necessari per creare questo scenario:  
  
-   Configurare l'applicazione  
  
-   Ottenere i dati  
  
-   Inviare i dati  
  
-   Ricevere e visualizzare i dati  
  
## <a name="step-1-set-up-the-application"></a>Passaggio 1: Configurare l'applicazione  
 Creare una directory virtuale IIS denominata "XMLPersist" con le autorizzazioni script. Creare due nuovi file di testo nella cartella a cui punta la directory virtuale, denominati "XMLResponse," l'altra denominata "Default.htm."  
  
## <a name="step-2-get-the-data"></a>Passaggio 2: Ottenere i dati  
 In questo passaggio si scriverà il codice per aprire un Recordset ADO e preparare inviare al client. Aprire il file XMLResponse con un editor di testo, ad esempio Blocco note e inserire il codice seguente.  
  
```  
<%@ language="VBScript" %>  
  
<!-- #include file='adovbs.inc' -->  
  
<%  
  Dim strSQL, strCon  
  Dim adoRec   
  Dim adoCon   
  Dim xmlDoc   
  
  ' You will need to change "MySQLServer" below to the name of the SQL   
  ' server machine to which you want to connect.  
  strCon = "Provider=sqloledb;Data Source=MySQLServer;Initial Catalog=Pubs;Integrated Security=SSPI;"  
  Set adoCon = server.createObject("ADODB.Connection")  
  adoCon.Open strCon  
  
  strSQL = "SELECT Title, Price FROM Titles ORDER BY Price"  
  Set adoRec = Server.CreateObject("ADODB.Recordset")  
  adoRec.Open strSQL, adoCon, adOpenStatic, adLockOptimistic, adCmdText  
```  
  
 Assicurarsi di modificare il valore della `Data Source` parametro `strCon` per il nome del computer di Microsoft SQL Server.  
  
 Mantenere il file aperto e procedere al passaggio successivo.  
  
## <a name="step-3-send-the-data"></a>Passaggio 3: Inviare i dati  
 Dopo aver creato un oggetto Recordset, è necessario inviare al client mediante il salvataggio in formato XML nell'oggetto ASP Response. Aggiungere il codice seguente alla fine della XMLResponse.  
  
```  
  Response.ContentType = "text/xml"  
  Response.Expires = 0  
  Response.Buffer = False  
  
  Response.Write "<?xml version='1.0'?>" & vbNewLine  
  adoRec.save Response, adPersistXML  
  adoRec.Close  
  Set adoRec=Nothing  
%>  
```  
  
 Si noti che l'oggetto risposta ASP viene specificato come destinazione per il Recordset [metodo Save](../../../ado/reference/ado-api/save-method.md). La destinazione del metodo Save può essere qualsiasi oggetto che supporta l'interfaccia IStream, ad esempio un oggetto ADO [flusso ADO (Object)](../../../ado/reference/ado-api/stream-object-ado.md), o un nome di file che include il percorso completo al quale viene salvato il Recordset.  
  
 Salvare e chiudere XMLResponse prima di procedere al passaggio successivo. Inoltre è possibile copiare il file Adovbs dalla cartella di installazione predefinito ADO libreria nella stessa cartella in cui è stato salvato il file XMLResponse.  
  
## <a name="step-4-receive-and-display-the-data"></a>Passaggio 4: Ricevere e visualizzare i dati  
 In questo passaggio si creerà un file HTML con incorporato [oggetto DataControl (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md) oggetto che punta al file XMLResponse per ottenere l'oggetto Recordset. Aprire default.htm con un editor di testo, ad esempio Blocco note e aggiungere il codice seguente. Sostituire "sqlserver" nell'URL con il nome del server.  
  
```  
<HTML>  
<HEAD><TITLE>ADO Recordset Persistence Sample</TITLE></HEAD>  
<BODY>  
  
<TABLE DATASRC="#RDC1" border="1">  
  <TR>  
<TD><SPAN DATAFLD="title"></SPAN></TD>  
<TD><SPAN DATAFLD="price"></SPAN></TD>  
  </TR>  
</TABLE>  
<OBJECT CLASSID="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33" ID="RDC1">  
   <PARAM NAME="URL" VALUE="XMLResponse.asp">  
</OBJECT>  
  
</BODY>  
</HTML>  
```  
  
 Chiudere il file default.htm e salvarlo nella stessa cartella in cui è stato salvato XMLResponse. Utilizzare Internet Explorer 4.0 o versioni successive, aprire l'URL http://*sqlserver*/XMLPersist/default.htm e osservare i risultati. I dati vengono visualizzati in una tabella DHTML associata. Aprire l'URL http:// *sqlserver* /XMLPersist/XMLResponse.asp e osservare i risultati. Viene visualizzato il codice XML.  
  
## <a name="see-also"></a>Vedere anche  
 [Save (metodo)](../../../ado/reference/ado-api/save-method.md)   
 [Salvataggio di record in formato XML](../../../ado/guide/data/persisting-records-in-xml-format.md)
