---
title: "如何︰ 尋找同層級節點 (XPATH-LINQ to XML) (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 73082738-2113-4438-8545-98d5df0927cb
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 615842d7b2fb1ae51d3380ecf928c22a59e42516
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017


---
# <a name="how-to-find-sibling-nodes-xpath-linq-to-xml-visual-basic"></a>如何︰ 尋找同層級節點 (XPATH-LINQ to XML) (Visual Basic)
您可能想要尋找具有特定名稱之節點的所有同層級。 如果內容節點也有特定的名稱，所產生的集合可能包含內容節點。  
  
 XPath 運算式為：  
  
 `../Book`  
  
## <a name="example"></a>範例  
 此範例會先尋找 `Book` 項目，然後尋找名稱為 `Book` 的所有同層級項目。 所產生的集合包含內容節點。  
  
 這個範例會使用下列 XML 文件︰[範例 XML 檔︰ 書籍 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md)。  
  
```vb  
Dim books As XDocument = XDocument.Load("Books.xml")  
Dim book As XElement = books.Root.<Book>.Skip(1).First()  
  
' LINQ to XML query  
Dim list1 As IEnumerable(Of XElement) = book.Parent.<Book>  
  
' XPath expression  
Dim list2 As IEnumerable(Of XElement) = book.XPathSelectElements("../Book")  
  
If list1.Count() = list2.Count() And _  
        list1.Intersect(list2).Count() = list1.Count() Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
For Each el As XElement In list1  
    Console.WriteLine(el)  
Next  
```  
  
 這個範例會產生下列輸出：  
  
```  
Results are identical  
<Book id="bk101">  
  <Author>Garghentini, Davide</Author>  
  <Title>XML Developer's Guide</Title>  
  <Genre>Computer</Genre>  
  <Price>44.95</Price>  
  <PublishDate>2000-10-01</PublishDate>  
  <Description>An in-depth look at creating applications   
      with XML.</Description>  
</Book>  
<Book id="bk102">  
  <Author>Garcia, Debra</Author>  
  <Title>Midnight Rain</Title>  
  <Genre>Fantasy</Genre>  
  <Price>5.95</Price>  
  <PublishDate>2000-12-16</PublishDate>  
  <Description>A former architect battles corporate zombies,   
      an evil sorceress, and her own childhood to become queen   
      of the world.</Description>  
</Book>  
```  
  
## <a name="see-also"></a>另請參閱  
 [LINQ to XML 的 XPath 使用者 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)

