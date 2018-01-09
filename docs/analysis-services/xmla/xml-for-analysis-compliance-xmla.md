---
title: "XML per la conformità Analysis (XMLA) | Documenti Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- compliance [XML for Analysis]
- XML for Analysis, compliance
- XMLA, extended functionality
- XML for Analysis, extended functionality
- XMLA, compliance
- extending XML for Analysis
ms.assetid: d987d320-5581-4454-ad45-68e3a22175b6
caps.latest.revision: "15"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: efd2d4cfd7adb6185abdd383a261494495817ec5
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="xml-for-analysis-compliance-xmla"></a>XML for Analysis Compliance (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]La specifica XML for Analysis 1.1 descrive uno standard aperto che supporta l'accesso a origini dati che risiedono sul World Wide Web. In questo argomento illustra in dettaglio il livello di conformità con la specifica XML for Analysis 1.1 supportata da [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
## <a name="compliant-items"></a>Elementi conformi  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] è conforme a tutti gli elementi obbligatori elencati nella specifica XML for Analysis 1.1. In aggiunta, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] implementa l'elemento facoltativo seguente descritto nella specifica XML for Analysis 1.1.  
  
|Elemento|Specifica|Implementazione|  
|----------|-------------------|--------------------|  
|Supporto sessione|Gli elementi dell'intestazione SOAP elencati nella sezione "Supporto per Statefulness in XML for Analysis" della specifica XML for Analysis 1.1.|Tutti gli elementi dell'intestazione SOAP elencati sono supportati da [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], come descritto all'interno della specifica.|  
  
## <a name="extensions"></a>Estensioni  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] estende anche la specifica XML for Analysis 1.1 per supportare le seguenti caratteristiche e potenzialità aggiuntive.  
  
|Elemento|Specifica|Implementazione|  
|----------|-------------------|--------------------|  
|Negoziazione del protocollo|Nessuna informazione contenuta nella specifica XML for Analysis 1.1|Elemento ProtocolCapabilities dell'intestazione aggiunto da [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] per supportare la negoziazione delle funzionalità del protocollo.|  
|Comandi XML for Analysis (XMLA) supportati dal metodo Discover|I comandi seguenti sono supportati dalla specifica XML for Analysis 1.1:<br /><br /> [Elemento Statement &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/statement-element-xmla.md)|I seguenti comandi sono supportati da [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]:<br /><br /> [Modificare l'elemento &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/alter-element-xmla.md)<br /><br /> [Elemento backup &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md)<br /><br /> [Elemento batch &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md)<br /><br /> [Elemento BeginTransaction &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/begintransaction-element-xmla.md)<br /><br /> [Annulla l'elemento &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md)<br /><br /> [Elemento ClearCache &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/clearcache-element-xmla.md)<br /><br /> [Elemento CommitTransaction &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/committransaction-element-xmla.md)<br /><br /> [Creare l'elemento &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/create-element-xmla.md)<br /><br /> [Eliminare l'elemento &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/delete-element-xmla.md)<br /><br /> [Elemento DesignAggregations &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/designaggregations-element-xmla.md)<br /><br /> [Eliminare l'elemento &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md)<br /><br /> [Inserisci elemento &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)<br /><br /> [Blocca elemento &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/lock-element-xmla.md)<br /><br /> [Elemento MergePartitions &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/mergepartitions-element-xmla.md)<br /><br /> [Elemento NotifyTableChange &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/notifytablechange-element-xmla.md)<br /><br /> [Elemento Process &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md)<br /><br /> [Ripristinare l'elemento &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)<br /><br /> [Elemento RollbackTransaction &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/rollbacktransaction-element-xmla.md)<br /><br /> [Elemento Statement &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/statement-element-xmla.md)<br /><br /> [La sottoscrizione elemento &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/subscribe-element-xmla.md)<br /><br /> [Sincronizzare elemento &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)<br /><br /> [Sblocca elemento &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/unlock-element-xmla.md)<br /><br /> [Elemento Update &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)<br /><br /> [Elemento UpdateCells &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/updatecells-element-xmla.md)|  
|Errori di colonna nei set di righe di tabella|Non elencato nella specifica XML for Analysis 1.1.|Il [errore](../../analysis-services/xmla/xml-elements-properties/error-element-xmla.md) elemento viene usato da [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] per segnalare gli errori per gli elementi delle colonne contenuti un [riga](../../analysis-services/xmla/xml-elements-properties/error-element-xmla.md) elemento.|  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento a XML for Analysis &#40;XMLA&#41;](../../analysis-services/xmla/xml-for-analysis-xmla-reference.md)  
  
  
