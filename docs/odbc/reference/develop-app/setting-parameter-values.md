---
title: Impostazione dei valori di parametro | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: parameter values [ODBC]
ms.assetid: 13e5da79-b60c-48d0-b467-773f481ef2a4
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c89f68450a7d4ffe65f5d7bc0e8697b5ac2cb1b1
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="setting-parameter-values"></a>Impostazione dei valori di parametro
Per impostare il valore di un parametro, l'applicazione imposta semplicemente il valore della variabile associata al parametro. Non è importante quando questo valore è impostato, fino a quando è impostato prima dell'esecuzione dell'istruzione. L'applicazione può impostare il valore prima o dopo l'associazione della variabile e può cambiare il valore come tutte le volte che desidera. Quando viene eseguita l'istruzione, il driver recupera semplicemente il valore corrente della variabile. Questo è particolarmente utile quando un'istruzione preparata viene eseguita più volte. l'applicazione imposta nuovi valori per alcune o tutte le variabili ogni volta che viene eseguita l'istruzione. Per un esempio, vedere [esecuzione preparata](../../../odbc/reference/develop-app/prepared-execution-odbc.md), più indietro in questa sezione.  
  
 Se è stato associato un buffer di lunghezza/indicatore nella chiamata a **SQLBindParameter**, deve essere impostata su uno dei seguenti valori prima dell'esecuzione dell'istruzione:  
  
-   La lunghezza in byte dei dati nella variabile associata. Il driver controlla questa lunghezza solo se la variabile è di tipo carattere o binario (*ValueType* è SQL_C_CHAR o SQL_C_BINARY).  
  
-   SQL_NTS. I dati sono una stringa con terminazione null.  
  
-   SQL_NULL_DATA. Il valore di dati è NULL e il driver ignora il valore della variabile associata.  
  
-   Il risultato della macro SQL_LEN_DATA_AT_EXEC o SQL_DATA_AT_EXEC. Il valore del parametro è venga inviato con **SQLPutData**. Per ulteriori informazioni, vedere [l'invio di dati Long](../../../odbc/reference/develop-app/sending-long-data.md), più avanti in questa sezione.  
  
 Nella tabella seguente vengono illustrati i valori di variabile associata e il buffer di lunghezza/indicatore che consente di impostare l'applicazione per un'ampia gamma di valori di parametro.  
  
|Parametro<br /><br /> Valore|Parametro<br /><br /> (SQL)<br /><br /> Tipo di dati|Variable (C)<br /><br /> Tipo di dati|Valore in<br /><br /> Associato<br /><br /> variabile|Valore in<br /><br /> lunghezza/indicatore<br /><br /> buffer [d]|  
|-------------------------|-----------------------------------------|----------------------------------|-------------------------------------|----------------------------------------------------|  
|"ABC"|SQL_CHAR|SQL_C_CHAR|ABC\0 [a]|SQL_NTS o 3|  
|10|SQL_INTEGER|SQL_C_SLONG|10|--|  
|10|SQL_INTEGER|SQL_C_CHAR|[a] 10 \ 0|SQL_NTS o 2|  
|ORE 13.00|SQL_TYPE_TIME|SQL_C_TYPE_TIME|13,0,0 [b]|--|  
|ORE 13.00|SQL_TYPE_TIME|SQL_C_CHAR|{t ' 13: 00:00'} \0 [a] e [c]|SQL_NTS o 14|  
|NULL|SQL_SMALLINT|SQL_C_SSHORT|--|SQL_NULL_DATA|  
  
 [a] "\0" rappresenta un carattere di terminazione null. Il carattere di terminazione null è necessario solo se il valore nel buffer di lunghezza/indicatore è SQL_NTS.  
  
 [b] i numeri in questo elenco sono i numeri memorizzati nei campi della struttura TIME_STRUCT.  
  
 [c] la stringa viene utilizzata la clausola di escape ODBC Data. Per ulteriori informazioni, vedere [Date, Time e Timestamp letterali](../../../odbc/reference/develop-app/date-time-and-timestamp-literals.md).  
  
 [d] driver sempre deve controllare questo valore per verificare se è un valore speciale, ad esempio SQL_NULL_DATA.  
  
 Funzionamento di un driver con un valore di parametro in fase di esecuzione è dipendente dal driver. Se necessario, il driver converte il valore dalla C byte e tipo lunghezza dei dati della variabile di associazione per il tipo di dati SQL, precisione e scala del parametro. Nella maggior parte dei casi, il driver invia quindi il valore per l'origine dati. In alcuni casi, formatta il valore come testo e lo inserisce nell'istruzione SQL prima di inviare l'istruzione per l'origine dati.
