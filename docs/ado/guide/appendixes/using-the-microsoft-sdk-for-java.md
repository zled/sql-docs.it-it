---
title: Utilizzo di Microsoft SDK per Java | Documenti Microsoft
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 02/15/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Java (Microsoft SDK for)
- Microsoft SDK for Java [ADO]
ms.assetid: 2d7cb5b5-8307-49dd-b07e-c07069bb1626
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b7473f3a8772c53834c964071c2385736ff45cbf
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="using-the-microsoft-sdk-for-java"></a>Utilizzo di Microsoft SDK per Java

> [!IMPORTANT]
> Microsoft non è più supportata di Visual J++ nel gennaio 2004.

Microsoft SDK per Java è il kit per sviluppatori per l'ambiente di Microsoft Internet Explorer. Strumenti, informazioni ed esempi vengono forniti per lo sviluppo di applicazioni Java e applet Java in base a JDK 1.1 e la macchina virtuale di Microsoft Win32 (Microsoft VM). Microsoft SDK per Java non è collegato a Microsoft Visual J++. Per scaricare questo SDK, fare clic qui.  
  
 L'utilità Jactivex.exe genera classi da una libreria dei tipi, ma può essere richiamato solo sulla riga di comando. Questa funzionalità non è integrata con l'ambiente di sviluppo Visual J++. A differenza delle classi generate dalla procedura guidata libreria tipo Java, è possibile eseguirne il wrapper della classe creato dal SDK. Ciò è utile per il debug come il codice utilizza le classi wrapper di ADO.  
  
 Questo meccanismo legge la libreria dei tipi ADO e genera le classi che è possibile creare un'istanza all'interno dell'applicazione. Genera le classi nel percorso seguente: \\< directory di windows\>\Java\trustlib\msado15.  
  
 Creazione di un'applicazione ADO in Java utilizzando Microsoft SDK per Java è essenzialmente identica, dalla prospettiva del codice sorgente, per la creazione guidata raccolta tipo Java. Per esempio di codice, vedere [wrapper di classe Java ADO](../../../ado/guide/appendixes/ado-java-class-wrappers.md). L'unica differenza concreta è nella modalità di generazione di classi wrapper in primo luogo, come illustrato nei passaggi seguenti.  
  
### <a name="to-create-an-ado-project-with-the-microsoft-sdk-for-java"></a>Per creare un progetto di ADO con Microsoft SDK per Java  
  
1.  Eseguire il comando seguente a un prompt dei comandi. È necessario impostare il percorso per includere Microsoft SDK per la directory Bin di Java o eseguire il comando da quel percorso. In genere, Microsoft SDK per Java è installato nello stesso percorso di Visual Studio. Si tratta di un'istruzione singolo comando.  
  
    ```  
    \<path to DevStudio>\<path to Java SDK>\bin\JactiveX.exe /javatlb "C:\program files\common files\system\ado\msado15.dll"  
    ```  
  
2.  Eseguire il comando seguente per compilare le classi generate. Il parametro /g: t attiva la generazione di simboli di debug in modo che sia possibile tenere traccia di. Simboli di Java. Rimuovere la build di rilascio.  
  
    ```  
    jvc /g:t c:\<windows>\Java\trustlib\msado15\*.Java  
    ```  
  
3.  Per utilizzare questi file, aprire il progetto in Visual J++. Dal **progetto** menu, scegliere **Aggiungi a progetto**. Selezionare **file**e aggiungere tutti i. File JAVA generati nella directory trustlib\msado15 al progetto.  
  
## <a name="see-also"></a>Vedere anche  
 [Wrapper di classe Java ADO](../../../ado/guide/appendixes/ado-java-class-wrappers.md)   

