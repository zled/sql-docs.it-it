---
title: Finestra di dialogo Salva (non consentito) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.swb.table.tablerecreatenosave.f1
ms.assetid: 7efda8e3-739f-4c97-a497-b8808a0acbea
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b491d5d0bf14c90d813b0fc66c0112eac1ff0e16
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47635299"
---
# <a name="save-not-permitted-dialog-box"></a>Finestra di dialogo Salva (non consentito)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
La finestra di dialogo **Salva** (non consentito) avvisa che il salvataggio delle modifiche non è consentito perché prima devono essere eliminate e ricreate le tabelle elencate.  
  
Per le azioni seguenti può essere necessario ricreare una tabella:  
  
-   Aggiunta di una nuova colonna a metà tabella  
  
-   Eliminazione di una colonna  
  
-   Modifica dell'ammissione di valori Null nella colonna  
  
-   Modifica dell'ordine delle colonne  
  
-   Modifica del tipo di dati di una colonna  
  
Per modificare questa opzione, scegliere **Opzioni** dal menu **Strumenti**, espandere **Finestre di progettazione**, quindi fare clic su **Progettazione tabelle e Progettazione database**. Selezionare o deselezionare la casella di controllo **Impedisci il salvataggio delle modifiche per cui è necessario ricreare la tabella** .  
  
