---
title: Impostazione delle proprietà | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SMO [SQL Server], properties
- SQL Server Management Objects, properties
- properties [SMO]
ms.assetid: 342569ba-d2f7-44d2-8f3f-ae9c701c7f0f
caps.latest.revision: 48
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d372a0c777e8b4f345b821c3d2c7c864f0f5229c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36069793"
---
# <a name="setting-properties"></a>Impostazione delle proprietà
  Le proprietà sono valori in cui sono archiviate informazioni descrittive sull'oggetto. Ad esempio [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] le opzioni di configurazione sono rappresentate dal <xref:Microsoft.SqlServer.Management.Smo.Server.Configuration%2A> proprietà dell'oggetto. Alle proprietà è possibile accedere direttamente o indirettamente utilizzando la relativa raccolta. Per l'accesso diretto alle proprietà viene utilizzata la sintassi seguente:  
  
 `objInstance.PropertyName`  
  
 Un valore di proprietà può essere modificato o recuperato a seconda che la proprietà disponga di accesso in lettura/scrittura o di accesso in sola lettura. È inoltre necessario impostare determinate proprietà prima che sia possibile creare un oggetto. Per ulteriori informazioni, vedere la documentazione di riferimento di SMO per l'oggetto specifico.  
  
> [!NOTE]  
>  Le raccolte di oggetti figlio vengono visualizzate come proprietà di un oggetto. Ad esempio, il `Tables` raccolta è una proprietà di un `Server` oggetto. Per altre informazioni, vedere [utilizzo di raccolte](using-collections.md).  
  
 Le proprietà di un oggetto sono membri della raccolta Properties. Tale raccolta può essere utilizzata per scorrere tutte le proprietà di un oggetto.  
  
 Talvolta una proprietà non è disponibile per i motivi seguenti:  
  
-   La versione del server non supporta la proprietà, ad esempio se si tenta di accedere a una proprietà che rappresenta una nuova funzionalità di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in una versione precedente di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   Il server non è forniti dati per la proprietà, ad esempio se si tenta di accedere a una proprietà che rappresenta un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] componente che non è installato.  
  
 Per gestire queste situazioni è possibile individuare le eccezioni SMO <xref:Microsoft.SqlServer.Management.Smo.UnknownPropertyException> e <xref:Microsoft.SqlServer.Management.Smo.PropertyCannotBeRetrievedException>.  
  
## <a name="setting-default-initialization-fields"></a>Impostazione dei campi di inizializzazione predefiniti  
 SMO consente di eseguire un'ottimizzazione durante il recupero di oggetti. L'ottimizzazione riduce il numero di proprietà caricate mediante il passaggio automatico tra gli stati seguenti:  
  
1.  Parzialmente caricato. Quando viene fatto riferimento a un oggetto per la prima volta, esso dispone di un minimo di proprietà disponibili (ad esempio Name e Schema).  
  
2.  Completamente caricato. Quando viene fatto riferimento a una proprietà, le proprietà restanti, che sono rapide da caricare, vengono inizializzate e rese disponibili.  
  
3.  Proprietà che utilizzano grandi quantità di memoria. Le restanti proprietà non disponibili utilizzano grandi quantità di memoria e hanno un' <xref:Microsoft.SqlServer.Management.Smo.Property.Expensive%2A> ha valore true (ad esempio <xref:Microsoft.SqlServer.Management.Smo.Database.DataSpaceUsage%2A>). Tali proprietà vengono caricate solo quando viene fatto loro riferimento in modo specifico.  
  
 Se l'applicazione recupera proprietà aggiuntive, oltre a quelle fornite nello stato di caricamento parziale, invia una query per recuperarle e passa allo stato di caricamento completo. Ciò può provocare traffico non necessario tra il client e server. Maggiore ottimizzazione può essere ottenuta tramite la chiamata di <xref:Microsoft.SqlServer.Management.Smo.Server.SetDefaultInitFields%2A> metodo. Il metodo <xref:Microsoft.SqlServer.Management.Smo.Server.SetDefaultInitFields%2A> consente la specifica delle proprietà caricate quando viene inizializzato l'oggetto.  
  
 Il metodo <xref:Microsoft.SqlServer.Management.Smo.Server.SetDefaultInitFields%2A> imposta il comportamento di caricamento della proprietà per la parte restante dell'applicazione o fino a quando non viene reimpostato. È possibile salvare il comportamento originale utilizzando il <xref:Microsoft.SqlServer.Management.Smo.Server.GetDefaultInitFields%2A> (metodo) e il ripristino come richiesto.  
  
