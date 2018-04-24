---
title: Gestione degli errori | Microsoft Docs
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- reporting errors [ADO]
- errors [ADO]
- ADO, error handling
ms.assetid: 4909e413-f3b0-4183-8ad3-67b1434df742
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4baa601f32a42a109ed32cb1056e5a4d5826c654
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="error-handling"></a>Gestione degli errori
ADO utilizza diversi metodi per notificare a un'applicazione di errori che si verificano. In questa sezione vengono descritti i tipi di errori che possono verificarsi quando si utilizza ADO e le modalità di notifica dell'applicazione. Conclude forniti alcuni suggerimenti su come gestire gli errori.  
  
## <a name="how-does-ado-report-errors"></a>Come ADO segnalazione degli errori  
 ADO gli errori vengono segnalati in diversi modi:  
  
-   Gli errori di ADO generano un errore di run-time. Gestire un errore di ADO l'esattamente come qualsiasi altro errore di run-time, ad esempio utilizzando un **in caso di errore** istruzione in Visual Basic.  
  
-   Il programma può ricevere errori da OLE DB. Un errore OLE DB genera anche un errore in fase di esecuzione.  
  
-   Se l'errore è specifico per il provider di dati, uno o più **errore** oggetti vengono inseriti nel **errori** insieme il **connessione** oggetto utilizzato per accedere ai dati archivio quando si è verificato l'errore.  
  
-   Se il processo che ha generato un evento viene generato anche un errore, le informazioni di errore viene inserite un **errore** dell'oggetto e passato come parametro per l'evento. Vedere [gestione di eventi ADO](../../../ado/guide/data/handling-ado-events.md) per ulteriori informazioni sugli eventi.  
  
-   I problemi che si verificano durante l'elaborazione batch di aggiornamenti o altre operazioni bulk che includono un **Recordset** può essere indicato dal **stato** proprietà del **Recordset**. Ad esempio, le violazioni di vincolo dello schema o autorizzazioni insufficienti possono essere specificate da **RecordStatusEnum** valori.  
  
-   Problemi che interessano un determinato **campo** nel record corrente vengono inoltre indicati tramite il **stato** proprietà di ogni **campo** nel **campi**  insieme il **Record** o **Recordset**. Ad esempio, gli aggiornamenti non completati o tipi di dati incompatibili possono essere specificati da **FieldStatusEnum** valori.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Errori ADO](../../../ado/guide/data/ado-errors.md)  
  
-   [Errori del provider](../../../ado/guide/data/provider-errors.md)  
  
-   [Informazioni sugli errori associati ai campi](../../../ado/guide/data/field-related-error-information.md)  
  
-   [Informazioni sugli errori associati ai recordset](../../../ado/guide/data/recordset-related-error-information.md)  
  
-   [Gestione degli errori in altri linguaggi](../../../ado/guide/data/handling-errors-in-other-languages.md)  
  
-   [Prevenzione degli errori](../../../ado/guide/data/anticipating-errors.md)
