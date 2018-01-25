---
title: RESTORE REWINDONLY (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- RESTORE_REWINDONLY_TSQL
- RESTORE REWINDONLY
dev_langs: TSQL
helpviewer_keywords:
- closing backup devices
- backup devices [SQL Server], rewinding
- media [SQL Server]
- open back devices
- rewinding backup devices
- RESTORE REWINDONLY statement
ms.assetid: 7f825b40-2264-4608-9809-590d0f09d882
caps.latest.revision: "50"
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: bf67d54e58f08296878c0781158e7b878b0b2a49
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="restore-statements---rewindonly-transact-sql"></a>Istruzioni - RESTORE REWINDONLY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Riavvolge e chiude i dispositivi nastro specificati lasciati aperti dalle istruzioni BACKUP o RESTORE eseguite con l'opzione NOREWIND. Questo comando è supportato solo per i dispositivi nastro.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
RESTORE REWINDONLY   
FROM <backup_device> [ ,...n ]  
[ WITH {UNLOAD | NOUNLOAD}]  
}   
[;]  
  
<backup_device> ::=  
{   
   { logical_backup_device_name |  
      @logical_backup_device_name_var }  
   | TAPE = { 'physical_backup_device_name' |  
       @physical_backup_device_name_var }   
}   
```  
  
## <a name="arguments"></a>Argomenti  
 **\<backup_device> ::=** 
  
 Specifica i dispositivi di backup logici o fisici da utilizzare per il ripristino.  
  
 { *logical_backup_device_name* | **@ * * * logical_backup_device_name_var* } è il nome logico, conforme alle regole per gli identificatori, i dispositivi di backup creato da **sp_addumpdevice** da cui viene ripristinato il database. Se specificato come variabile (**@***logical_backup_device_name_var*), il nome di dispositivo di backup può essere specificato come costante stringa (**@ * * * logical_backup_device_name_var*  =   *logical_backup_device_name*) o come una variabile di tipo carattere, ad eccezione di **ntext** o **testo** tipi di dati.  
  
 {DISCO | NASTRO}  **=**  { **'***nome_dispositivo_backup_fisico***'** | **@ * * * physical_backup_device_name_var*  } Consente il backup da ripristinare dal dispositivo disco o nastro denominato. I tipi di dispositivo del disco e nastro devono essere specificati con il nome effettivo (ad esempio, percorso e il nome completo) del dispositivo: disco = 'C:\Program Files\Microsoft SQL Server\MSSQL\BACKUP\Mybackup.bak' or TAPE = '\\\\. \TAPE0'. Se specificato come variabile (**@***physical_backup_device_name_var*), il nome del dispositivo può essere specificato come costante stringa (**@ * * * physical_backup_device_name_var* = '* physical_backup_device_name *') o come una variabile di tipo carattere, ad eccezione di **ntext** o **testo** tipi di dati.  
  
 Se si utilizza un server di rete avente un nome UNC (che deve contenere il nome del server), specificare un dispositivo disco. Per ulteriori informazioni sull'utilizzo dei nomi UNC, vedere [dispositivi di Backup &#40; SQL Server &#41; ](../../relational-databases/backup-restore/backup-devices-sql-server.md).  
  
 L'account con cui si esegue Microsoft SQL Server deve avere accesso in lettura al computer remoto o al server di rete per eseguire un'operazione di ripristino.  
  
 *n*  
 Segnaposto che indica la possibilità di specificare più dispositivi di backup e logici. Il numero massimo di dispositivi di backup o di dispositivi di backup logici è **64**.  
  
 Una sequenza di ripristino può richiedere altrettanti dispositivi di backup quanti ne sono stati utilizzati per creare il set di supporti al quale appartengono i backup, a seconda che il ripristino sia online o offline. Il ripristino offline consente il ripristino di un backup utilizzando un numero minore di dispositivi di backup rispetto a quelli utilizzati per creare il backup. Il ripristino online richiede tutti i dispositivi di backup del backup. Non è possibile eseguire il ripristino con un numero inferiore di dispositivi.  
  
 Per altre informazioni, vedere [Dispositivi di backup &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-devices-sql-server.md).  
  
> [!NOTE]  
>  Durante il ripristino di un backup da un set di supporti con mirroring, è possibile specificare solo un mirror singolo per ogni gruppo di supporti. In caso di errori, tuttavia, la presenza di altri mirror, consente una risoluzione rapida di alcuni problemi di ripristino. È possibile sostituire un volume di un supporto danneggiato con il volume corrispondente da un altro mirror. Si noti che per i ripristini offline è possibile ripristinare da un numero inferiore di dispositivi rispetto a un gruppo di dispositivi, ma ogni gruppo viene elaborato soltanto una volta.  
  
 **CON le opzioni**  
  
 UNLOAD  
 Specifica che il nastro viene riavvolto ed espulso automaticamente al termine dell'operazione RESTORE. Per impostazione predefinita l'opzione UNLOAD viene impostata all'avvio di una nuova sessione utente e rimane attiva fino a quando non si specifica NOUNLOAD. Viene utilizzata solo per i dispositivi nastro. Se per l'operazione RESTORE non viene utilizzata un dispositivo nastro, questa opzione viene ignorata.  
  
 NOUNLOAD  
 Specifica che il nastro non viene scaricato automaticamente dall'unità dopo un'operazione RESTORE. L'opzione NOUNLOAD rimane attiva fino a quando non si specifica UNLOAD.  
  
 Specifica che il nastro non viene scaricato automaticamente dall'unità dopo un'operazione RESTORE. L'opzione NOUNLOAD rimane attiva fino a quando non si specifica UNLOAD.  
  
## <a name="general-remarks"></a>Osservazioni generali  
 RESTORE REWINDONLY è un'alternativa a RESTORE LABELONLY FROM TAPE = \<name > WITH REWIND. È possibile ottenere un elenco di unità nastro aperte dal [Sys.dm io_backup_tapes](../../relational-databases/system-dynamic-management-views/sys-dm-io-backup-tapes-transact-sql.md) vista a gestione dinamica.  
  
## <a name="security"></a>Sicurezza  
  
### <a name="permissions"></a>Autorizzazioni  
 Qualsiasi utente può utilizzare RESTORE REWINDONLY.  
  
## <a name="see-also"></a>Vedere anche  
 [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md)   
 [Set di supporti, gruppi di supporti e set di backup &#40;SQL Server&#41;](../../relational-databases/backup-restore/media-sets-media-families-and-backup-sets-sql-server.md)   
 [RESTORE &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-transact-sql.md)   
 [Informazioni sulla cronologia e sull'intestazione del backup &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-history-and-header-information-sql-server.md)  
  
  

