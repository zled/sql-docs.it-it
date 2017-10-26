---
title: Crea tabella - comando SQL | Documenti Microsoft
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
- CREATE TABLE [ODBC]
ms.assetid: be2143ba-fc16-42c9-84f7-8985cd924860
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 35a22420b5ecaf21539fd16aecb3870e3f3049dc
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="create-table---sql-command"></a>Crea tabella - comando SQL
Crea una tabella con i campi specificati.  
  
 Il Driver ODBC di Visual FoxPro supporta la sintassi del linguaggio Visual FoxPro native per questo comando. Per informazioni specifiche del driver, vedere **Driver osservazioni**.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
CREATE TABLE | DBF TableName1 [NAME LongTableName] [FREE]  
   (FieldName1FieldType [(nFieldWidth [, nPrecision])]  
      [NULL | NOT NULL]   
      [CHECK lExpression1 [ERROR cMessageText1]]  
      [DEFAULT eExpression1]  
      [PRIMARY KEY | UNIQUE]  
      [REFERENCES TableName2 [TAG TagName1]]  
      [NOCPTRANS]  
   [, FieldName2 ...]  
      [, PRIMARY KEY eExpression2 TAG TagName2  
      |, UNIQUE eExpression3 TAG TagName3]  
      [, FOREIGN KEY eExpression4 TAG TagName4 [NODUP]  
            REFERENCES TableName3 [TAG TagName5]]  
      [, CHECK lExpression2 [ERROR cMessageText2]])  
| FROM ARRAY ArrayName  
```  
  
## <a name="arguments"></a>Argomenti  
 CREARE una tabella &#124; DBF *TableName1*  
 Specifica il nome della tabella da creare. Le opzioni di tabella e DBF sono identiche.  
  
 NOME *LongTableName*  
 Specifica un nome lungo per la tabella. Solo quando un database è aperto, poiché i nomi di tabella lunghi sono archiviati nel database, è possibile specificare un nome di tabella lunghi.  
  
 I nomi lunghi possono contenere fino a 128 caratteri e possono essere utilizzati al posto di nomi di file brevi nel database.  
  
 FREE  
 Specifica che la tabella non verrà aggiunto a un database aperto. DISPONIBILE non è necessario se un database non è aperto.  
  
 *(FieldType FieldName1* [( *nFieldWidth* [, *nPrecision*])]  
 Specifica il nome del campo, il tipo di campo, larghezza del campo e precisione di campi (numero di posizioni decimali), rispettivamente.  
  
 *FieldType* è una singola lettera che indica il campo [tipo di dati](../../odbc/microsoft/visual-foxpro-field-data-types.md). Alcuni tipi di dati di campo che è necessario specificare *nFieldWidth* o *nPrecision* o entrambi.  
  
 *nFieldWidth* e *nPrecision* vengono ignorate per D, G, I, G, M, P, T e Y tipi. *nPrecision* valore predefinito è zero (senza cifre decimali) se *nPrecision* non sono incluse per i tipi di B, F e N.  
  
 NULL  
 Ammette valori null nel campo.  
  
 NOT NULL  
 I valori null nel campo.  
  
 Se si omette NULL e non NULL, l'impostazione corrente di SET NULL determina se sono consentiti valori null nel campo. Tuttavia, se si omette NULL e non NULL e includa la chiave primaria o UNIVOCA clausola, viene ignorata l'impostazione corrente di SET NULL e il campo valore predefinito è NOT NULL.  
  
 CONTROLLARE *lExpression1*  
 Specifica una regola di convalida per il campo. *lExpression1* può essere una funzione definita dall'utente. Ogni volta che viene aggiunto un record vuoto, viene controllata la regola di convalida. Viene generato un errore se la regola di convalida non consente un valore di campo vuoto in un record accodato.  
  
 ERRORE *cMessageText1*  
 Specifica il messaggio di errore di Visual FoxPro viene visualizzato quando la regola di campo genera un errore. Il messaggio viene visualizzato solo quando si modificano i dati all'interno di una finestra o una finestra di modifica.  
  
 PREDEFINITO *eExpression1*  
 Specifica un valore predefinito per il campo. Il tipo di dati *eExpression1* deve essere uguale al tipo di dati del campo.  
  
 PRIMARY KEY  
 Crea un indice primario per il campo. Il tag di indice primario ha lo stesso nome del campo.  
  
 UNIQUE  
 Crea un indice di candidati per il campo. Il tag di indice candidato ha lo stesso nome del campo.  
  
> [!NOTE]  
>  Candidato indici (creati specificando l'opzione univoco in CREATE TABLE o ALTER TABLE - SQL) non sono uguali come gli indici creati con l'opzione nel comando indice univoco. Un indice creato con l'opzione nel comando indice univoco consente a chiavi duplicate dell'indice; gli indici Candidate non consentono chiavi duplicate dell'indice. Vedere [indice](../../odbc/microsoft/index-command.md) per ulteriori informazioni sulla relativa opzione univoco.  
  
 I valori null e i record duplicati non consentiti in un campo usato per un indice primarie o candidate. Tuttavia, Visual FoxPro non genererà un errore se si crea un indice primarie o candidate per un campo che supporta valori null. Se si tenta di immettere un valore null o è duplicato in un campo usato per un indice primarie o candidate, Visual FoxPro genererà un errore.  
  
 RIFERIMENTI *TableName2*[TAG *TagName1*]  
 Specifica la tabella padre a cui viene stabilita una relazione permanente. Se si omette TAG *TagName1*, viene stabilita la relazione utilizzando la chiave di indice primario della tabella padre. Se la tabella padre non dispone di un indice primario, Visual FoxPro genera un errore.  
  
 Includere TAG *TagName1* per stabilire una relazione in base a un tag di indice esistente per la tabella padre. I nomi di tag di indice possono contenere fino a 10 caratteri.  
  
 Nella tabella padre non può essere una tabella disponibile.  
  
 NOCPTRANS  
 Impedisce la traduzione in una diversa tabella codici per i campi di tipo carattere e di credito. Se la tabella viene convertita in un'altra tabella codici, i campi per cui è stato specificato NOCPTRANS non vengono convertiti. NOCPTRANS può essere specificato solo per i campi di tipo carattere e di credito.  
  
 L'esempio seguente crea una tabella denominata mytable contenente due campi di tipo carattere e i due campi di dati memo. Il secondo campo di tipo carattere, char2 e il secondo campo memo memo2, includere NOCPTRANS per evitare di traduzione.  
  
```  
CREATE TABLE mytable (char1 C(10), char2 C(10) NOCPTRANS,;  
   memo1 M, memo2 M NOCPTRANS)  
