---
title: "Editor destinazione elaborazione dimensione (pagina Avanzate) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.dimprocessingtransformation.advanced.f1"
helpviewer_keywords: 
  - "Editor destinazione elaborazione dimensione"
ms.assetid: 2b30835a-2680-4d98-89a4-4f17e29e3818
caps.latest.revision: 27
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 27
---
# Editor destinazione elaborazione dimensione (pagina Avanzate)
  Usare la pagina **Avanzate** della finestra di dialogo **Editor destinazione elaborazione dimensione** per configurare la gestione degli errori.  
  
 Per ulteriori informazioni sulla destinazione elaborazione dimensione, vedere [Dimension Processing Destination](../../integration-services/data-flow/dimension-processing-destination.md).  
  
## Opzioni  
 **Usa configurazione errori predefinita**  
 Consente di specificare se utilizzare la gestione degli errori predefinita di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Il valore predefinito è **True**.  
  
 **Azione per errore chiave**  
 Consente di specificare la modalità di gestione dei record che hanno valori di chiave non validi.  
  
|Valore|Description|  
|-----------|-----------------|  
|**ConvertToUnknown**|Consente di convertire il valore di chiave non valido nel valore **UnknownMember**.|  
|**DiscardRecord**|Consente di scartare il record.|  
  
 **Ignora errori**  
 Consente di specificare che gli errori devono essere ignorati.  
  
 **Arresta in caso di errore**  
 Consente di specificare che l'elaborazione deve essere arrestata al verificarsi di un errore.  
  
 **Numero di errori**  
 Consente di specificare la soglia di errore alla quale l'elaborazione deve arrestarsi quando è stata selezionata l'opzione **Arresta in caso di errore**.  
  
 **Azione in caso di errore**  
 Consente di specificare l'azione che deve essere intrapresa al raggiungimento della soglia di errore quando è stata selezionata l'opzione **Arresta in caso di errore**.  
  
|Valore|Description|  
|-----------|-----------------|  
|**StopProcessing**|Consente di arrestare l'elaborazione.|  
|**StopLogging**|Consente di arrestare la registrazione degli errori.|  
  
 **Chiave non trovata**  
 Consente di specificare l'azione che deve essere intrapresa per un errore di chiave non trovata. Il valore predefinito è **ReportAndContinue**.  
  
|Valore|Description|  
|-----------|-----------------|  
|**IgnoreError**|Consente di ignorare l'errore e continuare l'elaborazione.|  
|**ReportAndContinue**|Consente di segnalare l'errore e continuare l'elaborazione.|  
|**ReportAndStop**|Consente di segnalare l'errore e arrestare l'elaborazione.|  
  
 **Chiave duplicata**  
 Consente di specificare l'azione che deve essere intrapresa per un errore di chiave duplicata. Il valore predefinito è **IgnoreError**.  
  
|Valore|Description|  
|-----------|-----------------|  
|**IgnoreError**|Consente di ignorare l'errore e continuare l'elaborazione.|  
|**ReportAndContinue**|Consente di segnalare l'errore e continuare l'elaborazione.|  
|**ReportAndStop**|Consente di segnalare l'errore e arrestare l'elaborazione.|  
  
 **Chiave Null convertita in sconosciuta**  
 Consente di specificare l'azione che deve essere intrapresa quando una chiave Null è stata convertita nel valore **UnknownMember**. Il valore predefinito è **IgnoreError**.  
  
|Valore|Description|  
|-----------|-----------------|  
|**IgnoreError**|Consente di ignorare l'errore e continuare l'elaborazione.|  
|**ReportAndContinue**|Consente di segnalare l'errore e continuare l'elaborazione.|  
|**ReportAndStop**|Consente di segnalare l'errore e arrestare l'elaborazione.|  
  
 **Chiave Null non consentita**  
 Consente di specificare l'azione che deve essere intrapresa quando viene incontrata una chiave Null e le chiavi Null non sono consentite. Il valore predefinito è **ReportAndContinue**.  
  
|Valore|Description|  
|-----------|-----------------|  
|**IgnoreError**|Consente di ignorare l'errore e continuare l'elaborazione.|  
|**ReportAndContinue**|Consente di segnalare l'errore e continuare l'elaborazione.|  
|**ReportAndStop**|Consente di segnalare l'errore e arrestare l'elaborazione.|  
  
 **Percorso log degli errori**  
 Consente di digitare il percorso del log degli errori o di selezionare una destinazione mediante il pulsante **Sfoglia (…)**.  
  
 **Sfoglia (...)**  
 Consente di selezionare il percorso del log degli errori.  
  
## Vedere anche  
 [Guida di riferimento ai messaggi e agli errori di Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Editor destinazione elaborazione dimensione &#40;pagina Gestione connessione&#41;](../../integration-services/data-flow/dimension-processing-destination-editor-connection-manager-page.md)   
 [Editor destinazione elaborazione dimensione &#40;pagina Mapping&#41;](../../integration-services/data-flow/dimension-processing-destination-editor-mappings-page.md)  
  
  