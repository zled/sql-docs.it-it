---
title: Buffer | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- input buffers [ODBC]
- length/indicator buffers [ODBC]
- output buffers [ODBC]
- buffers [ODBC], about buffers
- application buffers [ODBC]
- buffers [ODBC]
ms.assetid: 42c5226c-cb40-4d1e-809f-2ea50ce6bd55
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0d63aa103ac71aa89d245f6b8e4770b2c4943f2a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="buffers"></a>Buffer
Un buffer è qualsiasi porzione di memoria dell'applicazione utilizzata per passare dati tra l'applicazione e il driver. Ad esempio, i buffer dell'applicazione può essere associato a, o *associato,* colonne con set di risultati **SQLBindCol**. Come viene recuperata ogni riga, i dati vengono restituiti per ogni colonna in questi buffer. *I buffer di input* vengono utilizzati per passare dati dall'applicazione al driver; *buffer di output* vengono utilizzate per restituire i dati dal driver per l'applicazione.  
  
> [!NOTE]  
>  Se una funzione ODBC restituisce SQL_ERROR, il contenuto di tutti gli argomenti di output a tale funzione è indefinito.  
  
 Questa sezione riguarda stesso principalmente con buffer di tipo non determinato. Gli indirizzi di questi buffer vengono visualizzati come argomenti di tipo SQLPOINTER, ad esempio il *TargetValuePtr* argomento **SQLBindCol**. Tuttavia, alcuni degli elementi descritti in questo caso, ad esempio gli argomenti utilizzati con buffer, si applicano anche agli argomenti utilizzati per passare stringhe al driver, ad esempio il *TableName* argomento **SQLTables**.  
  
 In genere, questi buffer entrano nelle coppie. *Buffer di dati* sono consente di passare i dati stessi, mentre *buffer di lunghezza/indicatore* vengono utilizzati per passare la lunghezza dei dati nel buffer di dati o un valore speciale, ad esempio SQL_NULL_DATA, che indica che i dati sono NULL. La lunghezza dei dati in un buffer di dati è diversa dalla lunghezza del buffer di dati stesso. Nella figura seguente viene illustrata la relazione tra il buffer dei dati e il buffer di lunghezza/indicatore.  
  
 ![Buffer dei dati e lunghezza&#47;buffer di indicatore](../../../odbc/reference/develop-app/media/pr09.gif "pr09")  
  
 Ogni volta che il buffer dei dati contiene dati a lunghezza variabile, ad esempio carattere o dati binari, è necessario un buffer di lunghezza/indicatore. Se il buffer dei dati contiene dati a lunghezza fissa, ad esempio una struttura di tipo integer o data, è necessario un buffer di lunghezza/indicatore solo per passare i valori di indicatore perché la lunghezza dei dati è già nota. Se un'applicazione utilizza un buffer di lunghezza/indicatore con dati a lunghezza fissa, il driver ignora qualsiasi lunghezza passata in essa contenuti.  
  
 La lunghezza del buffer di dati e i dati in che esso contenuti è misurata in byte, anziché i caratteri. Questa distinzione è importante per programmi che utilizzano le stringhe ANSI perché lunghezza in byte e i caratteri è uguali.  
  
 Quando il buffer dei dati rappresenta un campo di descrizione definito dal driver, diagnostica campo o attributo, l'applicazione deve indicare a gestione Driver la natura dell'argomento di funzione che indica il valore per il campo o attributo. L'applicazione esegue questa operazione impostando l'argomento di lunghezza in qualsiasi chiamata di funzione che imposta il campo o attributo in uno dei valori seguenti. (Lo stesso vale per le funzioni che recuperano i valori del campo o attributo, con l'eccezione che fa riferimento l'argomento per i valori per la funzione di impostazione in argomento stesso.)  
  
-   Se l'argomento della funzione che indica il valore per il campo o attributo è un puntatore a una stringa di caratteri di *lunghezza* argomento è la lunghezza della stringa o SQL_NTS.  
  
-   Se l'argomento della funzione che indica il valore per il campo o attributo è un puntatore a un buffer binario, viene visualizzato il risultato di SQL_LEN_BINARY_ATTR (*lunghezza*) macro di *lunghezza* argomento. In questo modo un valore negativo nel *lunghezza* argomento.  
  
-   Se l'argomento della funzione che indica il valore per il campo o attributo è un puntatore a un valore diverso da una stringa di caratteri o una stringa binaria, il *lunghezza* argomento deve avere il valore SQL_IS_POINTER.  
  
-   Se l'argomento della funzione che indica il valore per il campo o attributo contiene un valore di lunghezza fissa, il *lunghezza* argomento è SQL_IS_INTEGER, SQL_IS_UINTEGER, SQL_IS_SMALLINT o SQL_ISI_USMALLINT, come appropriato.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Buffer posticipati](../../../odbc/reference/develop-app/deferred-buffers.md)  
  
-   [Allocazione e liberazione di buffer](../../../odbc/reference/develop-app/allocating-and-freeing-buffers.md)  
  
-   [Utilizzo dei buffer dei dati](../../../odbc/reference/develop-app/using-data-buffers.md)
