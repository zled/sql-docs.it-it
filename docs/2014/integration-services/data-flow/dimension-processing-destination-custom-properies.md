---
title: Proprietà personalizzate della destinazione elaborazione dimensione | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9700f663-53f2-49b6-b1ef-92c7b752d6a1
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: f4dae4c9661e8a04e34b5d2b78ccdd0f556bfa7c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36055537"
---
# <a name="dimension-processing-destination-custom-properies"></a>Proprietà personalizzate della destinazione elaborazione dimensione
  La destinazione elaborazione dimensione include sia proprietà personalizzate che le proprietà comuni a tutti i componenti del flusso di dati.  
  
 Nella tabella seguente vengono descritte le proprietà personalizzate della destinazione elaborazione dimensione. Tutte le proprietà sono di lettura/scrittura.  
  
|Proprietà|Tipo di dati|Description|  
|--------------|---------------|-----------------|  
|ASConnectionString|String|Stringa di connessione a un'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] o a un progetto [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .|  
|KeyDuplicate|Integer (enumerazione)|Quando è UseDefaultConfiguration `False`, un valore che indica come gestire errori di chiave duplicata. I possibili valori sono `IgnoreError` (0), `ReportAndContinue` (1), e `ReportAndStop` (2). Il valore predefinito di questa proprietà è `IgnoreError` (0).|  
|KeyErrorAction|Integer (enumerazione)|Quando è UseDefaultConfiguration `False`, un valore che indica come gestire errori di chiave. I valori possibili sono `ConvertToUnknown` (0) e `DiscardRecord` (1). Il valore predefinito di questa proprietà è `ConvertToUnknown` (0).|  
|KeyErrorLimit|Valore intero|Quando è UseDefaultConfiguration `False`, il limite massimo di errori di chiave che sono abilitati.|  
|KeyErrorLimitAction|Integer (enumerazione)|Quando è UseDefaultConfiguration `False`, un valore che indica l'azione da eseguire quando `KeyErrorLimit` viene raggiunto. I valori possibili sono `StopLogging` (1) e `StopProcessing` (0). Il valore predefinito di questa proprietà è `StopProcessing` (0).|  
|KeyErrorLogFile|String|Quando è UseDefaultConfiguration `False`, il percorso e il nome del file di log di errori.|  
|KeyNotFound|Integer (enumerazione)|Quando è UseDefaultConfiguration `False`, un valore che indica come gestire gli errori di chiave mancante. I possibili valori sono `IgnoreError` (0), `ReportAndContinue` (1), e `ReportAndStop` (2). Il valore predefinito di questa proprietà è `IgnoreError` (0).|  
|NullKeyConvertedToUnknown|Integer (enumerazione)|Quando è UseDefaultConfiguration `False`, un valore che indica come gestire le chiavi null convertite nel valore sconosciuto. I possibili valori sono `IgnoreError` (0), `ReportAndContinue` (1), e `ReportAndStop` (2). Il valore predefinito di questa proprietà è `IgnoreError` (0).|  
|NullKeyNotAllowed|Integer (enumerazione)|Quando è UseDefaultConfiguration `False`, un valore che indica come gestire valori null non consentiti. I possibili valori sono `IgnoreError` (0), `ReportAndContinue` (1), e `ReportAndStop` (2). Il valore predefinito di questa proprietà è `IgnoreError` (0).|  
|ProcessType|Integer (enumerazione)|Tipo di elaborazione della dimensione utilizzata dalla trasformazione. I valori possibili sono `ProcessAdd` (1) (incrementale), `ProcessFull` (0) e `ProcessUpdate` (2).|  
|UseDefaultConfiguration|Boolean|Valore che specifica se la trasformazione utilizza la configurazione degli errori predefinita. Se questa proprietà è `False`, la trasformazione include informazioni sull'elaborazione degli errori.|  
  
 L'input e le colonne di input della destinazione elaborazione dimensione non includono proprietà personalizzate.  
  
 Per altre informazioni, vedere [Destinazione elaborazione dimensione](dimension-processing-destination.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà comuni](../common-properties.md)  
  
  