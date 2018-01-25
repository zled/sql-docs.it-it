---
title: Dati SQL Azure Perms GRANT-DENY, REVOKE e Parallel Data warehouse | Documenti Microsoft
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: 5a3b7424-408e-4cb0-8957-667ebf4596fc
caps.latest.revision: "9"
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: c46d4df3d19b2c548b203f62a14ea4ebc0226296
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="permissions-grant-deny-revoke-azure-sql-data-warehouse-parallel-data-warehouse"></a>Autorizzazioni: GRANT, DENY o REVOKE (Azure SQL Data Warehouse, Parallel Data Warehouse)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Utilizzare [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] o [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] **GRANT** e **DENY** istruzioni per concedere o negare un'autorizzazione (ad esempio **aggiornamento**) su un'entità a protezione diretta (ad esempio un database, tabella, vista ecc.) per un'entità di sicurezza (un account di accesso, un utente del database o un ruolo del database). Utilizzare **revocare** per rimuovere la concessione o negare un'autorizzazione.  
  
 Le autorizzazioni a livello di server vengono applicate agli account di accesso. Le autorizzazioni a livello di database vengono applicate agli utenti e ruoli del database.  
  
 Per vedere quali autorizzazioni sono state concesse e negate, eseguire una query di viste Sys. server_permissions e Sys. database_permissions. Le autorizzazioni concesse o negate per un'entità di sicurezza in modo non esplicito possono essere ereditate da con l'appartenenza a un ruolo che dispone delle autorizzazioni. Le autorizzazioni dei ruoli predefiniti del database non possono essere modificate e non vengono visualizzati nelle visualizzazioni Sys. server_permissions e Sys. database_permissions.  
  
-   **GRANT** concede in modo esplicito uno o più autorizzazioni.  
  
-   **DENY** all'entità viene negata in modo esplicito dalla presenza di una o più autorizzazioni.  
  
