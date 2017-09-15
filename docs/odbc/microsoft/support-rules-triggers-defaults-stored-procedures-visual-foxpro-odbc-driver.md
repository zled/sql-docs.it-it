---
title: Supporto per la Stored procedure, trigger, i valori predefiniti e regole | Documenti Microsoft
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
- Visual FoxPro ODBC driver [ODBC], stored procedures
- FoxPro ODBC driver [ODBC], commands and functions
- commands for FoxPro ODBC driver [ODBC]
- FoxPro ODBC driver [ODBC], default values
- FoxPro ODBC driver [ODBC], triggers
- stored procedures [ODBC], Visual FoxPro ODBC driver
- Visual FoxPro ODBC driver [ODBC], rules
- FoxPro commands and functions [ODBC]
- rules [ODBC]
- Visual FoxPro ODBC driver [ODBC], default values
- FoxPro ODBC driver [ODBC], rules
- functions [ODBC], Visual FoxPro
- default values [ODBC]
- Visual FoxPro ODBC driver [ODBC], commands and functions
- Visual FoxPro ODBC driver [ODBC], triggers
- FoxPro ODBC driver [ODBC], stored procedures
- Visual FoxPro commands and functions [ODBC]
ms.assetid: e449de20-d6ca-4902-9f8e-814eb6e86650
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e11b18afb96c7e5c1dc6ef6c23fc56cd3a75548e
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="support-for-rules-triggers-default-values-and-stored-procedures-visual-foxpro-odbc-driver"></a>Supporto per le regole, valori predefiniti, trigger e Stored procedure, Driver ODBC di Visual FoxPro,
È possibile creare regole di Visual FoxPro, trigger, i valori predefiniti o stored procedure utilizzando il Driver ODBC di Visual FoxPro. Tuttavia, l'applicazione potrebbe interagire con le regole esistenti, trigger, i valori predefiniti o stored procedure come inserisce, aggiorna o Elimina Visual FoxPro i dati archiviati in un database.  
  
 Nella tabella seguente sono elencati i comandi di Visual FoxPro e funzioni supportate dal Driver ODBC Visual FoxPro quando sono presenti i comandi o le funzioni in stored procedure, trigger, i valori predefiniti o regole.  
  
 Se l'applicazione interagisca con dati la cui regole, trigger, i valori predefiniti o stored procedure chiamano altri comandi di Visual FoxPro o funzioni, il driver genera un errore. Vedere [funzioni e i comandi non supportati da Visual FoxPro](../../odbc/microsoft/unsupported-visual-foxpro-commands-and-functions-visual-foxpro-odbc-driver.md) per un elenco di comandi e funzioni non supportate dal driver.  
  
> [!TIP]  
>  Se si desidera inserire il codice condizionale le regole, trigger o stored procedure che determina i comandi da eseguire quando viene chiamato dal driver, è possibile utilizzare il **() versione** (funzione). Il **() versione** risultato della funzione "Driver ODBC Visual FoxPro * \<versione >*" quando viene chiamato dal driver.  
  
## <a name="visual-foxpro-commands-and-functions-supported-in-rules-triggers-default-values-and-stored-procedures"></a>Funzioni supportate in Stored procedure, trigger, i valori predefiniti e regole e i comandi di Visual FoxPro  
  
||||  
|-|-|-|  
|Operatore $|% (Operatore)|& Comando|  
|& & Comando|* Comando|= Comando|  
  
## <a name="a"></a>Un  
  
||||  
|-|-|-|  
|ABS () (funzione)|Funzione ACOPY)|AGGIUNGERE il comando di tabella|  
|Funzione ADATABASES)|Funzione ADBOBJECTS)|Funzione AERROR)|  
|Funzione di ADEL)|Funzione AELEMENT)|Funzione ALEN)|  
|Funzione AFIELDS)|Funzione AINS)|ALTER TABLE - comando SQL|  
|Funzione ALIAS)|Funzione ALLTRIM)|AGGIUNGERE il comando di matrice|  
|AND (operatore)|Aggiungi comando|AGGIUNGERE il comando di credito|  
|AGGIUNGERE dal comando|AGGIUNGERE il comando generale|Funzione ASCAN)|  
|AGGIUNGERE il comando procedure|Funzione)|Funzione ASUBSCRIPT)|  
|ASIN () (funzione)|Funzione ASORT)|ATAN () (funzione)|  
|FUNZIONE)|Funzione AT_C)|Funzione ATCLINE)|  
|Funzione di traffico aereo)|Funzione ATCC)|Funzione AUSED)|  
|Funzione ATLINE)|ATN2-funzione)||  
|Comando medio|ACOS () (funzione)||  
  
## <a name="b"></a>B  
  
||||  
|-|-|-|  
|Comando BEGIN TRANSACTION|TRA () (funzione)|Funzione BITNOT)|  
|Funzione BITCLEAR)|Funzione BITLSHIFT)|BITSET () (funzione)|  
|BITOR () (funzione)|Funzione BITRSHIFT)|Comando vuota|  
|Funzione BITTEST)|Funzione BITXOR)||  
|Funzione BOF)|BITAND () (funzione)||  
  