```  
  
 CHIAVE primaria *eExpression2* TAG *TagName2*  
 Specifica un indice primario per la creazione. *eExpression2* specifica qualsiasi campo o una combinazione di campi della tabella. TAG *TagName2 s*specifica il nome per il tag di indice primario che viene creato. I nomi di tag di indice possono contenere fino a 10 caratteri.  
  
 Poiché una tabella può avere un solo indice primario, è possibile includere questa clausola se è già stato creato un indice primario per un campo. Visual FoxPro genera un errore se si include più di una clausola di chiave primaria in CREATE TABLE.  
  
 UNIVOCO *eExpression3*TAG *TagName3*  
 Crea un indice candidato. *eExpression3* specifica qualsiasi campo o una combinazione di campi della tabella. Tuttavia, se è stato creato un indice primario con una delle opzioni chiave primaria, è possibile includere il campo che è stato specificato per l'indice primario. TAG *TagName3 s*specifica un nome di tag per il tag di indice candidato creato. I nomi di tag di indice possono contenere fino a 10 caratteri.  
  
 Una tabella può avere più indici candidato.  
  
 CHIAVE esterna *eExpression4*TAG *TagName4*[NODUP]  
 Crea un indice (non primaria) esterno e stabilisce una relazione a una tabella padre. *eExpression4* specifica l'espressione di chiave esterna di indice, e *TagName4* specifica il nome del tag di chiave esterna indice creato*.* I nomi di tag di indice possono contenere fino a 10 caratteri. Includere NODUP per creare un indice esterna candidato.  
  
 È possibile creare più indici della tabella esterni, ma le espressioni di indice esterna devono specificare diversi campi nella tabella.  
  
 RIFERIMENTI *TableName3*[TAG *TagName5*]  
 Specifica la tabella padre a cui viene stabilita una relazione permanente. Includere TAG *TagName5* per stabilire una relazione in base a un tag di indice per la tabella padre. I nomi di tag di indice possono contenere fino a 10 caratteri. Per impostazione predefinita, se si omette TAG *TagName5,* viene stabilita la relazione di chiave di indice primario della tabella padre.  
  
 CONTROLLARE *eExpression2*[errore *cMessageText2*]  
 Specifica la regola di convalida della tabella. ERRORE *cMessageText2* specifica il messaggio di errore di Visual FoxPro viene visualizzato quando viene eseguita la regola di convalida della tabella. Il messaggio viene visualizzato solo quando i dati viene modificati all'interno di una finestra o finestra Modifica.  
  
 DALLA matrice *ArrayName*  
 Specifica il nome di una matrice esistente il cui contenuto è il nome, tipo, precisione e scala per ogni campo nella tabella. Il contenuto della matrice può essere definito con la **AFIELDS**funzione ().  
  
## <a name="remarks"></a>Osservazioni  
 La nuova tabella viene aperto nell'area di lavoro più basso e sono accessibili mediante il relativo alias. La nuova tabella viene aperto in modalità esclusiva, indipendentemente dall'impostazione corrente di SET esclusivo.  
  
 Se un database è aperto e non si include la clausola disponibile, la nuova tabella viene aggiunto al database. È possibile creare una nuova tabella con lo stesso nome di una tabella nel database.  
  
 Se un database è aperto, CREATE TABLE - SQL richiede l'uso esclusivo del database. Per aprire un database per l'uso esclusivo, includere esclusivo nel DATABASE di aprire.  
  
 Se non è un database aperto quando si crea la nuova tabella, tra cui le clausole di nome, CHECK, DEFAULT, FOREIGN KEY, PRIMARY KEY o riferimenti genera un errore.  
  
> [!NOTE]  
>  Sintassi di CREATE TABLE Usa le virgole per separare determinati opzioni CREATE TABLE. Inoltre, NULL, non NULL, CHECK, impostazione predefinita, chiave primaria e univoco clausola deve trovarsi all'interno delle parentesi che contiene le definizioni di colonna.  
  
## <a name="driver-remarks"></a>Sezione Osservazioni di driver  
 Quando l'applicazione invia l'istruzione ODBC SQL CREATE TABLE per l'origine dati, il Driver ODBC di Visual FoxPro traduce il comando al comando Visual FoxProCREATE tabella utilizzando la sintassi illustrata nella tabella seguente.  
  
|Sintassi ODBC|Sintassi di Visual FoxPro|  
|-----------------|--------------------------|  
|CREATE TABLE *nome-tabella di base*<br /><br /> (*identificatore di colonna tipo di dati*<br /><br /> [NON NULL]<br /><br /> [,*il tipo di dati colonna identificatore*<br /><br /> [NON NULL]...)|CREARE una tabella *TableName1* [nome *LongTableName*]<br /><br /> (*FieldName1* *FieldType*<br /><br /> [(*nFieldWidth* [, *nPrecision*])]<br /><br /> [NON NULL)]|  
  
 Quando si crea una tabella utilizzando il driver, il driver chiude la tabella subito dopo la creazione di consentire l'accesso alla tabella in base ad altri utenti. Questo comportamento è diverso da Visual FoxPro, che rimane aperto esclusivamente al momento della creazione della tabella. Tuttavia, se viene eseguita una stored procedure sull'origine dati che contiene un'istruzione CREATE TABLE, la tabella viene lasciata aperta.  
  
 Se l'origine dati è un database (file DBC), il Driver ODBC di Visual FoxPro creata una tabella denominata *LongTableName* con lo stesso nome di *nome-tabella di base*.  
  
### <a name="using-data-definition-language-ddl"></a>Utilizzo di Data Definition Language (DDL)  
 DDL non è possibile includere nelle seguenti posizioni:  
  
-   In un'istruzione SQL batch che richiede una transazione  
  
-   In modalità di commit manuale, dopo un'istruzione che hanno richiesto una transazione, a meno che l'applicazione chiama innanzitutto **SQLTransact**.  
  
 Ad esempio, se si desidera creare una tabella temporanea, è necessario creare la tabella prima di iniziare l'istruzione che richiedono una transazione. Se si include l'istruzione CREATE TABLE in un batch di istruzione SQL che richiede una transazione, il driver restituisce un messaggio di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [ALTER TABLE - comando SQL](../../odbc/microsoft/alter-table-sql-command.md)   
 [Tipi di dati supportati (Driver ODBC di Visual FoxPro)](../../odbc/microsoft/supported-data-types-visual-foxpro-odbc-driver.md)   
 [INSERT - comando SQL](../../odbc/microsoft/insert-sql-command.md)   
 [Selezionare - comando SQL](../../odbc/microsoft/select-sql-command.md)

