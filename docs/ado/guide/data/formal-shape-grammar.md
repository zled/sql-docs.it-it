---
title: Grammatica formale forma | Documenti Microsoft
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- shape commands [ADO], shape grammar
- data shaping [ADO], shape grammar
ms.assetid: ea691475-0f03-4abe-a785-b77e77712d1d
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ae47b751e9e62d84188927186f186c6c9d344ce0
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="formal-shape-grammar"></a>Grammatica formale forma
Questa è la grammatica formale per la creazione di qualsiasi comando forma:  
  
-   I termini grammaticali obbligatori sono stringhe di testo delimitate da parentesi quadre ("<>").  
  
-   Termini facoltativi sono delimitati da parentesi quadre ("[]").  
  
-   Alternative sono indicate da una barra ("&#124;").  
  
-   Alternative ripetute sono indicate dai puntini di sospensione ("...").  
  
-   *Alpha* indica una stringa di caratteri alfabetici.  
  
-   *Cifra* indica una stringa di numeri.  
  
-   *Cifra Unicode* indica una stringa di cifre unicode.  
  
 Tutti gli altri termini sono valori letterali.  
  
|Nome|Definizione|  
|----------|----------------|  
|\<comando Shape >|FORMA [\<exp-tabella > [[AS] \<alias >]] [\<forma Azione >]|  
|\<exp-tabella >|{\<testo del comando provider >} &#124;<br /><br /> (\<comando shape >) &#124;<br /><br /> TABELLA \<racchiuso tra virgolette-name > &#124;<br /><br /> \<racchiuso tra virgolette-name >|  
|\<forma Azione >|APPEND \<alias-field-list > &#124;<br /><br /> CALCOLO \<alias-field-list > [BY \<elenco campi >]|  
|\<elenco di campi con alias >|\<alias-field > [, \<alias-field... >]|  
|\<alias-field >|\<campo exp > [[AS] \<alias >]|  
|\<campo exp >|(\<relazione exp >) &#124;<br /><br /> \<exp calcolato > &#124;<br /><br /> \<funzione di aggregazione exp > &#124;<br /><br /> \<nuovo exp >|  
|< relation_exp >|\<exp-tabella > [[AS] \<alias >]<br /><br /> RELATE \<relazione-cond-list >|  
|\<relazione-cond-list >|\<relazione cond > [, \<relazione cond >...]|  
|\<relazione cond >|\<Nome campo > a \<figlio ref >|  
|\<figlio ref >|\<Nome campo > &#124;<br /><br /> PARAMETRO \<-ref param >|  
|\<riferimento a param >|\<numero >|  
|\<elenco di campi >|\<Nome campo > [, \<campo-name >]|  
|\<funzione di aggregazione exp >|SUM (\<nome campo completo >) &#124;<br /><br /> AVG (\<nome campo completo >) &#124;<br /><br /> MIN (\<nome campo completo >) &#124;<br /><br /> MAX (\<nome campo completo >) &#124;<br /><br /> CONTEGGIO (\<alias qualificato > &#124; \<qualified-name >) &#124;<br /><br /> STDEV (\<nome campo completo >) &#124;<br /><br /> QUALSIASI (\<nome campo completo >)|  
|\<exp calcolato >|CALC (\<espressione >)|  
|\<Nome campo completo >|\<alias >. [\<alias >...] \<campo-name >|  
|\<alias >|\<racchiuso tra virgolette-name >|  
|\<Nome campo >|\<racchiuso tra virgolette-name > [[AS] \<alias >]|  
|\<racchiuso tra virgolette-name >|"\<stringa >" &#124;<br /><br /> '\<stringa > "&#124;<br /><br /> [\<stringa >] &#124;<br /><br /> \<nome >|  
|\<nome completo >|alias [.alias]|  
|\<nome >|alfa [alfa &#124; cifra &#124; _ &#124; # &#124;: &#124;...]|  
|\<numero >|cifra [numero]|  
|\<nuovo exp >|NUOVO \<-tipo di campo > [(\<numero > [, \<numero >])]|  
|\<tipo di campo >|Un tipo di dati OLE DB o ADO.|  
|\<stringa >|carattere Unicode [unicode char....]|  
|\<espressione >|Un'espressione Visual Basic applicazioni cui gli operandi sono di altre colonne non CALC nella stessa riga.|  
  
## <a name="see-also"></a>Vedere anche  
 [Accesso alle righe in un Recordset gerarchico](../../../ado/guide/data/accessing-rows-in-a-hierarchical-recordset.md)   
 [Data Shaping Panoramica](../../../ado/guide/data/data-shaping-overview.md)   
 [Provider desiderati per il Data Shaping](../../../ado/guide/data/required-providers-for-data-shaping.md)   
 [Clausola APPEND forma](../../../ado/guide/data/shape-append-clause.md)   
 [Comandi Shape in generale](../../../ado/guide/data/shape-commands-in-general.md)   
 [Clausola COMPUTE forma](../../../ado/guide/data/shape-compute-clause.md)   
 [Le funzioni di Visual Basic](../../../ado/guide/data/visual-basic-for-applications-functions.md)
