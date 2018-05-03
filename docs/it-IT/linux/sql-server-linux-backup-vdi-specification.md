---
title: Specifica di Backup VDI - SQL Server in Linux | Documenti Microsoft
description: Specifica di interfaccia SQL Server Backup dispositivo virtuale.
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 03/17/2017
ms.topic: article
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.assetid: 0250ba2b-8cdd-450e-9109-bf74f70e1247
ms.openlocfilehash: 39d554e1da11745e1ea21537c7cc6b56ec9e83b7
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sql-server-on-linux-vdi-client-sdk-specification"></a>SQL Server nel client Linux VDI specifica SDK

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Questo documento descrive le interfacce fornite da SQL Server in Linux virtual interface (VDI) client dispositivo SDK. Fornitori di software indipendenti (ISV) è possono utilizzare il Virtual Backup Device interfaccia API (Application Programming) per integrare i prodotti di SQL Server. In generale, un'infrastruttura VDI in Linux è simile alla VDI in Windows con le modifiche seguenti:

- Memoria condivisa di Windows diventa memoria condivisa POSIX.
- I semafori Windows diventano i semafori POSIX.
- Tipi di Windows come HRESULT e DWORD vengono modificati agli equivalenti di integer.
- Le interfacce COM vengono rimosse e sostituite con una coppia di classi C++.
- SQL Server in Linux non supporta le istanze denominate in modo sono stati rimossi i riferimenti al nome di istanza. 
- La libreria condivisa viene implementata in libsqlvdi.so installato in /opt/mssql/lib/libsqlvdi.so

Questo documento è un supplemento a **vbackup.chm** che illustra la specifica di un'infrastruttura VDI di Windows. Scaricare il [specifica VDI Windows](http://www.microsoft.com/download/details.aspx?id=17282).

