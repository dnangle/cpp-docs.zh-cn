---
title: 泛型类型参数的约束 (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- where
helpviewer_keywords:
- where keyword [C++]
- constraints, C++
ms.assetid: eb828cc9-684f-48a3-a898-b327700c0a63
ms.openlocfilehash: 829f11c9f0c3935f9a415cae381cfc12d88df18a
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686751"
---
# <a name="constraints-on-generic-type-parameters-ccli"></a>泛型类型参数的约束 (C++/CLI)

在泛型类型或方法声明中，可以使用约束限定类型参数。 约束是用作类型参数的类型必须满足的需求。 例如，约束可能是类型参数必须实现特定接口或从特定类继承。

约束是可选的；不指定参数约束等效于将该参数约束为 <xref:System.Object>。

## <a name="syntax"></a>语法

```cpp
where type-parameter: constraint list
```

### <a name="parameters"></a>参数

*类型-参数*<br/>
要约束的其中一个类型参数。

constraint list**<br/>
constraint list** 是约束规范的逗号分隔列表。 列表可以包含由类型参数实现的接口。

列表也可以包含类。 要让类型参数满足基类约束，它必须与约束的类相同或从约束派生。

还可以指定 gcnew()****，以指明类型参数必须有公共的无参数构造函数；或指定 ref class****，以指明类型参数必须是引用类型（包括任意类、接口、委托或数组类型）；或指定 value class****，以指明类型参数必须是值类型。 可以指定除 Nullable 以外的任何值类型 \<T> 。

还可以指定泛型参数作为约束。 为要约束的类型提供的类型参数必须是或派生自约束的类型。 这称为裸类型约束。

## <a name="remarks"></a>备注

约束子句包括 where****，后面依次是类型参数、冒号 (:****)，以及用于指定对类型参数施加的限制性质的约束。 where**** 是上下文相关关键字；有关详细信息，请参阅[上下文相关关键字](context-sensitive-keywords-cpp-component-extensions.md)。 用空格分隔多个 where**** 子句。

约束可应用于类型参数，可对可用作泛型类型或方法的自变量的类型加以限制。

类和接口约束指定自变量类型必须是或继承自指定的类或实现指定接口。

对泛型类型或方法应用约束可以让该类型或方法中的代码利用约束类型的已知功能。 例如，可以声明一个泛型类，这样类型参数就能实现 `IComparable<T>` 接口：

```cpp
// generics_constraints_1.cpp
// compile with: /c /clr
using namespace System;
generic <typename T>
where T : IComparable<T>
ref class List {};
```

此约束要求，用于 `T` 的类型参数必须在编译时实现 `IComparable<T>`。 它还允许调用 `CompareTo` 等接口方法。 调用接口方法的类型参数实例不需要进行强制转换。

类型参数类的静态方法不能通过类型参数调用，只能通过实际命名类型调用。

约束不能是值类型，包括内置类型（如 **`int`** 或） **`double`** 。 由于值类型不能有派生类，因此只有一个类可以满足约束。 在这种情况下，可以使用特定值类型替换的类型参数重写泛型。

在某些情况下需要约束，因为编译器不允许使用未知类型的方法或其他功能，除非约束表示未知类型支持这些方法或接口。

可以在逗号分隔列表中指定同一类型参数的多个约束

```cpp
// generics_constraints_2.cpp
// compile with: /c /clr
using namespace System;
using namespace System::Collections::Generic;
generic <typename T>
where T : List<T>, IComparable<T>
ref class List {};
```

对于多个类型参数，请对每个类型参数使用一个 where**** 子句。 例如：

```cpp
// generics_constraints_3.cpp
// compile with: /c /clr
using namespace System;
using namespace System::Collections::Generic;

generic <typename K, typename V>
   where K: IComparable<K>
   where V: IComparable<K>
ref class Dictionary {};
```

总之，请根据下列规则在代码中使用约束：

- 如果列出多个约束，约束可以以任何顺序列出。

- 约束也可以是类类型，例如抽象基类。 但是，约束不能是值类型或封装的类。

- 约束自身不能是类型参数，但它们涉及开放构造类型中的类型参数。 例如：

    ```cpp
    // generics_constraints_4.cpp
    // compile with: /c /clr
    generic <typename T>
    ref class G1 {};

    generic <typename Type1, typename Type2>
    where Type1 : G1<Type2>   // OK, G1 takes one type parameter
    ref class G2{};
    ```

## <a name="examples"></a>示例

以下示例演示如何使用约束调用类型参数的实例方法。

```cpp
// generics_constraints_5.cpp
// compile with: /clr
using namespace System;

interface class IAge {
   int Age();
};

ref class MyClass {
public:
   generic <class ItemType> where ItemType : IAge
   bool isSenior(ItemType item) {
      // Because of the constraint,
      // the Age method can be called on ItemType.
      if (item->Age() >= 65)
         return true;
      else
         return false;
   }
};

ref class Senior : IAge {
public:
   virtual int Age() {
      return 70;
   }
};

ref class Adult: IAge {
public:
   virtual int Age() {
      return 30;
   }
};

int main() {
   MyClass^ ageGuess = gcnew MyClass();
   Adult^ parent = gcnew Adult();
   Senior^ grandfather = gcnew Senior();

   if (ageGuess->isSenior<Adult^>(parent))
      Console::WriteLine("\"parent\" is a senior");
   else
      Console::WriteLine("\"parent\" is not a senior");

   if (ageGuess->isSenior<Senior^>(grandfather))
      Console::WriteLine("\"grandfather\" is a senior");
   else
      Console::WriteLine("\"grandfather\" is not a senior");
}
```

```Output
"parent" is not a senior
"grandfather" is a senior
```

当泛型类型参数用作约束时，称其为裸类型约束。 当包含其自身类型参数的成员函数需要将该参数约束为所含类型的类型参数时，使用裸类型约束会很有用。

在下面的示例中，`T` 是 `Add` 方法上下文中的裸类型约束。

裸类型约束还可用于泛型类定义。 使用泛型类的裸类型约束的作用非常有限，因为编译器只会假设裸类型约束派生自 <xref:System.Object>。 在希望强制两个类型参数之间的继承关系时，可对泛型类使用裸类型约束。

```cpp
// generics_constraints_6.cpp
// compile with: /clr /c
generic <class T>
ref struct List {
   generic <class U>
   where U : T
   void Add(List<U> items)  {}
};

generic <class A, class B, class C>
where A : C
ref struct SampleClass {};
```

## <a name="see-also"></a>请参阅

[泛型](generics-cpp-component-extensions.md)
