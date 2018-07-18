---
title: Le funzionalità di accesso compatibili (AccessToSQL) | Documenti Microsoft
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssma-access
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Access databases
- Access databases, features incompatible with SQL Azure
- Access databases, features incompatible with SQL Server
- dates
- default expressions
- foreign keys
- hyperlink columns
- incompatible Access features
- indexes
- indexes, length of
- keywords
- primary keys
- reference, incompatible features
- replication columns
- special characters
- unique indexes
- validation rules
ms.assetid: 99d45b9c-e3b9-4d56-8c25-b594b887ace1
caps.latest.revision: 18
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: dbfcb395194371bf761f340cc74943791a649aaa
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="incompatible-access-features-accesstosql"></a>Funzionalità di accesso compatibili (AccessToSQL)
Non tutte le funzionalità di database di Access sono compatibili con [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Ad esempio, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] e dispone di accesso diversi set di parole chiave riservate. Problemi come questi può impedire la migrazione ha esito positivo a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Utilizzare la tabella seguente per informazioni sui problemi di migrazione possibili e le operazioni su di essi.  
  
## <a name="database-settings-or-features-that-might-affect-migration"></a>Le impostazioni o funzionalità che potrebbero influire sulla migrazione di database  
  
|Impostazione del Database o una funzionalità di accesso|Problema di migrazione|  
|--------------------------------------|-------------------|  
|Accedere a tabelle non dispone di indici univoci.|Se viene eseguita la migrazione di una tabella che non dispone di un indice univoco a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], non è possibile modificare la tabella dopo la migrazione. Questo può causare problemi di compatibilità.<br /><br />Quando si convertono gli oggetti di database di Access, nella finestra di Output verranno elencate tutte le tabelle di accesso che non contengono indici univoci.<br /><br />È possibile configurare l'accesso per aggiungere una chiave primaria di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] tabella durante la conversione. Per ulteriori informazioni, vedere [le impostazioni del progetto (conversione)](http://msdn.microsoft.com/en-us/bcebc635-c638-4ddb-924c-b9ccfef86388).|  
|Accedere a tabelle con colonne di replica.|Se viene eseguita la migrazione di una tabella di accesso che include le colonne di sistema di replica per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], la funzionalità di replica Jet verrà interrotta dopo la migrazione.<br /><br />Dopo la migrazione, è consigliabile utilizzare [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] per mantenere sincronizzate le copie dei database di replica.|  
|Accedere a tabelle con indici univoci contenga valori null.|Accedere a tabelle con indici univoci con più valori null non può essere trasferite a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], perché in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], gli indici univoci non consentire più valori null. La migrazione avrà esito negativo per queste tabelle.<br /><br />SSMA contrassegnerà questo problema nei report di valutazione. Per creare una relazione di valutazione, vedere [valutare gli oggetti di Database di Access per la conversione](http://msdn.microsoft.com/en-us/8b9e23d6-da62-437a-8c05-8ad2628b9441).<br /><br />Se questo problema, è necessario assicurarsi che la chiave primaria non dispone di valori null duplicati. In alternativa, è necessario rimuovere la chiave primaria o indici univoci che contengono più valori null.|  
|Accedere a tabelle contenga valori di data che sono fuori il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] intervallo.|Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **datetime** tipo accetta date nell'intervallo tra 1 gennaio 1753 al 31 dicembre 9999 solo. Accesso accetta le date dell'intervallo pari a 100 1 gennaio al 31 dicembre 9999.<br /><br />SSMA contrassegnerà questo problema nei report di valutazione. Per creare una relazione di valutazione, vedere [valutare gli oggetti di Database di Access per la conversione](http://msdn.microsoft.com/en-us/8b9e23d6-da62-437a-8c05-8ad2628b9441).<br /><br />È possibile configurare la modalità di risoluzione delle date SSMA che sono fuori il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] intervallo. Per ulteriori informazioni, vedere [le impostazioni del progetto (migrazione)](http://msdn.microsoft.com/en-us/4caebc9c-8680-4b99-a8fa-89c43161c95d).|  
|Lunghezze di indice in Access superano i 900 byte.|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] gli indici hanno un limite di 900 byte per le dimensioni totali delle colonne chiave indice. Se le tabelle di Access utilizzano gli indici di dimensioni maggiori, SSMA verrà visualizzato un avviso.<br /><br />Se si continua con la migrazione dei dati, la migrazione potrebbe non riuscire.|  
|I nomi degli oggetti di accesso sono [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] parole chiave, o contenere i caratteri speciali.|Accesso e [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] offrono diversi set di caratteri speciali e parole chiave riservate. [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] accetta oggetti che vengono denominati utilizzando [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] parole chiave o che contengono caratteri speciali se si utilizzano gli identificatori inseriti tra parentesi o tra virgolette, ad esempio "select" o [selezionare] p. Per ulteriori informazioni, vedere "Identificatori delimitati (motore di Database)" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] documentazione in linea.<br /><br />**Nota:** per utilizzare le virgolette per delimitare gli identificatori, SET QUOTED_IDENTIFIER deve essere impostata su ON.<br /><br />Ad esempio, `CREATE TABLE [schema](c1 [FOR])` è un'istruzione valida, anche se **schema** e **per** sono parole chiave riservate. Inoltre, `CREATE TABLE [xxx*yyy](c1 x&y)` è un'istruzione valida, anche se il nome di tabella e colonna contengono caratteri speciali  **\&#42;** e **&amp;**.<br /><br />Tutte le query che fanno riferimento a oggetti è necessario utilizzare anche i nomi con parentesi quadre o virgolette. Ad esempio, la query `SELECT * FROM schema` avrà esito negativo. La query corretta è: `SELECT * FROM [schema]`.<br /><br />Durante la conversione di oggetti di database di Access, il riquadro di Output verrà elencate tutte le tabelle di accesso che utilizzano parole chiave o caratteri speciali. È possibile modificare le tabelle di Access, quindi rimuovere e aggiungere il database. oppure è possibile modificare le query che fanno riferimento a oggetti in modo che le query utilizzano le parentesi quadre o virgolette doppie per delimitare gli identificatori. Se non si modificano le query, le applicazioni Access potrebbero restituire errori o altri problemi.|  
|Le dimensioni dei campi diversi in relazioni di chiave esterna o chiave primarie.|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] non supporta la funzionalità di Jet di collegamento tra le colonne contenenti tipi di dati diversi o dimensioni con vincoli di chiave esterna.<br /><br />Quando si convertono gli oggetti di database di Access, nella finestra di Output verranno elencate qualsiasi primari/chiavi vincoli di chiave esterna che non verranno convertiti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. È possibile modificare i tipi di dati e le dimensioni per le colonne di accesso in modo che corrispondano e quindi rimuovere e aggiungere nuovamente il database di Access. In alternativa, è possibile migrare i dati anche se questi vincoli non verrà creati [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].|  
|Le tabelle cui viene fatto riferimento nelle relazioni di accesso hanno una chiave primaria né un indice univoco.|Accesso accetta una relazione tra tabelle in cui la tabella di riferimento non dispone di una chiave primaria o un indice univoco. Tuttavia, questo non è supportato da [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].<br /><br />Quando si convertono gli oggetti di database di Access, nella finestra di Output verranno elencate tutte le tabelle con relazioni ma alcuna chiave primaria o un indice univoco. È possibile modificare le tabelle per aggiungere le chiavi primarie o gli indici univoci, quindi rimuovere e aggiungere nuovamente il database di Access. In alternativa, è possibile migrare i dati anche se la relazione tra le tabelle verranno interrotta.|  
|Accedere a tabelle con colonne di un collegamento ipertestuale.|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] non supporta **hyperlink** colonne. Al contrario, le colonne vengono considerate come colonne di tipo memo accesso. Per impostazione predefinita, queste colonne verranno convertite in **nvarchar (max)** colonne [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. È possibile personalizzare il mapping. Per ulteriori informazioni, vedere [Mapping tipi di origine e destinazione dati](http://msdn.microsoft.com/en-us/b362a075-16e7-423f-b63f-e1e9f02844a9).|  
|Espressioni di regole di convalida o predefinito contengono funzioni di accesso che non possono essere convertite in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure.|Espressioni di accesso predefinite o regole di convalida potrebbero includere funzioni di sistema di accesso o funzioni definite dall'utente che non sono mappati a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure. Utilizzo di funzioni che non sono mappati a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure sarà possibile caricare le espressioni predefinite o regole di convalida in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure.|  
  
## <a name="see-also"></a>Vedere anche  
[Preparazione dei database di Access per la migrazione](http://msdn.microsoft.com/en-us/9b80a9e0-08e7-4b4d-b5ec-cc998d3f5114)  
[La migrazione dei database di Access a SQL Server](http://msdn.microsoft.com/en-us/76a3abcf-2998-4712-9490-fe8d872c89ca)  
  
