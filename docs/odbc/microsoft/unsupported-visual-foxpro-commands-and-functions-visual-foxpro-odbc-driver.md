---
title: Non supportato di comandi di Visual FoxPro e funzioni | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- FoxPro ODBC driver [ODBC], commands and functions
- functions [ODBC], Visual FoxPro
- Visual FoxPro ODBC driver [ODBC], commands and functions
- Visual FoxPro commands and functions
- FoxPro ODBC driver
ms.assetid: afdb6b7e-738d-42ca-8053-67ae50873ca6
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 37231b78815901678b1956d89e9bc3720ae1590d
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="unsupported-visual-foxpro-commands-and-functions-visual-foxpro-odbc-driver"></a>I comandi di Visual FoxPro non supportato e funzioni (Driver ODBC di Visual FoxPro)
La tabella seguente elenca in FoxPro comandi e funzioni che non sono supportate dal Driver ODBC Visual FoxPro, ma sono supportate da Microsoft® Visual FoxPro.  
  
 Se l'applicazione interagisca con dati la cui regole, trigger, i valori predefiniti o chiamano di stored procedure di tali comandi di Visual FoxPro o funzioni, il driver può generare un errore.  
  
## <a name="unsupported-visual-foxpro-commands-and-functions"></a>Funzioni e i comandi di Visual FoxPro non supportato  
  
||||  
|-|-|-|  
|#DEFINE... #UNDEF|... #IF #ENDIF per il preprocessore|#IFDEF &AMP;#124; #IFNDEF|  
|#INCLUDE per il preprocessore (direttiva)|:: Operatore di risoluzione dell'ambito|! Comando (vedere esecuzione di &#124; . Comando)|  
|? &#124; ?? Comando|??? Comando|\ &#124; \\\ Comando|  
|@ ... Comando casella|@ ... Comando di classe|@ ... Comando CLEAR|  
|@ ... Modifica - comando caselle di modifica|@ ... RIEMPIMENTO di comando|@ ... GET|  
|@ ... Comando di MENU|@ ... Comando PROMPT|@ ... Ad esempio di comando|  
|@ ... Comando di scorrimento|@ ... AL comando||  
  
## <a name="a"></a>A  
  
||||  
|-|-|-|  
|ACCETTARE i comandi|Funzione ACLASS)|Attiva comando di MENU|  
|ATTIVARE il comando di scelta rapida|ATTIVARE il comando di SCHERMATA|ATTIVARE la finestra di comando|  
|Metodo ActivateCell|AGGIUNGERE il comando di classe|Funzione ADIR)|  
|Funzione AFONT)|Funzione AINSTANCE)|Variabile di memoria di sistema _ALIGNMENT|  
|Funzione AMEMBERS)|Funzione ANSITOOEM)|Funzione APRINTERS)|  
|Funzione ASELOBJ)|Comando ASSIST||  
  
## <a name="b"></a>B  
  
||||  
|-|-|-|  
|BARRA () (funzione)|Funzione BARCOUNT)|Funzione BARPROMPT)|  
|Variabile di memoria di sistema _BEAUTIFY|Variabile di memoria di sistema _BOX|Comando Sfoglia|  
|Variabile di memoria di sistema browser|COMPILARE il comando di APP|COMPILA file EXE (comando)|  
|COMPILA progetto (comando)|Variabile di memoria di sistema _BUILDER||  
  
## <a name="c"></a>C  
  
