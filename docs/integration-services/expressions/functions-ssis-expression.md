---
title: Funzioni (espressione SSIS) | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- functions [Integration Services]
- expressions [Integration Services], functions
- string functions
- SQL Server Integration Services, functions
- SSIS, functions
ms.assetid: e9a41a31-94f4-46a4-b737-c707dd59ce48
caps.latest.revision: 36
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: d147ad369495c4046e4387dca7abcec5e533c2af
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="functions-ssis-expression"></a>Funzioni (espressione SSIS)
  Nel linguaggio delle espressioni è incluso un set di funzioni che è possibile utilizzare nelle espressioni. Un'espressione può contenere anche una sola funzione, ma in genere in un'espressione vengono utilizzate più funzioni, in combinazione con vari operatori.  
  
 Le funzioni disponibili possono essere suddivise nelle categorie seguenti:  
  
-   Funzioni matematiche. Eseguono calcoli basati su valori di input numerici specificati come parametri e restituiscono valori numerici.  
  
-   Funzioni per i valori stringa. Eseguono operazioni su valori di input di tipo stringa o esadecimale e restituiscono un valore stringa o numerico.  
  
-   Funzioni di data e ora. Eseguono operazioni su valori di data e ora e restituiscono valori stringa, numerici o di data e ora.  
  
-   Funzioni di sistema. Restituiscono informazioni relative a un'espressione.  
  
 Il linguaggio delle espressioni include le funzioni matematiche seguenti.  
  
