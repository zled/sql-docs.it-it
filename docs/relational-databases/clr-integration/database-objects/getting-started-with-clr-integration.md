---
title: Introduzione all'integrazione con CLR | Documenti Microsoft
ms.custom: ''
ms.date: 08/02/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.suite: sql
ms.technology: reference
ms.topic: get-started-article
dev_langs:
- TSQL
- VB
- CSharp
helpviewer_keywords:
- database objects [CLR integration]
- namespaces [CLR integration]
- database objects [CLR integration], about CLR integration
- stored procedures [CLR integration]
- common language runtime [SQL Server], about CLR integration
- building database objects [CLR integration], about CLR integration
- common language runtime [SQL Server], stored procedures
- common language runtime [SQL Server], namespaces
- Hello World example [CLR integration]
- library [CLR integration]
ms.assetid: c73e628a-f54a-411a-bfe3-6dae519316cc
caps.latest.revision: 62
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 33904494978b4a85377ef4d3bdb3cee4f176f2f2
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2018
ms.locfileid: "35702372"
---
# <a name="getting-started-with-clr-integration"></a>Introduzione all'integrazione con CLR
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  In questo argomento viene fornita una panoramica di spazi dei nomi e le librerie necessarie per compilare oggetti di database utilizzando la [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] integrazione con common language runtime (CLR) di .NET Framework. In questo argomento viene inoltre illustrato come scrivere, compilare ed eseguire una stored procedure CLR semplice scritta in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C#.  
  
