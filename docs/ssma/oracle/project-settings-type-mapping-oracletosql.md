---
title: Impostazioni (Mapping dei tipi) del progetto (OracleToSQL) | Documenti Microsoft
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssma-oracle
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 4bb8466e-2199-4f00-8513-b04e9586723d
caps.latest.revision: 8
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: 18d49c123b42a41db33fd6eb37f580eba34f786e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="project-settings-type-mapping-oracletosql"></a>Impostazioni (Mapping dei tipi) del progetto (OracleToSQL)
La pagina Mapping dei tipi del **impostazioni progetto** la finestra di dialogo contiene le impostazioni che consentono di personalizzare la modalità SSMA converte i tipi di dati Oracle in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] tipi di dati.  
  
La pagina Mapping dei tipi è disponibile nel **impostazioni progetto** e **impostazioni di progetto predefinite** finestre di dialogo.  
  
-   Per specificare impostazioni per tutti i progetti futuri di SSMA, il **strumenti** dal menu **impostazioni di progetto predefinite**, selezionare il tipo di progetto di migrazione per i quali impostazioni sono necessarie per essere visualizzati o modificati da **versione di destinazione della migrazione** elenco a discesa e quindi fare clic su **del mapping dei tipi** nella parte inferiore del riquadro a sinistra.  
  
-   Per specificare le impostazioni per il progetto corrente, il **strumenti** dal menu **impostazioni progetto**e quindi fare clic su **del mapping dei tipi** nella parte inferiore del riquadro a sinistra.  
  
Per specificare le impostazioni per l'oggetto corrente o di una classe di oggetti, usare il **del mapping dei tipi** scheda nella finestra di SSMA primaria.  
  
## <a name="options"></a>Opzioni  
La tabella seguente mostra il **del mapping dei tipi** scheda Opzioni:  
  
**Tipo origine**  
Il tipo di dati Oracle mappato.  
  
**Tipo di destinazione**  
La destinazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] il tipo di dati per il tipo di dati Oracle specificato.  
  
Vedere le tabelle nella sezione successiva per il valore predefinito SSMA per i mapping dei tipi di Oracle.  
  
**Aggiungi**  
Fare clic per aggiungere un tipo di dati nell'elenco di mapping.  
  
**Modifica**  
Fare clic per modificare il tipo di dati selezionato nell'elenco di mapping.  
  
**Rimuovi**  
Fare clic per rimuovere il mapping dei tipi di dati selezionato dall'elenco di mapping.  
  
**Ripristina predefiniti**  
Fare clic per reimpostare l'elenco di mapping del tipo di SSMA predefinite.  
  
## <a name="default-type-mappings"></a>Mapping dei tipi predefiniti  
In SSMA per Oracle, è possibile impostare i mapping dei tipi personalizzato per gli argomenti, colonne, variabili locali e i valori restituiti. Il mapping predefinito per gli argomenti e i tipi restituiti è pressoché identico.  
  
### <a name="default-argument-type-and-return-value-type-mapping"></a>Tipo di argomento predefinito e restituisce i Mapping dei tipi di valore  
Nella tabella seguente contiene il mapping dei tipi di dati predefinito per gli argomenti e valori restituiti.  
  
|Tipo di dati Oracle|Predefinito [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] tipo di dati|  
|--------------------|-------------------------------------------------------------------------|  
|BFILE|varbinary(max)|  
|binary_double|float [53]|  
|binary_float|float [53]|  
|binary_integer|int|  
|blob|varbinary(max)|  
|boolean|bit|  
|char|ntext|  
|char varying|ntext|  
|character|ntext|  
|character varying|ntext|  
|Oggetto CLOB|ntext|  
|data|datetime2 [0]|  
|dec|DEC [38] [0]|  
|Decimal|float [53]|  
|valore a precisione doppia|float [53]|  
|float|float [53]|  
|int|int|  
|integer|int|  
|long|ntext|  
|long raw|varbinary(max)|  
|long raw [\*... 8000]<sup>*</sup>|varbinary [*]|  
|long raw [8001...\*]<sup>*</sup>|varbinary(max)|  
|char nazionali|nvarchar(max)|  
|char National variabile|nvarchar(max)|  
|caratteri nazionali|nvarchar(max)|  
|variabile di caratteri nazionali<sup>**</sup>|nvarchar(max)|  
|variabile di caratteri nazionali<sup>*</sup>|nvarchar(max)|  
|NCHAR|nvarchar(max)|  
|NCLOB|nvarchar(max)|  
|number|float [53]|  
|numeric|float [53]|  
|NVARCHAR2|nvarchar(max)|  
|pls_integer|int|  
|raw|varbinary(max)|  
|real|float [53]|  
|ROWID|uniqueidentifier|  
|Signtype|smallint|  
|smallint|smallint|  
|string|ntext|  
|TIMESTAMP|datetime2|  
|timestamp con fuso orario locale|datetimeoffset|  
|timestamp con fuso orario|datetimeoffset|  
|UROWID|uniqueidentifier|  
|varchar|ntext|  
|VARCHAR2|ntext|  
|XmlType|xml|  
  
