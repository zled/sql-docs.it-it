---
title: Set di righe DMSCHEMA_MINING_FUNCTIONS | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DMSCHEMA_MINING_FUNCTIONS
topic_type:
- apiref
helpviewer_keywords:
- DMSCHEMA_MINING_FUNCTIONS rowset
ms.assetid: 9ace7493-a7b1-45ca-93de-3cb2f3597017
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b769476650bdb97479f3d8c61871980605e75635
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48190417"
---
# <a name="dmschemaminingfunctions-rowset"></a>Set di righe DMSCHEMA_MINING_FUNCTIONS
  Vengono descritte le funzioni di data mining di dati supportati da algoritmi di data mining disponibili in un server che esegue [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il `DMSCHEMA_MINING_FUNCTIONS` set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Length|Description|  
|-----------------|--------------------|------------|-----------------|  
|`SERVICE_NAME`|`DBTYPE_WSTR`||Nome dell'algoritmo.|  
|`FUNCTION_NAME`|`DBTYPE_WSTR`||Nome della funzione.|  
|`FUNCTION_SIGNATURE`|`DBTYPE_WSTR`||Firma della funzione.|  
|`RETURNS_TABLE`|`DBTYPE_BOOL`||È `FALSE` se la funzione restituisce contenuto scalare, ad esempio la lunghezza dell'argomento di tipo character, mentre è `TRUE` se la funzione restituisce una tabella, ad esempio una tabella dell'istogramma.|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Descrizione intuitiva della funzione.|  
|`HELP_FILE`|`DBTYPE_WSTR`||Nome del file che contiene la documentazione relativa a questa funzione.|  
|`HELP_CONTEXT`|`DBTYPE_I4`||ID di contesto della Guida per questa funzione.|  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il set di righe `DMSCHEMA_MINING_FUNCTIONS` può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|`SERVICE_NAME`|`DBTYPE_WSTR`|Facoltativa.|  
|`FUNCTION_NAME`|`DBTYPE_WSTR`|Facoltativa.|  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe dello schema di data mining](../../schema-rowsets/data-mining/data-mining-schema-rowsets.md) 
  
  
