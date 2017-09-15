---
title: Comando indice | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- index command [ODBC]
ms.assetid: 694e8cf5-2f69-4001-9c1e-b735a4da3aff
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: cdec619d99c610c75b9b27de710cd4e5913602f6
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="index-command"></a>Comando indice
Crea un file di indice per visualizzare e accedere ai record di tabella in ordine logico.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
INDEX ON eExpression TO IDXFileName | TAG TagName [OF CDXFileName]  
   [FOR lExpression]  
   [COMPACT]  
   [ASCENDING | DESCENDING]  
   [UNIQUE | CANDIDATE]  
   [ADDITIVE]  
```  
  
## <a name="arguments"></a>Argomenti  
 *eExpression*  
 Specifica un'espressione di indice che può includere il nome di uno o più campi dalla tabella corrente. Nel file di indice per ogni record nella tabella viene creata una chiave di indice in base all'espressione di indice. Visual FoxPro utilizza tali chiavi per visualizzare e accedere ai record nella tabella.  
  
> [!NOTE]  
>  Sebbene non sia consigliato, *eExpression* può anche essere una variabile di memoria, un elemento della matrice o un campo o l'espressione di campo da una tabella in un'altra area di lavoro. Campi Memo non possono essere utilizzati da solo in espressioni di file di indice. devono essere combinati con altre espressioni di caratteri. Se si accede a un indice che contiene una variabile o un campo che non esiste o non è possibile individuare, Visual FoxPro genera un messaggio di errore.  
  
 Se si tenta di compilare un indice con una chiave che possa variare in lunghezza, la chiave viene riempita con spazi. Le chiavi di indice a lunghezza variabile non sono supportate in Visual FoxPro.  
  
 È possibile creare una chiave di indice con lunghezza zero. Ad esempio, una chiave di indice zero lunghezza viene creata quando l'espressione di indice è una sottostringa di un campo vuoto di credito. Una chiave di indice zero lunghezza genera un messaggio di errore. Quando Visual FoxPro viene creato un indice, valuta i campi del primo record nella tabella. Se un campo è vuoto, potrebbe essere necessario immettere alcuni dati temporanei nel campo del primo record per evitare una chiave di indice di lunghezza 0.  
  
 PER *IDXFileName*  
 Crea un file di indice IDX. Il file di indice viene assegnato l'IDX di estensione predefinito.  
  
 TAG *TagName*[OF *CDXFileName*]  
 Crea un file di indice composto. Un file di indice composto è un file di indice singolo costituito da un numero qualsiasi di tag separato (voci di indice). Ogni tag viene identificato in base al nome di tag univoco. I nomi di tag devono iniziare con una lettera o un carattere di sottolineatura e possono contenere qualsiasi combinazione di lettere, cifre o caratteri di sottolineatura fino a 10. Il numero di tag in un file di indice composto è limitato solo dalla memoria disponibile e lo spazio su disco.  
  
 File di indice composto più voce sono sempre compact. Non è necessario includere COMPACT durante la creazione di un file di indice composto. Un'estensione cdx vengono forniti nomi di file di indice composto.  
  
 Creare due tipi di file di indice composto: strutturali e non strutturali.  
  
 **File di indice composto strutturale** è possibile creare un file di indice composto strutturale con TAG *TagName* escludendo il parametro facoltativo di *CDXFileName* clausola. Un file di indice composto strutturale sempre ha lo stesso nome di base della tabella e viene aperto automaticamente quando la tabella è aperta.  
  
 **File di indice composto** è possibile creare un file di indice composto includendo OF *CDXFileName* dopo il TAG *TagName*. A differenza di un file di indice composto strutturale, un file di indice composto deve essere aperto in modo esplicito con la clausola di indice in uso.  
  
 Se già creato e aperto un file di indice composto, emettendo l'indice con TAG *TagName* aggiunge un tag per il file di indice composto.  
  
 PER *lExpression*  
 Specifica una condizione in base al quale solo i record che soddisfano l'espressione di filtro *lExpression* sono disponibili per la visualizzazione e di accesso; le chiavi di indice vengono create nel file di indice per solo i record corrispondenti all'espressione di filtro.  
  
 Tecnologia di Visual FoxPro Rushmore Ottimizza un indice... PER *lExpression* comando se *lExpression* è un'espressione ottimizzabile. Per prestazioni ottimali, utilizzare un'espressione ottimizzabile nella clausola FOR.  
  
 COMPACT  
 Crea un file IDX compact.  
  
 ORDINE CRESCENTE  
 Specifica un ordine crescente per il file cdx. Per impostazione predefinita, i tag cdx vengono creati in ordine crescente. (È possibile includere crescente come promemoria di ordine del file di indice). Una tabella può essere indicizzata in ordine inverso includendo DECRESCENTE.  
  
 DECRESCENTE  
 Specifica un ordine decrescente per il file cdx. È possibile includere DECRESCENTE durante la creazione di file di indice IDX.  
  
 UNIQUE  
 Specifica che solo il primo record rilevato con un valore di chiave di indice specifico è incluso in un file IDX o un tag cdx. UNIQUE può essere utilizzato per impedire l'accesso o visualizzazione di record duplicati. Tutti i record aggiunti con chiavi di indice duplicati vengono esclusi dal file di indice. Utilizzando l'opzione di indice univoco è identico all'esecuzione di SET UNIQUE ON prima di rilasciare l'indice o REINDICIZZAZIONE.  
  
 Quando è attivo un indice univoco o un tag di indice e un record duplicato viene modificato in modo che modifica la chiave di indice, viene aggiornato l'indice o un tag di indice. Tuttavia, è Impossibile accedere o visualizzato finché non si reindicizzare il file utilizzando REINDICIZZAZIONE il successivo record duplicato con la chiave di indice originale.  
  
 CANDIDATO  
 Crea un tag di indice strutturale candidato. La parola chiave CANDIDATA può essere inclusa solo durante la creazione di un tag di un indice strutturale; in caso contrario, Visual FoxPro genera un messaggio di errore.  
  
 Valori duplicati nel campo o una combinazione dei campi specificati nell'espressione di indice impedisce a un tag di indice candidato *eExpression*. Il termine *candidato* fa riferimento al tipo di indice, perché gli indici candidato evitare valori duplicati, siano qualificati come "candidato" da un indice primario.  
  
 Visual FoxPro genera un errore se si crea un tag di indice di candidati per un campo o una combinazione di campi che già contiene valori duplicati.  
  
 ADDITIVO  
 Mantiene aprire qualsiasi file di indice precedentemente aperti. Se si omette la clausola additivo quando si crea un file di indice o di file per una tabella con indice, vengono chiusi tutti i file di indice aperto in precedenza (ad eccezione dell'indice composto strutturale).  
  
## <a name="remarks"></a>Osservazioni  
 Record in una tabella che dispone di un file di indice sono visualizzati e nell'ordine specificato dall'espressione di indice. L'ordine fisico dei record nella tabella non viene modificato da un file di indice.  
  
## <a name="index-types"></a>Tipi di indice  
 Visual FoxPro consente di creare due tipi di file di indice:  
  
-   File di indice cdx contenente più voci di indice denominate tag compositi  
  
-   file di indice IDX contenente una voce di indice  
  
 È anche possibile creare un file di indice composto strutturale, che viene aperto automaticamente con la tabella.  
  
> [!NOTE]  
>  File di indice composto strutturale vengono automaticamente aperti quando viene aperto nella tabella, sono il tipo di indice preferito.  
  
 Includere COMPACT per creare file di indice di compact IDX. File di indice composto sono sempre compact.  
  
## <a name="index-order-and-updating"></a>Ordine dell'indice e l'aggiornamento  
 Tag (tag master) o un solo indice (il file indice master) determina l'ordine in cui la tabella viene visualizzata o accessibile. Alcuni comandi (ad esempio SEEK) utilizzano il file di indice master o di un tag per cercare i record. Tuttavia tutti aprire IDX e i file di indice cdx vengono aggiornati quando vengono apportate modifiche alla tabella.  
  
## <a name="user-defined-functions"></a>Funzioni definite dall'utente  
 Sebbene un'espressione di indice può contenere una funzione definita dall'utente, è consigliabile non utilizzare funzioni definite dall'utente in un'espressione di indice. Funzioni definite dall'utente in un'espressione di indice aumentano il tempo che necessario per creare o aggiornare l'indice. Inoltre, gli aggiornamenti dell'indice potrebbero non verificarsi quando una funzione definita dall'utente viene utilizzata per un'espressione di indice.  
  
 Se si utilizza una funzione definita dall'utente in un'espressione di indice, Visual FoxPro deve essere in grado di individuare la funzione definita dall'utente. Quando Visual FoxPro viene creato un indice, l'espressione di indice viene salvata nel file di indice, ma solo un riferimento alla funzione definita dall'utente è incluso nell'espressione di indice.  
  
## <a name="see-also"></a>Vedere anche  
 [ALTER TABLE - comando SQL](../../odbc/microsoft/alter-table-sql-command.md)   
 [ELIMINARE i comandi di TAG](../../odbc/microsoft/delete-tag-command.md)   
 [Comando COLLATE SET](../../odbc/microsoft/set-collate-command.md)   
 [Comando univoco SET](../../odbc/microsoft/set-unique-command.md)
