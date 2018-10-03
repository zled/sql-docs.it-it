---
title: Impostazioni progetto (Mapping di tipo) (MySQLToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 136fdf6d-657f-447b-af41-49bbc6e0e93e
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: e0a11a0b49589c3763b5af67623c9e819038c217
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47713249"
---
# <a name="project-settings-type-mapping-mysqltosql"></a>Impostazioni del progetto (mapping dei tipi) (MySQLToSQL)
Le impostazioni di progetto del mapping dei tipi consentono di impostare i mapping dei tipi predefiniti per il progetto SSMA.  

Mapping dei tipi è disponibile nelle finestre di dialogo Impostazioni di progetto e le impostazioni di progetto predefinito:  
  
-   Utilizzare la finestra di dialogo Impostazioni di progetto per impostare le opzioni di configurazione per il progetto corrente. Per accedere alle impostazioni di mapping di tipo, nel menu Strumenti, selezionare le impostazioni del progetto e quindi nel riquadro sinistro fare clic su Mapping dei tipi.  
  
-   Utilizzare la finestra di dialogo Impostazioni di progetto predefinito per impostare le opzioni di configurazione per tutti i progetti. Per accedere ai mapping dei tipi di impostazioni, nel menu Strumenti, selezionare impostazioni di progetto predefinite, tipo di progetto di migrazione selezionare per i quali impostazioni sono necessarie per essere visualizzati / modificato da **versione di destinazione della migrazione** elenco a discesa e quindi fare clic sul tipo Mapping nel riquadro sinistro.  
  
## <a name="options"></a>Opzioni  
  
##### <a name="source-type"></a>Tipo origine  
È il tipo di dati di MySQL, che deve essere mappato al tipo di dati database di destinazione.  
  
##### <a name="target-type"></a>Tipo di destinazione  
Tipo di dati del database di destinazione per il tipo di dati MySQL specificato.  
  
##### <a name="add"></a>Aggiungi  
Fare clic per aggiungere un tipo di dati all'elenco di mapping.  
  
##### <a name="edit"></a>Edit  
Fare clic per modificare il tipo di dati selezionato nell'elenco di mapping.  
  
##### <a name="remove"></a>Rimuovi  
Fare clic per rimuovere il mapping dei tipi di dati selezionato dall'elenco di mapping.  
  
##### <a name="reset-to-default"></a>Ripristina predefiniti  
Fare clic per reimpostare l'elenco di mapping di tipo ai valori predefiniti di SSMA.  
  
## <a name="type-mappings"></a>Mapping dei tipi  
La tabella seguente illustra il mapping predefinito tra i tipi di dati di origine e destinazione  
  
|||  
|-|-|  
|**Tipo di dati di MySQL**|**Tipo di dati SQL Server**|  
|BIGINT|BIGINT|  
|bigint [*.. 255]|BIGINT|  
|BINARY|binario [1]|  
|binario [0..1]|binario [1]|  
|binario [2..255]|binario [*]|  
|bit|binario [1]|  
|bit [0..8]|binario [1]|  
|bit[17..24]|binary[3]|  
|bit[25..32]|binary[4]|  
|bit [33..40]|binario [5]|  
|bit [41..48]|binario [6]|  
|bit [49..56]|binario [7]|  
|bit[57..64]|binario [8]|  
|bit [9..16]|binario [2]|  
|blob|varbinary(max)|  
|BLOB [0..1]|varbinary [1]|  
|blob[2..8000]|varbinary [*]|  
|blob[8001..*]|varbinary(max)|  
|bool|bit|  
|boolean|bit|  
|char|nchar [1]|  
|carattere a byte|binario [1]|  
|carattere a byte [0..1]|binario [1]|  
|carattere a byte [2..255]|binario [*]|  
|Char [0..1]|nchar [1]|  
|Char [2..255]|nchar [*]|  
|character|nchar [1]|  
|caratteri diversi [0..1]|nvarchar [1]|  
|caratteri diversi [2..255]|NVARCHAR|  
|caratteri [0..1]|nchar [1]|  
|caratteri [2..255]|nchar [*]|  
|Data|Data|  
|DATETIME|datetime2 [0]|  
|dec|Decimal|  
|DEC [*.. 65]|decimal[*][0]|  
|dec[*..65][\*..30]|decimal[*][\*]|  
|Decimal|Decimal|  
|decimal[*..65]|decimal[*][0]|  
|decimal[*..65][\*..30]|decimal[*][\*]|  
|double|float [53]|  
|valore a precisione doppia|float [53]|  
|valore a precisione doppia [*.. 255] [\*.. 30]|numerico [*] [\*]|  
|double[*..255][\*..30]|numerico [*] [\*]|  
|risolto|NUMERIC|  
|fixed[*..65][\*..30]|numerico [*] [\*]|  
|FLOAT|float [24]|  
|float [*.. 255] [\*.. 30]|numerico [*] [\*]|  
|float [*.. 53]|float [53]|  
|INT|INT|  
|int [*.. 255]|INT|  
|integer|INT|  
|integer[*..255]|INT|  
|longblob|varbinary(max)|  
|LONGTEXT|nvarchar(max)|  
|mediumblob|varbinary(max)|  
|mediumint|INT|  
|mediumint [*.. 255]|INT|  
|mediumtext|nvarchar(max)|  
|National char|nchar [1]|  
|National char [0..1]|nchar [1]|  
|National char [2..255]|nchar [*]|  
|caratteri nazionali|nchar [1]|  
|variabile di caratteri nazionali|nvarchar [1]|  
|variabili [0..1] di caratteri nazionali|nvarchar [1]|  
|variabili [2..4000] di caratteri nazionali|nvarchar [*]|  
|variabile di caratteri nazionali [4001.. *]|nvarchar(max)|  
|caratteri nazionali [0..1]|nchar [1]|  
|caratteri nazionali [2..255]|nchar [*]|  
|varchar nazionali|nvarchar [1]|  
|varchar National [0..1]|nvarchar [1]|  
|varchar National [2..4000]|nvarchar [*]|  
|varchar National [4001.. *]|nvarchar(max)|  
|NCHAR|nchar [1]|  
|nchar varchar|nvarchar [1]|  
|nchar varchar [0..1]|nvarchar [1]|  
|nchar varchar [2..4000]|nvarchar [*]|  
|nchar varchar [4001.. *]|nvarchar(max)|  
|nchar [0..1]|nchar [1]|  
|nchar [2..255]|nchar [*]|  
|NUMERIC|NUMERIC|  
|numerico [*.. 65]|numerico [*] [0]|  
|numerico [*.. 65] [\*.. 30]|numerico [*] [\*]|  
|NVARCHAR|nvarchar [1]|  
|nvarchar [0..1]|nvarchar [1]|  
|nvarchar [2..4000]|nvarchar [*]|  
|nvarchar [4001.. *]|nvarchar(max)|  
|REAL|float [53]|  
|real[*..255][\*..30]|numerico [*] [\*]|  
|seriale|BIGINT|  
|SMALLINT|SMALLINT|  
|smallint [*.. 255]|SMALLINT|  
|text|nvarchar(max)|  
|testo [0..1]|nvarchar [1]|  
|text[2..4000]|nvarchar [*]|  
|testo [4001.. *]|nvarchar(max)|  
|time|time|  
|TIMESTAMP|DATETIME|  
|tinyblob|varbinary[255]|  
|TINYINT|SMALLINT|  
|tinyint[*..255]|SMALLINT|  
|tinytext|nvarchar [255]|  
|bigint senza segno|BIGINT|  
|bigint senza segno [*.. 255]|BIGINT|  
|dec senza segno|Decimal|  
|dec unsigned [*.. 65]|decimal[*][0]|  
|dec unsigned [*.. 65] [\*.. 30]|decimal[*][\*]|  
|numero decimale senza segno|Decimal|  
|numero decimale senza segno [*.. 65]|decimal[*][0]|  
|numero decimale senza segno [*.. 65] [\*.. 30]|decimal[*][\*]|  
|valore double non firmati|float [53]|  
|senza segno a precisione doppia|float [53]|  
|Unsigned a precisione doppia [*.. 255] [\*.. 30]|numerico [*] [\*]|  
|double unsigned [*.. 255] [\*.. 30]|numerico [*] [\*]|  
|Unsigned fisso|NUMERIC|  
|Unsigned fissa [*.. 65] [\*.. 30]|numerico [*] [\*]|  
|float non firmati|float [24]|  
|float non firmati [*.. 255] [\*.. 30]|numerico [*] [\*]|  
|float non firmati [*.. 53]|float [53]|  
|int senza segno|BIGINT|  
|int senza segno [*.. 255]|BIGINT|  
|intero senza segno|BIGINT|  
|intero senza segno [*.. 255]|BIGINT|  
|mediumint senza segno|INT|  
|mediumint unsigned [*.. 255]|INT|  
|numerico senza segno|NUMERIC|  
|numerico senza segno [*.. 65]|numerico [*] [0]|  
|numerico senza segno [*.. 65] [\*.. 30]|numerico [*] [\*]|  
|Unsigned reale|float [53]|  
|Unsigned reale [*.. 255 [[\*.. 30]|numerico [*] [\*]|  
|smallint non firmati|INT|  
|smallint non firmati [*.. 255]|INT|  
|tinyint non firmati|TINYINT|  
|tinyint non firmati [*.. 255]|TINYINT|  
|varbinary [0..1]|varbinary [1]|  
|varbinary [2..8000]|varbinary [*]|  
|varbinary [8001 e.. *]|varbinary(max)|  
|varchar [0..1]|nvarchar [1]|  
|varchar [2..4000]|nvarchar [*]|  
|varchar [4001.. *]|nvarchar(max)|  
|year|SMALLINT|  
|anno [2..2]|SMALLINT|  
|anno [4..4]|SMALLINT|  
  
##### <a name="add"></a>Aggiungi  
Fare clic per aggiungere un tipo di dati all'elenco di mapping.  
  
##### <a name="edit"></a>Edit  
Fare clic per modificare un tipo di dati nell'elenco di mapping.  
  
##### <a name="remove"></a>Rimuovi  
Fare clic per rimuovere il mapping dei tipi di dati selezionato dall'elenco di mapping.  
  
##### <a name="reset-to-default"></a>Ripristina predefiniti  
Fare clic per reimpostare tutti i mapping dei tipi di dati per le impostazioni predefinite SSMA.  
  