Esaminare inoltre la soluzione di backup VDI di esempio nella [repository GitHub degli esempi di SQL Server](http://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sqlvdi-linux).

## <a name="user-permissions-setup"></a>Impostazione delle autorizzazioni utente

In Linux, primitive POSIX sono proprietà dell'utente la creazione di loro e il gruppo predefinito. Per gli oggetti creati da SQL Server, questi saranno per impostazione predefinita di proprietà dall'utente mssql e il gruppo mssql. Per consentire la condivisione tra SQL Server e il client VDI, uno dei due metodi seguenti sono consigliate:

1. Eseguire il Client VDI come utente mssql
   
   Eseguire il comando seguente per passare all'utente mssql:
   
   ```bash
   sudo su mssql
   ```

2. Aggiungere l'utente mssql al gruppo del vdiuser e il vdiuser al gruppo mssql.
   
   Eseguire i comandi seguenti:

   ```bash
   sudo useradd vdiuser
   sudo usermod -a -G mssql vdiuser
   sudo usermod -a -G vdiuser mssql
   ```

   Riavviare il server di rilevare i nuovi gruppi per SQL Server e vdiuser

## <a name="client-functions"></a>Funzioni client

In questo capitolo contiene le descrizioni di tutte le funzioni di client. Le descrizioni sono le seguenti informazioni:

- Scopo della funzione
- Sintassi della funzione
- Elenco di parametri
- Valori restituiti
- Osservazioni

## <a name="clientvirtualdevicesetcreate"></a>ClientVirtualDeviceSet::Create

**Scopo** questa funzione crea il set di dispositivo virtuale.

**Sintassi**
   ```
   int ClientVirtualDeviceSet::Create (
   char *   name,       // name for the set
   VDConfig   * cfg     // configuration for the set
   );
   ```

| Parametri | Argomento | Spiegazione
| ----- | ----- | ------ |
| | **name** | Identifica il set di dispositivo virtuale. Le regole per i nomi utilizzati dai CreateFileMapping() devono essere seguite. Qualsiasi carattere tranne una barra rovesciata (\) possono essere utilizzate. Si tratta di una stringa di caratteri. È consigliabile apponendo il prefisso della stringa con nome di prodotto o la società e del database dell'utente. |
| |**cfg** | Questa è la configurazione per il set di dispositivo virtuale. Per ulteriori informazioni, vedere "Configurazione" più avanti in questo documento.

| Valori restituiti | Argomento | Spiegazione
| ----- | ----- | ------ |
| |**NOERROR** | Funzione completata. |
| |**VD_E_NOTSUPPORTED** |Uno o più dei campi nella configurazione non è valido o non è supportato in caso contrario. |
| |**VD_E_PROTOCOL** | Il dispositivo virtuale impostato già esiste.

**La sezione Osservazioni** crea il metodo deve essere chiamato una sola volta per ogni operazione di BACKUP o ripristino. Dopo la chiamata di metodo di chiusura, il client può riutilizzare l'interfaccia per creare un altro set di dispositivo virtuale.

## <a name="clientvirtualdevicesetgetconfiguration"></a>ClientVirtualDeviceSet::GetConfiguration

**Scopo** questa funzione viene utilizzata per attendere che il server configurare il set di dispositivo virtuale.
**Sintassi**
   ```
   int ClientVirtualDeviceSet::GetConfiguration (
   time_t       timeout,    // in milliseconds
   VDConfig *       cfg // selected configuration
   );
   ```

| Parametri | Argomento | Spiegazione
| ----- | ----- | ------ |
| | **timeout** | Questo è il timeout in millisecondi. Utilizzare INFINITE o qualsiasi numero intero negativo per impedire i timeout.
| | **cfg** | Al termine dell'esecuzione ha esito positivo, contiene la configurazione selezionata dal server. Per ulteriori informazioni, vedere "Configurazione" più avanti in questo documento.

| Valori restituiti | Argomento | Spiegazione
| ----- | ----- | ------ |
| |**NOERROR** | La configurazione è stata restituita.
| |**VD_E_ABORT** |SignalAbort è stato richiamato.
| |**VD_E_TIMEOUT** |La funzione di timeout.

**La sezione Osservazioni** questa funzione blocca in uno stato di avviso. Dopo la chiamata ha esito positivo, i dispositivi nel set di dispositivo virtuale possono essere aperta.


## <a name="clientvirtualdevicesetopendevice"></a>ClientVirtualDeviceSet::OpenDevice
**Scopo** questa funzione consente di aprire uno dei dispositivi nel set di dispositivo virtuale.
**Sintassi**
   ```
   int ClientVirtualDeviceSet::OpenDevice (
   char *           name,       // name for the set
   ClientVirtualDevice **       ppVirtualDevice // returns interface to device
   );
   ```

| Parametri | Argomento | Spiegazione
| ----- | ----- | ------ |
| | **name** |Identifica il set di dispositivo virtuale.
| | **ppVirtualDevice** |Quando la funzione ha esito positivo, viene restituito un puntatore al dispositivo virtuale. Il dispositivo viene utilizzato per GetCommand e CompleteCommand.

| Valori restituiti | Argomento | Spiegazione
| ----- | ----- | ------ |
| |**NOERROR** |Funzione completata.
| |**VD_E_ABORT** | È stato richiesto Abort.
| |**VD_E_OPEN** |  Tutti i dispositivi sono aperti.
| |**VD_E_PROTOCOL** |  Il set non è in stato di inizializzazione o il dispositivo è già aperto.
| |**VD_E_INVALID** |Il nome del dispositivo non è valido. Non è uno dei nomi noti che costituiscono il set.

**La sezione Osservazioni** VD_E_OPEN può essere restituito senza problemi. Il client può chiamare OpenDevice mezzo di un ciclo finché non viene restituito il codice.
Se è configurato più di un dispositivo, ad esempio *n* i dispositivi, verrà restituito il set di dispositivo virtuale *n* interfacce univoco del dispositivo.

Il `GetConfiguration` funzione può essere usata per attendere fino a quando i dispositivi possono essere aperti.
Se questa funzione non riesce, viene restituito un valore null tramite il ppVirtualDevice.
 
## <a name="clientvirtualdevicegetcommand"></a>ClientVirtualDevice::GetCommand

**Scopo** questa funzione viene utilizzata per ottenere il successivo comando in coda in un dispositivo. Quando richiesto, questa funzione è in attesa per il comando successivo.

**Sintassi**
   ```
   int ClientVirtualDevice::GetCommand (
   time_t       timeout,    // time-out in milliseconds
   VDC_Command**    ppCmd   // returns the next command
   );
   ```

| Parametri | Argomento | Spiegazione
| ----- | ----- | ------ |
| |**timeout** |Questo è il tempo di attesa, espresso in millisecondi. Utilizzare INFINTE per un'attesa indefinita. Usare 0 per eseguire il polling per un comando. VD_E_TIMEOUT viene restituito se il comando non è attualmente disponibile. Se si verifica il timeout, il client stabilisce l'azione successiva.
| |**Timeout** |Questo è il tempo di attesa, espresso in millisecondi. Utilizzare INFINTE o un valore negativo per un'attesa indefinita. Usare 0 per eseguire il polling per un comando. VD_E_TIMEOUT viene restituito se non è disponibile prima della scadenza del timeout. Se si verifica il timeout, il client stabilisce l'azione successiva.
| |**ppCmd** |Quando un comando è stato restituito correttamente, il parametro restituisce l'indirizzo di un comando da eseguire. La memoria restituita è di sola lettura. Quando il comando viene completato, l'indicatore di misura viene passato alla routine CompleteCommand. Per informazioni dettagliate su ogni comando, vedere "Comandi" più avanti in questo documento.
        
| Valori restituiti | Argomento | Spiegazione
| ----- | ----- | ------ |
| |**NOERROR** |È stato recuperato un comando.
| |**VD_E_CLOSE** |Il dispositivo è stato chiuso dal server.
| |**VD_E_TIMEOUT** |Comando non è disponibile e il timeout è scaduto.
| |**VD_E_ABORT** |Il client o il server ha usato il SignalAbort per forzare l'arresto.

**La sezione Osservazioni** VD_E_CLOSE quando viene restituito, SQL Server ha chiuso il dispositivo. Questo fa parte dell'arresto normale. Dopo la chiusura di tutti i dispositivi, il client richiama ClientVirtualDeviceSet::Close per chiudere il set di dispositivo virtuale.
Quando questa routine deve bloccarsi in attesa per un comando, il thread è disponibile in una condizione di avviso.

## <a name="clientvirtualdevicecompletecommand"></a>ClientVirtualDevice::CompleteCommand

**Scopo** questa funzione viene utilizzata per notificare a SQL Server che ha completato un comando. Informazioni sul completamento appropriati per il comando deve essere restituiti. Per ulteriori informazioni, vedere "Comandi" più avanti in questo documento.

**Sintassi** 

   ```
   int ClientVirtualDevice::CompleteCommand (
   VDC_Command pCmd,        // the command
   int  completionCode,     // completion code
   unsigned long    bytesTransferred,   // bytes transferred
   int64_t  position        // current position
   );
   ```

| Parametri | Argomento | Spiegazione
| ----- | ----- | ------ |
| |**pCmd** |Questo è l'indirizzo di un comando precedentemente restituito da ClientVirtualDevice::GetCommand.
| |**completionCode** |Si tratta di un codice di stato che indica lo stato di completamento. Questo parametro deve essere restituito per tutti i comandi. Il codice restituito deve essere appropriato per il comando viene eseguito. ERROR_SUCCESS è usato in tutti i casi per indicare un comando eseguito correttamente. Per l'elenco completo dei possibili codici, vedere il file, vdierror.h. Un elenco di codici di stato per ogni comando viene visualizzata in "Comandi" più avanti in questo documento.
| |**bytesTransferred** |Questo è il numero di byte trasferiti. Viene restituito solo per il trasferimento di dati, i comandi di lettura e scrittura.
| |**position** |Si tratta di una risposta al comando GetPosition solo.
        
| Valori restituiti | Argomento | Spiegazione
| ----- | ----- | ------ |
| |**NOERROR** |Il completamento corretto è stato indicato.
| |**VD_E_INVALID** |pCmd non è un comando attivo.
| |**VD_E_ABORT** |È stata segnalata l'interruzione.
| |**VD_E_PROTOCOL** |Il dispositivo non è aperto.

**La sezione Osservazioni** nessuno

## <a name="clientvirtualdevicesetsignalabort"></a>ClientVirtualDeviceSet::SignalAbort

**Scopo** questa funzione viene utilizzata per segnalare che non deve verificarsi una terminazione anomala.

**Sintassi** 

   ```
   int ClientVirtualDeviceSet::SignalAbort ();
   ```

| Parametri | Argomento | Spiegazione
| ----- | ----- | ------ |
| |Nessuno | Non applicabile
        
| Valori restituiti | Argomento | Spiegazione
| ----- | ----- | ------ |
| |**NOERROR**|La notifica di interruzione è stata registrata correttamente.

**La sezione Osservazioni** in qualsiasi momento, il client può scegliere di interrompere l'operazione di BACKUP o ripristino. Questa routine segnala che devono smettere tutte le operazioni. Lo stato del set di dispositivo virtuale complessiva entra in uno stato anomalo. Viene restituito alcun comando di ulteriore su qualsiasi dispositivo. Tutti i comandi incompiuti vengono completati automaticamente, restituendo 995L come un codice di completamento. Il client deve chiamare ClientVirtualDeviceSet::Close dopo qualsiasi uso di buffer fornito al client in attesa è terminato in modo sicuro. Per ulteriori informazioni, vedere "Anomala" più indietro in questo documento.

## <a name="clientvirtualdevicesetclose"></a>ClientVirtualDeviceSet::Close

**Scopo** questa funzione chiude il set di dispositivi virtuali creato da ClientVirtualDeviceSet::Create. Comporta il rilascio di tutte le risorse associate al set di dispositivo virtuale.

**Sintassi** 

   ```
   int ClientVirtualDeviceSet::Close ();
   ```

| Parametri | Argomento | Spiegazione
| ----- | ----- | ------ |
| |Nessuno |Non applicabile
        
| Valori restituiti | Argomento | Spiegazione
| ----- | ----- | ------ |
| |**NOERROR** |Viene restituito quando il set di dispositivo virtuale è stato chiuso.
| |**VD_E_PROTOCOL** |È stata eseguita alcuna azione perché il set di dispositivo virtuale non è stato aperto.
| |**VD_E_OPEN** |I dispositivi sono stati ancora aperti.

**La sezione Osservazioni** la chiamata di Close è una dichiarazione di client che devono essere rilasciate tutte le risorse usate dal set di dispositivo virtuale. Il client deve verificare che tutte le attività che coinvolgono i buffer di dati e i dispositivi virtuali vengano terminata prima di richiamare una chiusura. Tutte le interfacce di dispositivo virtuale restituite da OpenDevice Invalidate da chiudere.
Il client è autorizzato a eseguire una chiamata di creazione dell'interfaccia di set di dispositivo virtuale dopo la chiamata di chiusura viene restituito. Una chiamata di questo tipo è necessario creare un nuovo dispositivo virtuale impostato per un'operazione di BACKUP o RESTORE successiva.
Se Chiudi viene chiamato quando uno o più dispositivi virtuali sono ancora aperti, viene restituito VD_E_OPEN. In questo caso, SignalAbort viene attivata internamente, per garantire una corretta chiusura se possibile. VDI risorse vengono rilasciate. Per un'indicazione VD_E_CLOSE su ogni dispositivo prima di richiamare ClientVirtualDeviceSet::Close di attesa del client. Se il client sa che la periferica virtuale è già in uno stato anomalo e non prevede un'indicazione VD_E_CLOSE da GetCommand e può richiamare ClientVirtualDeviceSet::Close non appena è terminata l'attività su buffer condiviso.
Per ulteriori informazioni, vedere "Anomala" più indietro in questo documento.

## <a name="clientvirtualdevicesetopeninsecondary"></a>ClientVirtualDeviceSet::OpenInSecondary

**Scopo** questa funzione consente di aprire il dispositivo virtuale impostato in un client secondario. Il client primario deve essere già utilizzato Create e GetConfiguration per impostare il set di dispositivo virtuale.

**Sintassi** 
   
   ```
   int ClientVirtualDeviceSet::OpenInSecondary (
   char *   setName         // name of the set
   );
   ```

| Parametri | Argomento | Spiegazione
| ----- | ----- | ------ |
| |**setName** |Identifica il set. Questo nome è tra maiuscole e minuscole e deve corrispondere al nome utilizzato dal client primario, quando richiamata ClientVirtualDeviceSet::Create.

| Valori restituiti | Argomento | Spiegazione
| ----- | ----- | ------ |
| |**NOERROR** |Funzione completata.
| |**VD_E_PROTOCOL** |Il set di dispositivo virtuale non è stato creato, è già stata aperta nel client o il dispositivo virtuale set non è pronto per accettare richieste aperte dai client secondario.
| |**VD_E_ABORT** |L'operazione viene interrotta.

**La sezione Osservazioni** quando si utilizza un modello di processo più, il client primario è responsabile del rilevamento normale e anomala terminazione dei client secondario.

## <a name="clientvirtualdevicesetgetbufferhandle"></a>ClientVirtualDeviceSet::GetBufferHandle

**Scopo** alcune applicazioni possono richiedere più di un processo su cui operare il buffer restituito da ClientVirtualDevice::GetCommand. In questi casi, il processo che riceve il comando è possibile utilizzare GetBufferHandle per ottenere un handle di processo indipendenti che identifica il buffer. Questo handle può essere comunicato quindi a qualsiasi altro processo che dispone anche di aprire la periferica virtuale impostata stesso. Tale processo utilizzerebbe quindi ClientVirtualDeviceSet::MapBufferHandle per ottenere l'indirizzo del buffer. Poiché ogni processo può essere mapping buffer indirizzi diversi, l'indirizzo saranno probabilmente un indirizzo diverso da quello nel proprio partner.

**Sintassi** 

   ```
   int ClientVirtualDeviceSet::GetBufferHandle (
   uint8_t*     pBuffer,        // in: buffer address
   unsigned int*        pBufferHandle   // out: buffer handle
   );
   ```

| Parametri | Argomento | Spiegazione
| ----- | ----- | ------ |
| |**pBuffer** |Questo è l'indirizzo di un buffer ottenuto da un comando di lettura o scrittura.
| |**BufferHandle** |Un identificatore univoco per il buffer viene restituito.

| Valori restituiti | Argomento | Spiegazione
| ----- | ----- | ------ |
| |**NOERROR** |Funzione completata.
| |**VD_E_PROTOCOL** |Il set di dispositivo virtuale non è attualmente aperto.
| |**VD_E_INVALID** |Il pBuffer non è un indirizzo valido.
La sezione Osservazioni il processo che richiama la funzione GetBufferHandle è responsabile del richiamo ClientVirtualDevice::CompleteCommand una volta completato il trasferimento dei dati.

## <a name="clientvirtualdevicesetmapbufferhandle"></a>ClientVirtualDeviceSet::MapBufferHandle

**Scopo** questa funzione viene utilizzata per ottenere un indirizzo valido del buffer da un handle del buffer ottenuto da un altro processo. 

**Sintassi** 

   ```
   int ClientVirtualDeviceSet::MapBufferHandle (
   i        nt  dwBuffer,   // in: buffer handle
   uint8_t**    ppBuffer        // out: buffer address
   );
   ```

| Parametri | Argomento | Spiegazione
| ----- | ----- | ------ |
| |**dwBuffer** |Questo è l'handle restituito da ClientVirtualDeviceSet::GetBufferHandle.
| |**ppBuffer** |Questo è l'indirizzo del buffer che è valido nel processo corrente.

| Valori restituiti | Argomento | Spiegazione
| ----- | ----- | ------ |
| |**NOERROR** |Funzione completata.
| |**VD_E_PROTOCOL** |Il set di dispositivo virtuale non è attualmente aperto.
| |**VD_E_INVALID** |Il ppBuffer è un handle non valido.

**La sezione Osservazioni** necessario prestare attenzione per comunicare correttamente i punti di controllo. Gli handle sono locali a un set unico dispositivo virtuale. I processi di partner, la condivisione di un handle devono verificare buffer handle vengono utilizzati solo nell'ambito del dispositivo virtuale impostata da cui è stato originariamente ottenuto il buffer.


