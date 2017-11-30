---
title: Sys.fn_all_changes_&lt;capture_instance&gt; (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 06/02/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server (starting with 2008)
f1_keywords:
- fn_all_changes
- sys.fn_all_changes
- fn_all_changes_TSQL
- sys.fn_all_changes_TSQL
dev_langs: TSQL
helpviewer_keywords:
- fn_all_changes_<capture_instance>
- sys.fn_all_changes_<capture_instance>
ms.assetid: 564fae96-b88c-4f22-9338-26ec168ba6f5
caps.latest.revision: "15"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 29f9560f7308fef45468c7ce67a6f8a15e120a3b
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/27/2017
---
# <a name="sysfnallchangesltcaptureinstancegt-transact-sql"></a>Sys.fn_all_changes_&lt;capture_instance&gt; (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Wrapper per il **tutte le modifiche** funzioni di query. Gli script necessari per creare queste funzioni vengono generati dalla stored procedure sys.sp_cdc_generate_wrapper_function.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
fn_all_changes_<capture_instance> ('start_time' ,'end_time', '<row_filter_option>' )  
  
<capture_instance> ::= The name of the capture instance.  
<row_filter_option> ::=  
{ all  
  | all update old  
}  
```  
  
## <a name="arguments"></a>Argomenti  
 *start_time*  
 Il **datetime** valore che rappresenta l'endpoint inferiore dell'intervallo di modifica delle voci della tabella da includere nel set di risultati.  
  
 Solo le righe in cdc. < capture_instance > _CT modifiche di tabella che dispone di un'ora di commit associata maggiore di *start_time* sono inclusi nel set di risultati.  
  
 Se viene fornito un valore NULL per questo argomento, l'endpoint inferiore dell'intervallo della query corrisponderà all'endpoint inferiore dell'intervallo valido per l'istanza di acquisizione.  
  
 *end_time*  
 Il **datetime** valore che rappresenta l'endpoint superiore dell'intervallo di modifica delle voci della tabella da includere nel set di risultati.  
  
 Questo parametro può assumere uno dei due possibili significati a seconda del valore scelto per @closed_high_end_point quando Sys. sp_cdc_generate_wrapper_function viene chiamato per generare lo script di creazione per la funzione wrapper:  
  
-   @closed_high_end_point = 1  
  
     Solo le righe della tabella delle modifiche cdc.<capture_instance>_CT con un'ora di commit associata minore o uguale a end_time vengono incluse nel set di risultati.  
  
-   @closed_high_end_point = 0  
  
     Solo le righe della tabella delle modifiche cdc.capture_instance_CT con un'ora di commit associata minore di end_time vengono incluse nel set di risultati.  
  
 Se viene fornito un valore NULL per questo argomento, l'endpoint superiore dell'intervallo della query corrisponderà all'endpoint superiore dell'intervallo valido per l'istanza di acquisizione.  
  
 <row_filter_option> ::= { all | all update old }  
 Opzione applicata al contenuto delle colonne dei metadati e alle righe restituite nel set di risultati.  
  
 Le opzioni possibili sono le seguenti:  
  
 all  
 Restituisce tutte le modifiche all'interno dell'intervallo LSN specificato. Per le modifiche dovute a un'operazione di aggiornamento, questa opzione restituisce solo la riga che contiene i nuovi valori dopo l'applicazione dell'aggiornamento.  
  
 all update old  
 Restituisce tutte le modifiche all'interno dell'intervallo LSN specificato. Per le modifiche dovute a un'operazione di aggiornamento, questa opzione restituisce le due righe che contengono i valori della colonna prima e dopo l'aggiornamento.  
  
## <a name="table-returned"></a>Tabella restituita  
  
|Nome colonna|Tipo di colonna|Description|  
|-----------------|-----------------|-----------------|  
|__CDC_STARTLSN|**binary(10)**|Valore LSN di commit per la transazione associata alla modifica. Tutte le modifiche di cui è stato eseguito il commit nella stessa transazione condividono lo stesso valore LSN di commit.|  
|__CDC_SEQVAL|**binary(10)**|Valore di sequenza utilizzato per ordinare le modifiche alle righe in una transazione.|  
|\<le colonne di @column_list>|**varia**|Le colonne identificate nel *column_list* argomento sp_cdc_generate_wrapper_function funzione quando viene chiamato per generare lo script che crea la funzione wrapper.|  
|__CDC_OPERATION|**nvarchar(2)**|Codice operativo che indica l'operazione necessaria per applicare la riga all'ambiente di destinazione. Può variare in base al valore dell'argomento *row_filter_option* fornito nella chiamata:<br /><br /> *row_filter_option* = "all"<br /><br /> 'D' - operazione di eliminazione<br /><br /> 'I' - operazione di inserimento<br /><br /> 'UN' - operazione di aggiornamento ai nuovi valori<br /><br /> *row_filter_option* = 'all update old'<br /><br /> 'D' - operazione di eliminazione<br /><br /> 'I' - operazione di inserimento<br /><br /> 'UN' - operazione di aggiornamento ai nuovi valori<br /><br /> 'UO' - operazione di aggiornamento ai valori obsoleti|  
|\<le colonne di @update_flag_list>|**bit**|Un flag di bit viene denominato aggiungendo _uflag al nome della colonna. Il flag è sempre impostato su NULL quando \__CDC_OPERATION è ', 'I',' O 'UO'. Quando \__CDC_OPERATION è ' un' ', è impostato su 1 se l'aggiornamento ha apportato una modifica alla colonna corrispondente. Altrimenti, è impostato su 0.|  
  
## <a name="remarks"></a>Osservazioni  
 La funzione fn_all_changes_<capture_instance> viene utilizzata come wrapper per la funzione di query cdc.fn_cdc_get_all_changes_<capture_instance>. La stored procedure sys.sp_cdc_generate_wrapper viene utilizzata per generare lo script di creazione del wrapper.  
  
 Le funzioni wrapper non vengono create automaticamente. Per creare le funzioni wrapper, è necessario eseguire due operazioni:  
  
1.  Eseguire la stored procedure per generare lo script di creazione del wrapper.  
  
2.  Eseguire lo script per creare effettivamente la funzione wrapper.  
  
 Le funzioni wrapper consentono agli utenti di eseguire sistematicamente query per le modifiche che si sono verificati all'interno di un intervallo limitato dai **datetime** anziché i valori da valori LSN. Le funzioni wrapper eseguono tutte le conversioni necessarie tra forniti **datetime** valori e i valori LSN necessari internamente come argomenti alle funzioni di query. Quando le funzioni wrapper vengono utilizzate in sequenza per elaborare un flusso di dati delle modifiche, garantiscono che nessun dato persi o ripetuto purché venga rispettata la convenzione seguente: il @end_time valore dell'intervallo di cui è associata a una chiamata viene fornito come il @start_time valore per l'intervallo associato alla chiamata successiva.  
  
 Utilizzando il parametro @closed_high_end_point durante la creazione dello script, è possibile generare wrapper per supportare un limite superiore chiuso o un limite superiore aperto nella finestra della query specificata, ovvero è possibile decidere se le voci che dispongono di un'ora di commit uguale al limite superiore dell'intervallo di estrazione devono essere incluse nell'intervallo. Per impostazione predefinita, il limite superiore è incluso.  
  
 Il set di risultati restituito dal **tutte le modifiche** funzione wrapper restituisce _ $start_lsn e \_ \_$seqval colonne della tabella delle modifiche come colonne \__CDC_STARTLSN e \__ CDC_SEQVAL, rispettivamente. Tali con solo dalle colonne rilevate che venivano visualizzate nel  *@column_list*  parametro quando il wrapper è stato generato. Se  *@column_list*  è NULL, tutto il codice sorgente rilevate vengono restituite le colonne. Le colonne di origine sono seguite da una colonna dell'operazione, \__CDC_OPERATION, ovvero una colonna di uno o due caratteri che identifica l'operazione.  
  
 I flag di bit vengono quindi aggiunti al set di risultati per ogni colonna identificata nel parametro @update_flag_list. Per il **tutte le modifiche** wrapper, i flag di bit saranno sempre NULL se cdc_operation è ', 'I' o 'UO'. Se \__CDC_OPERATION è ' un' ', il flag verrà impostato su 1 o 0, a seconda se l'operazione di aggiornamento ha causato una modifica alla colonna.  
  
 Il modello di configurazione di Change Data Capture 'Instantiate CDC Wrapper TVFs for Schema' mostra come utilizzare la stored procedure sp_cdc_generate_wrapper_function per ottenere gli script CREATE per tutte le funzioni wrapper per le funzioni di query definite di uno schema. Il modello crea quindi tali script. Per ulteriori informazioni sui modelli, vedere [Esplora modelli](http://msdn.microsoft.com/library/b9ee55c5-bb44-4f76-90ac-792d8d83b4c8).  
  
## <a name="see-also"></a>Vedere anche  
 [Sys. sp_cdc_generate_wrapper_function &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-generate-wrapper-function-transact-sql.md)   
 [CDC. fn_cdc_get_all_changes_ &#60; capture_instance &#62;  &#40; Transact-SQL &#41;](../../relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql.md)  
  
  
