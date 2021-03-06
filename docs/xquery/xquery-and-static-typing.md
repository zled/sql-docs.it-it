---
title: XQuery e statico digitando | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- XQuery, static typing
- static typing
- checking static types
- inference [XQuery]
ms.assetid: d599c791-200d-46f8-b758-97e761a1a5c0
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 3b9390b198ddcb9a54691a7f33b8f52d520356d8
ms.sourcegitcommit: 0f7cf9b7ab23df15624d27c129ab3a539e8b6457
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2018
ms.locfileid: "51292423"
---
# <a name="xquery-and-static-typing"></a>XQuery e tipizzazione statica
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  In [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], XQuery è un linguaggio tipizzato in modo statico, ovvero genera errori di tipo durante la compilazione della query quando un'espressione restituisce un valore con una cardinalità o un tipo non accettato da una funzione o da un operatore specifico. Il controllo dei tipi statici può inoltre rilevare se un'espressione di percorso in un documento XML tipizzato è stata tipizzata in modo non corretto. Il compilatore XQuery applica innanzitutto la fase di normalizzazione che aggiunge le operazioni implicite, ad esempio l'atomizzazione, e quindi esegue l'inferenza e il controllo dei tipi statici.  
  
## <a name="static-type-inference"></a>Inferenza dei tipi statici  
 L'inferenza dei tipi statici determina il tipo restituito di un'espressione considerando i tipi statici dei parametri di input e la semantica statica dell'operazione e derivando il tipo statico del risultato. Ad esempio, il tipo statico dell'espressione 1 + 2,3 viene determinato nel modo seguente:  
  
-   Il tipo statico di 1 viene **xs: integer** ed è il tipo statico di 2,3 **xs: decimal**. In base alla semantica dinamica, la semantica statica del **+** operazione converte l'intero in un numero decimale e quindi restituisce un valore decimale. Il tipo statico derivato sarebbe **xs: decimal**.  
  
 Per le istanze XML non tipizzate, sono disponibili tipi speciali per indicare che i dati non sono tipizzati. Tali informazioni vengono utilizzate durante il controllo dei tipi statici e per l'esecuzione di determinati cast impliciti.  
  
 Per i dati tipizzati, il tipo di input viene derivato dalla raccolta di XML Schema che vincola l'istanza con tipo di dati XML. Ad esempio, se lo schema consente solo elementi di tipo **xs: integer**, i risultati di un'espressione di percorso utilizza tale elemento saranno zero o più elementi di tipo **xs: integer**. Questo valore viene espresso attualmente tramite un'espressione, ad esempio `element(age,xs:integer)*` in cui l'asterisco (\*) indica la cardinalità del tipo risultante. In questo esempio, l'espressione può restituire zero o più elementi di nome "age" e il tipo **xs: integer**. Altre cardinalità corrispondono esattamente a uno e sono espressi usando il nome del tipo da solo, zero o uno, espresso con un punto interrogativo (**?**) e 1 o più, espresso con un segno più (**+**) .  
  
 Talvolta, mediante l'inferenza dei tipi statici è possibile dedurre che un'espressione restituirà sempre una sequenza vuota. Ad esempio, se un'espressione di percorso su un tipo di dati XML tipizzato Cerca un \<nome > elemento all'interno di un \<cliente > elemento (/ cliente/nome), ma lo schema non consente un \<nome > all'interno di un \<cliente >, l'inferenza del tipo statico verrà dedotto che il risultato sarà vuoto. Questo verrà usato per rilevare query non corrette e verrà segnalato come errore statico, a meno che l'espressione sia () o **dei dati (())**.  
  
 Le regole di inferenza dettagliate sono indicate nella semantica formale delle specifiche XQuery. Microsoft ha modificato solo in misura minima tali regole per utilizzare istanze tipizzate con tipo di dati XML. La modifica più importante rispetto allo standard consiste nel fatto che il nodo di documento implicito conosce il tipo dell'istanza con tipo di dati XML. Di conseguenza, un'espressione di percorso con formato /age verrà tipizzata esattamente in base a tali informazioni.  
  
 Usando [modelli di SQL Server Profiler e autorizzazioni](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md), è possibile visualizzare i tipi statici restituiti come parte delle compilazioni di query. A tal fine, la traccia deve includere l'evento XQuery Static Type nella categoria di eventi TSQL.  
  
## <a name="static-type-checking"></a>Controllo dei tipi statici  
 Il controllo dei tipi statici verifica che l'esecuzione di run-time riceva solo valori di tipo appropriato per l'operazione. Poiché il controllo dei tipi non è necessario in fase di esecuzione, è possibile rilevare eventuali errori nelle fasi iniziali della compilazione, migliorando in tal modo le prestazioni. Per la tipizzazione statica, invece, è necessario che l'autore della query presti maggiore attenzione durante la formulazione.  
  
 I tipi appropriati che è possibile utilizzare sono i seguenti:  
  
-   Tipi consentiti in modo esplicito da una funzione o da un'operazione  
  
