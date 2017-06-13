---
title: Introduzione al controllo ReportViewer 2016 | Documenti Microsoft
ms.custom: 
ms.date: 06/12/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
- reporting-services-sharepoint
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 01a821c4-2920-400c-be03-93d26c749bb1
caps.latest.revision: 12
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: a6a0bbee9141df565966df3e90f396e33c9b96a7
ms.contentlocale: it-it
ms.lasthandoff: 06/13/2017

---
# <a name="integrating-reporting-services-using-reportviewer-controls---get-started"></a>L'integrazione di Reporting Services utilizzando i controlli ReportViewer - introduzione

Informazioni su come gli sviluppatori possono incorporare report impaginati in siti web ASP.Net e le applicazioni di Windows forms, tramite il controllo ReportViewer di Reporting Services 2016. È possibile aggiungere il controllo a un progetto nuovo o aggiornare un progetto esistente.

## <a name="adding-the-reportviewer-control-to-a-new-web-project"></a>Aggiunta del controllo ReportViewer a un nuovo progetto web

1. Creare un nuovo **sito Web ASP.NET vuoto** o aprire un progetto ASP.NET esistente.

    ![Creare-nuova-ASPNET-progetto ssRS](../../reporting-services/application-integration/media/ssrs-create-new-aspnet-project.png)

2. Installare il pacchetto nuget di controllo ReportViewer 2016 tramite il **console di gestione pacchetti Nuget**.

    ```
    Install-Package Microsoft.ReportingServices.ReportViewerControl.WebForms -Pre
    ```
3. Aggiungere una nuova pagina aspx al progetto e registrare l'assembly del controllo ReportViewer per l'utilizzo all'interno della pagina.

    ```
    <%@ Register assembly="Microsoft.ReportViewer.WebForms, Version=14.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91" namespace="Microsoft.Reporting.WebForms" tagprefix="rsweb" %>
    ```
    
4. Aggiungere un **ScriptManagerControl** alla pagina.

5. Aggiungere il controllo ReportViewer alla pagina. Nel frammento seguente può essere aggiornato per fare riferimento a un report ospitato in un server di report remoto.

    ```
    <rsweb:ReportViewer ID="ReportViewer1" runat="server" ProcessingMode="Remote">
      <ServerReport ReportPath="" ReportServerUrl="" />
    </rsweb:ReportViewer>
    ```
    
Nella pagina finale dovrebbe essere simile al seguente.

```
<%@ Page Language="C#" AutoEventWireup="true" CodeBehind="WebForm1.aspx.cs" Inherits="Sample" %>

<%@ Register assembly="Microsoft.ReportViewer.WebForms, Version=14.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91" namespace="Microsoft.Reporting.WebForms" tagprefix="rsweb" %>

<!DOCTYPE html>

<html xmlns="http://www.w3.org/1999/xhtml">
<head runat="server">
    <meta http-equiv="X-UA-Compatible" content="IE=edge" /> 
    <title></title>
</head>
<body>
    <form id="form1" runat="server">
    <asp:ScriptManager runat="server"></asp:ScriptManager>        
        <rsweb:ReportViewer ID="ReportViewer1" runat="server" ProcessingMode="Remote">
            <ServerReport ReportServerUrl="http://AContosoDepartment/ReportServer" ReportPath="/LatestSales" />
        </rsweb:ReportViewer>
    </form>
</body>
</html>

```

## <a name="updating-an-existing-project-to-use-the-reportviewer-control"></a>Aggiornamento di un progetto esistente per utilizzare il controllo ReportViewer

Per rendere l'utilizzo del controllo ReportViewer 2016 in un progetto esistente, aggiungere il controllo tramite Nuget e aggiornare i riferimenti all'assembly alla versione *14.0.0.0*. Ciò include l'aggiornamento di Web. config del progetto e tutte le pagine aspx che fa riferimento il controllo ReportViewer.

### <a name="sample-webconfig-changes"></a>Modifiche di Web. config di esempio

