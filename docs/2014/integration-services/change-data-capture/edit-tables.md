---
title: Modificare le tabelle | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- tabProps
ms.assetid: fed8fada-2abc-45e2-8228-0656f9c599cb
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 8f8945827cb4a0170ceac43c313554b9a88db478
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48215011"
---
# <a name="edit-tables"></a>Modificare le tabelle
  Utilizzare la scheda **Tabelle** per apportare modifiche alle tabelle e alle colonne selezionate dal database di origine Oracle. Nella scheda sono presenti gli elementi seguenti:  
  
 **Elenco Tabella**  
 Nell'elenco tabelle sono presenti tre colonne:  
  
-   **Nome tabella Oracle**: nome della tabella, incluso lo schema.  
  
-   **Istanza di acquisizione**: nome dell'istanza di acquisizione usato per denominare gli oggetti Change Data Capture specifici dell'istanza. L'istanza di acquisizione non può essere NULL. Se non è specificato, il nome deriva dal nome dello schema di origine più il nome della tabella di origine nel formato `<schema-name>_<table-name>.` Il nome dell'istanza di acquisizione non può superare i 100 caratteri e deve essere univoco nel database. È possibile fare clic in qualsiasi cella di questa colonna per modificare manualmente **capture_instance**.  
  
-   **Ruolo di sicurezza**: nome del ruolo del database utilizzato per ottenere l'accesso ai dati delle modifiche. È possibile fare clic in qualsiasi cella di questa colonna per modificare manualmente **security_role**.  
  
 **Aggiungi tabelle**  
 Fare clic su **Aggiungi tabelle** per aprire la finestra di dialogo Selezione tabelle in cui è possibile [aggiungere tabelle a un'istanza di CDC](add-tables-to-a-cdc-instance.md). Al primo accesso di questa sessione al database Oracle, è necessario [Connect to Oracle](connect-to-oracle.md).  
  
 **Modifica**  
 Selezionare una tabella dall'elenco e selezionare **Modifica** per aprire la finestra di dialogo **Proprietà** per tale tabella in cui è possibile [Modificare le proprietà della tabella](edit-the-table-properties.md).  
  
> [!NOTE]  
>  Non è possibile modificare il mapping dei tipi per le tabelle che dispongono già di tabelle mirror. Questa operazione è possibile unicamente per le tabelle nuove.  
  
 **Rimuovi**  
 Selezionare una tabella dall'elenco e fare clic su **Rimuovi** per rimuovere la tabella dall'istanza di CDC.  
  
## <a name="see-also"></a>Vedere anche  
 [Come modificare le proprietà di istanza di CDC](how-to-edit-the-cdc-instance-properties.md)   
 [Selezionare tabelle e colonne Oracle](select-oracle-tables-and-columns.md)  
  
  
