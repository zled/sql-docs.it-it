---
title: Programmazione ADO JScript | Documenti Microsoft
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
dev_langs: JScript
helpviewer_keywords:
- JScript programming in ADO
- ADO, JScript programming
ms.assetid: 62273658-0fe7-4aac-b4d8-f725e6baf043
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b786f76f5032678901516ede26d388a41d615b31
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="jscript-ado-programming"></a>Programmazione ADO JScript
## <a name="creating-an-ado-project"></a>Creazione di un progetto ADO  
 Microsoft JScript non supporta le librerie dei tipi, in modo non è necessario fare riferimento ad ADO nel progetto. Di conseguenza, è supportata alcuna funzionalità associati, ad esempio il completamento della riga di comando. Inoltre, per impostazione predefinita, le costanti enumerate ADO non sono definite in JScript.  
  
 ADO, tuttavia, fornisce che con due simboli di includere i file che contiene le definizioni seguenti da utilizzare con JScript:  
  
-   Per la creazione di script sul lato server utilizzare Adojavas. Inc, che viene installato nella cartella libreria ADO.  
  
-   Per la creazione di script sul lato client utilizzare Adcjavas. Inc, che viene installato nella cartella libreria ADO.  
  
 È possibile copiare e incollare le definizioni di costanti da questi file in pagine ASP o, se si eseguono gli script sul lato server, copiare i file Adojavas. inc in una cartella nel sito Web e farvi riferimento dalla pagina ASP simile al seguente:  
  
```  
<!--#include File="adojavas.inc"-->  
```  
  
## <a name="creating-ado-objects-in-jscript"></a>Creazione di oggetti ADO in JScript  
 È invece necessario utilizzare il **CreateObject** chiamata di funzione:  
  
```  
var Rs1;  
Rs1 = Server.CreateObject("ADODB.Recordset");  
```  
  
## <a name="jscript-example"></a>Esempio di JScript  
 Il codice seguente è un esempio generico di programmazione sul lato server JScript in un file della pagina ASP (Active Server) che apre un **Recordset** oggetto:  
  
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