## <a name="c"></a>C  
  
||||  
|-|-|-|  
|Il comando di calcolo|Funzione di candidato)|Funzione)|  
|Funzione CDX)|Ceiling-funzione)|Comandi CLOSE|  
|Funzione CHRTRAN)|Funzione CHRTRANC)|COPIARE il comando di indici|  
|Funzione CMONTH)|Comando di continuare|Comando di copia struttura estesa|  
|COPIARE il comando procedure|COPIARE il comando di struttura|COPIA al comando|  
|COPIARE il comando TAG|COPIARE il comando di matrice|Funzione CPCONVERT)|  
|COS () funzione|Comando COUNT|Funzione CTOD)|  
|Funzione CPCURRENT)|Funzione CPDBF)|Funzione CURSORSETPROP)|  
|Funzione CTOT)|Funzione CURSORGETPROP)||  
|Funzione CURVAL)|Funzione CDOW)||  
  
## <a name="d"></a>D  
  
||||  
|-|-|-|  
|Funzione di data)|DATETIME () (funzione)|GIORNO () (funzione)|  
|Funzione di due byte)|Funzione DBF)|Funzione DBGETPROP)|  
|Funzione DBUSED)|DELETE - comando SQL|Comando DELETE|  
|ELIMINARE i comandi di TAG|Funzione (eliminati)|DECRESCENTE () (funzione)|  
|Funzione di differenza)|Comando di dimensione|Funzione () su disco insufficiente|  
|Funzione DMY)|ESEGUIRE I CASI... Comando ENDCASE|Comando|  
|WHILE... Comando ENDDO|Funzione di finestra)|Funzione DTOC)|  
|Funzione DTOR)|Funzione di DTO)|Funzione DTOT)|  
  
## <a name="e"></a>E  
  
||||  
|-|-|-|  
|Funzione (vuoto)|VALUTARE la funzione)|EXIT-comando|  
|Funzione di errore)|EXP () (funzione)||  
|Comando END TRANSACTION|EOF () (funzione)||  
  
## <a name="f"></a>F  
  
||||  
|-|-|-|  
|Funzione FCOUNT)|Funzione FDATE)|Funzione di campo)|  
|Funzione FILE)|Funzione di filtro)|Funzione FLDLIST)|  
|Funzione di gruppo)|FLOOR () (funzione)|Comando SCARICAMENTO|  
|FOR... Comando ENDFOR|PER la funzione)|TROVARE la funzione)|  
|Comando tabella disponibile|Funzione FSIZE)|FTIME () (funzione)|  
|FULLPATH () (funzione)|Comando (funzione)|Funzione di Val)|  
  
## <a name="g"></a>G  
  
||||  
|-|-|-|  
|La raccolta di comando|Funzione GETNEXTMODIFIED)|Comando GO/GOTO|  
|Funzione GETFLDSTATE)|Funzione GOMONTH)||  
|Funzione GETCP)|GETENV () (funzione)||  
  
## <a name="h"></a>H  
  
|||  
|-|-|  
|Funzione di intestazione)|ORA () (funzione)|  
  
## <a name="i"></a>I  
  
||||  
|-|-|-|  
|Funzione IDXCOLLATE)|SE... Comando ENDIF|Funzione IIF)|  
|Funzione INDBC)|Comando indice|Funzione di elenco)|  
|Comando INSERT SQL|INT () (funzione)|ISALPHA () (funzione)|  
|Funzione di Val)|ISDIGIT (funzione))|Funzione ISEXCLUSIVE)|  
|ISLEADBYTE () (funzione)|() Di IsLower (funzione)|ISNULL ()-funzione|  
|Funzione ISREADONLY)|ISUPPER () (funzione)||  
  
## <a name="k"></a>K  
  
||||  
|-|-|-|  
|Funzione (chiave)|Funzione KEYMATCH)||  
  
## <a name="l"></a>L  
  
||||  
|-|-|-|  
|Funzione LEFT)|Funzione LEFTC)|Funzione LIKEC)|  
|Funzione LENC)|Ad esempio di funzione)|LOCK () (funzione)|  
|Comando locale|INDIVIDUARE comando|Funzione di ricerca)|  
|LOG () (funzione)|LOG10 (funzione))|LTRIM ()-funzione|  
|Funzione LOWER di)|Comando LPARAMETERS||  
|Funzione LUPDATE)|Funzione LEN)||  
  
## <a name="m"></a>M  
  
||||  
|-|-|-|  
|Variabile di memoria di sistema _MLINE|Funzione MAX)|Funzione MDX)|  
|Funzione MDY)|Funzione MEMLINES)|Funzione di messaggio)|  
|MIN () (funzione)|Funzione (minuti)|Funzione MLINE)|  
|Funzione MOD)|Funzione di mese)|Funzione MTON)|  
  
## <a name="n"></a>N  
  
