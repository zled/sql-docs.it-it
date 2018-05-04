---
title: I cursori keyset | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Keyset cursors [ADO]
- cursors [ADO], Keyset
ms.assetid: 14b51b17-6fd9-4146-af45-ca4b0fe6d48a
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6abebe52390c8c3423cd3c41f212236e051e1972
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="keyset-cursors"></a>Cursori keyset
Il cursore keyset fornisce funzionalità tra un valore statico e un cursore dinamico nella capacità di rilevare le modifiche. Un cursore statico, non sempre rileva le modifiche per l'appartenenza e l'ordine del set di risultati. È un cursore dinamico, di rilevare le modifiche ai valori delle righe nel set di risultati.  
  
 Cursori basati su keyset vengono controllati da un set di identificatori univoci (chiavi) noti come keyset. Le chiavi sono costituite da un set di colonne che identificano in modo univoco le righe del set di risultati. Il keyset corrisponde al set di valori di chiave da tutte le righe restituite dall'istruzione della query.  
  
 Con cursori, una chiave è generata, salvata per ogni riga del cursore e memorizzata sulla workstation client o sul server. Quando si accede a ogni riga, la chiave archiviata viene utilizzata per recuperare i valori dei dati corrente dall'origine dati. In un cursore basati su keyset, l'appartenenza al set di risultati è bloccata quando il keyset è completamente popolato. Successivamente, aggiunte o aggiornamenti che interessano l'appartenenza non fanno parte del gruppo di risultati fino a quando non viene riaperta.  
  
 Le modifiche ai valori di dati (apportate dal proprietario del keyset o altri processi) sono visibili quando l'utente scorre il set di risultati. Gli inserimenti eseguiti all'esterno del cursore (da altri processi) sono visibili solo se il cursore viene chiuso e riaperto. Gli inserimenti eseguiti dall'interno del cursore sono visibili alla fine del set di risultati.  
  
 Quando un cursore gestito da keyset tenta di recuperare una riga che è stata eliminata, la riga viene visualizzata come "foro" nel set di risultati. La chiave per la riga è presente il set di chiavi, ma la riga non esiste più nel set di risultati. Se vengono aggiornati i valori di chiave in una riga, la riga viene considerata sono stati eliminati e quindi inserite, tali righe vengono visualizzati anche come fori nel set di risultati. Mentre un cursore gestito da keyset sempre è in grado di individuare le righe eliminate da altri processi, facoltativamente è possibile rimuovere le chiavi per righe. Cursori basati su keyset di eseguire tale operazione non è in grado di rilevare le righe eliminate perché è stato rimosso l'evidenza.  
  
 Un aggiornamento a una colonna chiave equivale all'eliminazione di una vecchia chiave seguita da un inserimento della nuova chiave. Nuovo valore della chiave non è visibile se non è stato eseguito l'aggiornamento tramite il cursore. Se tramite il cursore è stato eseguito l'aggiornamento, il nuovo valore della chiave è visibile alla fine del set di risultati.  
  
 È una variante di cursori definiti cursori a standard basati su keyset. In un cursore standard basati su keyset, l'appartenenza delle righe nel set di risultati e l'ordine delle righe sono fissi all'apertura del cursore, ma le modifiche ai valori che vengono apportate dal proprietario del cursore e il commit delle modifiche apportate da altri processi sono visibili. Se una modifica invalida una riga per l'appartenenza o influisce sull'ordine di una riga, la riga non scompare o spostare, a meno che il cursore viene chiuso e riaperto. I dati inseriti non vengono visualizzati, ma le modifiche ai dati esistenti vengono visualizzati come le righe vengono recuperate.  
  
 Il cursore gestito da keyset è difficile usare correttamente perché la sensibilità alle modifiche dei dati dipende da numerose circostanze diverse, come descritto in precedenza. Tuttavia, se l'applicazione non è attualmente preoccupata aggiornamenti simultanei a livello di codice può gestire le chiavi non valide e deve accedere direttamente a determinate righe con chiave, il cursore gestito da keyset potrebbe funzionare per l'utente. Utilizzare il **su adOpenKeyset** per indicare che si desidera utilizzare un cursore keyset in ADO.  
  
## <a name="see-also"></a>Vedere anche  
 [Cursori forward-Only](../../../ado/guide/data/forward-only-cursors.md)   
 [Cursori statici](../../../ado/guide/data/static-cursors.md)   
 [Cursori dinamici](../../../ado/guide/data/dynamic-cursors.md)
