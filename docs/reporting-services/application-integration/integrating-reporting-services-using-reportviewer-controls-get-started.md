---
title: Introduzione al controllo ReportViewer 2016 |Microsoft Docs
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
caps.latest.revision: "12"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Active
ms.openlocfilehash: dff598efce33f778359c2b6fb4c3a0184f2b88f6
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="integrating-reporting-services-using-reportviewer-controls---get-started"></a>Integrazione di Reporting Services tramite i controlli ReportViewer - Introduzione

Informazioni su come gli sviluppatori possono incorporare report impaginati in siti Web ASP.NET e app di Windows Form, tramite il controllo ReportViewer di Reporting Services 2016. È possibile aggiungere il controllo a un nuovo progetto o aggiornare un progetto esistente.

## <a name="adding-the-reportviewer-control-to-a-new-web-project"></a>Aggiunta del controllo ReportViewer a un nuovo progetto Web

1. Creare un nuovo **sito Web ASP.NET vuoto** o aprire un progetto ASP.NET esistente.

    ![ssRS-Create-New-ASPNET-Project](../../reporting-services/application-integration/media/ssrs-create-new-aspnet-project.png)

2. Installare il pacchetto NuGet del controllo ReportViewer 2016 tramite la **console di Gestione pacchetti NuGet**.

    ```
    Install-Package Microsoft.ReportingServices.ReportViewerControl.WebForms
    ```
3. Aggiungere una nuova pagina ASPX al progetto e registrare l'assembly del controllo ReportViewer per l'uso all'interno della pagina.

    ```
    <%@ Register assembly="Microsoft.ReportViewer.WebForms, Version=14.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91" namespace="Microsoft.Reporting.WebForms" tagprefix="rsweb" %>
    ```
    
4. Aggiungere uno **ScriptManagerControl** alla pagina.

5. Aggiungere il controllo ReportViewer alla pagina. Il frammento seguente può essere aggiornato per fare riferimento a un report ospitato in un server di report remoto.

    ```
    <rsweb:ReportViewer ID="ReportViewer1" runat="server" ProcessingMode="Remote">
      <ServerReport ReportPath="" ReportServerUrl="" />
    </rsweb:ReportViewer>
    ```
    
La pagina finale sarà simile alla seguente.

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

## <a name="updating-an-existing-project-to-use-the-reportviewer-control"></a>Aggiornamento di un progetto esistente per usare il controllo ReportViewer

Per usare il controllo ReportViewer 2016 in un progetto esistente, aggiungere il controllo tramite NuGet e aggiornare i riferimenti all'assembly alla versione *14.0.0.0*. Ciò include l'aggiornamento del file web.config del progetto e di tutte le pagine ASPX che fanno riferimento al controllo ReportViewer.

### <a name="sample-webconfig-changes"></a>Modifiche del file web.config di esempio

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

### <a name="sample-aspx"></a>Pagina ASPX di esempio

```
<%@ Page Language="C#" AutoEventWireup="true" CodeBehind="WebForm1.aspx.cs" Inherits="SampleAspx" %>

<!-- Update version to 14.0.0.0 -->
<%@ Register assembly="Microsoft.ReportViewer.WebForms, Version=14.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91" namespace="Microsoft.Reporting.WebForms" tagprefix="rsweb" %>

<!DOCTYPE html>
```

## <a name="adding-the-reportviewer-control-to-a-new-windows-forms-project"></a>Aggiunta del controllo ReportViewer a un nuovo progetto Windows Forms

1. Creare una nuova **applicazione Windows Forms** o aprire un progetto esistente.

    ![ssRS-Create-New-winforms-Project](../../reporting-services/application-integration/media/ssrs-create-new-winforms-project.png)

2. Installare il pacchetto NuGet del controllo ReportViewer 2016 tramite la **console di Gestione pacchetti NuGet**.

    ```
    Install-Package Microsoft.ReportingServices.ReportViewerControl.WinForms
    ```