-   Un sottotipo di un tipo consentito in modo esplicito  
  
 I sottotipi vengono definiti in base alle regole di sottotipizzazione per l'utilizzo della derivazione per restrizione o per estensione di XML Schema. Ad esempio, un tipo S è un sottotipo del tipo T se tutti i valori di tipo S sono anche istanze del tipo T.  
  
 Inoltre, tutti i valori interi sono anche valori decimali, basati sulla gerarchia dei tipi di XML Schema. Tuttavia, non tutti i valori decimali sono valori interi. Pertanto, un valore intero è un sottotipo di un valore decimale ma non viceversa. Ad esempio, il **+** operazione consente solo valori di determinati tipi, ad esempio i tipi numerici **xs: integer**, **xs: decimal**, **xs: float**, e **xs: double**. Se i valori di altri tipi, ad esempio **xs: String**, sono passato, l'operazione genera un errore di tipo. Questo processo viene chiamato tipizzazione forte. È possibile convertire in modo implicito valori di altri tipi, ad esempio il tipo atomico utilizzato per indicare istanze XML non tipizzate, in un valore di un tipo accettato dall'operazione. Questo processo viene chiamato tipizzazione debole.  
  
 Se è necessario dopo una conversione implicita, il controllo dei tipi statici garantisce che solo i valori dei tipi consentiti con la cardinalità corretta vengano passati a un'operazione. Per "string" + 1, riconosce che il tipo statico di "string" sia **xs: String**. Poiché non si tratta di un tipo consentito per il **+** viene generato un errore di tipo operazione.  
  
 In caso di addizione del risultato di un'espressione arbitraria E1 a un'espressione arbitraria E2 (E1 + E2), l'inferenza dei tipi statici determina innanzitutto i tipi statici di E1 e di E2 e quindi confronta tali tipi statici con quelli consentiti per l'operazione. Ad esempio, se il tipo statico di E1 può essere un' **xs: String** o un' **xs: integer**, il controllo dei tipi statici restituisce un errore di tipo, anche se alcuni valori in fase di esecuzione potrebbe essere Integer. Lo stesso sarebbe il caso se fosse il tipo statico di E1 **xs: integer\***. Poiché il **+** operazione accetta solo un numero intero ed E1 può restituire zero o maggiore di 1, il controllo dei tipi statici genera un errore.  
  
 Come menzionato in precedenza, l'inferenza deduce spesso un tipo più complesso rispetto alle informazioni in possesso dell'utente riguardo ai tipi di dati da passare. In tali casi, l'utente deve riformulare la query. In genere, tra i casi tipici rientrano i seguenti:  
  
-   Il tipo deriva un tipo più generale, ad esempio un supertipo o un'unione di tipi. Nel caso di un tipo atomico, è consigliabile utilizzare l'espressione cast o la funzione costruttore per indicare il tipo statico effettivo. Ad esempio, se il tipo derivato dell'espressione E1 è una scelta tra **xs: String** oppure **xs: integer** e l'addizione richiede **xs: integer**, è consigliabile scrivere `xs:integer(E1) + E2` invece di `E1+E2`. Questa espressione potrebbe non riuscire in fase di esecuzione se viene rilevato un valore stringa che non è possibile eseguire il cast **xs: integer**. Tuttavia, l'espressione passerà il controllo dei tipi statici. Viene eseguito il mapping di questa espressione alla sequenza vuota.  
  
-   Il tipo deriva una cardinalità più elevata rispetto a quella effettiva dei dati. Ciò avviene di frequente, in quanto il **xml** tipo di dati può contenere più di un elemento di primo livello e una raccolta XML schema non può vincolarlo. Per limitare il tipo statico e garantire che venga passato effettivamente un unico valore, è consigliabile utilizzare il predicato basato sulla posizione `[1]`. Ad esempio, per aggiungere 1 al valore dell'attributo `c` dell'elemento `b` di livello inferiore rispetto all'elemento a di livello principale, è necessario scrivere utilizzare `write (/a/b/@c)[1]+1`. È inoltre possibile utilizzare la parola chiave DOCUMENT con una raccolta di XML Schema.  
  
-   Per alcune operazioni si verifica la perdita delle informazioni sul tipo durante l'inferenza. Ad esempio, se non è possibile determinare il tipo di un nodo, diventa **anyType**. di cui non è possibile eseguire il cast implicito ad altri tipi. Queste conversioni si verificano con più frequenza durante l'esplorazione tramite asse parent. Se l'espressione crea un errore di tipo statico, è consigliabile evitare l'utilizzo di tali operazioni e riformulare la query.  
  
## <a name="type-checking-of-union-types"></a>Verifica dei tipi unione  
 I tipi unione devono essere gestiti con particolare attenzione, perché possono causare problemi durante la verifica dei tipi. Due di questi problemi sono illustrati negli esempi seguenti.  
  
### <a name="example-function-over-union-type"></a>Esempio: funzione su tipo unione  
 Si consideri la seguente definizione per l'elemento <`r`> di tipo unione:  
  
```  
<xs:element name="r">  
<xs:simpleType>  
   <xs:union memberTypes="xs:int xs:float xs:double"/>  
</xs:simpleType>  
</xs:element>  
```  
  
 Nel contesto di XQuery, la funzione "average" `fn:avg (//r)` restituisce un errore statico perché il compilatore XQuery non è possibile aggiungere valori di tipi diversi (**xs: int**, **xs: float** o **xs: doppie**) per il <`r`> elementi nell'argomento **fn:avg()**. Per risolvere il problema, è necessario riscrivere la chiamata alla funzione nel modo seguente: `fn:avg(for $r in //r return $r cast as xs:double ?)`.  
  
### <a name="example-operator-over-union-type"></a>Esempio: operatore su tipo unione  
 L'operazione di addizione ('+') richiede tipi di operandi specifici. Di conseguenza, per l'elemento <`r`> l'espressione `(//r)[1] + 1` restituisce un errore statico con la definizione di tipo illustrata in precedenza. È possibile risolvere il problema riscrivendo l'espressione nel modo seguente: `(//r)[1] cast as xs:int? +1`, dove "?" indica zero o una occorrenza. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] richiede "cast as" con "?", perché ogni operazione di cast può generare una sequenza vuota in caso di errore di run-time.  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento al linguaggio XQuery &#40;SQL Server&#41;](../xquery/xquery-language-reference-sql-server.md)  
  
  
