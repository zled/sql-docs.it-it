---
title: Comando COLLATE SET | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: set collate command [ODBC]
ms.assetid: 00efbcd4-fea8-4061-86a5-82de413cb753
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 73bf988f0ab1b181a75c7569c8b279b36a9b76d8
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="set-collate-command"></a>Comando COLLATE SET
Specifica una sequenza di confronto per i campi di tipo carattere in operazioni di ordinamento e di indicizzazione successive.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SET COLLATE TO cSequenceName  
```  
  
## <a name="arguments"></a>Argomenti  
 *cSequenceName*  
 Specifica una sequenza di confronto. Le opzioni di sequenza di regole di confronto disponibili sono descritte nella tabella seguente.  
  
|Opzioni|Linguaggio|  
|-------------|--------------|  
|OLANDESE|Olandese|  
|GENERAL|Inglese, francese, tedesco, spagnolo moderno, portoghese e altre lingue dell'Europa occidentale|  
|TEDESCO|Ordine della Rubrica telefonica tedesco (DIN)|  
|ISLANDA|Islandese|  
|MACCHINA|Computer (la sequenza di confronto predefinito per le versioni precedenti FoxPro)|  
|NORDAN|Norvegese, danese|  
|SPAGNOLO|Spagnolo tradizionale|  
|SWEFIN|Svedese, finlandese|  
|UNIQWT|Peso univoco|  
  
> [!NOTE]  
>  Quando si specifica l'opzione SPAGNOLA, *ch* è una singola lettera che ordina tra *c* e *d*, e *ll* Ordina tra  *l* e *m*.  
  
 Se si specifica un'opzione della sequenza delle regole di confronto come una stringa di caratteri letterali, sarà necessario racchiudere tra virgolette l'opzione:  
  
```  
SET COLLATE TO "SWEFIN"  
```  
  
 MACCHINA è l'opzione di sequenza di regole di confronto predefinito e si che hanno familiari con gli utenti Xbase sequenza. Caratteri vengono ordinati in cui appaiono nella tabella codici corrente.  
  
 GENERALE potrebbe essere preferibile per gli utenti negli Stati Uniti e occidentale. Caratteri vengono ordinati in cui appaiono nella tabella codici corrente. Nelle versioni FoxPro precedenti alla 2.5, gli indici potrebbero essere stati creati utilizzando il **superiore**() o **inferiore**funzioni () per convertire i campi di tipo carattere a un case coerenza. In FoxPro successive alla 2.5, è invece possibile specificare l'opzione della sequenza generale delle regole di confronto e omettere il **superiore**conversione ().  
  
 Se si specifica un'opzione della sequenza di regole di confronto diverse da computer e se si crea un file IDX, viene sempre creato un compact IDX.  
  
 Utilizzare SET("COLLATE") per restituire la sequenza di confronto correnti.  
  
 È possibile specificare una sequenza di confronto per un'origine dati utilizzando il [la finestra di dialogo programma di installazione ODBC Visual FoxPro](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md) o utilizzando la parola chiave Collate nella stringa di connessione con [SQLDriverConnect](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md). Questo è identico a eseguire il comando seguente:  
  
```  
SET COLLATE TO cSequenceName  
```  
  
## <a name="remarks"></a>Osservazioni  
 SET COLLATE consente alle tabelle di ordine contenente i caratteri accentati per le lingue supportate. La modifica dell'impostazione di SET COLLATE non influisce sulla sequenza di confronto di indici precedentemente aperti. Visual FoxPro gestisce automaticamente gli indici esistenti, che fornisce la flessibilità necessaria per creare molti tipi diversi di indici, anche per lo stesso campo.  
  
 Ad esempio, se un indice viene creato con SET COLLATE impostato su Generale e l'impostazione SET COLLATE viene modificata in seguito sullo spagnolo, l'indice consente di mantenere la sequenza di confronto generali.  
  
## <a name="see-also"></a>Vedere anche  
 [Finestra di dialogo di configurazione ODBC Visual FoxPro](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md)
