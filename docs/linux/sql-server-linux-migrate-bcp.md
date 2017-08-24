---
title: Copia bulk di dati a SQL Server in Linux | Documenti Microsoft
description: 
author: sanagama
ms.author: sanagama
manager: jhubbard
ms.date: 03/17/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 7b93d0d7-7946-4b78-b33a-57d6307cdfa9
ms.translationtype: MT
ms.sourcegitcommit: ea75391663eb4d509c10fb785fcf321558ff0b6e
ms.openlocfilehash: a4fa8a4080a8483aba8494dd1195c7fbb1aec67a
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="bulk-copy-data-with-bcp-to-sql-server-on-linux"></a>Copia bulk di dati con bcp per SQL Server in Linux

[!INCLUDE[tsql-appliesto-sslinux-only](../../docs/includes/tsql-appliesto-sslinux-only.md)]

In questo argomento viene illustrato come utilizzare il [bcp](https://msdn.microsoft.com/en-us/library/ms162802.aspx) utilità della riga di comando di copia bulk dei dati tra un'istanza di SQL Server 2017 RC2 in Linux e un file di dati in un formato specificato dall'utente.

È possibile utilizzare `bcp` per importare un numero elevato di righe in tabelle SQL Server oppure per esportare dati dalle tabelle di SQL Server nei file di dati. Tranne quando è usato con l'opzione queryout, `bcp` non richiede alcuna conoscenza di Transact-SQL. Il `bcp` utilità della riga di comando funziona con Microsoft SQL Server in esecuzione in locale o nel cloud, Linux, Windows o Docker e Database SQL di Azure e Azure SQL Data Warehouse.

In questo argomento viene illustrato come in:
- Importare dati in una tabella con il `bcp in` comando
- Esportare i dati da una tabella di abbonamento di `bcp out` comando

## <a name="install-the-sql-server-command-line-tools"></a>Installare gli strumenti da riga di comando di SQL Server

`bcp`fa parte di strumenti della riga di comando di SQL Server, che non vengono installati automaticamente con SQL Server in Linux. Se non è già installato gli strumenti da riga di comando di SQL Server nel computer Linux, è necessario installarli. Per ulteriori informazioni su come installare gli strumenti, selezionare la distribuzione di Linux dall'elenco seguente:

- [Red Hat Enterprise Linux (RHEL)](sql-server-linux-setup-tools.md#RHEL)
- [Ubuntu](sql-server-linux-setup-tools.md#ubuntu)
- [SUSE Linux Enterprise Server (SLES)](sql-server-linux-setup-tools.md#SLES)

## <a name="import-data-with-bcp"></a>Importare i dati con bcp

In questa esercitazione si creerà un database di esempio e una tabella nell'istanza locale di SQL Server (**localhost**) e quindi utilizzare `bcp` per caricare nella tabella di esempio da un file di testo su disco.

### <a name="create-a-sample-database-and-table"></a>Creare un database di esempio e una tabella

Iniziamo creando un database di esempio con una semplice tabella che verrà utilizzata nel resto di questa esercitazione.

1. Nella casella di Linux, aprire un terminale di comando.

2. Copiare e incollare i comandi nella finestra terminal. Questi comandi usano il **sqlcmd** utilità della riga di comando per creare un database di esempio (**BcpSampleDB**) e una tabella (**TestEmployees**) nell'istanza locale di SQL Server (**localhost**). Ricordarsi di sostituire il `username` e `<your_password>` necessarie prima di eseguire i comandi.

Creare il database **BcpSampleDB**:
```bash 
sqlcmd -S localhost -U sa -P <your_password> -Q "CREATE DATABASE BcpSampleDB;"
```
Creare la tabella **TestEmployees** nel database **BcpSampleDB**:
```bash 
sqlcmd -S localhost -U sa -P <your_password> -d BcpSampleDB -Q "CREATE TABLE TestEmployees (Id INT IDENTITY(1,1) NOT NULL PRIMARY KEY, Name NVARCHAR(50), Location NVARCHAR(50));"
```
### <a name="create-the-source-data-file"></a>Creare il file di dati di origine
Copiare e incollare il comando seguente nella finestra del terminale. Verrà utilizzato l'elemento predefinito `cat` comando per creare un file di dati di testo di esempio con 3 record salvare il file nella directory principale come **~/test_data.txt**. I campi nei record sono delimitati da una virgola.

```bash
cat > ~/test_data.txt << EOF
1,Jared,Australia
2,Nikita,India
3,Tom,Germany
EOF
```

È possibile verificare che il file di dati è stato creato correttamente eseguendo il comando seguente nella finestra terminal:
```bash 
cat ~/test_data.txt
```

Nella finestra terminal verrà visualizzato quanto segue:
```bash
1,Jared,Australia
2,Nikita,India
3,Tom,Germany
```

### <a name="import-data-from-the-source-data-file"></a>Importare i dati dal file di dati di origine
Copiare e incollare i comandi nella finestra terminal. Questo comando Usa `bcp` per connettersi all'istanza locale di SQL Server (**localhost**) e importare i dati dal file di dati (**~/test_data.txt**) nella tabella (**TestEmployees**) nel database (**BcpSampleDB**). Ricordarsi di sostituire il nome utente e `<your_password>` necessarie prima di eseguire i comandi.

```bash 
bcp TestEmployees in ~/test_data.txt -S localhost -U sa -P <your_password> -d BcpSampleDB -c -t  ','
```

Ecco una breve panoramica dei parametri della riga di comando è utilizzati con `bcp` in questo esempio:
- `-S`: specifica l'istanza di SQL Server a cui connettersi
- `-U`: specifica l'ID di accesso utilizzato per connettersi a SQL Server
- `-P`: specifica la password per l'ID di accesso
- `-d`: Specifica il database a cui connettersi
- `-c`: consente di eseguire operazioni utilizzando un tipo di dati carattere
- `-t`: Specifica il carattere di terminazione del campo. Si sta usando `comma` come carattere di terminazione di campo per i record nel file di dati

> [!NOTE]
> In questo esempio, è non stiamo specificando un terminatore di riga personalizzato. Le righe nel file di dati di testo sono state terminate correttamente con `newline` quando è stato usato il `cat` comando per creare il file di dati in precedenza.

È possibile verificare che i dati sono stati importati correttamente eseguendo il comando seguente nella finestra del terminale. Ricordarsi di sostituire il `username` e `<your_password>` necessarie prima di eseguire il comando.
```bash 
sqlcmd -S localhost -d BcpSampleDB -U sa -P <your_password> -I -Q "SELECT * FROM TestEmployees;"
```

Verrà visualizzato i risultati seguenti:
```bash
Id          Name                Location
----------- ------------------- -------------------
          1 Jared               Australia
          2 Nikita              India
          3 Tom                 Germany

(3 rows affected)
```

## <a name="export-data-with-bcp"></a>Esportare i dati con bcp

In questa esercitazione si utilizzerà `bcp` per esportare i dati dalla tabella di esempio creato in precedenza in un nuovo file di dati.

Copiare e incollare i comandi nella finestra terminal. Questi comandi usano il `bcp` utilità della riga di comando per esportare i dati dalla tabella **TestEmployees** nei nel database **BcpSampleDB** in un nuovo file di dati denominato **~/test_export.txt**.  Ricordarsi di sostituire il nome utente e `<your_password>` necessarie prima di eseguire il comando.

```bash 
bcp TestEmployees out ~/test_export.txt -S localhost -U sa -P <your_password> -d BcpSampleDB -c -t ','
```

È possibile verificare che i dati è stati esportati correttamente eseguendo il comando seguente nella finestra terminal:
```bash 
cat ~/test_export.txt
```

Nella finestra terminal verrà visualizzato quanto segue:
```
1,Jared,Australia
2,Nikita,India
3,Tom,Germany
```

## <a name="see-also"></a>Vedere anche
- [utilità bcp](https://msdn.microsoft.com/en-us/library/ms162802.aspx)
- [Formati di dati per la compatibilità mediante bcp](https://msdn.microsoft.com/en-us/library/ms190759.aspx)
- [Importazione Bulk dei dati tramite BULK INSERT](https://msdn.microsoft.com/en-us/library/ms175915.aspx)
- [BULK INSERT (Transact-SQL)](https://msdn.microsoft.com/en-us/library/ms188365.aspx)

