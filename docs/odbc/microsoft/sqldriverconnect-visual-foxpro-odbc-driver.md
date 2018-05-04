---
title: SQLDriverConnect (Driver ODBC di Visual FoxPro) | Documenti Microsoft
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
- SQLDriverConnect function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 10492c8f-3a18-4971-9db8-879e878083b9
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d1aedce0d1e2888a4aada3a92cf0eb5973d489a5
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sqldriverconnect-visual-foxpro-odbc-driver"></a>SQLDriverConnect (Driver ODBC di Visual FoxPro)
> [!NOTE]  
>  In questo argomento contiene informazioni specifiche del Driver ODBC Visual FoxPro. Per informazioni generali su questa funzione, vedere l'argomento appropriato in [riferimento all'API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Supporto: completo  
  
 Conformità di API ODBC: Livello 1  
  
 Si connette a un'origine dati esistente, che può essere un [database](../../odbc/microsoft/visual-foxpro-terminology.md) o una directory di [libero tabelle](../../odbc/microsoft/visual-foxpro-terminology.md). Le parole chiave attributo ODBC UID e PWD vengono ignorate. La tabella seguente elenca le parole chiave aggiuntive attributo non supportato.  
  
|Parola chiave di attributo ODBC|Valore di attributo|  
|----------------------------|---------------------|  
|DSN||  
|UID|Ignorata dal Driver ODBC Visual FoxPro, ma non genera un errore.|  
|PWD|Ignorata dal Driver ODBC Visual FoxPro, ma non genera un errore.|  
|Driver|Il nome e il percorso del Driver ODBC di Visual FoxPro; implementato da Gestione Driver.|  
  
|Parola chiave di attributo Visual FoxPro ODBC Driver|Valore di attributo|  
|-------------------------------------------------|---------------------|  
|BackgroundFetch|"Yes" o "No"|  
|Fascicola|"Macchina" o altra sequenza di ordinamento. Per un elenco di sequenze di confronto supportate, vedere [SET COLLATE](../../odbc/microsoft/set-collate-command.md).|  
|Description||  
|Exclusive|"Yes" o "No"|  
|SourceDB|Il percorso completo alla directory contenente zero o più [libero tabelle](../../odbc/microsoft/visual-foxpro-terminology.md), o il nome di file e percorso assoluto per un [database](../../odbc/microsoft/visual-foxpro-terminology.md).|  
|SourceType|"DBC" o "DBF"|  
|Versione||  
  
 Se non è stato specificato il nome dell'origine dati, gestione Driver richiesto all'utente le informazioni (a seconda dell'impostazione del *fDriverCompletion* argomento) e continua. Se sono necessarie ulteriori informazioni, il Driver ODBC di Visual FoxPro consente di visualizzare la finestra di dialogo prompt dei comandi.  
  
 Per ulteriori informazioni, vedere [SQLDriverConnect](../../odbc/reference/syntax/sqldriverconnect-function.md) nel *riferimento per programmatori ODBC*.
