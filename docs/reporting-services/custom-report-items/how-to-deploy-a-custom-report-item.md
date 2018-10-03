---
title: 'Procedura: Distribuire un elemento del report personalizzato | Microsoft Docs'
ms.date: 03/18/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: custom-report-items
ms.topic: reference
helpviewer_keywords:
- custom report items, deploying
ms.assetid: 80e97b0d-e355-4240-aebd-08cbc84089ed
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 6315362b4c8d308e3be8d812ccfdeadaa1e7de8b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47717049"
---
# <a name="how-to-deploy-a-custom-report-item"></a>Procedura: Distribuzione di un elemento del report personalizzato
  Per distribuire un elemento del report personalizzato in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], è necessario modificare i file di configurazione del server di report e copiare gli assembly del componente runtime e della fase di progettazione nelle cartelle appropriate dell'applicazione sia per Progettazione report sia per il server di report.  
  
### <a name="to-deploy-a-custom-report-item"></a>Per distribuire un elemento del report personalizzato  
  
1.  Modificare il file Rsreportdesigner.config per configurare i componenti runtime e della modalità progettazione del report personalizzato da utilizzare nella finestra di progettazione. Si noti che **ReportItemName** deve corrispondere all'attributo **CustomReportItemAttribute** usato nella classe **CustomReportItemDesigner**. Ad esempio  
  
    ```  
    <ReportItems>  
       <ReportItem Name="Polygons" Type="PolygonsCRI.PolygonsCRI,PolygonsCRI"/>  
    </ReportItems>  
    <ReportItemDesigner>  
       <ReportItem Name="Polygons" Type="PolygonsCRI.PolygonsDesigner, PolygonsDesigner" />  
    </ReportItemDesigner>  
    <ReportItemConverter>  
       <Converter Source="Chart" Target="Polygons" Type="PolygonsCRI.PolygonsConverter, PolygonsDesigner" />  
    </ReportItemConverter>  
    ```  
  
2.  Modificare il file Rsreportserver.config per registrare il componente runtime dell'elemento del report personalizzato. Ad esempio  
  
    ```  
    <ReportItems>  
       <ReportItem Name="Polygons" Type="PolygonsCRI.PolygonsCRI,PolygonsCRI"/>  
    </ReportItems>  
    ```  
  
3.  Modificare il file Rsssrvpolicy.config per aggiungere **CodeGroup** che concede le autorizzazioni appropriate all'elemento del report personalizzato. Ad esempio  
  
    ```  
    <CodeGroup   
       class="UnionCodeGroup"   
       version="1"   
       PermissionSetName="FullTrust"  
       Description="This code group grants MyCustomReportItem.dll FullTrust permission. ">  
       <IMembershipCondition   
          class="UrlMembershipCondition"  
          version="1"  
       Url="C:\Program Files\Microsoft SQL Server\ MSRS10_50.SQLSERVER\Reporting Services\ReportServer\bin\MyCustomReportItem.dll" />  
    </CodeGroup>  
    ```  
  
4.  Copiare la DLL del componente runtime dell'elemento del report personalizzato nelle directory %Programmi%\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies e \Programmi\Microsoft SQL Server\MSRS10_50.SQLSERVER\Reporting Services\ReportServer\bin.  
  
5.  Copiare la DLL del componente della modalità progettazione dell'elemento del report personalizzato nella directory %Programmi %\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies.  
  
## <a name="see-also"></a>Vedere anche  
 [File di configurazione di Reporting Services](../../reporting-services/report-server/reporting-services-configuration-files.md)   
 [Librerie di classi dell'elemento del report personalizzato](../../reporting-services/custom-report-items/custom-report-item-class-libraries.md)  
  
  