||||  
|-|-|-|  
|Variabile di memoria di sistema _CALCVALUE|Variabile di memoria di sistema _CLIPTEXT|Variabile di memoria di sistema _CONVERTER|  
|Variabile di memoria di sistema _CUROBJ|Comando di chiamata|Comando Annulla|  
|CAPSLOCK () (funzione)|Comando CD|Comando di modifica|  
|Comando CHDIR|Funzione CHRSAW)|Comando Chiudi MEMO|  
|Funzione CNTBAR)|Funzione CNTPAD)|Funzione di COL)|  
|Comando di compilazione|COMPILARE il comando DATABASE|COMPILARE il comando FORM|  
|Funzione COMPOBJ)|Oggetto contenitore|Oggetto di controllo|  
|COPIARE i FILE (comando)|COPIARE il comando di credito|CREARE un comando di classe|  
|CREARE un comando CLASSLIB|CREARE un comando SET di colori|CREARE un comando|  
|CREARE un comando di connessione|CREARE un comando di DATABASE|CREARE un comando di FORM|  
|Il nome di comando|CREARE un comando di etichetta|CREARE un comando di MENU|  
|CREARE un comando di progetto|CREARE un comando di QUERY|CREARE un comando di REPORT|  
|CREARE un comando di SCHERMATA|CREARE un comando di vista SQL|CREARE un comando di TRIGGER|  
|CREARE un comando di visualizzazione|CREATEOBJECT () (funzione)|Funzione CURDIR)|  
  
## <a name="d"></a>D  
  
||||  
|-|-|-|  
|Variabile di memoria di sistema _DBLCLICK|Variabile di memoria di sistema _DIARYDATE|Funzione DBSETPROP)|  
|Funzioni DDE|DISATTIVARE il comando MENU|DISATTIVARE il comando di scelta rapida|  
|DISATTIVARE la finestra di comando|DICHIARARE - comando DLL|DICHIARARE comando|  
|DEFINIRE barra dei comandi|DEFINIRE il comando casella|DEFINIRE il comando di classe|  
|DEFINIRE il comando MENU|DEFINIRE il comando di riempimento|DEFINIRE il comando di scelta rapida|  
|DEFINIRE una finestra di comando|ELIMINARE il comando di connessione|ELIMINARE il comando DATABASE|  
|ELIMINARE i FILE (comando)|Comando TRIGGER DELETE|VISUALIZZAZIONE comando DELETE|  
|Comando DIR|Comando di DIRECTORY|Comando di visualizzazione|  
|Comando connessioni di visualizzazione|Comando DATABASE di visualizzazione|Comando DLL di visualizzazione|  
|VISUALIZZAZIONE file (comando)|Comando memoria visualizzazione|Comando oggetti visualizzazione|  
|Comando procedure visualizzazione|Comando lo stato di visualizzazione|VISUALIZZAZIONE struttura comando|  
|Comando di visualizzazione tabelle|Comando di viste di visualizzazione|MODULO di comando|  
  
## <a name="e"></a>E  
  
||||  
|-|-|-|  
|Comando di modifica|Errore del comando||  
|Comando di cancellazione|Comando esterno|Comando di esportazione|  
|RIMOZIONE di comando|RIMUOVERE il comando pagina||  
  
## <a name="f"></a>F  
  
||||  
|-|-|-|  
|Variabile di memoria di sistema _FOXDOC|Variabile di memoria di sistema _FOXGRAPH|FEOF () (funzione)|  
|FCLOSE () (funzione)|Funzione FCREATE)|() Di fgets (funzione)|  
|FERROR () (funzione)|FFLUSH () (funzione)|Funzione FKLABEL)|  
|Comando di filtro|Comando Trova|FOPEN () (funzione)|  
|Funzione FKMAX)|Funzione FONTMETRIC)|FSEEK () (funzione)|  
|() Di fputs (funzione)|FREAD () (funzione)||  
|FWRITE () (funzione)|Funzione FCHSIZE)||  
  
## <a name="g"></a>G  
  
||||  
|-|-|-|  
|Variabile di memoria di sistema _GENGRAPH|Variabile di memoria di sistema _GENMENU|Variabile di memoria di sistema _GENPD|  
|Variabile di memoria di sistema _GENSCRN|Variabile di memoria di sistema _GENXTAB|Funzione GETBAR)|  
|GETCOLOR () (funzione)|Funzione GETDIR)|Comando GETEXPR|  
|Funzione GETFILE)|GETFONT () (funzione)|GETOBJECT () (funzione)|  
|Funzione GETPAD)|Funzione GETPICT)|Funzione GETPRINTER)|  
  
