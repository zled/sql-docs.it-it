---
title: Flussi e persistenza | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- persisted streams [ADO]
- streams [ADO], persistence
ms.assetid: ad5bf52c-fd10-4cfa-bf7d-fcedcaa41eea
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d39b1eee58a466ea57febf439f736ce8fa86bd52
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="streams-and-persistence"></a>Persistenza e flussi
Il [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetto [salvare](../../../ado/reference/ado-api/save-method.md) metodo archivi, o *persiste*, **Recordset** in un file e [aprire](../../../ado/reference/ado-api/open-method-ado-recordset.md)metodo ripristini il **Recordset** da tale file.  
  
 Con ADO 2.7 o versioni successiva, il **salvare** e **aprire** metodi possono rendere persistente un **Recordset** per un [flusso](../../../ado/reference/ado-api/stream-object-ado.md) anche l'oggetto. Questa funzionalità è particolarmente utile quando si lavora con Remote Data Service (RDS) e Active Server Pages (ASP).  
  
 Per ulteriori informazioni sulle modalità di utilizzo persistenza possa essere da solo nelle pagine ASP, vedere la documentazione di ASP corrente.  
  
 Di seguito sono riportati alcuni scenari che illustrano come **flusso** oggetti e la persistenza possono essere utilizzati.  
  
## <a name="scenario-1"></a>Scenario 1  
 Questo scenario viene salvato un **Recordset** a un file e quindi a un **flusso**. Viene quindi aperto il flusso persistente in un altro **Recordset**.  
  
```  
Dim rs1 As ADODB.Recordset  
Dim rs2 As ADODB.Recordset  
Dim stm As ADODB.Stream  
  
Set rs1 = New ADODB.Recordset  
Set rs2 = New ADODB.Recordset  
Set stm = New ADODB.Stream  
  
rs1.Open   "SELECT * FROM Customers", "Provider=sqloledb;" & _  
        "Data Source=MyServer;Initial Catalog=Northwind;" & _  
        "Integrated Security=SSPI;""", adopenStatic, adLockReadOnly, adCmdText  
rs1.Save "c:\myfolder\mysubfolder\myrs.xml", adPersistXML  
rs1.Save stm, adPersistXML  
rs2.Open stm  
```  
  
## <a name="scenario-2"></a>Scenario 2  
 Questo scenario persiste un **Recordset** in un **flusso** in formato XML. Quindi legge il **flusso** in una stringa che è possibile esaminare, modificare o visualizzare.  
  
```  
Dim rs As ADODB.Recordset  
Dim stm As ADODB.Stream  
Dim strRst As String  
  
Set rs = New ADODB.Recordset  
Set stm = New ADODB.Stream  
  
' Open, save, and close the recordset.   
rs.Open "SELECT * FROM Customers", "Provider=sqloledb;" & _  
        "Data Source=MyServer;Initial Catalog=Northwind;" & _  
        "Integrated Security=SSPI;"""  
rs.Save stm, adPersistXML  
rs.Close  
Set rs = nothing  
  
' Put saved Recordset into a string variable.  
strRst = stm.ReadText(adReadAll)  
  
' Examine, manipulate, or display the XML data.  
...  
```  
  
## <a name="scenario-3"></a>Scenario 3  
 Questo codice di esempio viene illustrato come salvare codice ASP in modo permanente un **Recordset** come XML direttamente il **risposta** oggetto:  
  
```  
...  
<%  
response.ContentType = "text/xml"  
  
' Create and open a Recordset.  
Set rs = Server.CreateObject("ADODB.Recordset")  
rs.Open "select * from Customers", "Provider=sqloledb;" & _  
        "Data Source=MyServer;Initial Catalog=Northwind;" & _  
        "Integrated Security=SSPI;"""  
  
' Save Recordset directly into output stream.  
rs.Save Response, adPersistXML   
  
' Close Recordset.  
rs.Close  
Set rs = nothing  
%>  
...  
```  
  
## <a name="scenario-4"></a>Scenario 4  
 In questo scenario, il codice ASP scrive il contenuto del **Recordset** in formato ADTG al client. Il [servizio cursore per OLE DB](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md) possibile utilizzare questi dati per creare un disconnesso **Recordset**.  
  
 Una nuova proprietà nel servizio dati di riferimento [DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md), [URL](../../../ado/reference/rds-api/url-property-rds.md), punta alla pagina ASP che genera il **Recordset**. Ciò significa un **Recordset** oggetto può essere ottenuto senza servizi desktop remoto utilizzando lato server [DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) oggetto o l'utente la scrittura di un oggetto business. Questa operazione semplifica il modello di programmazione di servizi desktop remoto in modo significativo.  
  
 Codice lato server, denominato http://server/directory/recordset.asp:  
  
```  
<%  
Dim rs   
Set rs = Server.CreateObject("ADODB.Recordset")  
rs.Open "select au_fname, au_lname, phone from Authors", ""& _  
        "Provider=sqloledb;Data Source=MyServer;" & _  
        "Initial Catalog=Pubs;Integrated Security=SSPI;"  
response.ContentType = "multipart/mixed"  
rs.Save response, adPersistADTG  
%>  
```  
  
 Codice sul lato client:  
  
```  
<HTML>  
<HEAD>  
<TITLE>RDS Query Page</TITLE>  
</HEAD>  
<body>  
<CENTER>  
<H1>Remote Data Service 2.5</H1>  
<TABLE DATASRC="#DC1">  
   <TR>   
      <TD><SPAN DATAFLD="au_fname"></SPAN></TD>  
      <TD><SPAN DATAFLD="au_lname"></SPAN></TD>  
      <TD><SPAN DATAFLD="phone"></SPAN></TD>  
   </TR>  
</TABLE>  
<BR>  
  
<OBJECT classid="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33"  
    ID=DC1 HEIGHT=1 WIDTH = 1>  
    <PARAM NAME="URL" VALUE="http://server/directory/recordset.asp">  
</OBJECT>  
  
</SCRIPT>  
</BODY>  
</HTML>  
```  
  
 Gli sviluppatori dispongono inoltre la possibilità di usare un **Recordset** oggetto nel client:  
  
```  
...  
function GetRs()   
    {  
    rs = CreateObject("ADODB.Recordset");  
    rs.Open "http://server/directory/recordset.asp"  
    DC1.SourceRecordset = rs;  
    }  
...  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Open (metodo) (Recordset ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [Oggetto di record (ADO)](../../../ado/reference/ado-api/record-object-ado.md)   
 [Metodo Save](../../../ado/reference/ado-api/save-method.md)
