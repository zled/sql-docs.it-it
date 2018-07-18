---
title: Programmazione ADO VBScript | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- ADO, VBScript
- VBScript [ADO]
ms.assetid: 6aaaf6d0-1376-4473-bea6-b81f2645a9ac
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a3f565f610e5f98adae7160d61acf01ab7e41c46
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35270470"
---
# <a name="vbscript-ado-programming"></a>Programmazione ADO VBScript
## <a name="creating-an-ado-project"></a>Creazione di un progetto ADO  
 Microsoft Visual Basic, Scripting Edition non supporta le librerie dei tipi, pertanto non è necessario fare riferimento a ADO nel progetto. Di conseguenza, è supportata alcuna funzionalità associati, ad esempio il completamento della riga di comando. Inoltre, per impostazione predefinita, le costanti enumerate ADO non sono definite in VBScript.  
  
 ADO, tuttavia, fornisce che con due simboli di includere i file che contiene le definizioni seguenti da utilizzare con VBScript:  
  
-   Per la creazione di script sul lato server utilizzare Adovbs. Inc, installato nella cartella c:\Program Files\Common Files\System\ado\ per impostazione predefinita.  
  
-   Per la creazione di script sul lato client utilizzare Adcvbs. Inc, installato nella cartella c:\Program Files\Common Files\System\msdac\ per impostazione predefinita.  
  
 È possibile copiare e incollare le definizioni di costanti da questi file in pagine ASP o, se si eseguono gli script sul lato server, copiare i file Adovbs. inc in una cartella nel sito Web e farvi riferimento dalla pagina ASP simile al seguente:  
  
```  
<!--#include File="adovbs.inc"-->  
```  
  
## <a name="creating-ado-objects-in-vbscript"></a>Creazione di oggetti ADO in VBScript  
 Non è possibile utilizzare il **Dim** istruzione per assegnare gli oggetti a un tipo specifico in VBScript. VBScript, inoltre, non supporta il **New** sintassi utilizzata con la **Dim** istruzione in Visual Basic, Applications Edition. È invece necessario utilizzare il **CreateObject** chiamata di funzione:  
  
```  
Dim Rs1  
Set Rs1 = Server.CreateObject( "ADODB.Recordset" )  
```  
  
## <a name="vbscript-examples"></a>Esempi di VBScript  
 Il codice seguente è un esempio generico di programmazione sul lato server VBScript in un file della pagina ASP (Active Server):  
  
```  
<%  @LANGUAGE="VBSCRIPT" %>  
<%  Option Explicit %>  
<!--#include File="adovbs.inc"-->  
<HTML>  
    <BODY BGCOLOR="White" topmargin="10" leftmargin="10">  
  
    <!-- Your ASP Code goes here -->  
<%  
Dim Source  
Dim Connect  
Dim Rs1  
  
Source = "SELECT * FROM Authors"  
Connect = "Provider=sqloledb;Data Source=srv;" & _  
    "Initial Catalog=Pubs;Integrated Security=SSPI;"  
  
Set Rs1 = Server.CreateObject( "ADODB.Recordset" )  
Rs1.Open Source, Connect, adOpenForwardOnly  
Response.Write("Success!")  
%>  
    </BODY>  
</HTML>  
```  
  
 Esempi di VBScript più specifici sono inclusi nella documentazione di ADO. Per ulteriori informazioni, vedere [esempi di codice ADO in Microsoft Visual Basic Scripting Edition](../../../ado/reference/ado-api/ado-code-examples-vbscript.md).  
  
## <a name="differences-between-vbscript-and-visual-basic"></a>Differenze tra VBScript e Visual Basic  
 Utilizzo di ADO con VBScript è simile all'utilizzo di ADO con Visual Basic in diversi modi, ad esempio la modalità in cui viene utilizzata la sintassi. Tuttavia, esistono alcune differenze significative:  
  
-   VBScript supporta solo il tipo di dati Variant, che può contenere diversi tipi di dati. È possibile archiviare i dati che necessari in un tipo di dati Variant e i dati funzionerà in modo appropriato a causa di cast eseguito da VBScript. Riconosce il tipo richiesto da ADO e converte il valore Variant di conseguenza.  
  
-   Non è possibile utilizzare **in errore goto \<etichetta >** all'interno di VBScript.  
  
-   VBScript supporta alcune delle funzioni predefinite di Visual Basic, ad esempio **Msgbox**, **data**, e **IsNumeric**. Tuttavia, poiché VBScript è un subset di Visual Basic, non tutte le funzioni predefinite sono supportate. Ad esempio, VBScript non supporta il **formato** funzione e le funzioni dei / o file.
