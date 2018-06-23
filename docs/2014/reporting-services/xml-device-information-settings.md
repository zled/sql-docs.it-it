---
title: Impostazioni relative alle informazioni sul dispositivo XML | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- XML [Reporting Services], rendering
- device information settings [Reporting Services], PDF rendering
ms.assetid: a32e83fe-c10e-4ebd-8975-5be7dcc422e7
caps.latest.revision: 44
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: b60e0abfbd6a0487fbc264a824c80ae8a5db60b1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36067120"
---
# <a name="xml-device-information-settings"></a>Impostazioni relative alle informazioni sul dispositivo XML
  Nella tabella seguente sono elencate le impostazioni relative alle informazioni sul dispositivo per il rendering nel formato XML.  
  
|Impostazione|valore|  
|-------------|-----------|  
|`XSLT`|Percorso nello spazio dei nomi del server di report di una trasformazione XSLT da applicare al file XML, ad esempio `/Transforms/myxslt`. Il file con estensione xsl deve essere una risorsa pubblicata nel server di report ed è necessario accedervi tramite un percorso di un elemento del server di report. Il valore di questa impostazione viene applicato dopo qualsiasi trasformazione XSLT specificata nel report. Se viene applicata l'impostazione `XSLT`, l'impostazione `OmitSchema` viene ignorata.|  
|**MIMEType**|Tipo MIME (Multipurpose Internet Mail Extensions) del file XML.|  
|**UseFormattedValues**|Indica se eseguire il rendering del valore formattato di una casella di testo quando vengono generati i dati XML. Il valore false indica che viene utilizzato il valore sottostante della casella di testo.|  
|**Indented**|Indica se generare codice XML con rientro. Il valore predefinito di `false` genera XML compresso senza rientro.|  
|`OmitNamespace`|Indica se omettere lo spazio dei nomi predefinito dai dati XML.<br /><br /> Se true, i dati XML non specificano uno spazio dei nomi predefinito.<br /><br /> Se false, i dati XML specificano uno spazio dei nomi predefinito con il valore della proprietà DataSchema del report. L'impostazione predefinita della proprietà DataSchema corrisponde al nome del report.<br /><br /> Il valore predefinito è `false`.|  
|`OmitSchema`|Indica se omettere la posizione dello schema dai dati XML. Il percorso è l'attributo SchemaLocation. Il valore predefinito di OmitSchema dipende dal valore di OmitNamespace:<br /><br /> Se OmitNamespace = False, OmitSchema = `False` per impostazione predefinita. L'utente può eseguire l'override dell'impostazione predefinita impostando OmitSchema = True.<br /><br /> Se OmitNamespace = True, OmitSchema funzionerà come `True` indipendentemente dal valore configurato in modo esplicito per OmitSchema.|  
|**Codifica**|Il nome IANA (Internet Assigned Numbers Authority) di una codifica dei caratteri supportata da .NET Framework. Il valore predefinito è `UTF-8`. Esempi di altri valori includono ASCII, UTF-7 e UTF-16.|  
|**FileExtension**|Estensione di file da utilizzare per il file generato.|  
|**Schema**|Indica se viene eseguito il rendering di XSD (XML Schema Definition) o dei dati XML effettivi. Il valore `true` indica che viene eseguito il rendering di un elemento XML schema. Il valore predefinito è `false`.|  
  
## <a name="see-also"></a>Vedere anche  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 [Passaggio Device Information Settings a estensioni per il Rendering](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Personalizzare i parametri di estensione per il rendering in RSReportServer.Config](customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Riferimento tecnico &#40;SSRS&#41;](../../2014/reporting-services/technical-reference-ssrs.md)  
  
  