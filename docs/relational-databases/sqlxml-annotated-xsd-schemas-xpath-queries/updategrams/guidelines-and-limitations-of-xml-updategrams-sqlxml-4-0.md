---
title: Linee guida e limitazioni di Updategram XML (SQLXML 4.0) | Documenti Microsoft
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: sqlxml
ms.reviewer: ''
ms.suite: sql
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- updategrams [SQLXML], about updategrams
ms.assetid: b5231859-14e2-4276-bc17-db2817b6f235
caps.latest.revision: 31
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 744bab53401852303e04c6ffa665d37557a9db8e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="guidelines-and-limitations-of-xml-updategrams-sqlxml-40"></a>Linee guida e limitazioni per gli updategram XML (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Quando si utilizzano updategram XML, tenere presenti le considerazioni seguenti:  
  
-   Se si utilizza un updategram per un'operazione di inserimento con solo una singola coppia di  **\<prima >** e  **\<dopo >** blocchi, il  **\<prima >** blocco può essere omesso. Viceversa, in caso di un'operazione di eliminazione, il  **\<dopo >** blocco può essere omesso.  
  
-   Se si utilizza un updategram con più  **\<prima >** e  **\<dopo >** in blocco il  **\<sincronizzazione >** tag, entrambi  **\<prima >** blocchi e  **\<dopo >** per modulo, è necessario specificare i blocchi  **\<prima >** e  **\<dopo >** coppie.  
  
-   Gli aggiornamenti in un updategram vengono applicati alla vista XML fornita da XML Schema. Ai fini della corretta esecuzione del mapping predefinito, è pertanto necessario specificare il nome del file dello schema nell'updategram o, se il nome di file non viene fornito, i nomi di elemento e di attributo devono corrispondere ai nomi di tabella e di colonna nel database.  
  
-   SQLXML 4.0 richiede che tutti i valori di colonna in un updategram vengano mappati in modo esplicito nello schema (XDR o XSD) fornito per creare la vista XML per i relativi elementi figlio. Questo comportamento differisce dalle versioni precedenti di SQLXML che è consentito un valore per una colonna non mappata nello schema se definita in modo implicito come parte della chiave esterna in un **SQL: Relationship** annotazione. Si noti che questa modifica non influisce sulla propagazione dei valori di chiave primaria negli elementi figlio, che si verifica tuttora per SQLXML 4.0 se non viene specificato in modo esplicito alcun valore per l'elemento figlio.  
  
-   Se si utilizza un updategram per modificare i dati in una colonna di dati binari (ad esempio il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **immagine** tipo di dati), è necessario fornire uno schema di mapping in cui il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tipo di dati (ad esempio, **SQL: DataType = "image"** ) e il tipo di dati XML (ad esempio, **dt: Type = "binhex"** o **dt: Type = "binbase64**) deve essere specificato. I dati per la colonna binaria devono essere specificati nell'updategram. il **SQL: URL-codificare** annotazione specificata nello schema di mapping viene ignorata dall'updategram.  
  
-   Quando si scrive uno schema XSD, se il valore specificato per il **SQL: relation** o **SQL: field** annotazione include un carattere speciale, ad esempio un carattere di spazio (ad esempio, in "Order Details" nome della tabella), questo valore deve essere racchiuso tra parentesi (ad esempio, "[Dettagli ordine]").  
  
-   Quando si utilizzano updategram, le relazioni a catena non sono supportate. Se, ad esempio, le tabelle A e C sono correlate tramite una relazione a catena che utilizza la tabella B, si verifica l'errore seguente quando si tenta di eseguire l'updategram:  
  
    ```  
    There is an inconsistency in the schema provided.  
    ```  
  
     Anche se lo schema e l'updategram sono entrambi altrimenti corretti e hanno un formato valido, l'errore si verifica se è presente una relazione a catena.  
  
-   Gli updategram non permettono il passaggio di **immagine** tipo di dati come parametri durante gli aggiornamenti.  
  
-   Tipi di oggetto binario di grandi dimensioni (BLOB) come **text/ntext** e le immagini non devono essere utilizzati nel  **\<prima >** blocco quando si utilizzano updategram, perché in questo caso verrà inclusi per l'utilizzo in controllo della concorrenza. Ciò può provocare problemi con [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] a causa delle limitazioni applicate al confronto per i tipi BLOB. Ad esempio, viene utilizzata la parola chiave LIKE nella clausola WHERE per il confronto tra le colonne di **testo** del tipo di dati; tuttavia, i confronti avrà esito negativo nel caso di tipi BLOB in cui le dimensioni dei dati sono maggiore di 8 KB.  
  
-   Caratteri speciali nel **ntext** dati possono provocare problemi con SQLXML 4.0 a causa delle limitazioni applicate al confronto per i tipi BLOB. Ad esempio, l'utilizzo di "[Serializable]" nel  **\<prima >** blocco di un updategram, se utilizzato nel controllo della concorrenza di una colonna di **ntext** tipo avrà esito negativo con il seguente SQLOLEDB Descrizione dell'errore:  
  
    ```  
    Empty update, no updatable rows found   Transaction aborted  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [Considerazioni sulla sicurezza di updategram &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
