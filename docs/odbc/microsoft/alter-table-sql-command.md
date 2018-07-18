---
title: ALTER TABLE - comando SQL | Documenti Microsoft
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
- alter table [ODBC]
ms.assetid: 3a01a291-f4d9-43bc-a725-5a95546ff364
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 255ce0a4e9e06f2cdd20dd8d1e707b7f7823e6bd
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="alter-table---sql-command"></a>ALTER TABLE - comando SQL
A livello di codice modifica la struttura di una tabella.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
ALTER TABLE TableName1  
   ADD | ALTER [COLUMN] FieldName1  
      FieldType [(nFieldWidth [, nPrecision])]  
      [NULL | NOT NULL]  
      [CHECK lExpression1 [ERROR cMessageText1]]  
      [DEFAULT eExpression1]  
      [PRIMARY KEY | UNIQUE]  
      [REFERENCES TableName2 [TAG TagName1]]  
      [NOCPTRANS]  
 - Or -  
ALTER TABLE TableName1  
   ALTER [COLUMN] FieldName2  
      [NULL | NOT NULL]  
      [SET DEFAULT eExpression2]  
      [SET CHECK lExpression2 [ERROR cMessageText2]]  
      [DROP DEFAULT]  
      [DROP CHECK]  
 - Or -  
ALTER TABLE TableName1  
   [DROP [COLUMN] FieldName3]  
   [SET CHECK lExpression3 [ERROR cMessageText3]]  
   [DROP CHECK]  
   [ADD PRIMARY KEY eExpression3 TAG TagName2]  
   [DROP PRIMARY KEY]  
   [ADD UNIQUE eExpression4 [TAG TagName3]]  
   [DROP UNIQUE TAG TagName4]  
   [ADD FOREIGN KEY [eExpression5] TAG TagName4  
      REFERENCES TableName2 [TAG TagName5]]  
   [DROP FOREIGN KEY TAG TagName6 [SAVE]]  
   [RENAME COLUMN FieldName4 TO FieldName5]  
   [NOVALIDATE]  
```  
  
## <a name="arguments"></a>Argomenti  
 *TableName1*  
 Specifica il nome della tabella la cui struttura è stato modificato.  
  
 Aggiungi [colonna] *FieldName1*  
 Specifica il nome del campo da aggiungere.  
  
 ALTER [colonna] *FieldName1*  
 Specifica il nome di un campo esistente da modificare.  
  
 *FieldType* [( *nFieldWidth* [, *nPrecision*]])  
 Specifica il tipo di campo, una larghezza del campo e una precisione di campi (numero di posizioni decimali) per un campo nuovo o modificato.  
  
 *FieldType* è una singola lettera che indica il campo [tipo di dati](../../odbc/microsoft/visual-foxpro-field-data-types.md). Alcuni tipi di dati di campo che è necessario specificare *nFieldWidth* o *nPrecision* o entrambi.  
  
 *nFieldWidth* e *nPrecision* vengono ignorate per D, G, I, G, M, P, T e Y tipi. Per impostazione predefinita, *nPrecision* non è zero (cifre decimali) se *nPrecision* non è incluso per i tipi di B, F e N.  
  
 NULL &#124; NOT NULL  
 Consente o impedisce che i valori null nel campo.  
  
 Se si omette NULL e non NULL, l'impostazione corrente di SET NULL determina se sono consentiti valori null nel campo. Tuttavia, se si omette NULL e non NULL e includa la chiave primaria o una clausola univoco, viene ignorata l'impostazione corrente di SET NULL e il campo non è NULL per impostazione predefinita.  
  
 CONTROLLARE *lExpression1*  
 Specifica una regola di convalida per il campo. *lExpression1* deve restituire un'espressione logica e può essere una funzione definita dall'utente o una stored procedure. Ogni volta che viene aggiunto un record vuoto, viene controllata la regola di convalida. Viene generato un errore se la regola di convalida non consente un valore di campo vuoto in un record accodato.  
  
 ERRORE *cMessageText1*  
 Specifica il messaggio di errore visualizzato quando la regola di convalida del campo genera un errore.  
  
 PREDEFINITO *eExpression1*  
 Specifica un valore predefinito per il campo. Il tipo di dati *eExpression1* deve essere lo stesso come il tipo di dati per il campo.  
  
 PRIMARY KEY  
 Crea un tag di indice primario. Il tag di indice ha lo stesso nome del campo.  
  
 UNIQUE  
 Crea un tag di indice di candidati con lo stesso nome del campo.  
  
> [!NOTE]  
>  Candidato indici (creati specificando l'opzione univoco, fornito per compatibilità con ANSI in ALTER TABLE o CREATE TABLE) diversi da indici creati utilizzando l'opzione univoco nel comando indice. Un indice creato utilizzando il comando di indice UNIQUE consente chiavi duplicate dell'indice; gli indici Candidate non consentono chiavi duplicate dell'indice.  
  
 I valori null e i record duplicati non consentiti in un campo che viene utilizzato per un indice primarie o candidate.  
  
 Se si sta creando un nuovo campo usando Aggiungi colonna, Visual FoxPro non genererà un errore se si crea un indice primarie o candidate per un campo che supporta valori null. Tuttavia, Visual FoxPro genererà un errore se si tenta di immettere un valore null o è duplicato in un campo che viene utilizzato per un indice primarie o candidate.  
  
 Se si modifica un campo esistente e il database primario o candidato è costituita da campi della tabella, Visual FoxPro controlla i campi per vedere se contengono valori null o i record duplicati. In questo caso, Visual FoxPro genera un errore e la tabella non viene modificata.  
  
 I riferimenti *TableName2* TAG *TagName1*  
 Specifica la tabella padre a cui viene stabilita una relazione permanente. TAG *TagName1* specifica il tag di indice della tabella padre in cui si basa la relazione. I nomi di tag di indice possono contenere fino a 10 caratteri.  
  
 NOCPTRANS  
 Impedisce la traduzione in una diversa tabella codici per i campi di tipo carattere e di credito. Se la tabella viene convertita in un'altra tabella codici, i campi per cui è stato specificato NOCPTRANS non vengono convertiti. NOCPTRANS può essere specificato solo per i campi di tipo carattere e di credito.  
  
 L'esempio seguente crea una tabella denominata mytable contenente due campi di tipo carattere e i due campi di dati memo. Il secondo campo di tipo carattere, char2 e il secondo campo memo memo2, includere NOCPTRANS per evitare di traduzione.  
  
```  
CREATE TABLE mytable (char1 C(10), char2 C(10) NOCPTRANS,;  
   memo1 M, memo2 M NOCPTRANS)  
