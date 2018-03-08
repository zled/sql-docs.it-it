---
title: Aggiunta di record | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- AddNew method [ADO]
- ADO, editing data
- editing data [ADO], AddNew method
- editing data [ADO], adding data
ms.assetid: dd34669e-6f06-403b-9241-1c85c82aecc2
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1dc55762f934ecd3371aeb4d14311e6458b44c2c
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="adding-records-to-a-recordset"></a>Aggiungere i record in un Recordset
Utilizzare il **AddNew** per creare e inizializzare un nuovo record in un oggetto esistente **Recordset**. È possibile utilizzare il **supporta** metodo con un **CursorOptionEnum** valore **adAddNew** per verificare se è possibile aggiungere record corrente **Recordset** oggetto.

 Dopo aver chiamato il **AddNew** (metodo), il nuovo record diventa il record corrente e rimane tale dopo la chiamata di **aggiornamento** metodo. Se il **Recordset** oggetto non supporta i segnalibri, potrebbe essere in grado di accedere al nuovo record dopo il passaggio a un altro record. Pertanto, a seconda del tipo di cursore, potrebbe essere necessario chiamare il **Requery** metodo per rendere accessibile il nuovo record.

 Se si chiama **AddNew** durante la modifica del record corrente o durante l'aggiunta di un nuovo record, ADO chiama il **aggiornamento** per salvare le modifiche e quindi crea il nuovo record.

 In questa sezione vengono trattati gli argomenti seguenti.

-   [Aggiunta di record mediante AddNew](../../../ado/guide/data/adding-records-using-addnew.md)

-   [Aggiunta di più campi](../../../ado/guide/data/adding-multiple-fields.md)

-   [Determinazione della modalità di modifica](../../../ado/guide/data/determining-edit-mode.md)

-   [Uso di AddNew in modalità batch e immediata](../../../ado/guide/data/using-addnew-in-immediate-and-batch-modes.md)
