---
title: Programmazione AMO complementari classi e metodi | Documenti Microsoft
ms.custom: 
ms.date: 02/14/2018
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- restores [AMO]
- assemblies [AMO]
- AMO, backup and restore
- capture logs [AMO]
- programming [AMO]
- Analysis Management Objects, backup and restore
- traces [AMO]
- backups [AMO]
ms.assetid: 14aed554-d2e2-49e5-9c72-26660759bce2
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: ea3f2a07cc5d6e39bec7db5faf333986a56062f9
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2018
---
# <a name="programming-amo-complementary-classes-and-methods"></a>Programmazione di classi e metodi AMO complementari
  In questo argomento sono incluse le sezioni seguenti:  
  
-   [Classe di assembly](#Assembly)  
  
-   [Backup e ripristino](#BU)  
  
-   [Trace (classe)](#TRC)  
  
-   [Classe CaptureLog e capturexml](#CL)  
  
##  <a name="Assembly">Classe di assembly</a>  
 Gli assembly consentono di estendere le funzionalità di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] mediante l'aggiunta di nuove stored procedure o funzioni MDX (Multidimensional Expressions). Per ulteriori informazioni, vedere [AMO altre classi e metodi](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-other-classes-and-methods.md).  
  
 L'aggiunta e l'eliminazione di assembly sono operazioni semplici e possono essere eseguite in modalità online. Per aggiungere un assembly al database o all'oggetto server, è necessario disporre dei diritti di amministratore del database o del server rispettivamente.  
  
 Nell'esempio seguente viene aggiunto un assembly al database fornito e viene assegnato l'account del servizio per eseguire l'assembly. Se esiste nel database, l'assembly viene eliminato prima che venga eseguito il tentativo di aggiungerlo.  
  
```  
static public void CreateStoredProcedures(Database db)  
{  
    ClrAssembly clrAssembly;  
  
    // Verify That assembly exist in database and drop it  
    if (db.Assemblies.ContainsName("StoredProcedures"))  
    {  
        clrAssembly = db.Assemblies.FindByName("StoredProcedures");  
        clrAssembly.Drop();  
    }  
  
    // Create the CLR assembly  
    clrAssembly = db.Assemblies.Add("StoredProcedures");  
    clrAssembly.ImpersonationInfo = new ImpersonationInfo(  
        ImpersonationMode.ImpersonateServiceAccount);  
    clrAssembly.PermissionSet = PermissionSet.Unrestricted;  
  
    // Load the assembly files  
    clrAssembly.LoadFiles(Environment.CurrentDirectory  
        + @"\StoredProcedures2.dll", false);  
  
    clrAssembly.Update();  
}  
  
```  
  
##  <a name="BU"></a> Metodi backup e ripristino  
 I metodi Backup e Restore consentono agli amministratori di eseguire il backup di database e di ripristinarli.  
  
 Nell'esempio seguente vengono creati i backup per tutti i database presenti nel server specificato. Se un file di backup esiste già, viene sovrascritto. I file di backup vengono salvati nella cartella relativa della cartella Dati di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
```  
static public void BackUpAllDatabases(Server svr)  
{  
    string fileName;  
    if ((svr != null) && ( svr.Connected))  
        foreach (Database db in svr.Databases)  
        {  
            fileName = db.Name + "_" + ((Int64)(DateTime.Today.Year * 10000 + DateTime.Today.Month * 100 + DateTime.Today.Day)).ToString()+ ".abf";  
            db.Backup(fileName, true);  
        }  
}  
```  
  
 Nell'esempio seguente viene ripristinato il backup di "Adventure Works" dall'esempio precedente. Se il database "My Adventure WorksDW" esiste già, viene sovrascritto.  
  
```  
static public void RestoreAdventureWorks(Server svr)  
{  
    svr.Restore("Adventure Works DW_20051025.abf", "My Adventure WorksDW", true);  
}  
```  
  
##  <a name="TRC">Trace (classe)</a>  
 Per eseguire il monitoraggio dell'attività del server, è necessario utilizzare due tipi di tracce, ovvero le tracce della sessione e le tracce del server. La funzionalità di traccia eseguita sul server può indicare la modalità di esecuzione dell'attività corrente nel server (tracce della sessione), mentre le tracce possono fornire informazioni relative all'attività complessiva del server senza che sia necessario essere connessi al server stesso (tracce del server).  
  
 Durante l'esecuzione della traccia relativa all'attività corrente (tracce della sessione), il server invia all'applicazione corrente notifiche sugli eventi provocati dall'applicazione stessa che si verificano attualmente nel server. Gli eventi vengono acquisiti utilizzando gestori di eventi nell'applicazione corrente. È necessario innanzitutto assegnare le routine di gestione dell'evento all'oggetto <xref:Microsoft.AnalysisServices.SessionTrace>, quindi avviare la traccia della sessione.  
  
 Nell'esempio seguente viene illustrato come impostare una traccia della sessione per analizzare le attività correnti. Le routine del gestore di eventi si trovano alla fine dell'esempio e restituiranno tutte le informazioni di traccia all'oggetto System.Console. Per generare eventi di traccia, il cubo di esempio "Adventure Works" verrà elaborato completamente dopo l'avvio della traccia.  
  
```  
static public void TestSessionTraces(Server svr)  
{  
    // Start the default trace  
  
    svr.SessionTrace.OnEvent  
        += new TraceEventHandler(DefaultTrace_OnEvent);  
    svr.SessionTrace.Stopped  
        += new TraceStoppedEventHandler(DefaultTrace_Stopped);  
    svr.SessionTrace.Start();  
  
    // Process the databases  
    // The trace handlers will output all progress notifications   
    // to the console  
    Database db = svr.Databases.FindByName("Adventure Works DW Multidimensional 2012");  
    Cube cube = db.Cubes.FindByName("Adventure Works");  
    cube.Process(ProcessType.ProcessFull);  
  
    // Stop the default trace  
    svr.SessionTrace.Stop();  
  
}  
static public void DefaultTrace_OnEvent(object sender, TraceEventArgs e)  
{  
    Console.WriteLine("{0}", e.TextData);  
}  
  
static public void DefaultTrace_Stopped(ITrace sender, TraceStoppedEventArgs e)  
{  
    switch (e.StopCause)  
    {  
        case TraceStopCause.StoppedByUser:  
        case TraceStopCause.Finished:  
            Console.WriteLine("Processing completed successfully");  
            break;  
  
        case TraceStopCause.StoppedByException:  
            Console.WriteLine("Processing failed: {0}",  
                e.Exception.Message);  
            break;  
    }  
}  
```  
  
 Le tracce del server possono essere configurate per registrare tutte le informazioni in un file di traccia e possono essere riavviate automaticamente al riavvio del servizio.  
  
 Per impostare una traccia del server, è necessario innanzitutto definire gli eventi del server da monitorare e i dati relativi all'evento da salvare nel file di traccia. Per ogni evento, è necessario definire le colonne di dati da salvare nel file di traccia.  
  
 Per creare una traccia del server, sono necessari quattro passaggi:  
  
1.  Creazione dell'oggetto relativo alla traccia del server e popolamento degli attributi comuni di base.  
  
     LogFileSize definisce la dimensione massima del file di traccia e viene espresso in megabyte. LogFileRollOver abilita l'inizio di un file di log diverso se viene raggiunto il limite definito da LogFileSize. In caso di abilitazione, al nome file viene aggiunto un numero in sequenza. AutoRestart consente il riavvio della traccia se il servizio viene riavviato.  
  
2.  Creazione degli eventi e delle colonne di dati corrispondenti.  
  
3.  Avvio e arresto della traccia in base alle esigenze.  
  
     Anche dopo la traccia è stata arrestata, la traccia esiste nel server e dovrebbe avviarsi nuovamente se la traccia è stata definita con AutoRestart =**true**.  
  
4.  Eliminazione della traccia quando non è più necessaria.  
  
 Nell'esempio seguente, se esiste già, la traccia viene eliminata e successivamente ricreata. I file di traccia vengono salvati nella cartella Log della cartella Dati di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
```  
static public void TestServerTraces(Server svr)  
{  
    Trace trc;  
    TraceEvent te;  
  
        trc = svr.Traces.FindByName("TestServerTraces");  
        if (trc != null)  
            trc.Drop();  
        trc = svr.Traces.Add("TestServerTraces", "TestServerTraces");  
        trc.LogFileName = ("TestServerTraces_" +((Int64)(DateTime.Now.Year * 10000 + DateTime.Now.Month * 100 + DateTime.Now.Day)).ToString() + "_" +  
                ((Int64)(DateTime.Now.Hour * 10000 + DateTime.Now.Minute * 100 + DateTime.Now.Second)).ToString() + ".trc");  
        trc.LogFileSize = 100;  
        trc.LogFileRollover = true;  
        trc.AutoRestart = false;  
  
        #region Define Events to trace & data columns per event  
        te = trc.Events.Add(TraceEventClass.ProgressReportBegin);  
        te.Columns.Add(TraceColumn.TextData);  
        te.Columns.Add(TraceColumn.StartTime);  
        te.Columns.Add(TraceColumn.ObjectName);  
        te.Columns.Add(TraceColumn.ObjectPath);  
        te.Columns.Add(TraceColumn.DatabaseName);  
        te.Columns.Add(TraceColumn.NTCanonicalUserName);  
  
        te = trc.Events.Add(TraceEventClass.ProgressReportCurrent);  
        te.Columns.Add(TraceColumn.TextData);  
        te.Columns.Add(TraceColumn.CurrentTime);  
        te.Columns.Add(TraceColumn.ObjectName);  
        te.Columns.Add(TraceColumn.ObjectPath);  
        te.Columns.Add(TraceColumn.DatabaseName);  
  
        te = trc.Events.Add(TraceEventClass.ProgressReportEnd);  
        te.Columns.Add(TraceColumn.TextData);  
        te.Columns.Add(TraceColumn.StartTime);  
        te.Columns.Add(TraceColumn.CurrentTime);  
        te.Columns.Add(TraceColumn.EndTime);  
        te.Columns.Add(TraceColumn.Success);  
        te.Columns.Add(TraceColumn.Error);  
        te.Columns.Add(TraceColumn.ObjectName);  
        te.Columns.Add(TraceColumn.ObjectPath);  
        te.Columns.Add(TraceColumn.DatabaseName);  
        te.Columns.Add(TraceColumn.NTCanonicalUserName);  
        #endregion  
  
        trc.Update();  
        trc.Start();  
  
        #region Process the Adventure Works Cube  
        // The trace settings will output all progress notifications   
        // to the trace file  
        Database db = svr.Databases.FindByName("Adventure Works DW Multidimensional 2012");  
        Cube cube = db.Cubes.FindByName("Adventure Works");  
        cube.Process(ProcessType.ProcessFull);  
        #endregion  
  
        trc.Stop();  
        trc.Drop();  
  
}  
```  
  
##  <a name="CL"></a> Attributi CaptureLog e CaptureXml  
 L'attributo CaptureLog consente di creare file batch XMLA da operazioni AMO nonché di inserire nello script oggetti server, ad esempio database, cubi, dimensioni, strutture di data mining e altri.  
  
 Per creare un attributo CaptureLog, sono necessari i passaggi seguenti:  
  
1.  Avvio dell'acquisizione del log XMLA impostando il server attributo CaptureXml su **true**.  
  
     Questa opzione avvierà il salvataggio di tutte le operazioni AMO in una raccolta di stringhe anziché l'invio al server.  
  
2.  Avvio normale delle attività AMO. È necessario tenere presente che al server non viene inviata alcuna attività. Per attività si intende qualsiasi operazione, ad esempio l'elaborazione, la creazione, l'eliminazione, l'aggiornamento o qualsiasi altra azione eseguita su un oggetto.  
  
3.  Arrestare l'acquisizione del log XMLA impostando capturexml su **false**.  
  
4.  Verifica del log XMLA acquisito eseguendo l'analisi di ciascuna delle stringhe della raccolta di stringhe di CaptureLog oppure generando una stringa completa con il metodo ConcatenateCaptureLog che consente di generare il batch XMLA come transazione unica e di aggiungere l'opzione per l'elaborazione parallela al batch.  
  
 Nell'esempio seguente viene restituita una stringa con i comandi batch per eseguire un'elaborazione completa su tutte le dimensioni e su tutti i cubi del database [Adventure Works DW Multidimensional 2012].  
  
```  
static public string TestCaptureLog(Server svr)  
{  
    String capturedXmla = "";  
    if ((svr != null) && (svr.Connected))  
    {  
        svr.CaptureXml = true;  
  
        #region Actions to be captured to an XMLA file  
        //No action is executed during CaptureXml = true  
        Database db = svr.Databases.FindByName("Adventure Works DW Multidimensional 2012");  
        foreach (Dimension dim in db.Dimensions)  
            dim.Process(ProcessType.ProcessFull);  
        foreach (Cube cube in db.Cubes)  
            cube.Process(ProcessType.ProcessFull);  
        #endregion  
  
        svr.CaptureXml = false;  
  
        capturedXmla = svr.ConcatenateCaptureLog(true, true);  
  
    }  
  
    return capturedXmla;  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.AnalysisServices>   
 [Introduzione a classi AMO](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-classes-introduction.md)   
 [AMO altri metodi e classi](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-other-classes-and-methods.md)   
 [Architettura logica &#40; Analysis Services - dati multidimensionali &#41;](../../../analysis-services/multidimensional-models/olap-logical/understanding-microsoft-olap-logical-architecture.md)   
 [Gli oggetti di database &#40; Analysis Services - dati multidimensionali &#41;](../../../analysis-services/multidimensional-models/olap-logical/database-objects-analysis-services-multidimensional-data.md)   
 [L'elaborazione di un modello multidimensionale &#40; Analysis Services &#41;](../../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md)  
  
  
