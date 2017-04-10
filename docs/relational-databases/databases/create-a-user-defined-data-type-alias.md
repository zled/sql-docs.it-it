---
title: "Creare un alias del tipo di dati definito dall&#39;utente | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.swb.userdefineddatatype.general.f1"
  - "sql13.swb.new.datatype.properties.general.f1"
helpviewer_keywords: 
  - "tipi di dati alias [SQL Server], creazione"
ms.assetid: b1dd8413-0cd0-411b-a79b-1bb043ccc62d
caps.latest.revision: 27
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 27
---
# Creare un alias del tipo di dati definito dall&#39;utente
  In questo argomento si illustra come creare un nuovo alias del tipo di dati definito dall'utente in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Limitazioni e restrizioni](#Restrictions)  
  
     [Sicurezza](#Security)  
  
-   **Per creare un alias del tipo di dati definito dall'utente utilizzando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Restrictions"></a> Limitazioni e restrizioni  
  
-   Il nome di un alias del tipo di dati definito dall'utente deve essere conforme alle regole per gli identificatori.  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Autorizzazioni  
 È richiesta l'autorizzazione CREATE TYPE nel database corrente e l'autorizzazione ALTER per *schema_name*. Se *schema_name* viene omesso, vengono applicate le regole predefinite per la risoluzione dei nomi per determinare lo schema dell'utente corrente.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### Per creare un tipo di dati definito dall'utente  
  
1.  In Esplora oggetti espandere **Database**, espandere un database, **Programmabilità** e **Tipi**, fare clic con il pulsante destro del mouse su **Tipi di dati definiti dall'utente**, quindi scegliere **Nuovo tipo di dati definito dall'utente**.  
  
     **Consenti valori Null**  
     Specificare se dal tipo di dati definito dall'utente possono essere accettati valori Null. Il supporto di valori Null di un tipo di dati definito dall'utente esistente non può essere modificato.  
  
     **Tipo di dati**  
     Selezionare il tipo di dati di base dalla casella di riepilogo. In questa casella vengono visualizzati tutti i tipi di dati, ad eccezione di **geography**, **geometry**, **hierarchyid**, **sysname**, **timestamp** e **xml** . Il tipo di dati di un tipo di dati definito dall'utente esistente non può essere modificato.  
  
     **Valore predefinito**  
     Facoltativamente, selezionare una regola o un valore predefinito da associare all'alias del tipo di dati definito dall'utente.  
  
     **Lunghezza/Precisione**  
     Consente di visualizzare la lunghezza o la precisione del tipo di dati. L'opzione **Lunghezza** viene applicata ai tipi di dati carattere definiti dall'utente mentre **Precisione** solo ai tipi di dati numerici definiti dall'utente. L'etichetta varia a seconda del tipo di dati selezionato in precedenza. Se la lunghezza o la precisione del tipo di dati selezionato è fissa, la casella non è modificabile.  
  
     La lunghezza non viene visualizzata per tipi di dati **nvarchar(max)**, **varchar(max)** o **varbinary(max)**.  
  
     **Nome**  
     Se si crea un nuovo alias del tipo di dati definito dall'utente, digitare un nome univoco da utilizzare nel database per rappresentare il tipo di dati definito dall'utente. Il numero massimo di caratteri deve corrispondere al tipo di dati del sistema **sysname** . Il nome di un alias del tipo di dati definito dall'utente esistente non può essere modificato.  
  
     **Rule**  
     Facoltativamente, selezionare una regola da associare all'alias del tipo di dati definito dall'utente.  
  
     **Scala**  
     Specificare il numero massimo di cifre decimali che è possibile archiviare a destra del separatore decimale.  
  
     **Schema**  
     Consente di selezionare uno schema dall'elenco di tutti gli schemi disponibili per l'utente corrente. La selezione predefinita corrisponde allo schema predefinito per l'utente corrente.  
  
     **Archiviazione**  
     Consente di visualizzare la capacità di memorizzazione massima per l'alias del tipo di dati definito dall'utente. Le dimensioni di archiviazione massime variano in base alla precisione.  
  
    |||  
    |-|-|  
    |1 – 9|5|  
    |10 – 19|9|  
    |20 – 28|13|  
    |29 – 38|17|  
  
     Per i tipi di dati **nchar** e **nvarchar** il valore di archiviazione è sempre il doppio del valore specificato in **Lunghezza**.  
  
     L'archiviazione non viene visualizzata per tipi di dati **nvarchar(max)**, **varchar(max)** o **varbinary(max)**.  
  
2.  Nella casella **Schema** della finestra di dialogo **Nuovo tipo di dati definito dall'utente** digitare lo schema proprietario per questo alias del tipo di dati oppure usare il pulsante sfoglia per selezionare lo schema.  
  
3.  Nella casella **Nome** digitare un nome per il nuovo alias del tipo di dati.  
  
4.  Nella casella **Tipo di dati** selezionare il tipo di dati sul quale sarà basato il nuovo alias del tipo di dati.  
  
5.  Compilare le caselle **Lunghezza**, **Precisione**e **Scala** se necessarie per il tipo di dati selezionato.  
  
6.  Selezionare **Consenti valori NULL** se il nuovo alias del tipo di dati può consentire valori NULL.  
  
7.  Nell'area **Associazione** compilare le caselle **Valore predefinito** o **Regola** per associare un valore predefinito o una regola al nuovo alias del tipo di dati. In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]non è possibile creare valori predefiniti e regole. Usare [!INCLUDE[tsql](../../includes/tsql-md.md)]. Esempi di codice per la creazione di valori predefiniti e di regole sono disponibili in Esplora modelli.  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
  
#### Per creare un alias del tipo di dati definito dall'utente  
  
1.  Connettersi al [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dalla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra Query, quindi fare clic su **Esegui**. In questo esempio si crea un alias del tipo di dati basato sul tipo di dati di sistema `varchar`. L'alias del tipo di dati `ssn` viene utilizzato per colonne contenenti numeri di previdenza sociale a 11 cifre (999-99-9999). Questa colonna non può contenere valori NULL.  
  
```tsql  
CREATE TYPE ssn  
FROM varchar(11) NOT NULL ;  
```  
  
## Vedere anche  
 [Identificatori del database](../../relational-databases/databases/database-identifiers.md)   
 [CREATE TYPE &#40;Transact-SQL&#41;](../../t-sql/statements/create-type-transact-sql.md)  
  
  