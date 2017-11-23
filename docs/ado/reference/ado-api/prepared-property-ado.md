---
title: "Proprietà (ADO) preparato | Documenti Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords: Command15::Prepared
helpviewer_keywords: Prepared property [ADO]
ms.assetid: 11ca8825-765e-4bb4-a6ce-3f6564ad8755
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 62f01b807c56065c61e5cf8650c15f7210df6b7a
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="prepared-property-ado"></a>Proprietà Prepared (ADO)
Indica se salvare una versione compilata di un [comando](../../../ado/reference/ado-api/command-object-ado.md) prima dell'esecuzione.  
  
## <a name="settings-and-return-values"></a>Le impostazioni e valori restituiti  
 Restituisce o imposta un **booleano** valore che, se impostato su **True**, indica che il comando deve essere preparato.  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare il **Prepared** proprietà per il provider di salvare una versione preparata (compilata o) della query specificata nel [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) proprietà prima di un [comando](../../../ado/reference/ado-api/command-object-ado.md) dell'oggetto prima esecuzione. Questo potrebbe rallentare prima esecuzione di un comando, ma una volta che il provider consente di compilare un comando, il provider utilizzerà la versione compilata del comando per le esecuzioni successive, con conseguente miglioramento delle prestazioni.  
  
 Se la proprietà è **False**, il provider eseguirà il **comando** oggetto direttamente senza creare una versione compilata.  
  
 Se il provider non supporta la preparazione dei comandi, può restituire un errore quando questa proprietà è impostata su **True**. Se il provider non restituisce un errore, ignora semplicemente la richiesta di preparazione del comando e un set di **Prepared** proprietà **False**.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di proprietà Prepared (VB)](../../../ado/reference/ado-api/prepared-property-example-vb.md)   
 [Esempio di proprietà Prepared (VC++)](../../../ado/reference/ado-api/prepared-property-example-vc.md)   