<sup>*</sup> Si applica per restituire i mapping solo di valori tipo.  
  
<sup>**</sup> Si applica ai mapping solo di argomento tipo.  
  
### <a name="default-column-type-mapping"></a>Mapping dei tipi di colonna predefinito  
Nella tabella seguente contiene il mapping dei tipi predefiniti per le colonne.  
  
|Tipo di dati Oracle|Predefinito [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] tipo di dati|  
|--------------------|-------------------------------------------------------------------------|  
|BFILE|varbinary(max)|  
|binary_double|float [53]|  
|binary_float|float [53]|  
|blob|varbinary(max)|  
|char|char|  
|variabile Char [*... \*]|varchar [*]|  
|Char [*... \*]|Char [*]|  
|character|char|  
|variabile di tipo carattere [*... \*]|varchar [*]|  
|caratteri [*... \*]|Char [*]|  
|Oggetto CLOB|ntext|  
|data|datetime2 [0]|  
|dec|DEC [38] [0]|  
|DEC [*... \*]|dec[*][0]|  
|DEC [*... \*][\*.. \*]|dec[*][\*]|  
|Decimal|decimal[38][0]|  
|decimale [*... \*]|decimal[*][0]|  
|decimal[*..\*][\*..\*]|decimal[*][\*]|  
|valore a precisione doppia|float [53]|  
|float|float [53]|  
|float [*... 53]|float [*]|  
|float [54... *]|float [53]|  
|int|int|  
|integer|int|  
|long|ntext|  
|long raw|varbinary(max)|  
|long raw [*... 8000]|varbinary [*]|  
|long raw [8001... *]|varbinary(max)|  
|Long varchar|ntext|  
|long[*..8000]|varchar [*]|  
|long[8001..*]|ntext|  
|char nazionali|NCHAR|  
|char National varying [*... \*]|nvarchar [*]|  
|National char [*... \*]|nchar [*]|  
|caratteri nazionali|NCHAR|  
|variabile di caratteri nazionale [*... \*]|nvarchar [*]|  
|caratteri nazionali [*... \*]|nchar [*]|  
|NCHAR|NCHAR|  
|nchar [*]|nchar [*]|  
|NCLOB|nvarchar(max)|  
|number|float [53]|  
|numero [*... \*]|numerico [*]|  
|numero [*... \*][\*.. \*]|numerico [*] [\*]|  
|numeric|numeric|  
|numerico [*... \*]|numerico [*]|  
|numerico [*... \*][\*.. \*]|numerico [*] [\*]|  
|NVARCHAR2 [*... \*]|nvarchar [*]|  
|raw[*..\*]|varbinary [*]|  
|real|float [53]|  
|ROWID|uniqueidentifier|  
|smallint|smallint|  
|TIMESTAMP|datetime2|  
|timestamp con fuso orario locale|datetimeoffset|  
|timestamp con fuso orario locale [*... \*]|DateTimeOffset [*]|  
|timestamp con fuso orario|datetimeoffset|  
|timestamp con fuso orario [*... \*]|DateTimeOffset [*]|  
|timestamp [*... \*]|datetime2 [*]|  
|UROWID|uniqueidentifier|  
|UROWID [*... \*]|uniqueidentifier|  
|varchar [*... \*]|varchar [*]|  
|VARCHAR2 [*... \*]|varchar [*]|  
|XmlType|xml|  
  
### <a name="default-local-variable-type-mapping"></a>Mapping dei tipi di variabile locale predefinito  
Nella tabella seguente contiene il mapping dei tipi predefiniti per le variabili locali.  
  
