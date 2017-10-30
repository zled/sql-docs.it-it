---
title: Supporto multitargeting in componenti personalizzati | Documenti Microsoft
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server (starting with 2016)
ms.assetid: ec611374-16bf-4a56-8fd9-45d3ddd7befc
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: dc111f1d884a3553156b55ab490afef2f8df9d61
ms.contentlocale: it-it
ms.lasthandoff: 09/27/2017

---
# <a name="support-multi-targeting-in-your-custom-components"></a>Supporta il multitargeting in componenti personalizzati
 È ora possibile utilizzare Progettazione SSIS in SQL Server Data Tools (SSDT) per creare, gestire ed eseguire i pacchetti di tale destinazione SQL Server 2016, SQL Server 2014 o SQL Server 2012. Per ottenere SSDT per Visual Studio 2015, vedere [Download più recenti SQL Server Data Tools](../../ssdt/download-sql-server-data-tools-ssdt.md). 

 In Esplora soluzioni fare clic con il pulsante destro del mouse su un progetto di Integration Services e scegliere **Proprietà** per aprire le pagine delle proprietà per il progetto. Nella scheda **Generale** di **Proprietà di configurazione**selezionare la proprietà **TargetServerVersion** , quindi scegliere SQL Server 2016, SQL Server 2014 o SQL Server 2012.  
   
 ![La proprietà TargetServerVersion nella finestra di dialogo Proprietà progetto](../../integration-services/media/targetserverversion2.png "proprietà TargetServerVersion nella finestra di dialogo Proprietà progetto")  
 
 ## <a name="multiple-version-support-and-multi-targeting-for-custom-components"></a>Supporto delle versioni più e funzionalità di multitargeting per i componenti personalizzati
 
Tutti i cinque tipi di estensioni personalizzate di SSIS supportano il multitargeting.
-   Gestioni connessioni
-   Attività
-   Enumeratori
-   Provider di log
-   Componenti del flusso di dati

Per le estensioni gestite, Progettazione SSIS carica la versione dell'estensione per la versione di destinazione specificato. Esempio:
-   Quando la versione di destinazione è SQL Server 2012, la finestra di progettazione carica la versione 2012 dell'estensione.
-   Quando la versione di destinazione è SQL Server 2016, la finestra di progettazione carica la versione di 2016 dell'estensione.

Le estensioni COM non supportano la funzionalità di multitargeting. Progettazione SSIS Carica sempre l'estensione di COM per la versione corrente di SQL Server, indipendentemente dalla versione di destinazione specificato.

## <a name="add-basic-support-for-multiple-versions-and-multi-targeting"></a>Aggiungere il supporto di base per più versioni e funzionalità di multitargeting

Per linee guida di base, vedere [ottenere estensioni SSIS personalizzate devono essere supportati dal supporto di più versioni di 2015 di SSDT per SQL Server 2016](https://blogs.msdn.microsoft.com/ssis/2016/04/19/getting-your-ssis-custom-extensions-to-be-supported-by-the-multi-version-support-of-ssdt-2015-for-sql-server-2016/). Questo post di blog vengono descritti i passaggi o i requisiti seguenti.

-   Distribuire gli assembly nelle cartelle appropriate.

-   Creare un file con estensione map per SQL Server 2014 e versioni elevate.

## <a name="add-code-to-switch-versions"></a>Aggiungere il codice per passare le versioni

### <a name="switch-versions-in-a-custom-connection-manager-task-enumerator-or-log-provider"></a>Versioni di opzione in una gestione connessione personalizzata, attività, l'enumeratore o provider di log

Per una gestione connessione personalizzata, attività, l'enumeratore o provider di log, aggiungere logica di downgrade di **SaveToXML** metodo.

```csharp
public void SaveToXML(XmlDocument doc, IDTSInfoEvents events)
{
    if (TargetServerVersion == DTSTargetServerVersion.SQLServer2014)
    {
        // Add logic to downgrade from SQL Server 2016 to SQL Server 2014.
    }

    if (TargetServerVersion == DTSTargetServerVersion.SQLServer2012)
    {
         // Add logic to downgrade from SQL Server 2016 to SQL Server 2012.
    }
}
```

### <a name="switch-versions-in-a-custom-data-flow-component"></a>Versioni di opzione in un componente flusso di dati personalizzati

Per una gestione connessione personalizzata, attività, l'enumeratore o provider di log, aggiungere la logica di downgrade nel nuovo **PerformDowngrade** metodo.

```csharp
public override void PerformDowngrade(int pipelineVersion, DTSTargetServerVersion targetServerVersion)
{
    if (targetServerVersion == DTSTargetServerVersion.DTSTSV_SQLSERVER2014)
    {
        // Add logic to downgrade from SQL Server 2016 to SQL Server 2014.
        ComponentMetaData.Version = 8;
    }

    if (targetServerVersion == DTSTargetServerVersion.DTSTSV_SQLSERVER2012)
    {
          // Add logic to downgrade from SQL Server 2016 to SQL Server 2012.
        ComponentMetaData.Version = 6;
    }
}
```

## <a name="common-errors"></a>Errori comuni

### <a name="invalidcastexception"></a>InvalidCastException

**Messaggio di errore.** Impossibile oggetto COM di cast di tipo 'Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100' di tipo 'REC0 ComObject' interfaccia. Questa operazione non riuscita perché la chiamata QueryInterface sul componente COM per l'interfaccia con IID '{BE8C48A3-155B-4810-BA5C-BDF68A659E9E}' non è riuscita a causa del seguente errore: interfaccia non supportata (eccezione da HRESULT: 0x80004002 (E_NOINTERFACE)). (Dtspipelinewrap).

**Soluzione.** Se l'estensione personalizzata fa riferimento all'assembly di interoperabilità di SSIS, ad esempio dtspipelinewrap o dtsruntimewrap, impostare il valore della **incorpora tipi di interoperabilità** proprietà * * False ".

![Tipi di interoperabilità incorporati](../../integration-services/extending-packages-custom-objects/media/embed-interop-types.png)

### <a name="unable-to-load-some-types-when-target-version-is-sql-server-2012"></a>Impossibile caricare alcuni tipi quando la versione di destinazione è SQL Server 2012

Questo problema interessa determinati tipi, ad esempio IErrorReportingService o IUserPromptService.

**Messaggio di errore (ad esempio).** Impossibile caricare il tipo 'Microsoft.DataWarehouse.Design.IErrorReportingService' dall'assembly ' Microsoft.DataWarehouse, Version = 13.0.0.0, Culture = neutral, PublicKeyToken = 89845dcd8080cc91 ".

**Soluzione alternativa.** Utilizzare un database MessageBox anziché queste interfacce quando la versione di destinazione è SQL Server 2012.


