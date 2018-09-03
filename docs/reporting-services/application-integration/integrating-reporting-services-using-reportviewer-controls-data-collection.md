---
title: Raccolta dati nel controllo ReportViewer 2016 | Microsoft Docs
ms.date: 09/06/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: application-integration
ms.suite: pro-bi
ms.topic: reference
ms.assetid: 112e0240-351d-46a9-98c7-2be09f26ac60
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 782888c9946fd09d9c711a6eda2a8f77fd18c3ba
ms.sourcegitcommit: d96b94c60d88340224371926f283200496a5ca64
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/30/2018
ms.locfileid: "43267406"
---
# <a name="integrating-reporting-services-using-reportviewer-controls---data-collection"></a>Integrazione di Reporting Services tramite i controlli ReportViewer - Raccolta dati
Per impostazione predefinita, il controllo ReportViewer raccoglie informazioni anonime sull'utilizzo affinché Microsoft possa comprendere meglio come i clienti fanno uso del controllo. Con una migliore comprensione di come i clienti distribuiscono e usano il controllo Visualizzatore, lo sviluppo futuro può concentrarsi su miglioramenti in grado di offrire il massimo valore ai clienti.

Per una spiegazione delle procedure di raccolta e di trattamento dei dati per le versioni di Microsoft SQL Server 2016 e qualsiasi altro prodotto o servizio, fare riferimento a questa [informativa sulla privacy]((http://go.microsoft.com/fwlink/?LinkID=868444)).

## <a name="opting-out-of-telemetry"></a>Rifiuto esplicito della telemetria

La telemetria può essere disabilitata a livello di codice tramite "EnableTelemetry". Questa operazione può essere eseguita modificando la pagina con estensione aspx che contiene il controllo

```
\<rsweb:ReportViewer ID="ReportViewer1" runat="server" EnableTelemetry="false">
\</rsweb:ReportViewer>
```

In alternativa, è possibile eseguirla concretamente prima del rendering del controllo, ad esempio nella chiamata Page_Load della pagina di hosting.
    
```
protected void Page_Load(object sender, EventArgs e)
{
    ReportViewer1.EnableTelemetry = false;
}
```
## <a name="see-also"></a>Vedere anche

[Uso del controllo Web Form ReportViewer](../../reporting-services/application-integration/using-the-webforms-reportviewer-control.md)  
[Integrazione di Reporting Services tramite i controlli ReportViewer](../../reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls.md) 