```
<?xml version="1.0"?>
<!--
  For more information on how to configure your ASP.NET application, please visit
  http://go.microsoft.com/fwlink/?LinkId=169433
  -->
<configuration>
  <system.web>
    <compilation debug="true" targetFramework="4.5.2">
      <assemblies>
        <!-- All assemblies updated to version 14.0.0.0. -->
        <add assembly="Microsoft.ReportViewer.Common, Version=14.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"/>
        <add assembly="Microsoft.ReportViewer.DataVisualization, Version=14.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"/>
        <add assembly="Microsoft.ReportViewer.Design, Version=14.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"/>
        <add assembly="Microsoft.ReportViewer.ProcessingObjectModel, Version=14.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"/>
        <add assembly="Microsoft.ReportViewer.WebDesign, Version=14.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"/>
        <add assembly="Microsoft.ReportViewer.WebForms, Version=14.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"/>
        <add assembly="Microsoft.ReportViewer.WinForms, Version=14.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"/>
      </assemblies>
      <buildProviders>
        <!-- Version updated to 14.0.0.0. -->
        <add extension=".rdlc"
          type="Microsoft.Reporting.RdlBuildProvider, Microsoft.ReportViewer.WebForms, Version=14.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"/>
      </buildProviders>
    </compilation>
    <httpRuntime targetFramework="4.5.2"/>
    <httpHandlers>
      <!-- Version updated to 14.0.0.0 -->
      <add path="Reserved.ReportViewerWebControl.axd" verb="*"
        type="Microsoft.Reporting.WebForms.HttpHandler, Microsoft.ReportViewer.WebForms, Version=14.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"
        validate="false"/>
    </httpHandlers>
  </system.web>
  <system.webServer>
    <validation validateIntegratedModeConfiguration="false"/>
    <modules runAllManagedModulesForAllRequests="true"/>
    <handlers>
      <!-- Version updated to 14.0.0.0 -->
      <add name="ReportViewerWebControlHandler" verb="*" path="Reserved.ReportViewerWebControl.axd" preCondition="integratedMode"
        type="Microsoft.Reporting.WebForms.HttpHandler, Microsoft.ReportViewer.WebForms, Version=14.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"/>
    </handlers>
  </system.webServer>
</configuration>
```

### <a name="sample-aspx"></a>Esempio con estensione aspx

```
<%@ Page Language="C#" AutoEventWireup="true" CodeBehind="WebForm1.aspx.cs" Inherits="SampleAspx" %>

<!-- Update version to 14.0.0.0 -->
<%@ Register assembly="Microsoft.ReportViewer.WebForms, Version=14.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91" namespace="Microsoft.Reporting.WebForms" tagprefix="rsweb" %>

<!DOCTYPE html>
```

## <a name="adding-the-reportviewer-control-to-a-new-windows-forms-project"></a>Aggiunta del controllo ReportViewer a un nuovo progetto Windows Form

1. Creare un nuovo **Windows Forms Application** o aprire un progetto esistente.

    ![Creare-nuova-winforms-progetto ssRS](../../reporting-services/application-integration/media/ssrs-create-new-winforms-project.png)

2. Installare il pacchetto nuget di controllo ReportViewer 2016 tramite il **console di gestione pacchetti Nuget**.

    ```
    Install-Package Microsoft.ReportingServices.ReportViewerControl.WinForms -Pre
    ```
