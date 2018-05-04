---
title: Mapping di caratteri SQL Server e MySQL impostare (MySQLToSQL) | Documenti Microsoft
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-mysql
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
ms.assetid: 20b3f22e-16a2-4a87-b4eb-c277be6bf5c8
caps.latest.revision: 4
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 0a0b1abc184a6c7c0031d1b8d2dacd6d05cda324
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="mapping-mysql-and-sql-server-character-set-mysqltosql"></a>Mapping di caratteri SQL Server e MySQL impostare (MySQLToSQL)
Per i tipi di dati carattere, espressioni e valori letterali di MySQL, è possibile specificare il set di caratteri (set di caratteri).  
  
## <a name="charset-mapping"></a>Mapping di set di caratteri  
Mapping di set di caratteri è definito per ogni set di caratteri di MySQL e utilizzato durante la conversione di tipi di dati carattere. Specifica come convertire i tipi di dati di stringa di caratteri di un particolare set di caratteri:  
  
-   Ai tipi di caratteri nazionali SQL Server (NCHAR/NVARCHAR) o  
  
-   Ai tipi di carattere normale SQL Server (CHAR/VARCHAR)  
  
1.  **National** sono tipi di dati carattere di database di destinazione:  
  
    1.  **nchar**  
  
    2.  **nvarchar**  
  
2.  **regolare** sono tipi di dati carattere di database di destinazione:  
  
    1.  **char**  
  
    2.  **varchar**  
  
3.  Mapping dei tipi consente solo il mapping a **national** tipi di dati carattere. Dopo aver convertito il tipo di dati character MySQL in base ai mapping dei tipi, viene applicato il mapping di set di caratteri.  
  
> [!NOTE]  
> Mapping di set di caratteri possono essere definiti in ogni livello del nodo di Esplora oggetti di metadati e rappresentano tutti i set di caratteri letti da MySQL.  
  
## <a name="charset-mapping-on-different-node-levels"></a>Mapping di set di caratteri in diversi livelli di nodo  
Mapping di set di caratteri varia a livello di nodo diverso, vale a dire:  
  
1.  Nel livello del nodo di metadati principale  
  
2.  Nel Database, categoria e livello di nodi oggetto  
  
> [!NOTE]  
> La scheda selezionata per la modifica il Mapping di set di caratteri, contiene tre pulsanti, indipendentemente dal mapping ai livelli di nodo diverso.  
>   
> ovvero:  
>   
> 1.  **Si applicano:** applica le modifiche apportate dall'utente, abilitato solo quando il mapping di set di caratteri viene modificato e non ancora salvato.  
> 2.  **Annulla:** Annulla le modifiche apportate dall'utente. Il pulsante ottiene attivato quando il mapping di set di caratteri è modificato ma non salvato.  
> 3.  **Ripristina predefiniti:** Reimposta tutti i mapping di valori predefiniti.  
  