## <a name="required-namespaces"></a>Spazi dei nomi necessari  
 I componenti necessari per sviluppare oggetti di database CLR base installati con [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. La funzionalità di integrazione CLR viene esposta in un assembly denominato system.data.dll, che fa parte di .NET Framework. Questo assembly è disponibile in Global Assembly Cache (GAC) e nella directory di .NET Framework. Poiché un riferimento a questo assembly viene in genere aggiunto tramite gli strumenti della riga di comando e [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio, non è necessario aggiungerlo manualmente.  
  
 L'assembly system.data.dll contiene gli spazi dei nomi seguenti, necessari per la compilazione di oggetti di database CLR:  
  
 `System.Data`  
  
 `System.Data.Sql`  
  
 `Microsoft.SqlServer.Server`  
  
 `System.Data.SqlTypes`  
  
## <a name="writing-a-simple-hello-world-stored-procedure"></a>Scrittura di una stored procedure "Hello World" semplice  
 Copiare e incollare il codice Visual C# o [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic seguente in un editor di testo e salvarlo in un file denominato "helloworld.cs" o "helloworld.vb".  
  
```csharp  
using System;  
using System.Data;  
using Microsoft.SqlServer.Server;  
using System.Data.SqlTypes;  
  
public class HelloWorldProc  
{  
    [Microsoft.SqlServer.Server.SqlProcedure]  
    public static void HelloWorld(out string text)  
    {  
        SqlContext.Pipe.Send("Hello world!" + Environment.NewLine);  
        text = "Hello world!";  
    }  
}  
```  
  
```vb  
Imports System  
Imports System.Data  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlTypes  
Imports System.Runtime.InteropServices  
  
Public Class HelloWorldProc  
    \<Microsoft.SqlServer.Server.SqlProcedure> _   
    Public Shared  Sub HelloWorld(\<Out()> ByRef text as String)  
        SqlContext.Pipe.Send("Hello world!" & Environment.NewLine)  
        text = "Hello world!"  
    End Sub  
End Class  
  
```  
  
 Questo semplice programma contiene un singolo metodo statico su una classe pubblica. Questo metodo utilizza due nuove classi, **[SqlContext](https://msdn.microsoft.com/library/microsoft.sqlserver.server.sqlcontext.aspx)** e  **[SqlPipe](https://msdn.microsoft.com/library/microsoft.sqlserver.server.sqlpipe.aspx)**, per la creazione di gestito all'output un testo semplice oggetti di database Messaggio. Il metodo assegna inoltre la stringa "Hello world!" come valore del parametro out. Questo metodo può essere dichiarato come stored procedure in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] e quindi eseguito allo stesso modo come stored procedure [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
 Compilazione di questo programma come una libreria, caricato in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], ed eseguirlo come una stored procedure.  
  
## <a name="compile-the-hello-world-stored-procedure"></a>Compilare la procedure "Hello World" archiviato  
 Per impostazione predefinita, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] installa i file di ridistribuzione di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework. Tali file includono csc.exe e vbc.exe, i compilatori della riga di comando per programmi Visual C# e Visual Basic. Per compilare l'esempio, è necessario modificare la variabile del percorso in modo che punti alla directory contenente csc.exe o vbc.exe. Di seguito viene indicato il percorso di installazione predefinito di .NET Framework.  
  
```  
C:\Windows\Microsoft.NET\Framework\(version)  
```  
  
 version contiene il numero di versione del file di ridistribuzione di .NET Framework installato. Esempio:  
  
```  
C:\Windows\Microsoft.NET\Framework\v4.6.1  
```  
  
 Dopo avere aggiunto la directory di .NET Framework al percorso, è possibile compilare la stored procedure di esempio in un assembly con il comando indicato di seguito. Il **/destinazione** opzione consente di compilare in un assembly.  
  
 Per i file di origine di Visual C#:  
  
```  
csc /target:library helloworld.cs   
```  
  
 Per i file di origine di Visual Basic:  
  
```  
vbc /target:library helloworld.vb  
```  
  
 Questi comandi consentono di avviare il compilatore Visual C# o Visual Basic utilizzando l'opzione /target per specificare la compilazione di una DLL della libreria.  
  
## <a name="loading-and-running-the-hello-world-stored-procedure-in-sql-server"></a>Caricamento ed esecuzione della stored procedure "Hello World" in SQL Server  
 Dopo avere compilato la procedura di esempio, è possibile testarla in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. A tale scopo, aprire [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] e creare una nuova query, connettendosi a un database di test appropriato, ad esempio il database di esempio AdventureWorks.  
  
 L'esecuzione di codice CLR (Common Language Runtime) in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] è disattivata per impostazione predefinita. Il codice CLR può essere abilitato usando il **sp_configure** stored procedure di sistema. Per altre informazioni, vedere [Enabling CLR Integration](../../../relational-databases/clr-integration/clr-integration-enabling.md).  
  
 A questo punto è necessario creare l'assembly per poter accedere alla stored procedure. Ai fini dell'esempio, si presuppone che sia stato creato l'assembly helloworld.dll nella directory C:\. Aggiungere l'istruzione [!INCLUDE[tsql](../../../includes/tsql-md.md)] seguente alla query:  
  
```  
CREATE ASSEMBLY helloworld from 'c:\helloworld.dll' WITH PERMISSION_SET = SAFE  
```  
  
 Dopo avere creato l'assembly, è possibile accedere al metodo HelloWorld utilizzando l'istruzione CREATE PROCEDURE. La stored procedure verrà denominata "hello":  
  
```  
  
CREATE PROCEDURE hello  
@i nchar(25) OUTPUT  
AS  
EXTERNAL NAME helloworld.HelloWorldProc.HelloWorld  
-- if the HelloWorldProc class is inside a namespace (called MyNS),  
-- the last line in the create procedure statement would be  
-- EXTERNAL NAME helloworld.[MyNS.HelloWorldProc].HelloWorld  
```  
  
 Una volta creata, la stored procedure può essere eseguita come una normale stored procedure scritta in [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Eseguire il comando seguente:  
  
```  
DECLARE @J nchar(25)  
EXEC hello @J out  
PRINT @J  
```  
  
 Verrà restituito l'output seguente nella finestra dei messaggi di [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].  
  
```  
Hello world!  
Hello world!  
```  
  
## <a name="removing-the-hello-world-stored-procedure-sample"></a>Rimozione della stored procedure "Hello World" di esempio  
 Al termine dell'esecuzione della stored procedure di esempio, è possibile rimuovere la procedura e l'assembly dal database di test.  
  
 Rimuovere innanzitutto la procedura utilizzando il comando drop procedure.  
  
```  
IF EXISTS (SELECT name FROM sysobjects WHERE name = 'hello')  
   drop procedure hello  
```  
  
 Dopo avere eliminato la procedura, è possibile rimuovere l'assembly contenente il codice di esempio.  
  
```  
IF EXISTS (SELECT name FROM sys.assemblies WHERE name = 'helloworld')  
   drop assembly helloworld  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure CLR](http://msdn.microsoft.com/library/bbdd51b2-a9b4-4916-ba6f-7957ac6c3f33)   
 [SQL Server In-Process estensioni specifiche per ADO.NET](../../../relational-databases/clr-integration-data-access-in-process-ado-net/sql-server-in-process-specific-extensions-to-ado-net.md)   
 [Debug di oggetti di Database CLR](../../../relational-databases/clr-integration/debugging-clr-database-objects.md)   
 [Sicurezza per l'integrazione con CLR](../../../relational-databases/clr-integration/security/clr-integration-security.md)  
  
  