## <a name="h"></a>H  
  
||||  
|-|-|-|  
|Comando della Guida|NASCONDERE il comando MENU|NASCONDERE il comando di scelta rapida|  
|Nascondi finestra di comando|Funzione (HOME)||  
  
## <a name="i"></a>I  
  
||||  
|-|-|-|  
|Funzione IMESTATUS)|Comando di importazione|Comandi di INPUT|  
|INDICE di comando|Funzione INKEY)|Funzione ISCOLOR)|  
|Comando di inserimento|Funzione INSMODE)||  
|Funzione ISMOUSE)|Variabile di memoria di sistema _INDENT||  
  
## <a name="j"></a>J  
  
||||  
|-|-|-|  
|Comando di JOIN|||  
  
## <a name="k"></a>K  
  
||||  
|-|-|-|  
|Comando da tastiera|||  
  
## <a name="l"></a>L  
  
||||  
|-|-|-|  
|Variabile di memoria di sistema _LMARGIN|Comando LABEL|Funzione LASTKEY)|  
|Funzione LINENO)|Comandi dell'elenco|ELENCA le connessioni (comando)|  
|Comando di caricamento|Funzione LOCFILE)||  
  
## <a name="m"></a>M  
  
||||  
|-|-|-|  
|Funzione MCOL)|Comando MD|Comando di MENU|  
|Funzione () di memoria|Comando di MENU|Comando MKDIR|  
|Funzione MENU)|Funzione MESSAGEBOX)|MODIFICARE il comando di connessione|  
|MODIFICARE il comando di classe|MODIFICARE il comando di comando|MODIFICARE il comando FORM|  
|MODIFICARE il comando DATABASE|MODIFICARE i FILE (comando)|MODIFICARE il comando di credito|  
|MODIFICARE il comando generale|MODIFICARE il comando di etichetta|MODIFICARE il comando di progetto|  
|MODIFICARE il comando MENU|Comando di routine di modifica|MODIFICARE il comando di SCHERMATA|  
|MODIFICARE il comando QUERY|MODIFICARE il comando REPORT|FINESTRA di comando di modifica|  
|Modifica struttura|Comando di visualizzazione di modifica|SPOSTARE una finestra di comando|  
|Comando del MOUSE|SPOSTARE il comando di scelta rapida|Funzione MROW)|  
|Funzione MRKBAR)|Funzione MRKPAD)||  
|Funzione MWINDOW)|Funzione MDOWN)||  
  
## <a name="n"></a>N  
  
||||  
|-|-|-|  
|Funzione di BLOCNUM)|||  
  
## <a name="o"></a>O  
  
||||  
|-|-|-|  
|Funzione OBJNUM)|Funzione OBJTOCLIENT)|ON barra dei comandi|  
|Funzione () non vengono|COMANDO APLABOUT|Comando MENU EXIT ON|  
|NEL comando di ESCAPE|IN uscita della barra dei comandi|CHIAVE = comando|  
|ON EXIT-comando riempimento|ON EXIT-comando POPUP|Comando riempimento ON|  
|COMANDO etichetta chiave|COMANDO MACHELP|IN selezione della barra dei comandi|  
|Nella pagina di comando|COMANDO READERROR|COMANDO POPUP di selezione|  
|NEL comando di MENU di selezione|NEL riquadro di selezione, comando||  
|NEL comando di arresto|Funzione OBJVAR)||  
  
## <a name="p"></a>P  
  
