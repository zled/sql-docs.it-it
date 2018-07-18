---
title: Sintassi del valore letterale numerica | Documenti Microsoft
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
- ODBC literals [ODBC], numeric
- numeric literals [ODBC]
- literals [ODBC], numeric
ms.assetid: fb17498d-4f1d-4b3d-b33d-1e62c7d3c32d
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 95fd850239c0ad3894105c94e3f8ff05459394ff
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="numeric-literal-syntax"></a>Sintassi del valore letterale numerica
Per i valori letterali numerici in ODBC, viene utilizzata la sintassi seguente:  
  
 *valore letterale numerico* :: = *letterale numerico firmati &#124; letterale numerico senza segno*  
  
 *firma-numerico-literal* :: = [*sign*] *letterale numerico senza segno*  
  
 *Unsigned-numerico-literal* :: = *letterale numerico esatto &#124; Colony-numerico-literal*  
  
 *valore esatto-numerico-literal* :: = *intero senza segno* [*periodo*[*intero senza segno*]]  *&#124;periodo unsigned integer*  
  
 *Sign* :: = *segno &#124; meno (-)*  
  
 *Colony-numerico-literal* :: = *esponente mantissa E*  
  
 *mantissa* :: = *esatta-numerico-literal*  
  
 *esponente* :: = *integer firmato*  
  
 *valore integer firmato* :: = [*sign*] *intero senza segno*  
  
 *intero senza segno* :: = *cifra...*  
  
 *segno di addizione* :: = *+*  
  
 *segno di sottrazione* :: = -  
  
 *cifra* :: = 1 &#124; 2 &#124; 3 &#124; 4 &#124; 5 &#124; 6 &#124; 7 &#124; 8 &#124; 9 &#124; 0  
  
 *periodo* :: =.
