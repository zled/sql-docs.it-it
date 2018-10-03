---
title: 'Lezione 3: Caricare una definizione del Report dal Server di Report | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 5ad8b31c-43b0-4481-a31b-090cbed4a438
author: craigg-msft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 17d53c7a49afc61d3e43606ac3f805a5b21e6bd5
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48208151"
---
# <a name="lesson-3-load-a-report-definition-from-the-report-server"></a>Lezione 3: Caricamento della definizione di un report dal Server report
  Dopo aver creato il progetto e generato le classi dallo schema RDL, è possibile caricare la definizione di un report dal server di report.  
  
### <a name="to-load-a-report-definition"></a>Per caricare la definizione di un report  
  
1.  Aggiungere un campo privato in cima il `ReportUpdater` classe (modulo se si usa [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) per il `Report` classe. Questo campo verrà utilizzato per mantenere un riferimento al report caricato dal server di report per tutta la durata dell'applicazione.  
  
    ```csharp  
    private Report _report;  
    ```  
  
    ```vb  
    Private m_report As Report  
    ```  
  
2.  Sostituire il codice per il metodo `LoadReportDefinition()` nel file Program.cs (Module1.vb per [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) con il codice seguente:  
  
    ```csharp  
    private void LoadReportDefinition()  
    {  
        System.Console.WriteLine("Loading Report Definition");  
  
        string reportPath =   
            "/AdventureWorks 2012 Sample Reports/Company Sales 2012";  
  
        // Retrieve the report defintion   
        // from the report server  
        byte[] bytes =   
            _reportService.GetItemDefinition(reportPath);  
  
        if (bytes != null)  
        {  
            XmlSerializer serializer =   
                new XmlSerializer(typeof(Report));  
  
            // Load the report bytes into a memory stream  
            using (MemoryStream stream = new MemoryStream(bytes))  
            {  
                // Deserialize the report stream to an   
                // instance of the Report class  
                _report = (Report)serializer.Deserialize(stream);  
            }  
        }  
    }  
    ```  
  
    ```vb  
    Private Sub LoadReportDefinition()  
  
        System.Console.WriteLine("Loading Report Definition")  
  
        Dim reportPath As String = _  
            "/AdventureWorks 2012 Sample Reports/Company Sales 2012"  
  
        'Retrieve the report defintion   
        'from the report server  
        Dim bytes As Byte() = _  
            m_reportService.GetItemDefinition(reportPath)  
  
        If Not (bytes Is Nothing) Then  
  
            Dim serializer As XmlSerializer = _  
                New XmlSerializer(GetType(Report))  
  
            'Load the report bytes into a memory stream  
            Using stream As MemoryStream = New MemoryStream(bytes)  
  
                'Deserialize the report stream to an   
                'instance of the Report class  
                m_report = CType(serializer.Deserialize(stream), _  
                                 Report)  
  
            End Using  
  
        End If  
  
    End Sub  
    ```  
  
## <a name="next-lesson"></a>Lezione successiva  
 Nella lezione successiva si scriverà il codice per l'aggiornamento della definizione del report caricata dal server di report. Visualizzare [lezione 4: aggiornare la definizione del Report a livello di programmazione](../../2014/tutorials/lesson-4-update-the-report-definition-programmatically.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Aggiornamento dei report mediante le classi generate dallo Schema RDL &#40;esercitazione su SSRS&#41;](../../2014/tutorials/updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial.md)   
 [Report Definition Language &#40;SSRS&#41;](../reporting-services/reports/report-definition-language-ssrs.md)  
  
  
