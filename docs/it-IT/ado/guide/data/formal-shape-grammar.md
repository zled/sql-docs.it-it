---
title: Grammatica formale forma | Documenti Microsoft
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
- shape commands [ADO], shape grammar
- data shaping [ADO], shape grammar
ms.assetid: ea691475-0f03-4abe-a785-b77e77712d1d
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4283d1858c18cd71e3128df9d58017d2a24cf977
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="formal-shape-grammar"></a>Grammatica formale forma
Questa è la grammatica formale per la creazione di qualsiasi comando forma:  
  
-   I termini grammaticali obbligatori sono stringhe di testo delimitate da parentesi quadre ("<>").  
  
-   Termini facoltativi sono delimitati da parentesi quadre ("[]").  
  
-   Le alternative sono indicate da una barra ("&#124;").  
  
-   Alternative ripetute sono indicate dai puntini di sospensione ("...").  
  
-   *Alpha* indica una stringa di caratteri alfabetici.  
  
-   *Cifra* indica una stringa di numeri.  
  
-   *Cifra Unicode* indica una stringa di cifre unicode.  
  
 Tutti gli altri termini sono valori letterali.  
  
|Nome|Definizione|  
|----------|----------------|  
|\<shape-command>|FORMA [\<exp-tabella > [[AS] \<alias >]] [\<forma Azione >]|  
|\<table-exp>|{\<provider-command-text>} &#124;<br /><br /> (\<comando shape >)&#124;<br /><br /> TABELLA \<racchiuso tra virgolette-name >&#124;<br /><br /> \<racchiuso tra virgolette-name >|  
|\<shape-action>|APPEND \<alias-field-list >&#124;<br /><br /> CALCOLO \<alias-field-list > [BY \<elenco campi >]|  
|\<aliased-field-list>|\<alias-field > [, \<alias-field... >]|  
|\<aliased-field>|\<campo exp > [[AS] \<alias >]|  
|\<field-exp>|(\<relazione exp >)&#124;<br /><br /> \<exp calcolato >&#124;<br /><br /> \<aggregate-exp> &#124;<br /><br /> \<new-exp>|  
|<relation_exp>|\<tabella exp > [[AS] \<alias >]<br /><br /> RELATE \<relazione-cond-list >|  
|\<relation-cond-list>|\<relazione cond > [, \<cond relazione >...]|  
|\<relazione cond >|\<campo-name > a \<figlio ref >|  
|\<child-ref>|\<nome di campo >&#124;<br /><br /> PARAMETRO \<-ref param >|  
|\<param-ref>|\<numero >|  
|\<field-list>|\<nome di campo > [, \<campo-name >]|  
|\<aggregate-exp>|SUM (\<qualified-campo-name >)&#124;<br /><br /> AVG (\<qualified-campo-name >)&#124;<br /><br /> MIN (\<qualified-campo-name >)&#124;<br /><br /> MAX (\<qualified-campo-name >)&#124;<br /><br /> CONTEGGIO (\<alias qualificato a livello > &#124; \<qualified-name >)&#124;<br /><br /> STDEV(\<qualified-field-name>) &#124;<br /><br /> QUALSIASI (\<nome campo completo >)|  
|\<calculated-exp>|CALC (\<espressione >)|  
|\<nome di campo qualificato >|\<alias>.[\<alias>...]\<field-name>|  
|\<alias>|\<racchiuso tra virgolette-name >|  
|\<field-name>|\<racchiuso tra virgolette-name > [[AS] \<alias >]|  
|\<racchiuso tra virgolette-name >|"\<string>" &#124;<br /><br /> '\<string>' &#124;<br /><br /> [\<string>] &#124;<br /><br /> \<Nome >|  
|\<nome qualificato >|alias[.alias...]|  
|\<Nome >|Alpha [alfa &#124; cifre &#124; _ &#124; # &#124; : &#124; ...]|  
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
