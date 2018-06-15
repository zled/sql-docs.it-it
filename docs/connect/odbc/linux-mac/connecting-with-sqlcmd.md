---
title: Connessione con sqlcmd | Documenti Microsoft
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
- sqlcmd
ms.assetid: 61a2ec0d-1bcb-4231-bea0-cff866c21463
caps.latest.revision: 45
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c330fd329f28fa7d89b62b9af6bb8d4bb67c2bc4
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32853086"
---
# <a name="connecting-with-sqlcmd"></a>Connessione con sqlcmd
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Il [sqlcmd](http://go.microsoft.com/fwlink/?LinkID=154481) utilità è disponibile nel [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] su Linux e macOS.
  
I comandi seguenti viene illustrato come utilizzare l'autenticazione di Windows (Kerberos) e [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] l'autenticazione, rispettivamente:
  
```  
sqlcmd –E –Sxxx.xxx.xxx.xxx  
sqlcmd –Sxxx.xxx.xxx.xxx –Uxxx -Pxxx  
```  
  
## <a name="available-options"></a>Opzioni disponibili

Nella versione corrente, sono disponibili le opzioni seguenti:  
  
- -? Visualizzazione `sqlcmd` utilizzo.  
  
- -una richiesta di una dimensione del pacchetto.  
  
- -b interrompi batch se si verifica un errore.  
  
- -c *batch_terminator* specificare il terminatore di batch.  
  
- -C un certificato server attendibile.  

- -d *database_name* problema un `USE ` *database_name* istruzione quando si avvia `sqlcmd`.  

- -D fa sì che il valore passato al `sqlcmd` opzione -S deve essere interpretato come nome dell'origine dati (DSN). Per ulteriori informazioni, vedere "supporto DSN in `sqlcmd` e `bcp`" alla fine di questo argomento.  
  
- -e scrivere gli script di input sul dispositivo di output standard (stdout).

- -E. utilizzare la connessione trusted (autenticazione integrata). Per ulteriori informazioni sull'esecuzione di connessioni trusted che utilizzano l'autenticazione integrata da un client Linux o Mac OS, vedere [Using Integrated Authentication](../../../connect/odbc/linux-mac/using-integrated-authentication.md).

- -h *number_of_rows* specificare il numero di righe da stampare tra le intestazioni di colonna.  
  
- -H specificare un nome di workstation.  
  
- -i *input_file*[,*input_file*[,...]] Identifica il file che include un batch di istruzioni SQL o stored procedure.  
  
- -I Set di `SET QUOTED_IDENTIFIER` opzione di connessione su ON.  
  
- -k rimuovere o sostituire i caratteri di controllo.  
  
- **-K * * * application_intent*  
Dichiara il tipo di carico di lavoro dell'applicazione in caso di connessione a un server. L'unico valore attualmente supportato è **ReadOnly**. Se **-K** non viene specificato, `sqlcmd` non supporta la connettività a una replica secondaria in un gruppo di disponibilità AlwaysOn. Per ulteriori informazioni, vedere [Driver ODBC in Linux e macOS - disponibilità elevata e ripristino di emergenza](../../../connect/odbc/linux-mac/odbc-driver-on-linux-support-for-high-availability-disaster-recovery.md).  
  
> [!NOTE]  
> **-K** non è supportata in CTP per SUSE Linux. Tuttavia, è possibile specificare il **ApplicationIntent = ReadOnly** parola chiave in un file DSN passato a `sqlcmd`. Per ulteriori informazioni, vedere "supporto DSN in `sqlcmd` e `bcp`" alla fine di questo argomento.  
  
- -l *timeout* specificare il numero di secondi prima che un `sqlcmd` timeout di accesso quando si tenta di connettersi a un server.

- -m *error_level* controllo i messaggi di errore vengono inviati a stdout.  
  
- **-M * * * multisubnet_failover*  
Specificare sempre **-M** in caso di connessione al listener di un gruppo di disponibilità di [!INCLUDE[ssSQL11](../../../includes/sssql11_md.md)] o a un'istanza del cluster di failover di [!INCLUDE[ssSQL11](../../../includes/sssql11_md.md)]. **-M** fornisce per rilevamento più veloce di failover e connessione al server attualmente attivo. Se non si specifica **–M** , significa che l'opzione **-M** è disattivata. Per ulteriori informazioni su [!INCLUDE[ssHADR](../../../includes/sshadr_md.md)], vedere [Driver ODBC in Linux e macOS - disponibilità elevata e ripristino di emergenza](../../../connect/odbc/linux-mac/odbc-driver-on-linux-support-for-high-availability-disaster-recovery.md).  
  
> [!NOTE]  
> **-M** non è supportata in CTP per SUSE Linux. Tuttavia, è possibile specificare il **MultiSubnetFailover = Yes** parola chiave in un file DSN passato a `sqlcmd`. Per ulteriori informazioni, vedere "supporto DSN in `sqlcmd` e `bcp`" alla fine di questo argomento.  
  
- -N crittografia connessione.  
  
- -o *output_file* identifica il file che riceve l'output di `sqlcmd`.  
  
- -p stampa le statistiche sulle prestazioni per ogni set di risultati.  
  
- -P specifica una password utente.  
  
- -q *commandline_query* eseguire una query quando `sqlcmd` viene avviata, ma non viene chiuso al termine dell'esecuzione della query.  

- -Q *commandline_query* eseguire una query quando `sqlcmd` viene avviato. `sqlcmd` si interromperà al termine della query.  

- -r reindirizza i messaggi di errore a stderr.

- -R, il driver da utilizzare impostazioni internazionali del client per la conversione valuta e data e ora in dati di tipo carattere. Attualmente viene usato solo il formato en_US (inglese Stati Uniti).
  
- -s *column_separator_char* specificare il carattere separatore di colonna.  

- -S [*protocollo*:] *server*[**, * * * porta*]  
Specificare l'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] a cui connettersi, o se -D viene utilizzato, un DSN. Il driver ODBC in Linux e macOS richiede - S. Si noti che **tcp** è l'unico protocollo valido.  
  
- -t *query_timeout* specificare il numero di secondi prima del timeout di un comando (o l'istruzione SQL).  
  
- -u specifica che output_file viene archiviato in formato Unicode, indipendentemente dal formato di input_file.  
  
- -U *login_id* specificare un ID di accesso utente.  
  
- -V *error_severity_level* controllare il livello di gravità che viene utilizzato per impostare la variabile ERRORLEVEL.  
  
- -w *column_width* specificare la larghezza della schermata per l'output.  
  
- -W rimuove gli spazi finali da una colonna.  
  
- sostituzione delle variabili Disable - x.  
  
- -X disabilita i comandi, script di avvio e le variabili di ambiente.  
  
- -y *variable_length_type_display_width* impostare il `sqlcmd` variabile di scripting `SQLCMDMAXFIXEDTYPEWIDTH`.
  
- -Y *fixed_length_type_display_width* impostare il `sqlcmd` variabile di scripting `SQLCMDMAXVARTYPEWIDTH`.


## <a name="available-commands"></a>Comandi disponibili

Nella versione corrente, sono disponibili i comandi seguenti:  
  
-   [:]!!  
  
-   :Connect  
  
-   :Error  
  
-   [:]EXIT  
  
-   GO [*conteggio*]  
  
-   :Help  
  
-   :List  
  
-   :Listvar  
  
-   :On Error  
  
-   :Out  
  
-   :Perftrace  
  
-   [:]QUIT  
  
-   :r  
  
-   :RESET  
  
-   :setvar  
  
## <a name="unavailable-options"></a>Opzioni non disponibili
Nella versione corrente, le opzioni seguenti non sono disponibili:  

- -A accedere a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] con una connessione amministrativa dedicata (DAC). Per informazioni su come effettuare una connessione amministrativa dedicata (DAC), vedere [linee guida di programmazione](../../../connect/odbc/linux-mac/programming-guidelines.md).  
  
- -f *code_page* specificare le tabelle codici di input e output.  
  
- -L elenco i computer server configurati localmente e i nomi dei computer server che trasmettono in rete.  
  
- -v crea un `sqlcmd` variabile di scripting che può essere usato in un `sqlcmd` script.  
  
È possibile utilizzare il seguente metodo alternativo: inserire i parametri all'interno di un file, è quindi possibile aggiungere a un altro file. Ciò consentirà di usare un file di parametri per sostituire i valori. Ad esempio, creare un file denominato `a.sql` (il file dei parametri) con il seguente contenuto:
  
    :setvar ColumnName object_id  
    :setvar TableName sys.objects  
  
Creare quindi un file denominato `b.sql`, con i parametri per la sostituzione:  
  
    select $(ColumnName) from $(TableName)  

Nella riga di comando, combinare `a.sql` e `b.sql` in `c.sql` utilizzando i comandi seguenti:  
  
    cat a.sql > c.sql 
  
    cat b.sql >> c.sql  
  
Eseguire `sqlcmd` e utilizzare `c.sql` come file di input:  
  
    slqcmd -S<…> -P<..> –U<..> -I c.sql  

- z - *password* Cambia password.  
  
- -Z *password* modificare la password e uscita.  

## <a name="unavailable-commands"></a>Comandi non disponibili

Nella versione corrente, i comandi seguenti non sono disponibili:  
  
-   :ED  
  
-   :ServerList  
  
-   :XML  
  
## <a name="dsn-support-in-sqlcmd-and-bcp"></a>Supporto di DSN in sqlcmd e bcp

È possibile specificare un nome origine dati (DSN) anziché un nome del server nel **sqlcmd** o **bcp** `-S` opzione (o **sqlcmd** : il comando Connetti) se si specifica - D. -D fa sì che **sqlcmd** o **bcp** per connettersi al server specificato nel DSN dall'opzione -S.  
  
DSN di sistema vengono memorizzati nel `odbc.ini` file nella directory SysConfigDir ODBC (`/etc/odbc.ini` nelle installazioni standard). DSN utente vengono archiviati `.odbc.ini` nella home directory dell'utente (`~/.odbc.ini`).
  
In un DSN in Linux o macOS sono supportate le seguenti voci:

-   **ApplicationIntent = ReadOnly**  

-   **Database = * * * database_name*  
  
-   **Driver = ODBC Driver 11 for SQL Server** o **Driver = ODBC Driver 13 for SQL Server**
  
-   **MultiSubnetFailover = Yes**  
  
-   **Server = * * * server_name_or_IP_address*  
  
-   **Trusted_Connection=yes**|**no**  
  
In un DSN, solo la voce DRIVER è obbligatoria, ma per connettersi a un server, `sqlcmd` o `bcp` necessita del valore nella voce del SERVER.  

Se è specificata l'opzione stessa in entrambi i DSN e `sqlcmd` o `bcp` riga di comando, l'opzione della riga di comando sostituisce il valore usato nel DSN. Ad esempio, se il DSN include una voce del DATABASE e `sqlcmd` riga di comando include **-d**, il valore passato a **-d** viene utilizzato. Se **Trusted_Connection = yes** specificato nel DSN, viene utilizzata l'autenticazione Kerberos e il nome utente (**– U**) e la password (**– P**), se specificato, vengono ignorati.

Gli script esistenti che richiamano `isql` può essere modificato per utilizzare `sqlcmd` definendo l'alias seguente: `alias isql="sqlcmd –D"`.  

## <a name="see-also"></a>Vedere anche  
[La connessione con **bcp**](../../../connect/odbc/linux-mac/connecting-with-bcp.md)  
 