||||  
|-|-|-|  
|Variabile di memoria di sistema _PADVANCE|Variabile di memoria di sistema _PAGENO|Variabile di memoria di sistema _PBPAGE|  
|Variabile di memoria di sistema _PCOLNO|Variabile di memoria di sistema _PCOPIES|Variabile di memoria di sistema _PDRIVER|  
|Variabile di memoria di sistema _PDSETUP|Variabile di memoria di sistema _PECODE|Variabile di memoria di sistema _PEJECT|  
|Variabile di memoria di sistema _PEPAGE|Variabile di memoria di sistema _PLENGTH|Variabile di memoria di sistema _PLINENO|  
|Variabile di memoria di sistema _PLOFFSET|Variabile di memoria di sistema _PPITCH|Variabile di memoria di sistema _PQUALITY|  
|Variabile di memoria di sistema _PRETEXT|Variabile di memoria di sistema _PSCODE|Variabile di memoria di sistema _PSPACING|  
|Variabile di memoria di sistema _PWAIT|Comando DATABASE di Service PACK|Funzione di riempimento)|  
|Funzione PCOL)|Funzione PEMSTATUS)|Comando di riproduzione (macro)|  
|Comando POP chiave|Comando di MENU POP|Comando POPUP POP|  
|Funzione POPUP)|PRINTJOB... Comando ENDPRINTJOB|Funzione PRINTSTATUS)|  
|Funzione PRMBAR)|Funzione PRMPAD)|Funzione (prompt dei comandi)|  
|Funzione PROW)|Funzione PRTINFO)|Comando chiave PUSH|  
|Comando di MENU PUSH|Comando POPUP PUSH|Funzione PUTFILE)|  
  
## <a name="q"></a>Q  
  
||||  
|-|-|-|  
|Chiudere comando|||  
  
## <a name="r"></a>L  
  
||||  
|-|-|-|  
|Variabile di memoria di sistema _RMARGIN|Comando di desktop remoto|Funzione READKEY)|  
|LEGGERE il comando|LEGGERE il comando MENU|VERSIONE della barra dei comandi|  
|Refresh() (funzione)|Comando di INDICIZZAZIONE|VERSIONE libreria comando|  
|Comando CLASSLIB versione|Comando di rilascio|Comando blocco note di rilascio|  
|Comando menu versione|Comando MODULE versione|Comando di WINDOWS versione|  
|Comando POPUPS versione|PROCEDURE di rilascio (comando)|Il comando di RIDENOMINAZIONE|  
|RIMUOVERE il comando di classe|RINOMINARE il comando di classe|Visualizza il comando di RIDENOMINAZIONE|  
|RINOMINARE il comando di connessione|RINOMINARE il comando di tabella|RIPRISTINO dal comando|  
|Comando REPORT|REQUERY () (funzione)|FINESTRA di comando di ripristino|  
|RIPRISTINARE il comando macro|RESTORE-comando SCHERMATA|Funzione RGBSCHEME)|  
|Comando Riprendi|Funzione RGB)|ESEGUIRE &AMP;#124; . Comando|  
|Comando RMDIR|Funzione di riga)||  
|Comando RUNSCRIPT|Funzione RDLEVEL)||  
  
## <a name="s"></a>S  
  