-   **REVOCARE** rimuove esistente **GRANT** o **DENY** autorizzazioni.  
  
 ![Icona di collegamento argomento](../../database-engine/configure-windows/media/topic-link.gif "icona Collegamento argomento") [convenzioni della sintassi Transact-SQL &#40; Transact-SQL &#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Azure SQL Data Warehouse and Parallel Data Warehouse  
GRANT   
    <permission> [ ,...n ]  
    [ ON [ <class_type> :: ] securable ]   
    TO principal [ ,...n ]  
    [ WITH GRANT OPTION ]  
[;]  
  
DENY   
    <permission> [ ,...n ]  
    [ ON [ <class_type> :: ] securable ]   
    TO principal [ ,...n ]  
    [ CASCADE ]  
[;]  
  
REVOKE   
    <permission> [ ,...n ]  
    [ ON [ <class_type> :: ] securable ]   
    [ FROM | TO ] principal [ ,...n ]  
    [ CASCADE ]  
[;]  
  
<permission> ::=  
{ see the tables below }  
  
<class_type> ::=  
{  
      LOGIN  
    | DATABASE  
    | OBJECT  
    | ROLE  
    | SCHEMA  
    | USER  
}  
```  
  
## <a name="arguments"></a>Argomenti  
 \<permission>[ **,**...*n* ]  
 Uno o più autorizzazioni da concedere, negare o revocare.  
  
 ON [ \<class_type >::] *entità a protezione diretta* il **ON** clausola è descritto il parametro di entità a protezione diretta in cui si desidera concedere, negare o revocare le autorizzazioni.  
  
 \<class_type > tipo di classe del tipo di entità a protezione diretta. Può trattarsi di **accesso**, **DATABASE**, **oggetto**, **SCHEMA**, **ruolo**, o **utente** . Inoltre è possibile concedere autorizzazioni per il **SERVER * * * class_type*, ma **SERVER** per tali autorizzazioni non è specificato. **DATABASE** non viene specificato quando l'autorizzazione include la parola **DATABASE** (ad esempio **ALTER ANY DATABASE**). Se non si *class_type* specificato e il tipo di autorizzazione non è limitato alla classe di database o server, viene utilizzata la classe sia **oggetto**.  
  
 *securable*  
 Il nome di account di accesso, database, tabella, vista, schema, procedure, ruolo o utente su cui si desidera concedere, negare o revocare le autorizzazioni. Il nome dell'oggetto può essere specificato con le regole di denominazione in tre parti sono descritti in [convenzioni della sintassi Transact-SQL &#40; Transact-SQL &#41; ](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).  
  
 PER *principale* [ **,**... *n* ]  
 Una o più entità concesse, negate o revocate le autorizzazioni. Entità è il nome di un account di accesso, l'utente del database o ruolo del database.  
  
 DA *principale* [ **,**... *n* ]  
 Una o più entità per revocare le autorizzazioni.  Entità è il nome di un account di accesso, l'utente del database o ruolo del database. **DA** può essere utilizzato solo con un **revocare** istruzione. **PER** può essere utilizzato con **GRANT**, **DENY**, o **revocare**.  
  
 WITH GRANT OPTION  
 Indica che l'utente autorizzato potrà inoltre concedere l'autorizzazione specificata ad altre entità.  
  
 CASCADE  
 Indica che l'autorizzazione viene negata o revocata all'entità specificata e a tutte le altre entità a cui l'entità ha concesso l'autorizzazione. Obbligatorio quando l'entità dispone dell'autorizzazione con **GRANT OPTION**.  
  
 GRANT OPTION FOR  
 Indica che verrà revocata la capacità di concedere l'autorizzazione specificata. Questa operazione è necessaria quando si utilizza il **CASCADE** argomento.  
  
> [!IMPORTANT]  
>  Se l'entità dispone dell'autorizzazione specificata senza la **GRANT** opzione, l'autorizzazione stessa verrà revocata.  
  
## <a name="permissions"></a>Autorizzazioni  
 Per concedere un'autorizzazione, l'utente che concede deve avere l'autorizzazione stessa con la **WITH GRANT OPTION**, o deve avere un'autorizzazione di livello superiore che include l'autorizzazione viene concessa.  I proprietari degli oggetti possono concedere autorizzazioni per gli oggetti di cui sono proprietari. Le entità con **controllo** autorizzazione sull'entità a protezione diretta possa concedere l'autorizzazione per quella entità.  I membri del **db_owner** e **db_securityadmin** ruoli predefiniti del database possono concedere qualsiasi autorizzazione nel database.  
  
## <a name="general-remarks"></a>Osservazioni generali  
 Negazione o revoca delle autorizzazioni per un'entità non verrà applicate le richieste che hanno superato l'autorizzazione e sono attualmente in esecuzione. Per limitare l'accesso immediatamente, è necessario annullare le richieste attive o terminare le sessioni correnti.  
  
> [!NOTE]  
>  Più ruoli server non sono disponibili in questa versione. In alternativa, usare i ruoli del database definito dall'utente. Impossibile aggiungere l'account di accesso per il **sysadmin** ruolo predefinito del server. Concessione di **CONTROL SERVER** autorizzazione è all'incirca l'appartenenza al **sysadmin** ruolo predefinito del server.  
  
 Alcune istruzioni sono necessarie più autorizzazioni. Ad esempio, per creare una tabella richiede il **CREATE TABLE** autorizzazioni nel database e **ALTER SCHEMA** dell'autorizzazione per la tabella che conterrà la tabella.  
  
 PDW esegue talvolta le stored procedure per distribuire le azioni dell'utente per i nodi di calcolo. Pertanto, non è possibile negare l'autorizzazione execute per un intero database. (Ad esempio `DENY EXECUTE ON DATABASE::<name> TO <user>;` avrà esito negativo.) Come per risolvere il problema, negare l'autorizzazione execute per schemi utente oppure specifici oggetti (procedure).  
  
### <a name="implicit-and-explicit-permissions"></a>Autorizzazioni implicite ed esplicite  
 Un *autorizzazione esplicita* è un **GRANT** o **DENY** autorizzazioni concesse a un'entità da un **GRANT** o **DENY**istruzione.  
  
 Un *autorizzazione implicita* è un **GRANT** o **DENY** autorizzazione che un'entità (account di accesso, utente o ruolo del database) ha ereditato da un altro ruolo del database.  
  
 Un'autorizzazione implicita può anche essere ereditata da una copertura o l'autorizzazione padre. Ad esempio, **aggiornamento** autorizzazione in una tabella può essere ereditata con **aggiornamento** autorizzazione per lo schema che contiene la tabella, o **controllo** autorizzazione per la tabella.  
  
### <a name="ownership-chaining"></a>Concatenamento della proprietà  
 Quando più oggetti di database accedono ad altri in sequenza, la sequenza è nota come un *catena*. Sebbene queste catene non esistono in modo indipendente, quando in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vengono attraversati i collegamenti contenuti in una catena, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] valuta le autorizzazioni per gli oggetti che compongono la catena diversamente da quanto farebbe se accedesse agli oggetti separatamente. Concatenamento della proprietà ha implicazioni molto importanti per la gestione della sicurezza. Per ulteriori informazioni sulle catene di proprietà, vedere [catene di proprietà](http://msdn.microsoft.com/en-us/library/ms188676\(v=sql11\).aspx) e [esercitazione: catene di proprietà e cambio di contesto](http://msdn.microsoft.com/en-us/library/bb153640\(v=sql11\).aspx).  
  
## <a name="permission-list"></a>Elenco di autorizzazioni  
  
### <a name="server-level-permissions"></a>Autorizzazioni a livello di server  
 Autorizzazioni a livello di server possono essere concessa, negate e revocate da account di accesso.  
  
 **Autorizzazioni valide per i server**  
  
-   CONTROL SERVER  
  
-   ADMINISTER BULK OPERATIONS  
  
-   ALTER ANY CONNECTION  
  
-   ALTER ANY DATABASE  
  
-   CREATE ANY DATABASE  
  
-   ALTER ANY EXTERNAL DATA SOURCE  
  
-   ALTER ANY EXTERNAL FILE FORMAT  
  
-   ALTER ANY LOGIN  
  
-   ALTER SERVER STATE  
  
-   CONNECT SQL  
  
-   VIEW ANY DEFINITION  
  
-   VIEW ANY DATABASE  
  
-   VIEW SERVER STATE  
  
 **Autorizzazioni valide per gli account di accesso**  
  
-   CONTROLLARE L'ACCOUNT DI ACCESSO  
  
-   ALTER PER L'ACCOUNT DI ACCESSO  
  
-   RAPPRESENTARE L'ACCOUNT DI ACCESSO  
  
-   VIEW DEFINITION  
  
### <a name="database-level-permissions"></a>Autorizzazioni a livello di database  
 Le autorizzazioni a livello di database possono concessa, negata e revocati dai ruoli di database definiti dall'utente e gli utenti del database.  
  
 **Autorizzazioni valide per tutte le classi di database**  
  
-   CONTROL  
  
-   ALTER  
  
-   VIEW DEFINITION  
  
 **Autorizzazioni valide per tutte le classi di database ad eccezione degli utenti**  
  
-   TAKE OWNERSHIP  
  
 **Autorizzazioni che si applicano solo ai database**  
  
-   ALTER ANY DATABASE  
  
-   ALTER DATABASE  
  
-   ALTER ANY DATASPACE  
  
-   ALTER ANY ROLE  
  
-   ALTER ANY SCHEMA  
  
-   ALTER ANY USER  
  
-   BACKUP DATABASE  
  
-   CONNESSIONE DATABASE  
  
-   CREATE PROCEDURE  
  
-   CREATE ROLE  
  
-   CREATE SCHEMA  
  
-   CREATE TABLE  
  
-   CREATE VIEW  
  
-   SHOWPLAN  
  
 **Autorizzazioni che si applicano solo agli utenti**  
  
-   IMPERSONATE  
  
 **Autorizzazioni valide per i database, schemi e oggetti**  
  
-   ALTER  
  
-   DELETE  
  
-   EXECUTE  
  
-   INSERT  
  
-   SELECT  
  
-   UPDATE  
  
-   RIFERIMENTO (REFERENCES)  
  
 Per una definizione di ogni tipo di autorizzazione, vedere [autorizzazioni (motore di Database)](http://msdn.microsoft.com/library/ms191291.aspx).  
  
### <a name="chart-of-permissions"></a>Grafico delle autorizzazioni  
 Tutte le autorizzazioni vengono rappresentate graficamente in questo poster. Questo è il modo più semplice per visualizzare la gerarchia nidificata di autorizzazioni. Ad esempio il **ALTER LOGIN ON** autorizzazione può essere concessa da sola, ma è anche incluso se un account di accesso viene concesso il **controllo** l'autorizzazione per tale account di accesso, o se un account di accesso viene concesso il **ALTER ANY Account di accesso** autorizzazione.  
  
 ![Documento relativo alle autorizzazioni di sicurezza APS](../../t-sql/statements/media/aps-security-perms-poster.png "poster relativo alle autorizzazioni di sicurezza APS")  
  
 Per scaricare una versione completa di dimensioni di questo poster, vedere [autorizzazioni di SQL Server PDW](http://go.microsoft.com/fwlink/?LinkId=244249)nella sezione del sito Yammer APS file (o richiesta tramite posta elettronica da  **apsdoc@microsoft.com** .  
  
## <a name="default-permissions"></a>Autorizzazioni predefinite  
 L'elenco seguente descrive le autorizzazioni predefinite:  
  
-   Quando un account di accesso viene creato utilizzando il **CREATE LOGIN** istruzione riceve il nuovo account di accesso di **CONNECT SQL** autorizzazione.  
  
-   Tutti gli account di accesso sono membri del **pubblica** ruolo del server e non può essere rimosso da **pubblica**.  
  
-   Quando un utente del database viene creato utilizzando il **CREATE USER** autorizzazione, l'utente del database riceve il **CONNETTI** autorizzazione per il database.  
  
-   Tutte le entità, inclusi il **pubblica** ruolo non dispone di alcuna autorizzazione esplicite o implicite per impostazione predefinita.  
  
-   Quando un account di accesso o un utente diventa il proprietario di un database o oggetto, l'account di accesso o utente dispone di tutte le autorizzazioni per database o dell'oggetto. Le autorizzazioni di proprietà non possono essere modificate e non sono visibili come le autorizzazioni esplicite. Il **GRANT**, **DENY**, e **revocare** istruzioni non hanno effetto sui proprietari.  
  
-   Il **sa** account di accesso dispone di tutte le autorizzazioni nel dispositivo. Simili alle autorizzazioni di proprietà, il **sa** autorizzazioni non può essere modificate e non sono visibili come le autorizzazioni esplicite. Il **GRANT**, **DENY**, e **revocare** istruzioni non hanno effetto sui **sa** account di accesso. Il **sa** non è possibile rinominare l'account di accesso.  
  
-   Il **utilizzare** istruzione non richiede le autorizzazioni. Eseguire tutte le entità di **utilizzare** istruzione in qualsiasi database.  
  
##  <a name="Examples"></a>Esempi: [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="a-granting-a-server-level-permission-to-a-login"></a>A. Concessione dell'autorizzazione a livello di server a un account di accesso  
 Le due istruzioni seguenti concedono l'autorizzazione a livello di server a un account di accesso.  
  
```  
GRANT CONTROL SERVER TO [Ted];  
```  
  
```  
GRANT ALTER ANY DATABASE TO Mary;  
```  
  
### <a name="b-granting-a-server-level-permission-to-a-login"></a>B. Concessione dell'autorizzazione a livello di server a un account di accesso  
 Nell'esempio seguente viene concessa l'autorizzazione a livello di server in un account di accesso a un'entità del server (accesso a un'altra).  
  
```  
GRANT  VIEW DEFINITION ON LOGIN::Ted TO Mary;  
```  
  
### <a name="c-granting-a-database-level-permission-to-a-user"></a>C. Concessione dell'autorizzazione a livello di database a un utente  
 Nell'esempio seguente viene concessa l'autorizzazione a livello di database su un utente per un'entità di database (un altro utente).  
  
```  
GRANT VIEW DEFINITION ON USER::[Ted] TO Mary;  
```  
  
### <a name="d-granting-denying-and-revoking-a-schema-permission"></a>D. Concedere, negare e revocare un'autorizzazione dello schema  
 Nell'esempio **GRANT** istruzione concede Yuen la possibilità di selezionare dati da qualsiasi tabella o vista nello schema dbo.  
  
```  
GRANT SELECT ON SCHEMA::dbo TO [Yuen];  
```  
  
 Nell'esempio **DENY** istruzione impedisce Yuen di selezione di dati da qualsiasi tabella o vista nello schema dbo. Yuen non può leggere i dati anche se Scott disponga dell'autorizzazione in modo diverso, ad esempio tramite l'appartenenza di un ruolo.  
  
```  
DENY SELECT ON SCHEMA::dbo TO [Yuen];  
```  
  
 Nell'esempio **revocare** istruzione rimuove il **DENY** autorizzazione. Ora le autorizzazioni esplicite del Yuen neutre. Yuen potrebbe essere in grado di selezionare i dati da qualsiasi tabella mediante alcune altre autorizzazioni implicite, ad esempio l'appartenenza a un ruolo.  
  
```  
REVOKE SELECT ON SCHEMA::dbo TO [Yuen];  
```  
  
### <a name="e-demonstrating-the-optional-object-clause"></a>E. Dimostrare l'oggetto facoltativo:: clausola  
 Poiché l'oggetto è la classe predefinita per un'istruzione di autorizzazione, le due istruzioni seguenti sono uguali. Il **oggetto::** clausola è facoltativa.  
  
```  
GRANT UPDATE ON OBJECT::dbo.StatusTable TO [Ted];  
```  
  
```  
GRANT UPDATE ON dbo.StatusTable TO [Ted];  
```  
  
  

