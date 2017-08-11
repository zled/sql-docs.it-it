---
title: Utilizzo di Try e Catch blocchi | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- exceptions [Reporting Services], try/catch blocks
- try/catch blocks [Reporting Services]
ms.assetid: a7a9ef53-e3b6-4bf7-81f3-d85615954e6f
caps.latest.revision: 29
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 659707603a24ff8d59bfc1b001d80e8184c119e1
ms.contentlocale: it-it
ms.lasthandoff: 08/09/2017

---
# <a name="using-try-and-catch-blocks"></a>Utilizzo di Try e blocchi Catch
  Dopo avere limitato le richieste non valide al server di report aggiungendo istruzioni condizionali al codice, è necessario fornire funzionalità adeguate di gestione delle eccezioni tramite l'utilizzo di blocchi try/catch. Questa tecnica fornisce un ulteriore livello di protezione dalle richieste non valide. Se una richiesta al server di report viene inserita in un blocco try e tale richiesta comporta la generazione di un'eccezione nel server di report, l'eccezione viene intercettata nel blocco catch, impedendo l'arresto imprevisto dell'applicazione. Dopo che l'eccezione è stata intercettata, è possibile utilizzarla per indicare all'utente di eseguire un'operazione diversa o semplicemente per visualizzare un messaggio descrittivo in cui viene indicato che si è verificato un errore. È quindi possibile utilizzare un blocco finally per la pulizia delle risorse. Idealmente, è consigliabile creare un piano generale di gestione delle eccezioni per evitare la duplicazione non necessaria dei blocchi try/catch.  
  
 Nell'esempio seguente vengono utilizzati blocchi try/catch per migliorare l'affidabilità del codice di gestione delle eccezioni.  
  
```  
// C#  
private void PublishReport()  
{  
   int index;  
   string reservedChar;  
   string message;  
  
   // Check the text value of the name text box for "/",  
   // a reserved character  
   index = nameTextBox.Text.IndexOf(@"/");  
  
   if ( index != -1) // The text contains the character  
   {  
      reservedChar = nameTextBox.Text.Substring(index, 1);  
      // Build a user-friendly error message  
      message = "The name of the report cannot contain the reserved character " +  
         "\"" + reservedChar + "\". " +  
         "Please enter a valid name for the report. " +  
         "For more information about reserved characters, " +  
         "consult the online documentation";  
  
      MessageBox.Show(message, "Invalid Input Error");  
   }  
   else // Publish the report  
   {  
      Byte[] definition = null;  
      Warning[] warnings = {};  
      string name = nameTextBox.Text;  
  
      try  
      {  
         FileStream stream = File.OpenRead("MyReport.rdl");  
         definition = new Byte[stream.Length];  
         stream.Read(definition, 0, (int) stream.Length);  
         stream.Close();  
         // Create report with user-defined name  
         rs.CreateCatalogItem("Report", name, "/Samples", false, definition, null, out warnings);  
         MessageBox.Show("Report: {0} created successfully", name);  
      }  
  
      // Catch expected exceptions beginning with the most specific,  
      // moving to the least specific  
      catch(IOException ex)  
      {  
         MessageBox.Show(ex.Message, "File IO Exception");  
      }  
  
      catch (SoapException ex)  
      {  
         // The exception is a SOAP exception, so use  
         // the Detail property's Message element.  
         MessageBox.Show(ex.Detail["Message"].InnerXml, "SOAP Exception");   
      }  
  
      catch (Exception ex)  
      {  
         MessageBox.Show(ex.Message, "General Exception");  
      }  
   }  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Introduzione a gestione delle eccezioni in Reporting Services](../../../reporting-services/report-server-web-service-net-framework-exception-handling/introducing-exception-handling-in-reporting-services.md)   
 [Classe SoapException di Reporting Services](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/reporting-services-soapexception-class.md)  
  
  
