---
title: Appendice - 1 (DB2ToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: c6a30367-d56f-4fcc-8920-c6a6b0335a67
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 8450ffcccf0daafbadd80e095873971a30c43029
ms.sourcegitcommit: 9f2edcdf958e6afce9a09fb2e572ae36dfe9edb0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/25/2018
ms.locfileid: "50098791"
---
# <a name="appendix---1-db2tosql"></a>Appendice - 1 (DB2ToSQL)
Panoramica della Console SSMA opzioni riga di comando:  
  
|Sl. No.|Opzione|Obbligatorio?|Argomento parametro|Valori consentiti|  
|-----------|----------|-------------|-------------------|--------------------|  
|1|-s o script|Sì|scriptfile|Nome file XML valido.<br /><br />File di definizione di Script della console.|  
|2|variabile o - v|no|variablevaluefile|Nome file XML valido.<br /><br />Se vengono usate nel file di script, è necessario specificare questo file.|  
|3|-c/serverconnection|no|serverconnectionfile|Nome file XML valido.<br /><br />Questo file contiene informazioni di connessione server.|  
|4|-x/xmloutput|no|xmloutputfile|Questa opzione indica l'output di console in formato XML. Se questa opzione non è specificata, l'output predefinito è in formato testo.<br /><br />Se non viene specificato xmloutputfile, output XML viene indirizzato a STDOUT.<br /><br />Xmloutputfile è il nome del file in cui viene scritto l'output della console in formato XML.|  
|5|-l/log|no|logfile|Nome file valido.|  
|6|-e/projectenvironment|no|projectenvironmentfolder|Nome di cartella valido che contiene file dell'ambiente di progetto SSMA.|  
|7|-p/securepassword|no|-un/aggiungere {< server_id > [,... n] &#124; tutti i} – c&#124;serverconnection < server-connection-file > [-v&#124;variabile < variabile-valore-file >] [-o/sovrascriverà]<br /><br />o Gestione configurazione<br /><br />-un/aggiungere {< server_id > [,... n] &#124; tutti i} – s&#124;script < file di script > [-v&#124;variabile < variabile-valore-file >] [-o/sovrascriverà]<br /><br />– r/Rimuovi {< server_id > [,... n] &#124; tutti}<br /><br />-l/list<br /><br />– e/esportazione {< server-id > [,... n] &#124; tutti i} < crittografati-password - file ><br /><br />-i / Importa {< server-id > [,... n] &#124; tutti i} < crittografati-password-file >|Se specificato, questa opzione non deve essere eseguita con qualsiasi altra opzione.<br /><br />id server: specificato un ID univoco per un server {string}<br /><br />file di connessione server: file di definizione del server (serverconnectionfile o scriptfile).<br /><br />variabile-file-value: è un file di definizione di variabile e usato nel file di connessione server.<br /><br />: file di password crittografato: è un file server di password crittografato con una specificata dall'utente-passphrase.|  
|8|-?|no|Non applicabile|Non applicabile|  
  
## <a name="see-also"></a>Vedere anche  
[Esecuzione della console SSMA](http://msdn.microsoft.com/ce63f633-067d-4f04-b8e9-e1abd7ec740b)  
  
