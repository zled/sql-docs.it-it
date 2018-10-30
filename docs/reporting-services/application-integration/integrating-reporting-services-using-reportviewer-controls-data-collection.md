---
title: Raccolta dati nel controllo ReportViewer 2016 | Microsoft Docs
ms.date: 09/18/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: application-integration
ms.topic: reference
ms.assetid: 112e0240-351d-46a9-98c7-2be09f26ac60
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 69cc665274d7463982cdfddd32d2b979e25a156e
ms.sourcegitcommit: 3daacc4198918d33179f595ba7cd4ccb2a13b3c0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/25/2018
ms.locfileid: "50028150"
---
# <a name="integrating-reporting-services-using-reportviewer-controls---data-collection"></a>Integrazione di Reporting Services tramite i controlli ReportViewer - Raccolta dati

Il controllo raccoglie dati di utilizzo anonimi per una miglior interpretazione delle modalità d'uso del prodotto da parte dei clienti. I dati di utilizzo consentono di concentrare le fasi di sviluppo future sui miglioramenti più importanti per i clienti.

Una spiegazione delle procedure di raccolta e utilizzo dei dati di Microsoft SQL Server e Visualizzatore report è disponibile nell'[Informativa sulla privacy](https://go.microsoft.com/fwlink/?LinkID=868444).

## <a name="opting-out-of-data-collection"></a>Rifiuto esplicito della raccolta dati

È possibile disabilitare la raccolta dei dati di utilizzo tramite la proprietà ```EnableTelemetry```.

```
<rsweb:ReportViewer ID="ReportViewer1" runat="server" EnableTelemetry="false">
</rsweb:ReportViewer>
```

In alternativa è possibile disabilitarla direttamente prima del rendering del controllo.
    
```
protected void Page_Load(object sender, EventArgs e)
{
    ReportViewer1.EnableTelemetry = false;
}
```
## <a name="see-also"></a>Vedere anche

[Uso del controllo Web Form Visualizzatore report](../../reporting-services/application-integration/using-the-webforms-reportviewer-control.md)  
[Integrazione di Reporting Services tramite i controlli Visualizzatore report](../../reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls.md) 



