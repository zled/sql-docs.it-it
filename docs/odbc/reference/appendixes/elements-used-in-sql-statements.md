---
title: Gli elementi utilizzati nelle istruzioni SQL | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], elements supported
- minimum SQL syntax supported [ODBC]
- ODBC drivers [ODBC], minimum SQL syntax supported
ms.assetid: 85777525-1555-4731-8309-63a464c6b43a
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 77b7fdcfbc91e63451615b20c7eedf2748f687c8
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32909706"
---
# <a name="elements-used-in-sql-statements"></a>Elementi utilizzati nelle istruzioni SQL
Gli elementi seguenti sono utilizzati nelle istruzioni SQL elencate in precedenza.  
  
## <a name="element"></a>Elemento  
 *Identificatore di tabella di base* :: = *nome definito dall'utente*  
  
 *nome di tabella di base* :: = *identificatore di tabella di base*  
  
 *valore booleano fattore* :: = [NOT] *boolean primario*  
  
 *valore booleano-primary* :: = confronto *-predicato* &#124; ( *condizione di ricerca* )  
  
 *in termini di valore booleano* :: = *fattore di valore booleano* [AND *boolean termine*]  
  
 *valore letterale stringa di caratteri* :: = "{*carattere*}... ' (*carattere* è qualsiasi carattere nel set di caratteri dell'origine dati/driver. Per includere una valore letterale virgoletta singola (') nel valore letterale di stringa di caratteri, utilizzare due virgolette singole letterale [' '].)  
  
 *Identificatore della colonna* :: = *nome definito dall'utente*  
  
 *Nome colonna* :: = [*-nome della tabella*.] *identificatore di colonna*  
  
 *operatore di confronto* :: = < &#124; > &#124; \<= &#124; > = &#124; = &#124; <>  
  
 *predicato di confronto* :: = *espressione* espressione di operatore di confronto  
  
 *tipo di dati* :: = *-stringa-tipo di carattere* (*-stringa-tipo di carattere* è qualsiasi tipo di dati per cui la colonna "" DATA_TYPE"" nel set di risultati restituiti da SQLGetTypeInfo entrambi SQL_CHAR o SQL_VARCHAR.)  
  
 *cifra* :: = 0 &#124; 1 &#124; 2 &#124; 3 &#124; 4 &#124; 5 &#124; 6 &#124; 7 &#124; 8 &#124; 9  
  
 *parametro dinamico* :: =?  
  
 *espressione* :: = termine &#124; espressione {+&#124;–} termine  
  
 *fattore* :: = [*+*&#124;*–*]*primario*  
  
 *valore di inserimento* :: =  
  
 *parametro dinamico*  
  
 &#124;*letterale*  
  
 &AMP;#124;NULL  
  
 &AMP;#124;UTENTE  
  
 *lettera* :: = *lower-case-lettera &#124; superiore-lettere maiuscole*  
  
 *valore letterale* :: = *valore letterale stringa di caratteri*  
  
 *Lower-case-lettera* :: = un &#124; b &#124; c &#124; 1!d &#124; e &#124; f &#124; c &#124; h &#124; i &#124; j &#124; k &#124; l &#124; m &#124; n &#124; o &#124; p &#124; q &#124; r &#124; s &#124; t &#124; u &#124; v &#124; w &#124; x &#124; y &#124; z  
  
 *clausola Order by* :: = ORDER BY *specifica di ordinamento* [, *specifica di ordinamento*]...  
  
 *primario* :: = *-nome della colonna*  
  
 &#124;*parametro dinamico*  
  
 &#124;*letterale*  
  
 &#124;( *espressione* )  
  
 *condizione di ricerca* :: = *boolean termine* [o *condizione di ricerca*]  
  
 *selezione-list* :: = \* &#124; *select sottoelenco* [, *selezionare sottoelenco*]...  (*elenco select* non possono contenere parametri.)  
  
 *Selezionare sottoelenco* :: = *espressione*  
  
 *Specifica di ordinamento* :: = {*integer non firmati &#124; nome di colonna*} [*ASC &#124; DESC*]  
  
 *Identificatore di tabella* :: = *nome definito dall'utente*  
  
 *nome di tabella* :: = *identificatore di tabella*  
  
 *riferimento alla tabella* :: = *-nome della tabella*  
  
 *elenco di riferimenti tabella* :: = *riferimento alla tabella* [,*riferimento alla tabella*]...  
  
 *termine* :: = *fattore* &#124; *termine* {\*&#124;*/*} *factor*  
  
 *intero senza segno* :: = {*cifre*}  
  
 *superiore-lettere maiuscole* :: = *A &#124; B &#124; C &#124; 1!d &#124; E &#124; F &#124; G &#124; H &#124; è &#124; J &#124; K &#124; L &#124; M &#124; N &#124; O &#124; &#124;Q &#124; R &#124; S &#124; T &#124; U &#124; V &#124; W &#124; X &#124; Y &#124; Z*  
  
 *nome definito dall'utente* :: = *lettera*[*cifra* &#124; *lettera* &#124; *_*]...
