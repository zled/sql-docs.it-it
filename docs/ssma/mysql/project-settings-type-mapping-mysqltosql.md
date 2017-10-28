---
title: Impostazioni (Mapping dei tipi) del progetto (MySQLToSQL) | Documenti Microsoft
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 136fdf6d-657f-447b-af41-49bbc6e0e93e
caps.latest.revision: 13
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 269c901b4242ae199f6d83fc7f678c29be39e5e5
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="project-settings-type-mapping-mysqltosql"></a>Impostazioni (Mapping dei tipi) del progetto (MySQLToSQL)
Le impostazioni di Mapping dei tipi del progetto consentono di impostare i mapping dei tipi predefiniti per il progetto SSMA.  

Mapping dei tipi è disponibile nelle finestre di dialogo Impostazioni di progetto e impostazioni di progetto predefinite:  
  
-   Utilizzare la finestra di dialogo Impostazioni di progetto per impostare le opzioni di configurazione per il progetto corrente. Per accedere alle impostazioni di mapping del tipo, nel menu Strumenti, selezionare le impostazioni di progetto e quindi nel riquadro sinistro fare clic su Mapping dei tipi.  
  
-   Utilizzare la finestra di dialogo Impostazioni di progetto predefinite per impostare le opzioni di configurazione per tutti i progetti. Per accedere ai mapping dei tipi di impostazioni, nel menu Strumenti, selezionare impostazioni di progetto predefinite, il tipo di progetto di migrazione selezionare per i quali impostazioni sono necessarie per essere visualizzati o modificati da **versione di destinazione della migrazione** elenco a discesa e quindi fare clic su Mapping dei tipi nel riquadro a sinistra.  
  
## <a name="options"></a>Opzioni  
  
##### <a name="source-type"></a>Tipo origine  
È il tipo di dati MySQL, che è necessario eseguire il mapping al tipo di dati di database di destinazione.  
  
##### <a name="target-type"></a>Tipo di destinazione  
Tipo di dati del database di destinazione per il tipo di dati MySQL specificato.  
  
##### <a name="add"></a>Aggiungi  
Fare clic per aggiungere un tipo di dati nell'elenco di mapping.  
  
##### <a name="edit"></a>Modifica  
Fare clic per modificare il tipo di dati selezionato nell'elenco di mapping.  
  
##### <a name="remove"></a>Rimuovi  
Fare clic per rimuovere il mapping dei tipi di dati selezionato dall'elenco di mapping.  
  
##### <a name="reset-to-default"></a>Ripristina predefiniti  
Fare clic per reimpostare l'elenco di mapping del tipo di SSMA predefinite.  
  
## <a name="type-mappings"></a>Mapping dei tipi  
Nella tabella seguente viene illustrato il mapping predefinito tra i tipi di dati di origine e di destinazione  
  
