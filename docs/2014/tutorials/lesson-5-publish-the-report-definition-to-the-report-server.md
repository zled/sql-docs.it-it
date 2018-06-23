---
title: 'Lezione 5: Pubblicare la definizione del Report nel Server di Report | Documenti Microsoft'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 57fab70f-4a72-4413-a0ad-d0525caca3f7
caps.latest.revision: 17
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: c7fa1c983ae58fd56450e6182499b105b68a322f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36156114"
---
# <a name="lesson-5-publish-the-report-definition-to-the-report-server"></a>Lezione 5: Pubblicazione della definizione del report nel Server report
  L'ultimo passaggio dell'aggiornamento della definizione del report consiste nella pubblicazione della definizione nel server di report.  
  
### <a name="to-publish-the-report-to-the-report-catalog"></a>Per pubblicare il report nel catalogo dei report  
  
1.  Sostituire il codice per il `PublishReportDefinition()` metodo nel file Program.cs (Module1.vb per [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) con il codice seguente:  
  
    ```csharp  
    private void PublishReportDefinition()  
    {  
        System.Console.WriteLine("Publishing Report Definition");  
  
        string reportPath =  
            "/AdventureWorks 2012 Sample Reports/Company Sales 2012";  
  
        XmlSerializer serializer =  
            new XmlSerializer(typeof(Report));  
  
        using (MemoryStream stream = new MemoryStream())  
        {  
            // Serialize the report into the MemoryStream  
            serializer.Serialize(stream, _report);  
            stream.Position = 0;  
  
            byte[] bytes = stream.ToArray();  
  
            // Update the report on the report server  
            Warning[] warnings =   
                _reportService.SetItemDefinition(reportPath, bytes, null);  
        }  
    }  
    ```  
  
    ```vb  
    Private Sub PublishReportDefinition()  
  
        System.Console.WriteLine("Publishing Report Definition")  
  
        Dim reportPath As String = _  
            "/AdventureWorks 2012 Sample Reports/Company Sales 2012"  
        Dim serializer As XmlSerializer = _  
            New XmlSerializer(GetType(Report))  
  
        Using stream As MemoryStream = New MemoryStream  
  
            'Serialize the report into the MemoryStream  
            serializer.Serialize(stream, m_report)  
            stream.Position = 0  
  
            'Update the report on the report server  
            Dim bytes As Byte() = stream.ToArray  
            Dim warnings As Warning() = _  
                m_reportService.SetItemDefinition(reportPath, bytes, Nothing)  
  
        End Using  
  
    End Sub  
    ```  
  
## <a name="next-lesson"></a>Lezione successiva  
 Nella lezione successiva verrà compilata ed eseguire il `SampleRDLSchema` dell'applicazione. Vedere [lezione 6: eseguire l'applicazione dello Schema RDL &#40;Visual Basic-C&#35;&#41;](../../2014/tutorials/lesson-6-run-the-rdl-schema-application-vb-csharp.md).  
  
## <a name="see-also"></a>Vedere anche  
 [L'aggiornamento di report mediante le classi generate dallo Schema RDL &#40;esercitazione su SSRS&#41;](../../2014/tutorials/updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial.md)   
 [Report Definition Language &#40;SSRS&#41;](../reporting-services/reports/report-definition-language-ssrs.md)  
  
  