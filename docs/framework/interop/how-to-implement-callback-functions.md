---
title: 'Comment : implémenter des fonctions de rappel'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- callback function, implementing
ms.assetid: e55b3712-b9ea-4453-bd9a-ad5cfa2f6bfa
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e081347129ce367cf6b46ca29c07a016bb64ab95
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33389273"
---
# <a name="how-to-implement-callback-functions"></a>Comment : implémenter des fonctions de rappel
La procédure et l'exemple suivants montrent comment une application managée peut, à l'aide de l'appel de code non managé, imprimer la valeur de handle de chaque fenêtre sur l'ordinateur local. En particulier, ils utilisent la fonction **EnumWindows** pour parcourir la liste des fenêtres et une fonction de rappel managée (nommée CallBack) pour imprimer la valeur du handle des fenêtres.  
  
### <a name="to-implement-a-callback-function"></a>Pour implémenter une fonction de rappel  
  
1.  Examinez la signature de la fonction **EnumWindows** avant d’aller plus loin dans l’implémentation. **EnumWindows** possède la signature suivante :  
  
    ```  
    BOOL EnumWindows(WNDENUMPROC lpEnumFunc, LPARAM lParam)  
    ```  
  
     La présence de l’argument **lpEnumFunc** indique que cette fonction nécessite un rappel. Le préfixe **lp** (pointeur long) est couramment associé au suffixe **Func** dans le nom des arguments qui acceptent un pointeur vers une fonction de rappel. Pour obtenir de la documentation sur les fonctions Win32, consultez le Kit de développement Microsoft Platform SDK.  
  
2.  Créez la fonction de rappel managée. L’exemple déclare un type délégué, appelé `CallBack`, qui accepte deux arguments (**hwnd** et **lparam**). Le premier argument est un handle de la fenêtre, alors que le second est défini par l’application. Dans cette version, les deux arguments doivent être des entiers.  
  
     Les fonctions de rappel retournent généralement des valeurs différentes de zéro pour indiquer la réussite et zéro pour indiquer l'échec. Dans cet exemple, **true** est explicitement défini comme valeur de retour pour poursuivre l’énumération.  
  
3.  Créez un délégué et passez-le en tant qu’argument à la fonction **EnumWindows**. L'appel de code non managé convertit automatiquement le délégué au format de rappel habituel.  
  
4.  Assurez-vous que le garbage collector ne récupère pas le délégué avant que la fonction de rappel n’ait effectué sa tâche. Quand vous transmettez un délégué en tant que paramètre ou un délégué contenu en tant que champ dans une structure, il n'est pas collecté pendant toute la durée de l'appel. Par conséquent, comme dans le cas de l'exemple d'énumération suivant, la fonction de rappel effectue sa tâche avant le retour d'appel et ne nécessite aucune action supplémentaire de la part de l'appelant managé.  
  
     Si, toutefois, la fonction de rappel peut être appelée après le retour d'appel, l'appelant managé doit prendre des mesures pour s’assurer que le délégué n'est pas collecté jusqu’à ce que la fonction de rappel termine sa tâche. Pour plus d’informations sur la façon d’empêcher l’opération de garbage collection, consultez [Marshaling d’interopérabilité](../../../docs/framework/interop/interop-marshaling.md) avec l’appel de code non managé.  
  
## <a name="example"></a>Exemple  
  
```vb  
Imports System  
Imports System.Runtime.InteropServices  
  
Public Delegate Function CallBack( _  
hwnd As Integer, lParam As Integer) As Boolean  
  
Public Class EnumReportApp  
  
    Declare Function EnumWindows Lib "user32" ( _  
       x As CallBack, y As Integer) As Integer  
  
    Public Shared Sub Main()  
        EnumWindows(AddressOf EnumReportApp.Report, 0)  
    End Sub 'Main  
  
    Public Shared Function Report(hwnd As Integer, lParam As Integer) _  
    As Boolean  
        Console.Write("Window handle is ")  
        Console.WriteLine(hwnd)  
        Return True  
    End Function 'Report  
End Class 'EnumReportApp  
```  
  
```csharp  
using System;  
using System.Runtime.InteropServices;  
  
public delegate bool CallBack(int hwnd, int lParam);  
  
public class EnumReportApp  
{  
    [DllImport("user32")]  
    public static extern int EnumWindows(CallBack x, int y);   
  
    public static void Main()   
    {  
        CallBack myCallBack = new CallBack(EnumReportApp.Report);  
        EnumWindows(myCallBack, 0);  
    }  
  
    public static bool Report(int hwnd, int lParam)  
    {   
        Console.Write("Window handle is ");  
        Console.WriteLine(hwnd);  
        return true;  
    }  
}  
```  
  
```cpp  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
// A delegate type.  
delegate bool CallBack(int hwnd, int lParam);  
  
// Managed type with the method to call.  
ref class EnumReport  
{  
// Report the window handle.  
public:  
    [DllImport("user32")]  
    static int EnumWindows(CallBack^ x, int y);  
  
    static void Main()  
    {  
        EnumReport^ er = gcnew EnumReport;  
        CallBack^ myCallBack = gcnew CallBack(&EnumReport::Report);  
        EnumWindows(myCallBack, 0);  
    }  
  
    static bool Report(int hwnd, int lParam)  
    {  
       Console::Write(L"Window handle is ");  
       Console::WriteLine(hwnd);  
       return true;  
    }  
};  
  
int main()  
{  
    EnumReport::Main();  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions de rappel](../../../docs/framework/interop/callback-functions.md)  
 [Appel à une fonction DLL](../../../docs/framework/interop/calling-a-dll-function.md)
