---
title: Grammatica formale forma | Documenti Microsoft
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
- shape commands [ADO], shape grammar
- data shaping [ADO], shape grammar
ms.assetid: ea691475-0f03-4abe-a785-b77e77712d1d
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f9eb99feba381701f7e590add3906cd0285b2720
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
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
|\<shape-command>|FORMA [\<exp-tabella > [[AS] \<alias >]] [\<forma Azione >]|  
|\<table-exp>|{\<provider-command-text>} &#124;<br /><br /> (\<shape-command>) &#124;<br /><br /> TABELLA \<racchiuso tra virgolette-name > &#124;<br /><br /> \<racchiuso tra virgolette-name >|  
|\<shape-action>|APPEND \<alias-field-list > &#124;<br /><br /> CALCOLO \<alias-field-list > [BY \<elenco campi >]|  
|\<aliased-field-list>|\<aliased-field> [, \<aliased-field...>]|  
|\<aliased-field>|\<field-exp> [[AS] \<alias>]|  
|\<field-exp>|(\<relation-exp>) &#124;<br /><br /> \<calculated-exp> &#124;<br /><br /> \<aggregate-exp> &#124;<br /><br /> \<new-exp>|  
|<relation_exp>|\<table-exp> [[AS] \<alias>]<br /><br /> RELATE \<relazione-cond-list >|  
|\<relation-cond-list>|\<relazione cond > [, \<relazione cond >...]|  
|\<relation-cond>|\<Nome campo > a \<figlio ref >|  
|\<child-ref>|\<field-name> &#124;<br /><br /> PARAMETRO \<-ref param >|  
|\<param-ref>|\<numero >|  
|\<field-list>|\<field-name> [, \<field-name>]|  
|\<aggregate-exp>|SUM (\<nome campo completo >) &#124;<br /><br /> AVG(\<qualified-field-name>) &#124;<br /><br /> MIN (\<nome campo completo >) &#124;<br /><br /> MAX(\<qualified-field-name>) &#124;<br /><br /> COUNT(\<qualified-alias> &#124; \<qualified-name>) &#124;<br /><br /> STDEV(\<qualified-field-name>) &#124;<br /><br /> QUALSIASI (\<nome campo completo >)|  
|\<calculated-exp>|CALC(\<expression>)|  
|\<qualified-field-name>|\<alias>.[\<alias>...]\<field-name>|  
|\<alias>|\<racchiuso tra virgolette-name >|  
|\<field-name>|\<racchiuso tra virgolette-name > [[AS] \<alias >]|  
|\<racchiuso tra virgolette-name >|"\<string>" &#124;<br /><br /> '\<string>' &#124;<br /><br /> [\<string>] &#124;<br /><br /> \<nome >|  
|\<qualified-name>|alias[.alias...]|  
|\<nome >|alpha [ alpha &#124; digit &#124; _ &#124; # &#124; : &#124; ...]|  
|\<numero >|cifra [numero]|  
|\<new-exp>|NUOVO \<-tipo di campo > [(\<numero > [, \<numero >])]|  
|\<field-type>|Un tipo di dati OLE DB o ADO.|  
|\<string>|carattere Unicode [unicode char....]|  
|\<expression>|Un'espressione Visual Basic applicazioni cui gli operandi sono di altre colonne non CALC nella stessa riga.|  
  
## <a name="see-also"></a>Vedere anche  
 [Accesso alle righe in un Recordset gerarchico](../../../ado/guide/data/accessing-rows-in-a-hierarchical-recordset.md)   
 [Data Shaping Panoramica](../../../ado/guide/data/data-shaping-overview.md)   
 [Provider desiderati per il Data Shaping](../../../ado/guide/data/required-providers-for-data-shaping.md)   
 [Clausola APPEND forma](../../../ado/guide/data/shape-append-clause.md)   
 [Comandi Shape in generale](../../../ado/guide/data/shape-commands-in-general.md)   
 [Clausola COMPUTE forma](../../../ado/guide/data/shape-compute-clause.md)   
 [Funzioni di Visual Basic, Applications Edition](../../../ado/guide/data/visual-basic-for-applications-functions.md)
