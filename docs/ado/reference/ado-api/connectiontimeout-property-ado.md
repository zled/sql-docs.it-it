---
title: Proprietà ConnectionTimeout (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::ConnectionTimeout
helpviewer_keywords:
- ConnectionTimeout property [ADO]
ms.assetid: 8904a403-1383-4b4b-b53d-5c01d6f5deac
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b5cb3e6e1cc4266551bfeabf09bde1a65fea032f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47707249"
---
# <a name="connectiontimeout-property-ado"></a>Proprietà ConnectionTimeout (ADO)
Indica per quanto tempo di attesa durante il tentativo di stabilire una connessione prima di terminare il tentativo e generare un errore.  
  
## <a name="settings-and-return-values"></a>Le impostazioni e valori restituiti  
 Imposta o restituisce un **lungo** valore che indica, in secondi, quanto tempo di attesa per la connessione da aprire. Valore predefinito è 15.  
  
## <a name="remarks"></a>Note  
 Usare la **ConnectionTimeout** proprietà in un [connessione](../../../ado/reference/ado-api/connection-object-ado.md) se ritardi di rete del traffico o con intensa attività di server rendono necessario interrompere un tentativo di connessione dell'oggetto. Se l'ora dal **ConnectionTimeout** l'impostazione della proprietà deve trascorrere prima dell'apertura della connessione, si verifica un errore e ADO non annullerà il tentativo. Se si imposta la proprietà su zero, ADO attenderà all'infinito finché non viene aperta la connessione. Assicurarsi che il provider a cui si sta scrivendo codice supporta il **ConnectionTimeout** funzionalità.  
  
 Il **ConnectionTimeout** è di lettura/scrittura quando la connessione è chiusa e di sola lettura quando è aperto.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [ConnectionString, ConnectionTimeout ed esempio di proprietà State (VB)](../../../ado/reference/ado-api/connectionstring-connectiontimeout-and-state-properties-example-vb.md)   
 [Esempio ConnectionString, ConnectionTimeout e proprietà State (VC + +)](../../../ado/reference/ado-api/connectionstring-connectiontimeout-and-state-properties-example-vc.md)   
 [Proprietà CommandTimeout (ADO)](../../../ado/reference/ado-api/commandtimeout-property-ado.md)
