---
title: XML per conformità Analysis (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- compliance [XML for Analysis]
- XML for Analysis, compliance
- XMLA, extended functionality
- XML for Analysis, extended functionality
- XMLA, compliance
- extending XML for Analysis
ms.assetid: d987d320-5581-4454-ad45-68e3a22175b6
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: cc7a8da77b72f25a68764636fbe15bc2d9e4ae04
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37267087"
---
# <a name="xml-for-analysis-compliance-xmla"></a>XML for Analysis Compliance (XMLA)
  La specifica XML for Analysis 1.1 descrive uno standard aperto che supporta l’accesso a origini dati che risiedono sul World Wide Web. In questo argomento illustra in dettaglio il livello di conformità con la specifica XML for Analysis 1.1 supportata da [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
## <a name="compliant-items"></a>Elementi conformi  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] è conforme a tutti gli elementi obbligatori elencati nella specifica XML for Analysis 1.1. In aggiunta, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] implementa l'elemento facoltativo seguente descritto nella specifica XML for Analysis 1.1.  
  
|Elemento|Specifica|Implementazione|  
|----------|-------------------|--------------------|  
|Supporto sessione|Gli elementi dell'intestazione SOAP elencati nella sezione "Supporto per Statefulness in XML for Analysis" della specifica XML for Analysis 1.1.|Tutti gli elementi dell'intestazione SOAP elencati sono supportati da [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], come descritto all'interno della specifica.|  
  
## <a name="extensions"></a>Estensioni  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] estende anche la specifica XML for Analysis 1.1 per supportare le seguenti caratteristiche e potenzialità aggiuntive.  
  
|Elemento|Specifica|Implementazione|  
|----------|-------------------|--------------------|  
|Negoziazione del protocollo|Nessuna informazione contenuta nella specifica XML for Analysis 1.1|[ProtocolCapabilities](xml-elements-headers/protocolcapabilities-element-xmla.md) elemento dell'intestazione aggiunto da [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] per supportare la negoziazione delle funzionalità del protocollo.|  
|Comandi XML for Analysis (XMLA) supportati dal metodo Discover|I comandi seguenti sono supportati dalla specifica XML for Analysis 1.1:<br /><br /> -   [Elemento dell'istruzione &#40;XMLA&#41;](xml-elements-commands/statement-element-xmla.md)|I seguenti comandi sono supportati da [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]:<br /><br /> -   [Elemento ALTER &#40;XMLA&#41;](xml-elements-commands/alter-element-xmla.md)<br />-   [Elemento di backup &#40;XMLA&#41;](xml-elements-commands/backup-element-xmla.md)<br />-   [Elemento batch &#40;XMLA&#41;](xml-elements-commands/batch-element-xmla.md)<br />-   [Elemento BeginTransaction &#40;XMLA&#41;](xml-elements-commands/begintransaction-element-xmla.md)<br />-   [Elemento Cancel &#40;XMLA&#41;](xml-elements-commands/cancel-element-xmla.md)<br />-   [Elemento ClearCache &#40;XMLA&#41;](xml-elements-commands/clearcache-element-xmla.md)<br />-   [Elemento CommitTransaction &#40;XMLA&#41;](xml-elements-commands/committransaction-element-xmla.md)<br />-   [Creare l'elemento &#40;XMLA&#41;](xml-elements-commands/create-element-xmla.md)<br />-   [Eliminare l'elemento &#40;XMLA&#41;](xml-elements-commands/delete-element-xmla.md)<br />-   [Elemento DesignAggregations &#40;XMLA&#41;](xml-elements-commands/designaggregations-element-xmla.md)<br />-   [Elemento DROP &#40;XMLA&#41;](xml-elements-commands/drop-element-xmla.md)<br />-   [Inserire l'elemento &#40;XMLA&#41;](xml-elements-commands/insert-element-xmla.md)<br />-   [Bloccare l'elemento &#40;XMLA&#41;](xml-elements-commands/lock-element-xmla.md)<br />-   [Elemento MergePartitions &#40;XMLA&#41;](xml-elements-commands/mergepartitions-element-xmla.md)<br />-   [Elemento NotifyTableChange &#40;XMLA&#41;](xml-elements-commands/notifytablechange-element-xmla.md)<br />-   [Elaborare l'elemento &#40;XMLA&#41;](xml-elements-commands/process-element-xmla.md)<br />-   [Elemento Restore &#40;XMLA&#41;](xml-elements-commands/restore-element-xmla.md)<br />-   [Elemento RollbackTransaction &#40;XMLA&#41;](xml-elements-commands/rollbacktransaction-element-xmla.md)<br />-Elemento SetPasswordEncryptionKey<br />-   [Elemento dell'istruzione &#40;XMLA&#41;](xml-elements-commands/statement-element-xmla.md)<br />-   [Elemento Subscribe &#40;XMLA&#41;](xml-elements-commands/subscribe-element-xmla.md)<br />-   [Elemento Synchronize &#40;XMLA&#41;](xml-elements-commands/synchronize-element-xmla.md)<br />-   [Elemento Unlock &#40;XMLA&#41;](xml-elements-commands/unlock-element-xmla.md)<br />-   [Aggiornare l'elemento &#40;XMLA&#41;](xml-elements-commands/update-element-xmla.md)<br />-   [Elemento UpdateCells &#40;XMLA&#41;](xml-elements-commands/updatecells-element-xmla.md)|  
|Errori di colonna nei set di righe di tabella|Non elencato nella specifica XML for Analysis 1.1.|Il [errore](xml-elements-properties/error-element-xmla.md) elemento viene usato da [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] per segnalare gli errori per gli elementi delle colonne contenuti un [riga](xml-elements-properties/error-element-xmla.md) elemento.|  
  
## <a name="see-also"></a>Vedere anche  
 [XML for Analysis &#40;XMLA&#41; riferimento](xml-for-analysis-xmla-reference.md)  
  
  