## <a name="examples"></a>Esempi  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
## <a name="getting-and-setting-a-property-in-visual-basic"></a>Ottenere e impostare una proprietà in Visual Basic  
 Questo esempio di codice viene illustrato come ottenere il <xref:Microsoft.SqlServer.Management.Smo.Information.Edition%2A> proprietà del <xref:Microsoft.SqlServer.Management.Smo.Information> oggetto e come impostare il <xref:Microsoft.SqlServer.Management.Common.ServerConnection.SqlExecutionModes%2A> proprietà del <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> proprietà per il `ExecuteSql` membro del <xref:Microsoft.SqlServer.Management.Common.SqlExecutionModes> tipo enumerato.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBProperties1](SMO How to#SMO_VBProperties1)]  -->  
  
## <a name="getting-and-setting-a-property-in-visual-c"></a>Ottenere e impostare una proprietà in Visual C#  
 Questo esempio di codice viene illustrato come ottenere il <xref:Microsoft.SqlServer.Management.Smo.Information.Edition%2A> proprietà del <xref:Microsoft.SqlServer.Management.Smo.Information> oggetto e come impostare il <xref:Microsoft.SqlServer.Management.Common.ServerConnection.SqlExecutionModes%2A> proprietà del <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> proprietà per il `ExecuteSql` membro del <xref:Microsoft.SqlServer.Management.Common.SqlExecutionModes> tipo enumerato.  
  
```  
{   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Get a property.   
Console.WriteLine(srv.Information.Version);   
//Set a property.   
srv.ConnectionContext.SqlExecutionModes = SqlExecutionModes.ExecuteSql;   
}  
```  
  
## <a name="setting-various-properties-before-an-object-is-created-in-visual-basic"></a>Impostazione di diverse proprietà prima della creazione di un oggetto in Visual Basic  
 Questo esempio di codice viene illustrato come impostare direttamente il <xref:Microsoft.SqlServer.Management.Smo.Table.AnsiNullsStatus%2A> proprietà del <xref:Microsoft.SqlServer.Management.Smo.Table> oggetto e come creare e aggiungere colonne prima di creare il <xref:Microsoft.SqlServer.Management.Smo.Table> oggetto.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBProperties2](SMO How to#SMO_VBProperties2)]  -->  
  
## <a name="setting-various-properties-before-an-object-is-created-in-visual-c"></a>Impostazione di diverse proprietà prima della creazione di un oggetto in Visual C#  
 Questo esempio di codice viene illustrato come impostare direttamente il <xref:Microsoft.SqlServer.Management.Smo.Table.AnsiNullsStatus%2A> proprietà del <xref:Microsoft.SqlServer.Management.Smo.Table> oggetto e come creare e aggiungere colonne prima di creare il <xref:Microsoft.SqlServer.Management.Smo.Table> oggetto.  
  
```  
{   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Create a new table in the AdventureWorks2012 database.   
Database db;   
db = srv.Databases("AdventureWorks2012");   
Table tb;   
//Specify the parent database, table schema, and the table name in the constructor.   
tb = new Table(db, "Test_Table", "HumanResources");   
//Add columns because the table requires columns before it can be created.   
Column c1;   
//Specify the parent table, the column name, and data type in the constructor.   
c1 = new Column(tb, "ID", DataType.Int);   
tb.Columns.Add(c1);   
c1.Nullable = false;   
c1.Identity = true;   
c1.IdentityIncrement = 1;   
c1.IdentitySeed = 0;   
Column c2;   
c2 = new Column(tb, "Name", DataType.NVarChar(100));   
c2.Nullable = false;   
tb.Columns.Add(c2);   
tb.AnsiNullsStatus = true;   
//Create the table on the instance of SQL Server.   
tb.Create();   
}  
```  
  
## <a name="iterating-through-all-properties-of-an-object-in-visual-basic"></a>Scorrimento di tutte le proprietà di un oggetto in Visual Basic  
 Questo esempio di codice scorre la `Properties` insieme del <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure> dell'oggetto e li visualizza nel [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] schermata di Output.  
  
 Nell'esempio, il <xref:Microsoft.SqlServer.Management.Smo.Property> oggetto è stato attivato le parentesi quadre perché fa anche un [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] (parola chiave).  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBProperties3](SMO How to#SMO_VBProperties3)]  -->  
  
## <a name="iterating-through-all-properties-of-an-object-in-visual-c"></a>Scorrimento di tutte le proprietà di un oggetto in Visual C#  
 Questo esempio di codice scorre la `Properties` insieme del <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure> dell'oggetto e li visualizza nel [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] schermata di Output.  
  
```  
{   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Set properties on the uspGetEmployeedManagers stored procedure on the AdventureWorks2012 database.   
Database db;   
db = srv.Databases("AdventureWorks2012");   
StoredProcedure sp;   
sp = db.StoredProcedures("uspGetEmployeeManagers");   
sp.AnsiNullsStatus = false;   
sp.QuotedIdentifierStatus = false;   
//Iterate through the properties of the stored procedure and display.   
  Property p;   
  foreach ( p in sp.Properties) {   
    Console.WriteLine(p.Name + p.Value);   
  }   
}  
```  
  
## <a name="setting-default-initialization-fields-in-visual-basic"></a>Impostazione dei campi di inizializzazione predefiniti in Visual Basic  
 In questo esempio di codice viene illustrato come ridurre il numero di proprietà dell'oggetto inizializzate in un programma SMO. È necessario includere il `using System.Collections.Specialized`; istruzione da utilizzare il <xref:System.Collections.Specialized.StringCollection> oggetto.  
  
 [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] consente di confrontare il numero di istruzioni inviate all'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] con questa ottimizzazione.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBDefaultInitFields1](SMO How to#SMO_VBDefaultInitFields1)]  -->  
  
## <a name="setting-default-initialization-fields-in-visual-c"></a>Impostazione dei campi di inizializzazione predefiniti in Visual C#  
 In questo esempio di codice viene illustrato come ridurre il numero di proprietà dell'oggetto inizializzate in un programma SMO. È necessario includere il `using System.Collections.Specialized`; istruzione da utilizzare il <xref:System.Collections.Specialized.StringCollection> oggetto.  
  
 [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] consente di confrontare il numero di istruzioni inviate all'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] con questa ottimizzazione.  
  
```  
{   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Reference the AdventureWorks2012 database.   
Database db;   
db = srv.Databases("AdventureWorks2012");   
//Assign the Table object type to a System.Type object variable.   
Table tb;   
Type typ;   
tb = new Table();   
typ = tb.GetType;   
//Assign the current default initialization fields for the Table object type to a   
//StringCollection object variable.   
StringCollection sc;   
sc = srv.GetDefaultInitFields(typ);   
//Set the default initialization fields for the Table object type to the CreateDate property.   
srv.SetDefaultInitFields(typ, "CreateDate");   
//Retrieve the Schema, Name, and CreateDate properties for every table in AdventureWorks2012.   
   //Note that the improvement in performance can be viewed in SQL Server Profiler.   
foreach ( tb in db.Tables) {   
   Console.WriteLine(tb.Schema + "." + tb.Name + " " + tb.CreateDate);   
}   
//Set the default initialization fields for the Table object type back to the original settings.   
srv.SetDefaultInitFields(typ, sc);   
}  
```  
  
  