||||  
|-|-|-|  
|Comando macro Salva|Salva SCHERMATA comando|Salvare al comando|  
|SALVARE il comando di WINDOWS|Funzione di combinazione)|Funzione SCOLS)|  
|Comando di scorrimento|Variabile di memoria di sistema schermo|Comando SET|  
|Comando ALTERNATIVO SET|Comando ANSI SET|Comando APLABOUT SET|  
|SET di comandi di salvataggio automatico|Comando CAMPANELLO SET|Comando BLINK SET|  
|Comando bordo SET|Comando BRSTATUS SET|Comando CLASSLIB SET|  
|Comando Cancella SET|Comando CLOCK SET|IMPOSTARE il colore di comando|  
|IMPOSTARE il colore del comando di schema|Comando SET di SET di colori|IMPOSTARE il colore di comando|  
|Comando compatibile SET|Comando conferma SET|Comando CONSOLE insieme|  
|SET CPCOMPILE|SET CPDIALOG|Comando valuta SET|  
|SET di cursore (comando)|Comando DATASESSION SET|SET di comandi DEBUG|  
|Comando DECIMALI SET|SET di DELIMITATORI comando|Comando sviluppo SET|  
|Comando SET|Comando di visualizzazione di SET|Comando DOHISTORY SET|  
|Comando ECHO SET|Comando ESCAPE SET|Comando formato SET|  
|Comando SET (funzione)|Comando intestazioni SET|Comando Guida SET|  
|Comando HELPFILTER SET|Comando intensità SET|Comando chiave SET|  
|Comando KEYCOMP SET|Comando LOGERRORS SET|Comando MACDESKTOP SET|  
|Comando MACHELP SET|Comando MACKEY SET|Comando margine SET|  
|CONTRASSEGNARE i SET di comandi|CONTRASSEGNO di SET di comandi|Comando MEMOWIDTH SET|  
|Comando messaggio SET|Comando MOUSE SET|Comando CHILOMETRAGGIO SET|  
|Comando OLEOBJECT SET|Comando TAVOLOZZA SET|Comando PDSETUP SET|  
|Comando Imposta punto|Comando stampante SET|Comando READBORDER SET|  
|Comando di aggiornamento di SET|Comando SET di risorse|Comando sicurezza SET|  
|Comando TABELLONE SET|Comando secondi SET|Comando separatore SET|  
|Comando SHADOWS SET|Ignora SET di comandi|Comando spazio SET|  
|Comando stato SET|IMPOSTARE lo stato della barra dei comandi|Comando istruzione SET|  
|Comando STICKY SET|Comando SYSFORMATS SET|Comando SYSMENU SET|  
|Comando PARLARE SET|Comando TEXTMERGE SET|Comando di DELIMITATORI TEXTMERGE SET|  
|Comando argomento SET|SET argomento ID comando|Comando TRBETWEEN SET|  
|Comando TYPEAHEAD SET|Comando di visualizzazione di SET|Imposta finestra di comando di credito|  
|Comando XCMDFILE SET|Variabile di memoria di sistema _SHELL|Mostra il comando GET|  
|Mostra comando Ottiene|Mostra voce di menu|Mostra l'oggetto comando|  
|Mostra il comando di scelta rapida|Mostra finestra di comando|Comando POPUP di dimensione|  
|DIMENSIONI finestra (comando)|Funzione SKPBAR)|Funzione SKPPAD)|  
|Funzione SOUNDEX)|Variabile di memoria di sistema _SPELLCHK|Funzioni SQL|  
|Funzione SROWS)|Variabile di memoria di sistema Startup|Comando di sospensione|  
|Funzioni di sys() eccetto SYS(2011)|Funzione SYSMETRIC)||  
  
## <a name="t"></a>T  
  
||||  
|-|-|-|  
|Variabile di memoria di sistema _TABS|TESTO... Comando ENDTEXT|Funzione TXTWIDTH)|  
|TRANSFORM (funzione))|Variabile di memoria di sistema _TRANSPORT||  
|Comando di tipo|Variabile di memoria di sistema _THROTTLE||  
  
## <a name="u"></a>U  
  
||||  
|-|-|-|  
|Funzione (AGGIORNATO)|COMANDO||  
  
## <a name="v"></a>V  
  
||||  
|-|-|-|  
|CONVALIDARE il comando DATABASE|Funzione VARREAD)|Funzione di versione)|  
  
## <a name="w"></a>W  
  
||||  
|-|-|-|  
|Variabile di memoria di sistema di Windows|Variabile di memoria di sistema _WIZARD|Funzione WCHILD)|  
|ATTESA di comando|Funzione WBORDER)|Funzione WFONT)|  
|Funzione WCOLS)|Funzione WEXIST)|Funzione WLROW)|  
|CON... Comando ENDWITH|Funzione WLAST)|Funzione WONTOP)|  
|Funzione WMAXIMUM)|Funzione WLCOL)|Funzione WREAD)|  
|Funzione WOUTPUT)|Funzione WMINIMUM)|Funzione WVISIBLE)|  
|Funzione WPARENT)|Funzione WTITLE)||  
|Funzione WROWS)|Variabile di memoria di sistema _WRAP||  
  
## <a name="z"></a>Z  
  
||||  
|-|-|-|  
|FINESTRA di ZOOM (comando)|||
