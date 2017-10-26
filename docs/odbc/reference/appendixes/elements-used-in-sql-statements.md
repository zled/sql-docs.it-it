---
title: Gli elementi utilizzati nelle istruzioni SQL | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL statements [ODBC], elements supported
- minimum SQL syntax supported [ODBC]
- ODBC drivers [ODBC], minimum SQL syntax supported
ms.assetid: 85777525-1555-4731-8309-63a464c6b43a
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c29dcd40090a380c124a0c72b07d5993d4295829
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="elements-used-in-sql-statements"></a>Elementi utilizzati nelle istruzioni SQL
Gli elementi seguenti sono utilizzati nelle istruzioni SQL elencate in precedenza.  
  
## <a name="element"></a>Elemento  
 *Identificatore di tabella di base* :: = *nome definito dall'utente*  
  
 *Nome-tabella di base* :: = *identificatore di tabella di base*  
  
 *valore booleano fattore* :: = [NOT] *booleano primario*  
  
 *valore booleano primario* :: = confronto*-predicato* &#124; ( *condizione di ricerca* )  
  
 *valore booleano termine* :: = *boolean-factor* [AND *in termini di valore booleano*]  
  
 *valore letterale stringa di caratteri* :: = ' {*carattere*}... ' (*carattere* è qualsiasi carattere nel set di caratteri dell'origine dati/driver. Per includere una valore letterale virgoletta singola (') nel valore letterale di stringa di caratteri, utilizzare due virgolette singole letterale [' '].)  
  
 *Identificatore della colonna* :: = *nome definito dall'utente*  
  
 *nome della colonna* :: = [*-nome della tabella*.] *identificatore di colonna*  
  
 *operatore di confronto* :: = < &#124; > &#124; \<= &#124; > = &#124; = &#124; <>  
  
 *predicato di confronto* :: = *espressione* espressione di operatore di confronto  
  
 *tipo di dati* :: = *stringa-tipo di carattere* (*tipo di carattere stringa* è qualsiasi tipo di dati per cui la colonna "" DATA_TYPE"" nel set di risultati restituiti da SQLGetTypeInfo entrambi SQL_CHAR o SQL_VARCHAR.)  
  
 *cifra* :: = 0 &#124; 1 &#124; 2 &#124; 3 &#124; 5 4 &#124; &#124; 7 6 &#124; &#124; 8 &#124; 9  
  
 *parametro dinamico* :: =?  
  
 *espressione* :: = termine &#124; espressione {+ &#124; –} termine  
  
 *fattore di* :: = [*+*&#124;* –*]*primario*  
  
 *valore di inserimento* :: =  
  
 *parametro dinamico*  
  
 &#124; *letterale*  
  
 &#124; NULL  
  
 &#124; UTENTE  
  
 *lettera* :: = *lettere lower-case &#124; superiore-lettere maiuscole*  
  
 *valore letterale* :: = *valore letterale stringa di caratteri*  
  
 *Lower-case-lettera* :: = un &#124; b &#124; c &#124; d &#124; e &#124; f &#124; g &#124; e &#124; i &#124; j &#124; k &#124; l &#124; m &#124; n &#124; o &#124; p &#124; q &#124; r &#124; s &#124; t &#124; u &#124; v &#124; in w &#124; x &#124; y &#124; z  
  
 *clausola Order by* :: = ORDER BY *specifica di ordinamento* [, *specifica di ordinamento*]...  
  
 *primario* :: = *nome colonna*  
  
 &#124; *dinamico-parametro*  
  
 &#124; *letterale*  
  
 &#124; ( *espressione* )  
  
 *condizione di ricerca* :: = *booleano termine* [o *condizione di ricerca*]  
  
 *elenco SELECT* :: = \* &#124; *selezionare sottoelenco* [, *selezionare sottoelenco*]...  (*elenco select* non possono contenere parametri.)  
  
 *Selezionare sottoelenco* :: = *espressione*  
  
 *Specifica di ordinamento* :: = {*intero senza segno &#124; nome della colonna*} [*ASC &#124; DESC*]  
  
 *Identificatore di tabella* :: = *nome definito dall'utente*  
  
 *nome di tabella* :: = *identificatore di tabella*  
  
 *riferimento alla tabella* :: = *-nome della tabella*  
  
 *elenco di riferimenti tabella* :: = *riferimento alla tabella* [,*riferimento alla tabella*]...  
  
 *termine* :: = *fattore* &#124; *termine* {\*&#124;* / *} *factor*  
  
 *intero senza segno* :: = {*cifra*}  
  
 *lettera di case superiore* :: = *A &#124; B &#124; C &#124; D &#124; E &#124; F &#124; G &#124; E &#124; &#124; J &#124; Manti &#124; L &#124; M &#124; N &#124; O &#124; P &#124; Q &#124; R &#124; S &#124; T &#124; U &#124; V &#124; In W &#124; X &#124; Y &#124; Z*  
  
 *nome definito dall'utente* :: = *lettera*[*cifra* &#124; *lettera* &#124; *_*]...