||||  
|-|-|-|  
|Funzione NDX)|NORMALIZZARE () (funzione)|NOT (operatore)|  
|Comando nota|Funzione NTOM)|Funzione NVL)|  
  
## <a name="o"></a>O  
  
||||  
|-|-|-|  
|Si verifica () (funzione)|Funzione OLDVAL)|NEL comando di errore|  
|COMANDO chiave|NELLA funzione)|Comando DATABASE aperti|  
|Operatore OR|Funzione di ordine)|Funzione () del sistema operativo|  
  
## <a name="p"></a>P  
  
||||  
|-|-|-|  
|Comando PACK|Funzione di parametri)|Funzione di pagamento)|  
|Comando di parametri|Funzione (primario)|Comando privato|  
|Funzione di PI)|Funzione () del programma|Funzione (corretto)|  
|PROCEDURE (comando)|Funzione di PV)||  
|Comando pubblico|() PADL &#124; () PADR &#124; Funzioni PADC)||  
  
## <a name="r"></a>L  
  
||||  
|-|-|-|  
|Funzione di RAND)|Funzione RAT)|Funzione RATC)|  
|Funzione RATLINE)|Richiama comando|Funzione RECCOUNT)|  
|Funzione RECNO)|Funzione RECSIZE)|Comando internazionale|  
|Funzione di relazione)|RIMUOVERE il comando di tabella|Sostituisci (comando)|  
|Sostituire dal comando di matrice|REPLICATE (funzione))|Ripetere i comandi|  
|RESTITUIRE comando|Funzione (destra)|Funzione RIGHTC)|  
|Funzione RLOCK)|Comando ROLLBACK|Funzione ROUND)|  
|Funzione RTOD)|RTRIM ()-funzione||  
  
## <a name="s"></a>S  
  
||||  
|-|-|-|  
|ANALISI... Comando ENDSCAN|Comando a dispersione|Funzione () al secondo|  
|Funzione () secondi|Comando di ricerca|SEEK (funzione))|  
|Selezionare i comandi|Funzione SELECT)|Comando SELECT-SQL|  
|Comando BLOCKSIZE SET|Comando CARRY SET|Comando secolo SET|  
|Comando COLLATE SET|Comando DATABASE SET|Comando Data SET|  
|Comando predefinito SET|Comando DELETED SET|Comando esatto SET|  
|Comando esclusivo SET|Comando FDOW SET|Comando SET di campi|  
|Comando filtro SET|SET di comandi fissi|Comando FULLPATH SET|  
|Comando FWEEK SET|Comando impostare ore|Comando SET|  
|Comando LOCK SET|Comando MULTILOCKS SET|IMPOSTARE prossimità del comando|  
|Comando NOCPTRANS SET|Comando di notifica SET|Comando NULL SET|  
|Comando OTTIMIZZA SET|Comando ordine SET|Comando percorso SET|  
|SET di PROCEDURE (comando)|Comando relazione SET|RELAZIONE di SET di comando|  
|Comando RIELABORAZIONE SET|Comando Ignora SET|Comando UDFPARMS SET|  
|Comando univoco SET|Comando VOLUME SET|Funzione sui SET)|  
|Funzione SETFLDSTATE)|Funzione di accesso)|SIN () (funzione)|  
|Comando Ignora|Comando SORT|Funzione di spazio)|  
|SQRT () (funzione)|Comando di archiviazione|STR ()-funzione|  
|Funzione STRCONV)|Funzione STRTRAN)|STUFF-funzione)|  
|Funzione STUFFC)|SUBSTR () (funzione)|Funzione SUBSTRC)|  
|Comando somma|SYS(2011) (funzione)||  
  
## <a name="t"></a>T  
  
||||  
|-|-|-|  
|Variabile di memoria di sistema _TALLY|Variabile di memoria di sistema _TRIGGERLEVEL|Funzione TAGCOUNT)|  
|Funzione TABLEUPDATE)|Funzione di TAG)|Funzione di destinazione)|  
|Funzione TAGNO)|Funzione TAN)|TRIM-funzione)|  
|TIME () (funzione)|Comando totale|Funzione TXNLEVEL)|  
|Funzione TTOC)|Funzione TTOD)||  
|Funzione di tipo)|Funzione TABLEREVERT)||  
  
## <a name="u"></a>U  
  
||||  
|-|-|-|  
|Funzione (univoco)|UNLOCK-comando|COMANDO|  
|Comando di aggiornamento|Funzione (superiore)||  
|FUNZIONE)|Comando SQL UPDATE-||  
  
## <a name="v"></a>V  
  
||||  
|-|-|-|  
|VAL () (funzione)|Funzione di versione)||  
  
## <a name="w"></a>W  
  
||||  
|-|-|-|  
|SETTIMANA ()-funzione|||  
  
## <a name="y"></a>S  
  
||||  
|-|-|-|  
|ANNO () (funzione)|||  
  
## <a name="z"></a>Z  
  
||||  
|-|-|-|  
|Comando ZAP|||
