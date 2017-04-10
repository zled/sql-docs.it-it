---
title: "Attivit&#224; Esegui DDL Analysis Services | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.asexecuteddltask.f1"
helpviewer_keywords: 
  - "Esegui DDL Analysis Services - attività"
  - "DDL"
ms.assetid: 7f25c8c6-b601-41f2-9553-be0a2ee0751a
caps.latest.revision: 48
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 48
---
# Attivit&#224; Esegui DDL Analysis Services
  L'attività Esegui DDL [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] consente di eseguire istruzioni DDL (Data Definition Language) in grado di creare, eliminare o modificare modelli di data mining e oggetti multidimensionali, quali cubi e dimensioni. Tramite un'istruzione DDL è ad esempio possibile creare una partizione nel cubo **Adventure Works** o eliminare una dimensione in [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)], il database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] di esempio incluso in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 L'attività Esegui DDL [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] utilizza una gestione connessione [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] per connettersi a un'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] o a un progetto di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Per altre informazioni, vedere [Gestione connessione Analysis Services](../../integration-services/connection-manager/analysis-services-connection-manager.md).  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] include numerose attività che eseguono operazioni di Business Intelligence, ad esempio l'elaborazione di oggetti di analisi e l'esecuzione di query di stima basate su modelli di data mining.  
  
 Per ulteriori informazioni sulle attività di Business Intelligence correlate, fare clic su uno degli argomenti seguenti:  
  
-   [Attività Elaborazione Analysis Services](../../integration-services/control-flow/analysis-services-processing-task.md)  
  
-   [Attività Query di data mining](../../integration-services/control-flow/data-mining-query-task.md)  
  
## Istruzioni DDL  
 Le istruzioni DDL sono rappresentate come istruzioni in ASSL ([!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Scripting Language) e inserite nell'ambito di un comando XMLA (XML for Analysis).  
  
-   Il linguaggio ASSL consente di definire e descrivere un'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], nonché dei database e degli oggetti di database contenuti. Per altre informazioni, vedere [Guida di riferimento ad Analysis Services Scripting Language &#40;ASSL&#41;](../../analysis-services/scripting/analysis-services-scripting-language-assl-for-xmla.md).  
  
-   XMLA è un linguaggio di comando che consente di inviare a un'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] comandi di azione quali Create, Alter o Process. Per altre informazioni, vedere [Guida di riferimento a XML for Analysis &#40;XMLA&#41;](../../analysis-services/xmla/xml-for-analysis-xmla-reference.md).  
  
 Se il codice DDL è archiviato in un file separato, l'attività Esegui DDL [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] userà una gestione connessione file per specificare il percorso del file. Per altre informazioni, vedere [File Connection Manager](../../integration-services/connection-manager/file-connection-manager.md).  
  
 Poiché le istruzioni DDL possono contenere password e altre informazioni sensibili, per i pacchetti che contengono una o più attività Esegui DDL [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] è necessario usare il livello di protezione del pacchetto **EncryptAllWithUserKey** o **EncryptAllWithPassword**. Per altre informazioni, vedere [Pacchetti di Integration Services &#40;SSIS&#41;](../../integration-services/integration-services-ssis-packages.md).  
  
### Esempi di DDL  
 Le tre istruzioni DDL seguenti sono state generate da oggetti di script in [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)], il database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] incluso in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 L'istruzione DDL seguente elimina la dimensione **Promotion**.  
  
```  
<Delete xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
    <Object>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
        <DimensionID>Dim Promotion</DimensionID>  
    </Object>  
</Delete>  
  
```  
  
 L'istruzione DDL seguente elabora il cubo [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)].  
  
```  
<Batch xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
  <Parallel>  
    <Process xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
      <Object>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
      </Object>  
      <Type>ProcessFull</Type>  
      <WriteBackTableCreation>UseExisting</WriteBackTableCreation>  
    </Process>  
  </Parallel>  
</Batch>  
  
```  
  
 L'istruzione DDL seguente crea il modello di data mining **Forecasting**.  
  