1.  **Livello del nodo di metadati principale on:** griglia di mapping di set di caratteri contiene set di caratteri griglia con una colonna separata per ogni set di caratteri. Le colonne della griglia sono:  
  
    1.  La prima colonna della griglia denominata **nome set di caratteri** contiene il nome di set di caratteri.  
  
    2.  Il secondo quello denominato **descrizione Charset** contiene una descrizione di set di caratteri.  
  
    3.  La terza colonna intitolata **il tipo di set di caratteri di destinazione** contiene le impostazioni di mapping per i set di caratteri specifico. I valori per questa colonna sono:  
  
        -   CHAR/VARCHAR  
  
        -   NCHAR/NVARCHAR  
  
    > [!IMPORTANT]  
    > Dopo CHAR/VARCHAR o NCHAR/NVARCHAR, i valori predefiniti per un particolare set di caratteri hanno il prefisso '(predefinito)'.  
  
    Il mapping di set di caratteri tra i database MySQL e il database di destinazione sul livello del nodo radice dei metadati è specificato di seguito:  
  
    ||||  
    |-|-|-|  
    |**Nome del set di caratteri**|**Descrizione set di caratteri**|**Tipo di set di caratteri di destinazione (impostazione predefinita)**|  
    |BIG5|Cinese tradizionale Big5|NCHAR/NVARCHAR (impostazione predefinita)|  
    |dec8|Europa occidentale DEC|CHAR/VARCHAR (impostazione predefinita)|  
    |cp850|Europa occidentale DOS|CHAR/VARCHAR (impostazione predefinita)|  
    |hp8|Europa occidentale HP|CHAR/VARCHAR (impostazione predefinita)|  
    |koi8r|Russo Relcom KOI8-R|CHAR/VARCHAR (impostazione predefinita)|  
    |alfabeto latino 1|Europa occidentale CP1252|CHAR/VARCHAR (impostazione predefinita)|  
    |Latin2|Europa centrale ISO 8859-2|CHAR/VARCHAR (impostazione predefinita)|  
    |swe7|Svedese a 7 bit|CHAR/VARCHAR (impostazione predefinita)|  
    |ascii|STATI UNITI ASCII|CHAR/VARCHAR (impostazione predefinita)|  
    |ujis|Giapponese EUC-JP|NCHAR/NVARCHAR (impostazione predefinita)|  
    |sjis|Giapponese Shift-JIS|NCHAR/NVARCHAR (impostazione predefinita)|  
    |Ebraico|ISO 8859-8 Ebraico|CHAR/VARCHAR (impostazione predefinita)|  
    |tis620|TIS620 Thai|CHAR/VARCHAR (impostazione predefinita)|  
    |eucKR|Coreano EUC-KR|NCHAR/NVARCHAR (impostazione predefinita)|  
    |koi8u|Ucraino KOI8-U|CHAR/VARCHAR (impostazione predefinita)|  
    |gb2312|GB2312 Cinese semplificato|NCHAR/NVARCHAR (impostazione predefinita)|  
    |Greco|ISO 8859-7 Greco|CHAR/VARCHAR (impostazione predefinita)|  
    |cp 1250|Europa centrale di Windows|CHAR/VARCHAR (impostazione predefinita)|  
    |GBK|Cinese semplificato GBK|NCHAR/NVARCHAR (impostazione predefinita)|  
    |Latin5|ISO 8859-9 Turco|CHAR/VARCHAR (impostazione predefinita)|  
    |armscii8|Armeno ARMSCII-8|CHAR/VARCHAR (impostazione predefinita)|  
    |UTF8|Unicode UTF-8|NCHAR/NVARCHAR (impostazione predefinita)|  
    |ucs2|Unicode UCS-2|NCHAR/NVARCHAR (impostazione predefinita)|  
    |cp866|Russo DOS|CHAR/VARCHAR (impostazione predefinita)|  
    |keybcs2|DOS Kamenicky ceco-slovacco|CHAR/VARCHAR (impostazione predefinita)|  
    |macce|Europa centrale Mac|CHAR/VARCHAR (impostazione predefinita)|  
    |MacRoman|Europa occidentale Mac|CHAR/VARCHAR (impostazione predefinita)|  
    |cp852|Europa centrale DOS|CHAR/VARCHAR (impostazione predefinita)|  
    |Latin7|ISO 8859-13 Baltico|CHAR/VARCHAR (impostazione predefinita)|  
    |cp 1251|Windows cirillico|CHAR/VARCHAR (impostazione predefinita)|  
    |cp 1256|Windows arabo|CHAR/VARCHAR (impostazione predefinita)|  
    |cp 1257|Baltico Windows|CHAR/VARCHAR (impostazione predefinita)|  
    |BINARY|Set di caratteri binari pseudo|CHAR/VARCHAR (impostazione predefinita)|  
    |geostd8|Georgiano GEOSTD8|CHAR/VARCHAR (impostazione predefinita)|  
    |cp932|SJIS per il giapponese di Windows|NCHAR/NVARCHAR (impostazione predefinita)|  
    |eucjpms|UJIS per il giapponese di Windows|NCHAR/NVARCHAR (impostazione predefinita)|  
  
2.  **Nel Database, di categoria o i livelli dei nodi oggetto:** a livello di Database, categoria o nodi oggetto, della griglia di mapping di set di caratteri contiene le stesse righe nel livello di nodo radice dei metadati, dei quali.:  
  
    1.  La prima colonna della griglia intitolata **imposta il nome del carattere** contiene il nome di set di caratteri.  
  
    2.  La seconda colonna denominata, **descrizione Set di caratteri** contiene una descrizione di set di caratteri.  
  
    3.  L'unica differenza è i valori della terza colonna della griglia. La terza colonna intitolata **il tipo di dati di destinazione** contiene le impostazioni di mapping per i set di caratteri specifico. I valori della colonna sono:  
  
        -   Ereditata (CHAR/VARCHAR o NCHAR/NVARCHAR)  
  
        -   CHAR/VARCHAR  
  
        -   NCHAR/NVARCHAR  
  
> [!IMPORTANT]  
> -   Nel mapping di set di caratteri tra database MySQL e database di destinazione nel Database, categoria e i livelli dei nodi oggetto, i valori predefiniti per un particolare set di caratteri a ogni livello diversa dalla radice per la colonna **il tipo di dati di destinazione** deve essere 'ereditata'.  
> -   Nella griglia, il valore **Inherited** è Posposto con '(CHAR/VARCHAR)' o '(NCHAR/NVARCHAR)' a seconda di quale valore è stato ereditato dall'elemento padre per questo specifico set di caratteri.  
  