|Funzione|Description|  
|--------------|-----------------|  
|[ABS &#40; Espressione SSIS &#41;](../../integration-services/expressions/abs-ssis-expression.md)|Restituisce il valore positivo assoluto di un'espressione numerica.|  
|[EXP &#40; Espressione SSIS &#41;](../../integration-services/expressions/exp-ssis-expression.md)|Restituisce il valore della base e elevato all'espressione specificata.|  
|[CEILING &#40; Espressione SSIS &#41;](../../integration-services/expressions/ceiling-ssis-expression.md)|Restituisce il più piccolo valore integer maggiore o uguale a un'espressione numerica specificata.|  
|[FLOOR &#40; Espressione SSIS &#41;](../../integration-services/expressions/floor-ssis-expression.md)|Restituisce il più alto valore integer minore o uguale a un'espressione numerica specificata.|  
|[LN &#40; Espressione SSIS &#41;](../../integration-services/expressions/ln-ssis-expression.md)|Restituisce il logaritmo naturale di un'espressione numerica.|  
|[LOG &#40; Espressione SSIS &#41;](../../integration-services/expressions/log-ssis-expression.md)|Viene restituito il logaritmo in base 10 di un'espressione numerica.|  
|[POWER &#40; Espressione SSIS &#41;](../../integration-services/expressions/power-ssis-expression.md)|Restituisce il risultato dell'elevamento a potenza di un'espressione numerica.|  
|[ROUND &#40; Espressione SSIS &#41;](../../integration-services/expressions/round-ssis-expression.md)|Restituisce un'espressione numerica arrotondata alla lunghezza o alla precisione specificata. .|  
|[SIGN &#40; Espressione SSIS &#41;](../../integration-services/expressions/sign-ssis-expression.md)|Restituisce il segno positivo (+), negativo (-) o zero (0) di un'espressione numerica.|  
|[QUADRATO &#40; Espressione SSIS &#41;](../../integration-services/expressions/square-ssis-expression.md)|Restituisce il quadrato di un'espressione numerica.|  
|[SQRT &#40; Espressione SSIS &#41;](../../integration-services/expressions/sqrt-ssis-expression.md)|Restituisce la radice quadrata di un'espressione numerica.|  
  
 L'analizzatore di espressioni include le funzioni per i valori stringa seguenti.  
  
|Funzione|Description|  
|--------------|-----------------|  
|[Punti di codice &#40; Espressione SSIS &#41;](../../integration-services/expressions/codepoint-ssis-expression.md)|Restituisce il codice Unicode corrispondente al primo carattere a sinistra in una stringa di caratteri.|  
|[FINDSTRING &#40; Espressione SSIS &#41;](../../integration-services/expressions/findstring-ssis-expression.md)|Restituisce l'indice in base uno dell'occorrenza specificata di una determinata stringa di caratteri in un'espressione.|  
|[HEX &#40; Espressione SSIS &#41;](../../integration-services/expressions/hex-ssis-expression.md)|Viene restituita una stringa che rappresenta il valore esadecimale di un valore integer.|  
|[LEN &#40; Espressione SSIS &#41;](../../integration-services/expressions/len-ssis-expression.md)|Viene restituito il numero di caratteri in un'espressione di caratteri.|  
|[SINISTRA &#40; Espressione SSIS &#41;](../../integration-services/expressions/left-ssis-expression.md)|Viene restituito il numero specificato di caratteri della parte più a sinistra dell'espressione di caratteri indicata.|  
|[INFERIORE &#40; Espressione SSIS &#41;](../../integration-services/expressions/lower-ssis-expression.md)|Viene restituita un'espressione di caratteri dopo aver convertito i caratteri maiuscoli in caratteri minuscoli.|  
|[LTRIM &#40; Espressione SSIS &#41;](../../integration-services/expressions/ltrim-ssis-expression.md)|Restituisce un'espressione di caratteri dopo aver rimosso gli spazi iniziali.|  
|[Sostituisci &#40; Espressione SSIS &#41;](../../integration-services/expressions/replace-ssis-expression.md)|Restituisce un'espressione di caratteri dopo aver sostituito una stringa nell'espressione con un'altra stringa o una stringa vuota.|  
|[REPLICA &#40; Espressione SSIS &#41;](../../integration-services/expressions/replicate-ssis-expression.md)|Viene restituita un'espressione di caratteri ripetuta per il numero di volte specificato.|  
|[REVERSE &#40; Espressione SSIS &#41;](../../integration-services/expressions/reverse-ssis-expression.md)|Viene restituita un'espressione di caratteri in ordine inverso.|  
|[DESTRA &#40; Espressione SSIS &#41;](../../integration-services/expressions/right-ssis-expression.md)|Viene restituito il numero specificato di caratteri della parte più a destra dell'espressione di caratteri indicata.|  
|[RTRIM &#40; Espressione SSIS &#41;](../../integration-services/expressions/rtrim-ssis-expression.md)|Viene restituita un'espressione di caratteri dopo aver rimosso gli spazi finali.|  
|[SOTTOSTRINGA &#40; Espressione SSIS &#41;](../../integration-services/expressions/substring-ssis-expression.md)|Restituisce parte di un'espressione di caratteri.|  
|[TRIM &#40; Espressione SSIS &#41;](../../integration-services/expressions/trim-ssis-expression.md)|Restituisce un'espressione di caratteri dopo aver rimosso gli spazi iniziali e finali.|  
|[Angolo &#40; Espressione SSIS &#41;](../../integration-services/expressions/upper-ssis-expression.md)|Restituisce un'espressione di caratteri dopo aver convertito i caratteri minuscoli in caratteri maiuscoli.|  
  
 L'analizzatore di espressioni fornisce le funzioni di data e ora seguenti.  
  
|Funzione|Description|  
|--------------|-----------------|  
|[DATEADD &#40; Espressione SSIS &#41;](../../integration-services/expressions/dateadd-ssis-expression.md)|Restituisce un nuovo valore DT_DBTIMESTAMP ottenuto aggiungendo una data o un intervallo di tempo a una data specificata.|  
|[DATEDIFF &#40; Espressione SSIS &#41;](../../integration-services/expressions/datediff-ssis-expression.md)|Restituisce il numero di unità di data e ora trascorse tra due date specificate.|  
|[DATEPART &#40; Espressione SSIS &#41;](../../integration-services/expressions/datepart-ssis-expression.md)|Restituisce un valore integer che rappresenta una parte di una data.|  
|[GIORNO &#40; Espressione SSIS &#41;](../../integration-services/expressions/day-ssis-expression.md)|Restituisce un valore integer che rappresenta il giorno nella data specificata.|  
|[GETDATE &#40; Espressione SSIS &#41;](../../integration-services/expressions/getdate-ssis-expression.md)|Restituisce la data di sistema corrente.|  
|[GETUTCDATE &#40; Espressione SSIS &#41;](../../integration-services/expressions/getutcdate-ssis-expression.md)|Restituisce la data corrente del sistema in base all'ora UTC (Universal Time Coordinate o ora di Greenwich).|  
|[MESE &#40; Espressione SSIS &#41;](../../integration-services/expressions/month-ssis-expression.md)|Restituisce un valore integer che rappresenta il mese nella data specificata.|  
|[ANNO &#40; Espressione SSIS &#41;](../../integration-services/expressions/year-ssis-expression.md)|Restituisce un valore integer che rappresenta l'anno nella data specificata.|  
  
 L'analizzatore di espressioni include le funzioni Null seguenti.  
  
|Funzione|Description|  
|--------------|-----------------|  
|[ISNULL &#40; Espressione SSIS &#41;](../../integration-services/expressions/isnull-ssis-expression.md)|Restituisce un risultato booleano che varia a seconda che un'espressione abbia o meno un valore Null.|  
|[NULL &#40; Espressione SSIS &#41;](../../integration-services/expressions/null-ssis-expression.md)|Restituisce un valore Null di un tipo di dati richiesto.|  
  
 I nomi delle espressioni sono indicati in maiuscolo, ma non viene fatta distinzione tra maiuscole e minuscole. È ad esempio possibile utilizzare indifferentemente "null" o "NULL".  
  
## <a name="see-also"></a>Vedere anche  
 [Operatori &#40; Espressione SSIS &#41;](../../integration-services/expressions/operators-ssis-expression.md)   
 [Esempi di espressioni di servizi di integrazione avanzata](../../integration-services/expressions/examples-of-advanced-integration-services-expressions.md)   
 [Integration Services &#40; SSIS &#41; Espressioni](../../integration-services/expressions/integration-services-ssis-expressions.md)  
  
  

