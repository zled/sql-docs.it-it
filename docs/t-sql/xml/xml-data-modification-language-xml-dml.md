---
title: Linguaggio (XML DML) | Documenti Microsoft
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- modifying data [SQL Server], XML DML
- XML [SQL Server], DML
- XML DML [SQL Server]
- data modification language [XML DML]
- data modifications [XML DML]
- DML [XML in SQL Server]
- XQuery, XML DML
- xml data type [SQL Server], XML DML
ms.assetid: 20ce50d2-c07b-4e41-93a7-1380d2cd49cb
caps.latest.revision: 29
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 18fb5825297754c59f2824b6f05150ddaed7bb9c
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="xml-data-modification-language-xml-dml"></a>Linguaggio XML di manipolazione dei dati (XML DML)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Il linguaggio XML DML è un'estensione del linguaggio XQuery. Come definito dal consorzio W3C, il linguaggio XQuery non include la parte relativa alla manipolazione dei dati (DML). Il linguaggio XML DML illustrato in questo argomento e il linguaggio XQuery, fornisce un completamente funzionale linguaggio di query e la modifica dei dati che è possibile utilizzare con il **xml** tipo di dati.  
  
 Rispetto al linguaggio XQuery, nel linguaggio XML DML sono state aggiunte le parole chiave con distinzione tra maiuscole e minuscole seguenti:  
  
-   **inserimento**  
  
-   **eliminare**  
  
-   **Sostituire il valore di**  
  
 Come descritto in [tipo di dati XML e le colonne &#40; SQL Server &#41; ](../../relational-databases/xml/xml-data-type-and-columns-sql-server.md), è possibile creare variabili e colonne di **xml** digitare e assegnarvi documenti o frammenti XML. Per modificare o aggiornare queste istanze XML, eseguire le operazioni seguenti:  
  
-   Utilizzare il [tipo di dati xml di metodo Modify ())](../../t-sql/xml/modify-method-xml-data-type.md) del **xml** tipo di dati.  
  
-   Specificare le istruzioni XML DML appropriate all'interno di **Modify ()** metodo.  
  
 Si noti che alcuni attributi non possono essere inseriti o eliminati o non è possibile modificarne il valore. Esempio:  
  
-   Per tipizzato o non tipizzato **xml,** gli attributi sono **xmlns**, **xmlns:\***, e **XML: base**.  
  
-   Per tipizzati **xml** , solo gli attributi sono **xsi: nil**, e **xsi: Type**.  
  
 Sono inoltre valide le restrizioni seguenti:  
  
-   Per tipizzato o non tipizzato **xml**, inserire l'attributo **XML: base** avrà esito negativo.  
  
-   Per tipizzati **xml**, l'eliminazione e modifica di **xsi: nil** attributo avrà esito negativo. Non tipizzato **xml**, è possibile eliminare l'attributo o modificarne il valore.  
  
-   Per tipizzati **xml**, modificando il valore del **xs: Type** attributo avrà esito negativo. Non tipizzato **xml**, è possibile modificare il valore dell'attributo.  
  
 Quando si modifica un'istanza XML tipizzata, il formato finale deve essere un'istanza valida del tipo specifico, in caso contrario verrà restituito un errore di convalida.  
  
## <a name="see-also"></a>Vedere anche  
 [Inserisci &#40; Linguaggio XML DML &#41;](../../t-sql/xml/insert-xml-dml.md)   
 [Elimina &#40; Linguaggio XML DML &#41;](../../t-sql/xml/delete-xml-dml.md)   
 [il valore di sostituzione di &#40; Linguaggio XML DML &#41;](../../t-sql/xml/replace-value-of-xml-dml.md)   
 [Confronto dati XML tipizzati con dati XML non tipizzati](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)   
 [Creare istanze di dati XML](../../relational-databases/xml/create-instances-of-xml-data.md)   
 [metodi con tipo di dati xml](../../t-sql/xml/xml-data-type-methods.md)  
  
  