```  
  
 ALTER [colonna] *FieldName2*  
 Specifica il nome di un campo esistente da modificare.  
  
 IMPOSTAZIONE del valore predefinito *eExpression2*  
 Specifica un nuovo valore predefinito per un campo esistente. Il tipo di dati *eExpression2* deve essere lo stesso come il tipo di dati per il campo.  
  
 CONTROLLO di SET *lExpression2*  
 Specifica una nuova regola di convalida per un campo esistente. *lExpression2* deve restituire un'espressione logica e può essere una funzione definita dall'utente o una stored procedure.  
  
 ERRORE *cMessageText2*  
 Specifica il messaggio di errore visualizzato quando la regola di convalida del campo genera un errore. Il messaggio viene visualizzato solo quando i dati vengono modificati all'interno di una finestra di esplorazione o di modifica.  
  
 DROP DEFAULT  
 Rimuove il valore predefinito per un campo esistente.  
  
 CONTROLLO DI RILASCIO  
 Rimuove la regola di convalida per un campo esistente.  
  
 Riepilogo [colonna] *FieldName3*  
 Specifica un campo da rimuovere dalla tabella. Rimozione di un campo dalla tabella rimuove anche regola di convalida e di impostazione del valore del campo predefinito.  
  
 Se le espressioni di trigger o chiave di indice fa riferimento il campo, le espressioni valide quando il campo viene rimosso. In questo caso, un errore non viene generato quando il campo viene rimosso, ma le espressioni di trigger o chiave di indice non valido non genererà errori in fase di esecuzione.  
  
 CONTROLLO di SET *lExpression3*  
 Specifica la regola di convalida della tabella. *lExpression3* deve restituire un'espressione logica e può essere una funzione definita dall'utente o una stored procedure.  
  
 ERRORE *cMessageText3*  
 Specifica il messaggio di errore visualizzato quando la regola di convalida della tabella genera un errore. Il messaggio viene visualizzato solo quando i dati vengono modificati all'interno di una finestra di esplorazione o di modifica.  
  
 CONTROLLO DI RILASCIO  
 Rimuove la regola di convalida della tabella.  
  
 Aggiungi chiave primaria *eExpression3*TAG *TagName2*  
 Aggiunge un indice primario per la tabella. *eExpression3* specifica l'espressione chiave di indice primario, e *TagName2* specifica il nome del tag indice primario. I nomi di tag di indice possono contenere fino a 10 caratteri. Se TAG *TagName2* viene omesso e *eExpression3* è un singolo campo, il tag di indice primario ha lo stesso nome del campo specificato in *eExpression3*.  
  
 ELIMINARE LA CHIAVE PRIMARIA  
 Rimuove l'indice primario e il relativo tag di indice. Poiché una tabella può avere solo una chiave primaria, non è necessario specificare il nome della chiave primaria. Rimozione dell'indice primario elimina inoltre eventuali relazioni permanente in base alla chiave primaria.  
  
 Aggiungi UNIQUE *eExpression4*[TAG *TagName3*]  
 Aggiunge un indice di candidati per la tabella. *eExpression4* specifica l'espressione chiave indice candidato, e *TagName3* specifica il nome del tag indice candidato. I nomi di tag di indice possono contenere fino a 10 caratteri. Se si omette TAG *TagName3* e se *eExpression4* è un singolo campo, il tag di indice candidato ha lo stesso nome del campo specificato in *eExpression4*.  
  
 Identificatore univoco di rilascio *TagName4*  
 Rimuove l'indice candidato e tag di indice. Poiché una tabella può avere più chiavi candidate, è necessario specificare il nome del tag indice candidato.  
  
 Aggiungi chiave esterna [ *eExpression5*] TAG *TagName4*  
 Aggiunge un indice (non primaria) esterno alla tabella. *eExpression5* specifica l'espressione chiave di indice esterna, e *TagName4* specifica il nome del tag indice esterna. I nomi di tag di indice possono contenere fino a 10 caratteri.  
  
 RIFERIMENTI *TableName2*[TAG *TagName5*]  
 Specifica la tabella padre a cui viene stabilita una relazione permanente. Includere TAG *TagName5* per stabilire una relazione in base a un tag di indice esistente per la tabella padre. I nomi di tag di indice possono contenere fino a 10 caratteri. Se si omette TAG *TagName5*, la relazione viene stabilita tramite il tag di indice primario della tabella padre.  
  
 TAG di chiave esterna di rilascio *TagName6*[Salva]  
 Elimina una chiave esterna tag il cui indice è *TagName6*. Se si omette salvataggio, il tag di indice viene eliminato dall'indice struttura. Includere salvare per evitare l'eliminazione del tag indice dall'indice struttura.  
  
 COLONNA RENAME *FieldName4*TO *FieldName5*  
 Consente di modificare il nome di un campo nella tabella. *FieldName4* specifica il nome del campo che è stato rinominato. *FieldName5* specifica il nuovo nome del campo.  
  
> [!CAUTION]  
>  Prestare attenzione durante la ridenominazione di campi tabella poiché le espressioni di indice, le regole di convalida di campi e tabelle, comandi e funzioni possono fare riferimento i nomi di campo originale.  
  
 NOVALIDATE  
 Specifica che Visual FoxPro consente modifiche da apportare alla struttura della tabella. Queste modifiche potrebbero violare l'integrità dei dati nella tabella. Per impostazione predefinita, Visual FoxPro impedisce ALTER TABLE di apportare modifiche che violano l'integrità dei dati nella tabella. Includere NOVALIDATE per eseguire l'override di questo comportamento predefinito.  
  
## <a name="remarks"></a>Osservazioni  
 Per modificare la struttura di una tabella che non è stato aggiunto a un database, è possibile utilizzare ALTER TABLE. Tuttavia, Visual FoxPro genera un errore se si includono l'impostazione predefinita, FOREIGN KEY, chiave primaria, riferimenti o quando si modifica una tabella libera di clausole SET.  
  
 ALTER TABLE può ricompilare la tabella creando una nuova intestazione di tabella e Accodamento di record per l'intestazione della tabella. Modifica il tipo o la larghezza di un campo, ad esempio, potrebbe causare la tabella da ricompilare.  
  
 Dopo che una tabella viene ricompilata, vengono eseguite le regole di convalida campo per tutti i campi il cui tipo o la larghezza viene modificati. Se si modifica il tipo o la larghezza di un campo nella tabella, viene eseguita la regola della tabella.  
  
 Se si modificano le regole di convalida campo o una tabella per una tabella che contiene record, Visual FoxPro testa le nuove regole di convalida campo o una tabella con i dati e genera un avviso con la prima occorrenza di una regola di convalida campo o una tabella o di una violazione di trigger.  
  
 Se la tabella che si modifica in un database, ALTER TABLE - SQL richiede l'uso esclusivo del database. Per aprire un database per l'uso esclusivo, includere esclusivo nel DATABASE di aprire.  
  
## <a name="see-also"></a>Vedere anche  
 [Crea tabella - comando SQL](../../odbc/microsoft/create-table-sql-command.md)   
 [INDEX (comando)](../../odbc/microsoft/index-command.md)
