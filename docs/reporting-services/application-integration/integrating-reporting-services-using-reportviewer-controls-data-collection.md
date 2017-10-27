---
title: La raccolta dei dati 2016 controllo ReportViewer | Documenti Microsoft
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
caps.latest.revision: 2
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 4e8b0226c27380bd2089acf8d2d6c8d7b27c7c5b
ms.contentlocale: it-it
ms.lasthandoff: 08/09/2017

---
# <a name="integrating-reporting-services-using-reportviewer-controls---data-collection"></a>Integrazione di Reporting Services utilizzando i controlli ReportViewer - raccolta dati
Per impostazione predefinita, il controllo ReportViewer raccoglie informazioni anonime sull'utilizzo affinché Microsoft comprendere meglio come i clienti realizzano utilizzo del controllo. Creando una migliore comprensione di come distribuisce e si utilizza il controllo Visualizzatore clienti, lo sviluppo futuro è possibile implementare sui miglioramenti apportati ai che forniscono il maggior valore ai clienti.

Per una spiegazione delle procedure di raccolta e di trattamento dei dati per le versioni di Microsoft SQL Server 2016 e qualsiasi altro prodotto o servizio, fare riferimento a questa [informativa sulla privacy da Microsoft](https://www.microsoft.com/EN-US/privacystatement/SQLServer/Default.aspx).

## <a name="opting-out-of-telemetry"></a>Rifiuto esplicito della telemetria

Dati di telemetria può essere disabilitata a livello di programmazione tramite "EnableTelemetry". Questa operazione può essere eseguita modificando il file aspx che contiene il controllo

```
\<rsweb:ReportViewer ID="ReportViewer1" runat="server" EnableTelemetry="false">
\</rsweb:ReportViewer>
```

In alternativa, è possibile pragmatically prima del rendering del controllo ad esempio come chiamata Page_Load della pagina di hosting.
    
```
protected void Page_Load(object sender, EventArgs e)
{
    ReportViewer1.EnableTelemetry = false;
}
```
## <a name="see-also"></a>Vedere anche

[Utilizzo del controllo Web Form ReportViewer](../../reporting-services/application-integration/using-the-webforms-reportviewer-control.md)  
[Integrazione di Reporting Services utilizzando i controlli ReportViewer](../../reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls.md) 




