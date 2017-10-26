---
title: Utilizzo delle variabili a livello di codice | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- System namespace
- scope [Integration Services]
- variables [Integration Services], programmatically
- configuration files [Integration Services]
- Variables collection
- User namespace
- custom variables [Integration Services]
- variables [Integration Services], customizing
ms.assetid: c4b76a3d-94ca-4a8e-bb45-cb8bd0ea3ec1
caps.latest.revision: 53
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 4a8ade977c971766c8f716ae5f33cac606c8e22d
ms.openlocfilehash: 5c8968302f42e1b8fde55894810ecb77cf715ab6
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="working-with-variables-programmatically"></a>Utilizzo delle variabili a livello di programmazione
  Le variabili consentono di impostare valori in modo dinamico e di controllare i processi in pacchetti, contenitori, attività e gestori eventi. Possono inoltre essere utilizzate dai vincoli di precedenza per controllare la direzione del flusso di dati verso attività diverse. Le variabili possono essere utilizzate per effettuare le operazioni seguenti:  
  
-   Aggiornare le proprietà di un pacchetto in fase di esecuzione.  
  
-   Popolare i valori dei parametri per le istruzioni Transact-SQL in fase di esecuzione.  
  
-   Controllare il flusso di un ciclo Foreach. Per ulteriori informazioni, vedere [enumerazione aggiungere un flusso di controllo](http://msdn.microsoft.com/library/f212b5fb-3cc4-422e-9b7c-89eb769a812a).  
  
-   Controllare un vincolo di precedenza in base al relativo utilizzo in un'espressione. Un vincolo di precedenza può includere variabili nella definizione del vincolo. Per altre informazioni, vedere [Aggiunta di espressioni ai vincoli di precedenza](http://msdn.microsoft.com/library/5574d89a-a68e-4b84-80ea-da93305e5ca1).  
  
-   Controllare la ripetizione condizionale di un contenitore Ciclo For. Per ulteriori informazioni, vedere [aggiungere iterazione per un flusso di controllo](http://msdn.microsoft.com/library/eb3a7494-88ae-4165-9d0f-58715eb1734a).  
  
-   Compilare espressioni che includono valori di variabili.  
  
-   È possibile creare variabili personalizzate per tutti i tipi di contenitore: pacchetti, **ciclo Foreach** contenitori, **ciclo For** contenitori, **sequenza** contenitori, TaskHost e gestori eventi. Per altre informazioni, vedere [Variabili di Integration Services &#40;SSIS&#41;](../../integration-services/integration-services-ssis-variables.md) e [Utilizzo di variabili nei pacchetti](http://msdn.microsoft.com/library/7742e92d-46c5-4cc4-b9a3-45b688ddb787).  
  
## <a name="scope"></a>Ambito  
 Ogni contenitore dispone di una propria raccolta <xref:Microsoft.SqlServer.Dts.Runtime.Variables>. Ogni nuova variabile creata si trova nell'ambito del relativo contenitore padre. Poiché il contenitore del pacchetto costituisce il livello principale della gerarchia dei contenitori, le variabili con ambito pacchetto sono variabili globali e sono visibili a tutti i contenitori del pacchetto. Alla raccolta di variabili per il contenitore possono accedere anche gli elementi figlio del contenitore tramite la raccolta <xref:Microsoft.SqlServer.Dts.Runtime.Variables>, utilizzando il nome della variabile o il relativo indice nella raccolta.  
  
 Poiché la visibilità di una variabile ha un ambito dall'alto in basso, le variabili dichiarate a livello di pacchetto sono visibili a tutti i contenitori nel pacchetto. Pertanto, la raccolta <xref:Microsoft.SqlServer.Dts.Runtime.Variables> in un contenitore include tutte le variabili che appartengono al relativo oggetto padre in aggiunta alle proprie variabili.  
  
 Viceversa, le variabili contenute in un'attività sono limitate in termini di ambito e visibilità e sono visibili solo all'attività.  
  
 Se un pacchetto esegue altri pacchetti, le variabili definite nell'ambito del pacchetto chiamante sono disponibili per il pacchetto chiamato. L'unica eccezione si verifica quando nel pacchetto chiamato esiste una variabile con lo stesso nome. Quando si verifica questa collisione, il valore della variabile nel pacchetto chiamato sostituisce il valore del pacchetto chiamante. Le variabili definite nell'ambito del pacchetto chiamato non sono mai nuovamente disponibili per il pacchetto chiamante.  
  
 Nell'esempio di codice seguente viene creata una variabile a livello di programmazione, `myCustomVar`, nell'ambito del pacchetto, quindi vengono scorse tutte le variabili visibili al pacchetto e ne vengono stampati il nome, il tipo di dati e il valore.  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      Application app = new Application();  
      // Load a sample package that contains a variable that sets the file name.  
      Package pkg = app.LoadPackage(  
        @"C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services" +  
        @"\Package Samples\CaptureDataLineage Sample\CaptureDataLineage\CaptureDataLineage.dtsx",  
        null);  
      Variables pkgVars = pkg.Variables;  
      Variable myVar = pkg.Variables.Add("myCustomVar", false, "User", "3");  
      foreach (Variable pkgVar in pkgVars)  
      {  
        Console.WriteLine("Variable: {0}, {1}, {2}", pkgVar.Name,  
          pkgVar.DataType, pkgVar.Value.ToString());  
      }  
      Console.Read();  
    }  
  }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module Module1  
  
  Sub Main()  
  
    Dim app As Application = New Application()  
    ' Load a sample package that contains a variable that sets the file name.  
    Dim pkg As Package = app.LoadPackage( _  
      "C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services" & _  
      "\Package Samples\CaptureDataLineage Sample\CaptureDataLineage\CaptureDataLineage.dtsx", _  
      Nothing)  
    Dim pkgVars As Variables = pkg.Variables  
    Dim myVar As Variable = pkg.Variables.Add("myCustomVar", False, "User", "3")  
    Dim pkgVar As Variable  
    For Each pkgVar In pkgVars  
      Console.WriteLine("Variable: {0}, {1}, {2}", pkgVar.Name, _  
        pkgVar.DataType, pkgVar.Value.ToString())  
    Next  
    Console.Read()  
  
  End Sub  
  
End Module  
```  
  
 **Esempio di Output:**  
  
 `Variable: CancelEvent, Int32, 0`  
  
 `Variable: CreationDate, DateTime, 4/18/2003 11:57:00 AM`  
  
 `Variable: CreatorComputerName, String,`  
  
 `Variable: CreatorName, String,`  
  
 `Variable: ExecutionInstanceGUID, String, {237AB5A4-7E59-4FC9-8D61-E8F20363DF25}`  
  
 `Variable: FileName, String, Junk`  
  
 `Variable: InteractiveMode, Boolean, False`  
  
 `Variable: LocaleID, Int32, 1033`  
  
 `Variable: MachineName, String, MYCOMPUTERNAME`  
  
 `Variable: myCustomVar, String, 3`  
  
 `Variable: OfflineMode, Boolean, False`  
  
 `Variable: PackageID, String, {F0D2E396-A6A5-42AE-9467-04CE946A810C}`  
  
 `Variable: PackageName, String, DTSPackage1`  
  
 `Variable: StartTime, DateTime, 1/28/2005 7:55:39 AM`  
  
 `Variable: UserName, String, <domain>\<userid>`  
  
 `Variable: VersionBuild, Int32, 198`  
  
 `Variable: VersionComments, String,`  
  
 `Variable: VersionGUID, String, {90E105B4-B4AF-4263-9CBD-C2050C2D6148}`  
  
 `Variable: VersionMajor, Int32, 1`  
  
 `Variable: VersionMinor, Int32, 0`  
  
 Si noti che tutte le variabili con ambite nel **sistema** dello spazio dei nomi sono disponibili per il pacchetto. Per altre informazioni, vedere [Variabili di sistema](../../integration-services/system-variables.md).  
  
## <a name="namespaces"></a>Spazi dei nomi  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ([!INCLUDE[ssIS](../../includes/ssis-md.md)]) offre due spazi dei nomi predefinito in cui risiedono le variabili; **Utente** e **sistema** gli spazi dei nomi. Per impostazione predefinita, qualsiasi variabile personalizzata creata dallo sviluppatore viene aggiunta la **utente** dello spazio dei nomi. Le variabili di sistema si trovano nel **sistema** dello spazio dei nomi. È possibile creare ulteriori spazi dei nomi diverso dal **utente** dello spazio dei nomi per contenere le variabili personalizzate ed è possibile modificare il nome del **utente** dello spazio dei nomi, ma è possibile aggiungere o modificare le variabili nel **sistema** dello spazio dei nomi, o assegnare variabili di sistema a uno spazio dei nomi diversi.  
  
 Le variabili di sistema disponibili variano a seconda del tipo di contenitore. Per un elenco delle variabili di sistema disponibili per pacchetti, contenitori, attività e gestori eventi, vedere [le variabili di sistema](../../integration-services/system-variables.md).  
  
## <a name="value"></a>Valore  
 Il valore di una variabile personalizzata può essere un valore letterale o un'espressione:  
  
-   Se si desidera che la variabile contenga un valore letterale, impostare il valore della relativa proprietà <xref:Microsoft.SqlServer.Dts.Runtime.Variable.Value%2A>.  
  
-   Se si desidera che la variabile contenga un'espressione, in modo che è possibile utilizzare i risultati dell'espressione come valore, impostare il <xref:Microsoft.SqlServer.Dts.Runtime.Variable.EvaluateAsExpression%2A> proprietà della variabile da **true**e specificare un'espressione nella <xref:Microsoft.SqlServer.Dts.Runtime.Variable.Expression%2A> proprietà. In fase di esecuzione l'espressione verrà valutata e il relativo risultato verrà utilizzato come valore della variabile. Se ad esempio la proprietà Expression di una variabile è `"100 * 2""100 * 2"`, la variabile restituirà il valore 200.  
  
 Non è possibile impostare in modo esplicito il valore <xref:Microsoft.SqlServer.Dts.Runtime.Variable.DataType%2A> di una variabile. Il valore <xref:Microsoft.SqlServer.Dts.Runtime.Variable.DataType%2A> è derivato dal valore iniziale assegnato alla variabile e non può essere modificato in seguito. Per ulteriori informazioni sui tipi di dati della variabile, vedere [tipi di dati di Integration Services](../../integration-services/data-flow/integration-services-data-types.md).  
  
 Esempio di codice seguente crea un nuovo set di variabili, <xref:Microsoft.SqlServer.Dts.Runtime.Variable.EvaluateAsExpression%2A> a **true**, assegna l'espressione `"100 * 2"` per la proprietà expression della variabile, quindi restituisce il valore della variabile.  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      Package pkg = new Package();  
      Variable v100 = pkg.Variables.Add("myVar", false, "", 1);  
      v100.EvaluateAsExpression = true;  
      v100.Expression = "100 * 2";  
      Console.WriteLine("Expression for myVar: {0}",   
        v100.Properties["Expression"].GetValue(v100));  
      Console.WriteLine("Value of myVar: {0}", v100.Value.ToString());  
      Console.Read();  
    }  
  }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module Module1  
  
  Sub Main()  
  
    Dim pkg As Package = New Package  
    Dim v100 As Variable = pkg.Variables.Add("myVar", False, "", 1)  
    v100.EvaluateAsExpression = True  
    v100.Expression = "100 * 2"  
    Console.WriteLine("Expression for myVar: {0}", _  
      v100.Properties("Expression").GetValue(v100))  
    Console.WriteLine("Value of myVar: {0}", v100.Value.ToString)  
    Console.Read()  
  
  End Sub  
  
End Module  
```  
  
 **Esempio di Output:**  
  
 `Expression for myVar: 100 * 2`  
  
 `Value of myVar: 200`  
  
 È necessario utilizzare un'espressione valida che utilizza la sintassi delle espressioni di [!INCLUDE[ssIS](../../includes/ssis-md.md)]. I valori letterali sono consentiti nelle espressioni delle variabili, in aggiunta agli operatori e alle funzioni disponibili nella sintassi delle espressioni, ma le espressioni non possono fare riferimento ad altre variabili o colonne. Per altre informazioni, vedere [Espressioni di Integration Services &#40;SSIS&#41;](../../integration-services/expressions/integration-services-ssis-expressions.md).  
  
## <a name="configuration-files"></a>File di configurazione  
 Se un file di configurazione include una variabile personalizzata, la variabile può essere aggiornata in fase di esecuzione. Questo significa che quando il pacchetto viene eseguito, il valore della variabile che si trovava originariamente nel pacchetto viene sostituito con un nuovo valore del file di configurazione. Questa tecnica di sostituzione risulta utile quando un pacchetto viene distribuito in più server che richiedono valori di variabili diversi. Ad esempio, una variabile può specificare il numero di volte in cui un **ciclo Foreach** contenitore ripete il flusso di lavoro o elenco destinatari che un gestore eventi invia messaggi di posta elettronica quando viene generato un errore oppure modificare il numero di errori che possono verificarsi prima che il pacchetto ha esito negativo. Queste variabili vengono fornite dinamicamente nei file di configurazione per ogni ambiente. Pertanto, nei file di configurazione sono consentite solo variabili di lettura/scrittura. Per altre informazioni, vedere [Creazione di configurazioni dei pacchetti](../../integration-services/packages/create-package-configurations.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Integration Services &#40; SSIS &#41; Variabili](../../integration-services/integration-services-ssis-variables.md)   
 [Utilizzare le variabili nei pacchetti](http://msdn.microsoft.com/library/7742e92d-46c5-4cc4-b9a3-45b688ddb787)  
  
  

