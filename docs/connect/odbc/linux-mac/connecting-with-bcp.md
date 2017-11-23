---
title: Connessione a bcp | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: bcp
ms.assetid: 3eca5717-e50f-40db-be16-a1cebbdfee70
caps.latest.revision: "33"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: f7e9db6a1ea636975a3f5719d9a1b3e9d5721eb6
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/18/2017
---
# <a name="connecting-with-bcp"></a>Connessione a bcp
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Il [bcp](http://go.microsoft.com/fwlink/?LinkID=190626) utilità è disponibile nel [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] su Linux e macOS. Questa pagina illustra le differenze della versione di Windows di `bcp`.
  
- Il carattere di terminazione del campo è tabulazione ("\t").  
  
- Il carattere di terminazione della riga è nuova riga ("\n").  
  
- Modalità carattere è il formato preferito per `bcp` formato di file e i file di dati che non contengono caratteri estesi.  
  
> [!NOTE]  
> Una barra rovesciata '\\' in un argomento della riga di comando deve essere racchiuso tra virgolette o caratteri di escape. Per specificare una nuova riga come carattere di terminazione riga personalizzato, ad esempio, è necessario utilizzare uno dei meccanismi seguenti:  
>   
> -   -r\\\n  
> -   -r "\n"  
> -   -r '\n'  
  
Di seguito è riportato una chiamata di comando di esempio di `bcp` per copiare le righe della tabella in un file di testo:  
  
```  
bcp AdventureWorks2008R2.Person.Address out test.dat -Usa -Pxxxx -Sxxx.xxx.xxx.xxx  
```  
  
## <a name="available-options"></a>Opzioni disponibili
Nella versione corrente, la sintassi e le opzioni seguenti sono disponibili:  

[*database***.**]*schema***.***table* **in** *data_file* | **out** *data_file*

- -a *packet_size*  
Specifica il numero di byte inviati al e dal server per ogni pacchetto di rete.  
  
- -b *batch_size*  
Specifica il numero di righe per ogni batch di dati importati.  
  
- -c  
Usa dati di tipo carattere.  
  
- -d *database_name*  
Specifica il database al quale connettersi.  
  
- -d  
Il valore passato a causa di `bcp` opzione -S deve essere interpretato come nome dell'origine dati (DSN). Per ulteriori informazioni, vedere "Supporto DSN in sqlcmd e bcp" in [connessione con sqlcmd](../../../connect/odbc/linux-mac/connecting-with-sqlcmd.md).  
  
- -e *error_file* specifica il percorso completo del file di errori utilizzato per archiviare qualsiasi le righe che il `bcp` utilità non è possibile trasferire dal file al database.  
  
- -e  
Usa i valori Identity per la colonna Identity nel file di dati importato.  
  
- -f *format_file*  
Specifica il percorso completo di un file di formato.  
  
- -F *first_row*  
Specifica il numero della prima riga da esportare da una tabella o da importare da un file di dati.  
  
- -k  
Specifica che durante l'operazione il valore delle colonne vuote deve essere Null, ovvero che non verranno inseriti valori predefiniti in tali colonne.  
  
- -l  
Specifica un timeout accesso. L'opzione – l Specifica il numero di secondi prima di un account di accesso [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] timeout quando si tenta di connettersi a un server. Il timeout di accesso predefinito è 15 secondi. Il timeout di accesso deve essere un numero compreso tra 0 e 65534. Se il valore specificato non è numerico o non è compreso in tale intervallo, `bcp` genera un messaggio di errore. Il valore 0 specifica un timeout infinito.
  
- -L *last_row*  
Specifica il numero dell'ultima riga da esportare da una tabella o da importare da un file di dati.  
  
- -m *max_errors*  
Specifica il numero massimo di errori di sintassi che possono verificarsi prima che il `bcp` operazione annullata.  
  
- -n  
Esegue l'operazione di copia bulk usando i tipi di dati nativi del database.  
  
- -P *password*  
Specifica la password per l'ID di accesso.  
  
- -Q  
Esegue l'istruzione SET QUOTED_IDENTIFIERS ON durante la connessione tra l'utilità `bcp` e l'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)].  
  
- -r *row_terminator*  
Specifica il carattere di terminazione della riga.  
  
- -r  
Specifica che la copia bulk dei dati relativi a valuta, data e ora verrà eseguita in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] utilizzando il formato definito per le impostazioni locali del computer client.  
  
- -S *server*  
Specifica il nome del [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] istanza a cui connettersi, o se -D viene utilizzato, un DSN.  
  
- -t *field_terminator*  
Specifica il carattere di terminazione del campo.  
  
- -T  
Specifica che il `bcp` utilità connettersi [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] con una connessione trusted (sicurezza integrata).  
  
- -U *login_id*  
Specifica l'ID di accesso utilizzato per connettersi a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)].  
  
- -v  
Visualizza numero di versione e informazioni sul copyright per l'utilità `bcp`.  
  
- -w  
Esegue l'operazione di copia bulk usando caratteri Unicode.  
  
In questa versione sono supportati i caratteri Latin 1 e UTF-16.  
  
## <a name="unavailable-options"></a>Opzioni non disponibili
Nella versione corrente, la sintassi e le opzioni seguenti non sono disponibili:  

- -c  
Specifica la tabella codici dei dati contenuti nel file di dati.  
  
- -h *hint*  
Specifica gli hint usati per l'importazione bulk di dati in una tabella o in una vista.  
  
- -i *input_file*  
Specifica il nome di un file di risposta.  
  
- -n  
Usa i tipi di dati nativi del database per i dati non di tipo carattere e i caratteri Unicode per i dati di tipo carattere.  
  
- -o *output_file*  
Specifica il nome di un file in cui viene reindirizzato l'output dal prompt dei comandi.  
  
- -V (80 | 90 | 100)  
Utilizza i tipi di dati da una versione precedente di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)].  
  
- -x  
Se usato con le opzioni format e -f format_file, genera un file di formato basato su XML anziché un file di formato predefinito non XML.  
  
## <a name="see-also"></a>Vedere anche

[Connessione con **sqlcmd**](../../../connect/odbc/linux-mac/connecting-with-sqlcmd.md)  