|||  
|-|-|  
|**Tipo di dati di MySQL**|**Tipo di dati SQL Server**|  
|bigint|bigint|  
|bigint [*..255]|bigint|  
|binary|binario [1]|  
|binario [0..1]|binario [1]|  
|binario [2..255]|binario [*]|  
|bit|binario [1]|  
|bit [0..8]|binario [1]|  
|bit [17..24]|binario [3]|  
|bit [25..32]|binario [4]|  
|bit [33..40]|binario [5]|  
|bit [41..48]|binario [6]|  
|bit [49..56]|binario [7]|  
|bit [57..64]|binario [8]|  
|bit [9..16]|binari [2]|  
|blob|varbinary(max)|  
|BLOB [0..1]|varbinary [1]|  
|BLOB [2..8000]|varbinary [*]|  
|BLOB [8001... *]|varbinary(max)|  
|bool|bit|  
|boolean|bit|  
|char|nchar [1]|  
|Char (byte)|binario [1]|  
|byte Char [0..1]|binario [1]|  
|byte Char [2..255]|binario [*]|  
|Char [0..1]|nchar [1]|  
|Char [2..255]|nchar [*]|  
|character|nchar [1]|  
|caratteri diversi [0..1]|nvarchar [1]|  
|caratteri diversi [2..255]|nvarchar|  
|caratteri [0..1]|nchar [1]|  
|caratteri [2..255]|nchar [*]|  
|data|data|  
|datetime|datetime2 [0]|  
|dec|Decimal|  
|DEC [*..65]|decimale [*] [0]|  
|DEC [*..65][\*..30]|decimale [*] [\*]|  
|Decimal|Decimal|  
|decimale [*..65]|decimale [*] [0]|  
|decimale [*..65][\*..30]|decimale [*] [\*]|  
|double|float [53]|  
|valore a precisione doppia|float [53]|  
|valore a precisione doppia [*..255][\*..30]|numerico [*] [\*]|  
|Double [*..255][\*..30]|numerico [*] [\*]|  
|predefinito|numeric|  
|fissa [*..65][\*..30]|numerico [*] [\*]|  
|float|float [24]|  
|float [*..255][\*..30]|numerico [*] [\*]|  
|float [*..53]|float [53]|  
|int|int|  
|int [*..255]|int|  
|integer|int|  
|numero intero [*..255]|int|  
|longblob|varbinary(max)|  
|LONGTEXT|nvarchar(max)|  
|mediumblob|varbinary(max)|  
|mediumint|int|  
|mediumint [*..255]|int|  
|mediumtext|nvarchar(max)|  
|char nazionali|nchar [1]|  
|National char [0..1]|nchar [1]|  
|National char [2..255]|nchar [*]|  
|caratteri nazionali|nchar [1]|  
|variabile di caratteri nazionali|nvarchar [1]|  
|caratteri nazionali varying [0..1]|nvarchar [1]|  
|caratteri nazionali varying [2..4000]|nvarchar [*]|  
|variabile di caratteri nazionale [4001... *]|nvarchar(max)|  
|caratteri nazionali [0..1]|nchar [1]|  
|caratteri nazionali [2..255]|nchar [*]|  
|varchar nazionali|nvarchar [1]|  
|National varchar [0..1]|nvarchar [1]|  
|National varchar [2..4000]|nvarchar [*]|  
|National varchar [4001... *]|nvarchar(max)|  
|nchar|nchar [1]|  
|nchar varchar|nvarchar [1]|  
|nchar varchar [0..1]|nvarchar [1]|  
|nchar varchar [2..4000]|nvarchar [*]|  
|nchar varchar [4001... *]|nvarchar(max)|  
|nchar [0..1]|nchar [1]|  
|nchar [2..255]|nchar [*]|  
|numeric|numeric|  
|numerico [*..65]|numerico [*] [0]|  
|numerico [*..65][\*..30]|numerico [*] [\*]|  
|nvarchar|nvarchar [1]|  
|nvarchar [0..1]|nvarchar [1]|  
|nvarchar [2..4000]|nvarchar [*]|  
|nvarchar [4001... *]|nvarchar(max)|  
|real|float [53]|  
|reale [*..255][\*..30]|numerico [*] [\*]|  
|Seriale|bigint|  
|smallint|smallint|  
|smallint [*..255]|smallint|  
|text|nvarchar(max)|  
|testo [0..1]|nvarchar [1]|  
|testo [2..4000]|nvarchar [*]|  
|testo [4001... *]|nvarchar(max)|  
|time|time|  
|timestamp|datetime|  
|tinyblob|varbinary [255]|  
|tinyint|smallint|  
|tinyint [*..255]|smallint|  
|tinytext|nvarchar [255]|  
|bigint senza segno|bigint|  
|senza segno bigint [*..255]|bigint|  
|dec senza segno|Decimal|  
|senza segno dec [*..65]|decimale [*] [0]|  
|senza segno dec [*..65][\*..30]|decimale [*] [\*]|  
|senza segno decimale|Decimal|  
|senza segno decimale [*..65]|decimale [*] [0]|  
|senza segno decimale [*..65][\*..30]|decimale [*] [\*]|  
|doppia senza segno|float [53]|  
|senza segno a precisione doppia|float [53]|  
|senza segno a precisione doppia [*..255][\*..30]|numerico [*] [\*]|  
|Unsigned double [*..255][\*..30]|numerico [*] [\*]|  
|Unsigned predefinito|numeric|  
|Unsigned fissa [*..65][\*..30]|numerico [*] [\*]|  
|float senza segno|float [24]|  
|senza segno float [*..255][\*..30]|numerico [*] [\*]|  
|senza segno float [*..53]|float [53]|  
|int senza segno|bigint|  
|int senza segno [*..255]|bigint|  
|intero senza segno|bigint|  
|intero senza segno [*..255]|bigint|  
|mediumint senza segno|int|  
|senza segno mediumint [*..255]|int|  
|numerico senza segno|numeric|  
|numerico senza segno [*..65]|numerico [*] [0]|  
|numerico senza segno [*..65][\*..30]|numerico [*] [\*]|  
|senza segno reale|float [53]|  
|Unsigned reale [*..255[[\*..30]|numerico [*] [\*]|  
|smallint senza segno|int|  
|smallint non firmati [*..255]|int|  
|tinyint senza segno|tinyint|  
|senza segno tinyint [*... 255]|tinyint|  
|varbinary [0..1]|varbinary [1]|  
|varbinary [2..8000]|varbinary [*]|  
|varbinary [8001... *]|varbinary(max)|  
|varchar [0..1]|nvarchar [1]|  
|varchar [2..4000]|nvarchar [*]|  
|varchar [4001... *]|nvarchar(max)|  
|year|smallint|  
|anno [2..2]|smallint|  
|anno [4..4]|smallint|  
  
##### <a name="add"></a>Aggiungi  
Fare clic per aggiungere un tipo di dati nell'elenco di mapping.  
  
##### <a name="edit"></a>Modifica  
Fare clic per modificare un tipo di dati nell'elenco di mapping.  
  
##### <a name="remove"></a>Rimuovi  
Fare clic per rimuovere il mapping dei tipi di dati selezionato dall'elenco di mapping.  
  
##### <a name="reset-to-default"></a>Ripristina predefiniti  
Fare clic per reimpostare tutti i mapping dei tipi di dati di SSMA predefinite.  
  