3. Aggiungere un nuovo controllo dal codice o [aggiungere il controllo della casella degli strumenti](##adding-control-to-visual-studio-toolbar).

    ```
    private Microsoft.Reporting.WinForms.ReportViewer reportViewer1;
    
    private void InitializeComponent()
    {
        this.reportViewer1 = new Microsoft.Reporting.WinForms.ReportViewer();
        this.SuspendLayout();
        // 
        // reportViewer1
        // 
        this.reportViewer1.Location = new System.Drawing.Point(168, 132);
        this.reportViewer1.Name = "reportViewer1";
        this.reportViewer1.ServerReport.BearerToken = null;
        this.reportViewer1.Size = new System.Drawing.Size(396, 246);
        this.reportViewer1.TabIndex = 0;
        // 
        // Form1
        // 
        this.Controls.Add(this.reportViewer1);
    }
    ```

## <a name="how-to-set-100-height-on-the-report-viewer-2016-control"></a>Come impostare l'altezza di 100% sul controllo Report Viewer 2016

Il nuovo controllo Report Viewer 2016 è ottimizzato per pagine in modalità standard di HTML5 e funziona su tutti i browser moderni. In passato, con il controllo RVC precedente, quando si imposta la proprietà height di 100%, funzionava anche se nessuno dei progenitori altezza specificata. Questo comportamento è cambiato in HTML5. Quando si imposta questa proprietà sul nuovo controllo RVC, funzionerà correttamente solo se l'elemento padre ha un'altezza definita, ad esempio, non un valore di auto o tutti i relativi predecessori RVC sono disponibili altezza 100%.

Di seguito sono i due esempi per eseguire questa operazione.

### <a name="by-setting-the-height-of-all-the-parent-elements-to-100"></a>Impostando l'altezza del padre tutti gli elementi al 100%

```
<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml">
<head runat="server">
    <style>
        html,body,form,#div1 {
            height: 100%; 
        }
    </style>
   </head>
<body>
    <form id="form1" runat="server">
    <div id="div1" >
            <asp:ScriptManager runat="server"></asp:ScriptManager>
        <rsweb:ReportViewer ID="ReportViewer1" runat="server" ProcessingMode="Remote" Height="100%" Width="100%">
            <ServerReport ReportServerUrl="http://test/ReportServer" ReportPath="/testreport" />
        </rsweb:ReportViewer>
    </div>
    </form>
</body>
</html>

```

### <a name="by-setting-the-style-height-attribute-on-the-parent-of-the-reportviewer-control"></a>Impostando l'attributo di stile altezza nell'elemento padre del controllo reportviewer

Per ulteriori informazioni sulle lunghezze percentuale viewport, vedere [Viewport percentuale lunghezze](https://www.w3.org/TR/css3-values/#viewport-relative-lengths).

```
<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml">
<head runat="server">
</head>
<body>
    <form id="form1" runat="server">
    <div style="height:100vh;">
            <asp:ScriptManager runat="server"></asp:ScriptManager>
        <rsweb:ReportViewer ID="ReportViewer1" runat="server" ProcessingMode="Remote" Height="100%" Width="100%">
            <ServerReport ReportServerUrl="http://test/ReportServer" ReportPath="/testreport" />
        </rsweb:ReportViewer>
    </div>
    </form>
</body>
</html>

```

## <a name="adding-control-to-visual-studio-toolbar"></a>Aggiunta controllo alla barra degli strumenti di Visual Studio

Il controllo Visualizzatore Report è ora disponibile come pacchetto NuGet. Per questo motivo, non noterai controllo Visualizzatore di Report visualizzati nella casella degli strumenti di Visual Studio per impostazione predefinita. È possibile aggiungere il controllo alla casella degli strumenti nel modo seguente.

1. Installare il pacchetto NuGet per Windows Form o Web Form, come indicato in precedenza.

2. Rimuovere il controllo ReportViewer che è elencato nella casella degli strumenti. Questo è il controllo con una versione di 12.x.

    ![ssRS-remove-vecchio-rvcontrol-della casella degli strumenti](../../reporting-services/application-integration/media/ssrs-remove-old-rvcontrol-toolbox.png)

3. Fare clic in un punto qualsiasi nella casella degli strumenti e quindi selezionare **Scegli elementi...** .

    ![ssRS--scegliere-elemento](../../reporting-services/application-integration/media/ssrs-toolbox-choose-item.png)
    
4. Nel **componenti .NET Framework**selezionare **Sfoglia**.

    ![ssRS: casella degli strumenti-Sfoglia](../../reporting-services/application-integration/media/ssrs-toolbox-browse.png)

5. Selezionare il **Microsoft.ReportViewer.WinForms.dll** o **Microsoft.ReportViewer.WebForms.dll** dal pacchetto NuGet è installato.

    > [!NOTE] 
    > Il pacchetto NuGet verrà installato nella directory della soluzione del progetto. Il percorso della DLL sarà simile al seguente: `{Solution Directory}\packages\Microsoft.ReportingServices.ReportViewerControl.Winforms.{version}\lib\net40` o `{Solution Directory}\packages\Microsoft.ReportingServices.ReportViewerControl.WebForms.{version}\lib\net40`.

6. Il nuovo controllo deve essere visualizzato all'interno della casella degli strumenti. È possibile quindi spostarlo in un'altra scheda all'interno della casella degli strumenti se si desidera.

    ![ssRS: casella degli strumenti-rvcontrol](../../reporting-services/application-integration/media/ssrs-toolbox-rvcontrol.png)

### <a name="things-to-be-aware-of"></a>Aspetti da tenere presenti

- Verrà aggiunto un riferimento per il pacchetto NuGet installato all'interno del progetto corrente. L'elemento della casella degli strumenti verrà mantenuti in altri progetti. Quando si installa il pacchetto NuGet in un nuova soluzione/progetto, l'elemento della casella degli strumenti può fare riferimento a una versione precedente. 

- Il controllo rimane nella casella degli strumenti anche se l'assembly non è più disponibile. Se è stato eliminato il progetto, Visual Studio genererà un errore se si prova e aggiungere il controllo dalla casella degli strumenti. Per correggere l'errore, rimuovere il controllo dalla casella degli strumenti e aggiungerlo di nuovo utilizzando la procedura descritta sopra.


## <a name="common-issues"></a>Problemi comuni
    
- Il controllo ReportViewer 2016 è progettato per essere utilizzato con i browser moderni. Il controllo potrebbe non funzionare se browser esegue il rendering della pagina web in una modalità di compatibilità di Internet Explorer. I siti Intranet richieda un tag meta per sostituire le impostazioni che incoraggia la collaborazione il rendering di pagine intranet in modalità di compatibilità.

    ```
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    ```
      
## <a name="providing-feedback"></a>Inviare commenti e suggerimenti

Informare il team sui problemi riscontrati con il controllo sul [forum di Reporting Services MSDN](https://social.msdn.microsoft.com/Forums/sqlserver/home?forum=sqlreportingservices) o tramite posta elettronica al [ RVCFeedback@microsoft.com ](mailto:RVCFeedback@microsoft.com).

## <a name="see-also"></a>Vedere anche

[Raccolta dei dati nel controllo ReportingViewer 2016](../../reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls-data-collection.md)  
Ulteriori domande? [Provare il forum di Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)