|Tipo di dati Oracle|Predefinito [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] tipo di dati|  
|--------------------|-------------------------------------------------------------------------|  
|BFILE|varbinary(max)|  
|binary_double|float [53]|  
|binary_float|float [53]|  
|binary_interger|int|  
|BLOB|varbinary(max)|  
|Boolean|bit|  
|Char|char|  
|variabile Char [*... 8000]|varchar [*]|  
|variabile Char [8001... *]|ntext|  
|Char [*... 8000]|Char [*]|  
|Char [8001... *]|ntext|  
|Carattere|char|  
|variabile di tipo carattere [*... 8000]|varchar [*]|  
|variabile di tipo carattere [8001... *]|ntext|  
|caratteri [*... 8000]|Char [*]|  
|caratteri [8001... *]|ntext|  
|Oggetto CLOB|ntext|  
|data|datetime2 [0]|  
|dec|DEC [38] [0]|  
|DEC [*... \*]|dec[*][0]|  
|DEC [*... \*][\*.. \*]|dec[*][\*]|  
|Decimal|decimal[38][0]|  
|decimale [*... \*]|decimal[*][0]|  
|decimal[*..\*][\*..\*]|decimal[*][\*]|  
|valore a precisione doppia|float [53]|  
|Float|float [53]|  
|float [*... 53]|float [*]|  
|float [54... *]|float [53]|  
|Int|int|  
|Integer|int|  
|numero intero [*... \*]|numerico [*] [0]|  
|Long|ntext|  
|long raw|varbinary(max)|  
|long raw [*... 8000]|varbinary [*]|  
|long raw [8001... *]|varbinary(max)|  
|char nazionali|NCHAR|  
|char National varying [*... 4000]|nvarchar [*]|  
|char National varying [4001... *]|nvarchar(max)|  
|National char [*... 4000]|nchar [*]|  
|National char [4001... *]|nvarchar(max)|  
|caratteri nazionali|NCHAR|  
|caratteri nazionali [*... 4000]|nvarchar [*]|  
|caratteri nazionali [4001... *]|nvarchar(max)|  
|variabile di caratteri nazionale [*... 4000]|nvarchar [*]|  
|variabile di caratteri nazionale [4001... *]|nvarchar(max)|  
|Nchar|NCHAR|  
|nchar [*... 4000]|nchar [*]|  
|nchar [4001... *]|nvarchar(max)|  
|nchar varying [*... 4000]|nvarchar [*]|  
|nchar varying [4001... *]|nvarchar(max)|  
|NCLOB|nvarchar(max)|  
|Number|float [53]|  
|numero [*... \*]|numerico [*]|  
|numero [*... \*][\*.. \*]|numerico [*] [\*]|  
|Numeric|numerico [38] [0]|  
|numerico [*... \*]|numerico [*]|  
|numerico [*... \*][\*.. \*]|numerico [*] [\*]|  
|nvarchar2[*..4000]|nvarchar [*]|  
|nvarchar2[4001..*]|nvarchar(max)|  
|pls_integer|int|  
|raw[*..8000]|varbinary [*]|  
|raw[8001..*]|varbinary(max)|  
|Real|float [53]|  
|ROWID|uniqueidentifier|  
|Signtype|smallint|  
|Smallint|smallint|  
|string[*..8000]|varchar [*]|  
|string[8001..*]|ntext|  
|TIMESTAMP|datetime2|  
|timestamp con fuso orario locale|datetimeoffset|  
|timestamp con fuso orario|datetimeoffset|  
|timestamp con fuso orario locale [*... \*]|DateTimeOffset [*]|  
|timestamp con fuso orario [*... \*]|DateTimeOffset [*]|  
|timestamp [*... \*]|datetime2 [*]|  
|UROWID|uniqueidentifier|  
|UROWID [*... \*]|uniqueidentifier|  
|varchar [*... 8000]|varchar [*]|  
|varchar [8001... *]|ntext|  
|VARCHAR2 [*... 8000]|varchar [*]|  
|VARCHAR2 [8001... *]|varcha(max)|  
|XmlType|xml|  
  
## <a name="see-also"></a>Vedere anche  
[Riferimento all'interfaccia utente &#40;OracleToSQL&#41;](../../ssma/oracle/user-interface-reference-oracletosql.md)  
  
