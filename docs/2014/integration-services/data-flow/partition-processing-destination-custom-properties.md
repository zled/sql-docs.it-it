---
title: Proprietà personalizzate della destinazione elaborazione partizione | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3eac4413-0c90-4b06-8f7e-d0d72f4d869d
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 2724682cebfcae1e5c6a14b9c7cd815c96ad4a7c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36068756"
---
# <a name="partition-processing-destination-custom-properties"></a>Proprietà personalizzate della destinazione elaborazione partizione
  La destinazione elaborazione partizione include sia proprietà personalizzate che le proprietà comuni a tutti i componenti del flusso di dati.  
  
 Nella tabella seguente vengono descritte le proprietà personalizzate della destinazione elaborazione partizione. Tutte le proprietà sono di lettura/scrittura.  
  
|Proprietà|Tipo di dati|Description|  
|--------------|---------------|-----------------|  
|ASConnectionString|String|Stringa di connessione a un progetto [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] o a un'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|KeyDuplicate|Integer (enumerazione)|Quando è UseDefaultConfiguration `False`, un valore che indica come gestire errori di chiave duplicata. I possibili valori sono `IgnoreError` (0), `ReportAndContinue` (1), e `ReportAndStop` (2). Il valore predefinito di questa proprietà è `IgnoreError` (0).|  
|KeyErrorAction|Integer (enumerazione)|Quando è UseDefaultConfiguration `False`, un valore che indica come gestire gli errori di chiave. I valori possibili sono `ConvertToUnknown` (0) e `DiscardRecord` (1). Il valore predefinito di questa proprietà è `ConvertToUnknown` (0).|  
|KeyErrorLimit|Valore intero|Quando è UseDefaultConfiguration `False`, il limite massimo di errori di chiave consentiti.|  
|KeyErrorLimitAction|Integer (enumerazione)|Quando è UseDefaultConfiguration `False`, un valore che indica l'azione da eseguire quando `KeyErrorLimit` viene raggiunto. I valori possibili sono `StopLogging` (1) e `StopProcessing` (0). Il valore predefinito di questa proprietà è `StopProcessing` (0).|  
|KeyErrorLogFile|String|Quando è UseDefaultConfiguration `False`, il percorso e il nome del file di log di errori.|  
|KeyNotFound|Integer (enumerazione)|Quando è UseDefaultConfiguration `False`, un valore che indica come gestire gli errori di chiave mancante. I possibili valori sono `IgnoreError` (0), `ReportAndContinue` (1), e `ReportAndStop` (2). Il valore predefinito di questa proprietà è `ReportAndContinue` (1).|  
|NullKeyConvertedToUnknown|Integer (enumerazione)|Quando è UseDefaultConfiguration `False`, un valore che indica come gestire le chiavi null convertite nel valore sconosciuto. I possibili valori sono `IgnoreError` (0), `ReportAndContinue` (1), e `ReportAndStop` (2). Il valore predefinito di questa proprietà è `IgnoreError` (0).|  
|NullKeyNotAllowed|Integer (enumerazione)|Quando è UseDefaultConfiguration `False`, un valore che indica come gestire valori null non consentiti. I possibili valori sono `IgnoreError` (0), `ReportAndContinue` (1), e `ReportAndStop` (2). Il valore predefinito di questa proprietà è `ReportAndContinue` (1).|  
|ProcessType|Integer (enumerazione)|Tipo di elaborazione della partizione utilizzata dalla trasformazione. I valori possibili sono `ProcessAdd` (1) (incrementale), `ProcessFull` (0) e `ProcessUpdate` (2).|  
|UseDefaultConfiguration|Boolean|Valore che specifica se la trasformazione utilizza la configurazione degli errori predefinita. Se questa proprietà è `False`, la trasformazione utilizza i valori delle proprietà personalizzate la gestione degli errori elencati in questa tabella, inclusi KeyDuplicate, KeyErrorAction e così via.|  
  
 L'input e le colonne di input della destinazione elaborazione partizione non includono proprietà personalizzate.  
  
 Per altre informazioni, vedere [Destinazione elaborazione partizione](partition-processing-destination.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà comuni](../common-properties.md)  
  
  