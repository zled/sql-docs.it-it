---
title: Editor trasformazione controllo | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.audittransformation.f1
helpviewer_keywords:
- Audit Transformation Editor
ms.assetid: 32786a34-5870-4fde-83c7-ec74d62404b8
caps.latest.revision: 13
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: c4c3cc4b661c58476a98e3528e5853cf80b9861d
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="audit-transformation-editor"></a>Editor trasformazione Controllo
  La trasformazione Controllo consente di includere nel flusso di dati di un pacchetto informazioni sull'ambiente in cui viene eseguito il pacchetto. Ad esempio, il nome del pacchetto, del computer e dell'operatore può essere aggiunto al flusso di dati. [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] include variabili di sistema che forniscono queste informazioni.  
  
 Per ulteriori informazioni sulla trasformazione Controllo, vedere [Audit Transformation](../../../integration-services/data-flow/transformations/audit-transformation.md).  
  
## <a name="options"></a>Opzioni  
 **Nome colonna di output**  
 Consente di specificare il nome di una nuova colonna di output che conterrà le informazioni di controllo.  
  
 **Tipo di controllo**  
 Consente di selezionare una variabile di sistema disponibile per visualizzare le informazioni di controllo.  
  
|Valore|Description|  
|-----------|-----------------|  
|**GUID istanza esecuzione**|Consente di specificare il GUID che identifica in modo univoco l'istanza di esecuzione del pacchetto.|  
|**ID pacchetto**|Consente di specificare il GUID che identifica in modo univoco il pacchetto.|  
|**Nome pacchetto**|Consente di specificare il nome del pacchetto.|  
|**ID versione**|Consente di specificare il GUID che identifica in modo univoco la versione del pacchetto.|  
|**Ora di inizio esecuzione**|Consente di specificare l'ora di inizio dell'esecuzione del pacchetto.|  
|**Nome computer**|Consente di specificare il nome del computer sul quale è stato avviato il pacchetto.|  
|**Nome utente**|Consente di specificare il nome dell'account di accesso dell'utente che ha avviato il pacchetto.|  
|**Nome attività**|Consente di specificare il nome dell'attività Flusso di dati a cui è associata la trasformazione Controllo.|  
|**ID attività**|Consente di specificare il GUID che identifica in modo univoco l'attività Flusso di dati a cui è associata la trasformazione Controllo.|  
  
## <a name="see-also"></a>Vedere anche  
 [Errori di Integration Services e riferimento ai messaggi](../../../integration-services/integration-services-error-and-message-reference.md)  
  
  
