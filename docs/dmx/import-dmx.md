---
title: IMPORTAZIONE (DMX) | Documenti Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- IMPORT
dev_langs:
- DMX
helpviewer_keywords:
- IMPORT statement
- mining structures [DMX], importing
ms.assetid: c053bc88-2daf-4ebb-81d7-5a330250536d
caps.latest.revision: 42
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: ae93e70bb0e5672ada244064feb12750a96d4ffd
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="import-dmx"></a>IMPORT (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Carica nel server un modello o una struttura di data mining da un file con estensione abf (Analysis Services Backup File).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
IMPORT FROM <filename>  
```  
  
## <a name="arguments"></a>Argomenti  
 *nome file*  
 Stringa contenente il nome e il percorso del file da importare.  
  
## <a name="remarks"></a>Osservazioni  
 Se non è specificato alcun oggetto, verrà caricato tutto il contenuto del file con estensione dmb. Se il file con estensione dmb include un database che non esiste sul server, il database verrà creato.  
  
 Per esportare o importare oggetti è necessario essere un amministratore del server o del database.  
  
## <a name="import-from-file-example"></a>Esempio di importazione da file  
 Nell'esempio seguente viene importato nel server corrente l'intero contenuto del file contenente la struttura e il modello di associazione.  
  
```  
IMPORT FROM 'C:\TEMP\Association_NEW.dmb'  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Estensioni Data Mining &#40;DMX&#41; le istruzioni di definizione dei dati](../dmx/dmx-statements-data-definition.md)   
 [Estensioni Data Mining &#40;DMX&#41; istruzioni Data Manipulation](../dmx/dmx-statements-data-manipulation.md)   
 [Data Mining Extensions & #40; DMX & #41; Riferimento istruzione](../dmx/data-mining-extensions-dmx-statements.md)   
 [ESPORTARE &AMP;#40;DMX&AMP;#41;](../dmx/export-dmx.md)   
 [Esportare e importare oggetti di Data Mining](../analysis-services/data-mining/export-and-import-data-mining-objects.md)  
  
  
