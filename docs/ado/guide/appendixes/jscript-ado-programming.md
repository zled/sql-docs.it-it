---
title: Programmazione ADO JScript | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- JScript
helpviewer_keywords:
- JScript programming in ADO
- ADO, JScript programming
ms.assetid: 62273658-0fe7-4aac-b4d8-f725e6baf043
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 63559af64241be111ed99c9996b63c1978b3d649
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47655629"
---
# <a name="jscript-ado-programming"></a>Programmazione ADO JScript
## <a name="creating-an-ado-project"></a>Creazione di un progetto di ADO  
 Microsoft JScript non supporta le librerie dei tipi, quindi non è necessario fare riferimento ad ADO nel progetto. Di conseguenza, è supportata alcuna funzionalità associata come il completamento della riga di comando. Inoltre, per impostazione predefinita, le costanti enumerate ADO non sono definite in JScript.  
  
 ADO fornisce, tuttavia, che è con due simboli di includere i file che contiene le definizioni seguenti da usare con JScript:  
  
-   Per la creazione di script sul lato server utilizzare Adojavas. Inc, che viene installato nella cartella libreria ADO.  
  
-   Per la creazione di script sul lato client utilizzare Adcjavas. Inc, che viene installato nella cartella libreria ADO.  
  
 È possibile copiare e incollare le definizioni di costanti da questi file nelle pagine ASP oppure, se si sta eseguendo lo scripting lato server, copiare Adojavas. Inc file in una cartella sul sito Web e farvi riferimento dalla pagina ASP simile al seguente:  
  
```  
<!--#include File="adojavas.inc"-->  
```  
  
## <a name="creating-ado-objects-in-jscript"></a>Creazione di oggetti ADO JScript  
 È invece necessario usare il **CreateObject** chiamata di funzione:  
  
```  
var Rs1;  
Rs1 = Server.CreateObject("ADODB.Recordset");  
```  
  
## <a name="jscript-example"></a>Esempio di JScript  
 Il codice seguente è un esempio generico di programmazione sul lato server JScript in un file di pagina ASP (Active Server) che consente di aprire una **Recordset** oggetto:  
  
```  
<%  @LANGUAGE="JScript" %>  
<!--#include File="adojavas.inc"-->  
<HTML>  
<BODY BGCOLOR="White" topmargin="10" leftmargin="10">  
<%  
var Source = "SELECT * FROM Authors";  
var Connect =  "Provider=sqloledb;Data Source=srv;" +  
    "Initial Catalog=Pubs;Integrated Security=SSPI;"  
var Rs1 = Server.CreateObject( "ADODB.Recordset.2.5" );  
Rs1.Open(Source,Connect,adOpenForwardOnly);  
Response.Write("Success!");  
%>  
</BODY>  
</HTML>  
```