3. Aggiungere un nuovo controllo dal codice o [aggiungere il controllo alla casella degli strumenti](##adding-control-to-visual-studio-toolbar).

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

## <a name="how-to-set-100-height-on-the-report-viewer-2016-control"></a>Come impostare l'altezza 100% sul controllo ReportViewer 2016

Il nuovo controllo ReportViewer 2016 è ottimizzato per le pagine in modalità standard HTML5 e funziona su tutti i browser moderni. In passato, con il controllo RVC precedente, quando si impostava la proprietà altezza 100% funzionava anche se nessuno dei predecessori aveva l'altezza specificata. Questo comportamento è stato modificato in HTML5. Quando si imposta questa proprietà sul nuovo controllo RVC, funzionerà correttamente solo se l'elemento padre avrà un'altezza definita, vale a dire un valore diverso da auto, o se anche tutti i predecessori di RVC avranno un'altezza 100%.

I due esempi seguenti illustrano questa operazione.

### <a name="by-setting-the-height-of-all-the-parent-elements-to-100"></a>Tramite l'impostazione dell'altezza di tutti gli elementi padre al 100%

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

### <a name="by-setting-the-style-height-attribute-on-the-parent-of-the-reportviewer-control"></a>Tramite l'impostazione dell'attributo di stile dell'altezza nell'elemento padre del controllo reportviewer

Per altre informazioni sulle lunghezze percentuali di Viewport, vedere [Viewport-percentage lengths](https://www.w3.org/TR/css3-values/#viewport-relative-lengths) (Viewport-lunghezze percentuali).

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

## <a name="adding-control-to-visual-studio-toolbar"></a>Aggiunta del controllo alla barra degli strumenti di Visual Studio

Il controllo ReportViewer è ora disponibile come pacchetto NuGet. Per questo motivo, il controllo ReportViewer non viene visualizzato nella casella degli strumenti di Visual Studio per impostazione predefinita. È possibile aggiungere il controllo alla casella degli strumenti nel modo seguente.

1. Installare il pacchetto NuGet per Windows Form o Web Form, come indicato in precedenza.

2. Rimuovere il controllo ReportViewer elencato nella casella degli strumenti. Si tratta del controllo versione 12.x.

    ![ssRS-remove-old-rvcontrol-toolbox](../../reporting-services/application-integration/media/ssrs-remove-old-rvcontrol-toolbox.png)

3. Fare clic con il pulsante destro del mouse in un punto qualsiasi della casella degli strumenti e scegliere **Scegli elementi**.

    ![ssRS-toolbox-choose-item](../../reporting-services/application-integration/media/ssrs-toolbox-choose-item.png)
    
4. In **Componenti di .NET Framework** selezionare **Sfoglia**.

    ![ssRS-toolbox-browse](../../reporting-services/application-integration/media/ssrs-toolbox-browse.png)

5. Selezionare il file **Microsoft.ReportViewer.WinForms.dll** o **Microsoft.ReportViewer.WebForms.dll** dal pacchetto NuGet installato.

    > [!NOTE] 
    > Il pacchetto NuGet verrà installato nella directory della soluzione del progetto. Il percorso al file DLL sarà simile al seguente: `{Solution Directory}\packages\Microsoft.ReportingServices.ReportViewerControl.Winforms.{version}\lib\net40` o `{Solution Directory}\packages\Microsoft.ReportingServices.ReportViewerControl.WebForms.{version}\lib\net40`.

6. Il nuovo controllo viene visualizzato all'interno della casella degli strumenti. È quindi possibile spostarlo in un'altra scheda all'interno della casella degli strumenti se necessario.

    ![ssRS-toolbox-rvcontrol](../../reporting-services/application-integration/media/ssrs-toolbox-rvcontrol.png)

### <a name="things-to-be-aware-of"></a>Aspetti da tenere presenti

- Con questa operazione verrà aggiunto un riferimento al pacchetto NuGet installato all'interno del progetto corrente. L'elemento nella casella degli strumenti verrà mantenuto negli altri progetti. Quando si installa il pacchetto NuGet in una nuova soluzione o progetto, l'elemento della casella degli strumenti può fare riferimento a una versione precedente. 

- Il controllo rimane nella casella degli strumenti anche se l'assembly non è più disponibile. Se il progetto è stato eliminato, Visual Studio genera un errore se si tenta di aggiungere il controllo dalla casella degli strumenti. Per correggere l'errore, rimuovere il controllo dalla casella degli strumenti e aggiungerlo di nuovo usando la procedura descritta sopra.


## <a name="common-issues"></a>Problemi comuni
    
- Il controllo ReportViewer 2016 è progettato per essere usato con i browser moderni. Il controllo potrebbe non funzionare se i browser eseguono il rendering della pagina Web in una modalità di compatibilità di Internet Explorer. I siti Intranet potrebbero richiedere un tag META per sostituire le impostazioni che incoraggiano il rendering delle pagine Intranet in modalità di compatibilità.

    ```
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    ```
      
## <a name="providing-feedback"></a>Invio di commenti

Informare il team sui problemi riscontrati con il controllo sui [forum MSDN su Reporting Services](https://social.msdn.microsoft.com/Forums/sqlserver/home?forum=sqlreportingservices) o tramite posta elettronica all'indirizzo [RVCFeedback@microsoft.com](mailto:RVCFeedback@microsoft.com).

## <a name="see-also"></a>Vedere anche

[Raccolta di dati nel controllo ReportingViewer 2016](../../reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls-data-collection.md)  
Altre domande? [Visitare il forum su Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)