```  
<Create xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
    <ParentObject>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
        <MiningStructureID>Forecasting</MiningStructureID>  
    </ParentObject>  
    <ObjectDefinition>  
        <MiningModel xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
            <ID>Forecasting</ID>  
            <Name>Forecasting</Name>  
            <Algorithm>Microsoft_Time_Series</Algorithm>  
            <AlgorithmParameters>  
                <AlgorithmParameter>  
                    <Name>PERIODICITY_HINT</Name>  
                    <Value xsi:type="xsd:string">{12}</Value>  
                </AlgorithmParameter>  
            </AlgorithmParameters>  
            <Columns>  
                <Column>  
                    <ID>Amount</ID>  
                    <Name>Amount</Name>  
                    <SourceColumnID>Amount</SourceColumnID>  
                    <Usage>Predict</Usage>  
                </Column>  
                <Column>  
                    <ID>Model Region</ID>  
                    <Name>Model Region</Name>  
                    <SourceColumnID>Model Region</SourceColumnID>  
                    <Usage>Key</Usage>  
                </Column>  
                <Column>  
                    <ID>Quantity</ID>  
                    <Name>Quantity</Name>  
                    <SourceColumnID>Quantity</SourceColumnID>  
                    <Usage>Predict</Usage>  
                </Column>  
                <Column>  
                    <ID>Time Index</ID>  
                    <Name>Time Index</Name>  
                    <SourceColumnID>Time Index</SourceColumnID>  
                    <Usage>Key</Usage>  
                </Column>  
            </Columns>  
            <Collation>Latin1_General_CS_AS_KS</Collation>  
        </MiningModel>  
    </ObjectDefinition>  
</Create>  
  
```  
  
 Le tre istruzioni DDL seguenti sono state generate da oggetti di script in [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)], il database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] incluso in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 L'istruzione DDL seguente elimina la dimensione **Promotion**.  
  
```  
<Delete xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
    <Object>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
        <DimensionID>Dim Promotion</DimensionID>  
    </Object>  
</Delete>  
  
```  
  
 L'istruzione DDL seguente elabora il cubo [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)].  
  
```  
<Batch xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
  <Parallel>  
    <Process xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
      <Object>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
      </Object>  
      <Type>ProcessFull</Type>  
      <WriteBackTableCreation>UseExisting</WriteBackTableCreation>  
    </Process>  
  </Parallel>  
</Batch>  
  
```  
  
 L'istruzione DDL seguente crea il modello di data mining **Forecasting**.  
  
```  
<Create xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
    <ParentObject>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
        <MiningStructureID>Forecasting</MiningStructureID>  
    </ParentObject>  
    <ObjectDefinition>  
        <MiningModel xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
            <ID>Forecasting</ID>  
            <Name>Forecasting</Name>  
            <Algorithm>Microsoft_Time_Series</Algorithm>  
            <AlgorithmParameters>  
                <AlgorithmParameter>  
                    <Name>PERIODICITY_HINT</Name>  
                    <Value xsi:type="xsd:string">{12}</Value>  
                </AlgorithmParameter>  
            </AlgorithmParameters>  
            <Columns>  
                <Column>  
                    <ID>Amount</ID>  
                    <Name>Amount</Name>  
                    <SourceColumnID>Amount</SourceColumnID>  
                    <Usage>Predict</Usage>  
                </Column>  
                <Column>  
                    <ID>Model Region</ID>  
                    <Name>Model Region</Name>  
                    <SourceColumnID>Model Region</SourceColumnID>  
                    <Usage>Key</Usage>  
                </Column>  
                <Column>  
                    <ID>Quantity</ID>  
                    <Name>Quantity</Name>  
                    <SourceColumnID>Quantity</SourceColumnID>  
                    <Usage>Predict</Usage>  
                </Column>  
                <Column>  
                    <ID>Time Index</ID>  
                    <Name>Time Index</Name>  
                    <SourceColumnID>Time Index</SourceColumnID>  
                    <Usage>Key</Usage>  
                </Column>  
            </Columns>  
            <Collation>Latin1_General_CS_AS_KS</Collation>  
        </MiningModel>  
    </ObjectDefinition>  
</Create>  
  
```  
  
## Configurazione dell'attività Esegui DDL Analysis Services  
 È possibile impostare le proprietà tramite Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] o a livello di codice.  
  
 Per ulteriori informazioni sulle proprietà che è possibile impostare in Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] , fare clic su uno degli argomenti seguenti:  
  
-   [Editor attività Esegui DDL Analysis Services &#40;pagina Generale&#41;](../../integration-services/control-flow/analysis-services-execute-ddl-task-editor-general-page.md)  
  
-   [Editor attività Esegui DDL Analysis Services &#40;pagina DDL&#41;](../../integration-services/control-flow/analysis-services-execute-ddl-task-editor-ddl-page.md)  
  
-   [Pagina Espressioni](../../integration-services/expressions/expressions-page.md)  
  
 Per altre informazioni sull'impostazione di queste proprietà in Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)], fare clic sull'argomento seguente:  
  
-   [Impostazione delle proprietà di un'attività o di un contenitore](../Topic/Set%20the%20Properties%20of%20a%20Task%20or%20Container.md)  
  
## Configurazione dell'attività Esegui DDL Analysis Services a livello di codice  
 Per ulteriori informazioni sull'impostazione di queste proprietà a livello di codice, fare clic sull'argomento seguente:  
  
-   <xref:Microsoft.DataTransformationServices.Tasks.DTSProcessingTask.ASExecuteDDLTask>  
  
  