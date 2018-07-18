---
title: ConnectPromptEnum | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ConnectPromptEnum
helpviewer_keywords:
- ConnectPromptEnum enumeration [ADO]
ms.assetid: 21026e24-62b7-4cc9-8aef-62c1fc6cba75
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 62b1bb38789dcfb2fd15b80501315d9c1be38a66
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35277240"
---
# <a name="connectpromptenum"></a>ConnectPromptEnum
Specifica se deve essere visualizzata una finestra di dialogo per la richiesta di parametri mancanti quando si apre una connessione a un'origine dati.  
  
|Costante|valore|Description|  
|--------------|-----------|-----------------|  
|**adPromptAlways**|1|Richiede sempre.|  
|**adPromptComplete**|2|Viene richiesto se sono necessarie ulteriori informazioni.|  
|**adPromptCompleteRequired**|3|Viene richiesto se sono necessarie ulteriori informazioni, ma non sono consentiti parametri facoltativi.|  
|**adPromptNever**|4|Non richiede mai.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC equivalente  
 Package: **com.ms.wfc.data**  
  
|Costante|  
|--------------|  
|AdoEnums.ConnectPrompt.ALWAYS|  
|AdoEnums.ConnectPrompt.COMPLETE|  
|AdoEnums.ConnectPrompt.COMPLETEREQUIRED|  
|AdoEnums.ConnectPrompt.NEVER|  
  
## <a name="applies-to"></a>Si applica a  
 [Proprietà dinamica Prompt (ADO)](../../../ado/reference/ado-api/prompt-property-dynamic-ado.md)
