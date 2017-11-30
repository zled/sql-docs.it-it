---
title: Raccolta dati nel controllo ReportViewer 2016 | Microsoft Docs
ms.custom: 
ms.date: 09/06/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 112e0240-351d-46a9-98c7-2be09f26ac60
caps.latest.revision: "2"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: b2f5f4743b838598aeb5f74271fa063af9bb60f3
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="integrating-reporting-services-using-reportviewer-controls---data-collection"></a>Integrazione di Reporting Services tramite i controlli ReportViewer - Raccolta dati
Per impostazione predefinita, il controllo ReportViewer raccoglie informazioni anonime sull'utilizzo affinché Microsoft possa comprendere meglio come i clienti fanno uso del controllo. Con una migliore comprensione di come i clienti distribuiscono e usano il controllo Visualizzatore, lo sviluppo futuro può concentrarsi su miglioramenti in grado di offrire il massimo valore ai clienti.

Per una spiegazione delle procedure di raccolta e di trattamento dei dati per le versioni di Microsoft SQL Server 2016 e qualsiasi altro prodotto o servizio, fare riferimento a questa [informativa sulla privacy da Microsoft](https://www.microsoft.com/EN-US/privacystatement/SQLServer/Default.aspx).

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



