---
title: Raccolta dati nel controllo ReportViewer 2016 | Microsoft Docs
ms.custom: ''
ms.date: 09/06/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.component: application-integration
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 112e0240-351d-46a9-98c7-2be09f26ac60
caps.latest.revision: 2
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: bc1edeb74cced8b18275b57deca6b078c13a56d3
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "33013758"
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



